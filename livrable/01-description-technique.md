# 1. Description technique de la solution

## 1.1 Contexte et contraintes de cadrage

La Socketterie est une TPE (boutique physique à Nice, activité de tricot artisanal) qui souhaite un **site vitrine + boutique en ligne**, à destination d'une cible jeune (20-35 ans), en français uniquement, en euros, avec livraison acceptée dans toute l'Union Européenne. Deux échéances contractuelles structurent le projet : le site doit être **présentable** dans 3 mois (tournage TV) et **totalement fonctionnel et testé** avant la diffusion, 1 mois plus tard (soit environ 4 mois / 18 semaines de projet au total).

Compte tenu de ces contraintes (délai court, équipe réduite composée de deux alternants à 80 %, deux freelances plafonnés à 5 jours chacun), l'architecture retenue privilégie des technologies **matures, largement documentées et rapides à mettre en œuvre**, plutôt que des choix expérimentaux.

## 1.2 Choix technologiques

### Architecture générale

Architecture **découplée** (headless) : une API back-end expose les données et la logique métier, consommée par une application front-end. Ce découplage permet à David (front) et Jonathan (back) de travailler en parallèle dès le début du sprint de développement, avec un contrat d'interface (API REST documentée en OpenAPI/Swagger) défini dès la phase de conception.

| Brique | Choix retenu | Justification |
|---|---|---|
| Front-end | **Next.js (React) + TypeScript** | Rendu serveur (SSR) et génération statique (SSG) pour les pages publiques → indispensable pour le **SEO** exigé ; meilleur temps de chargement (moins de JS exécuté côté client) → cohérent avec la démarche d'**éco-conception** ; écosystème React très documenté, facilite l'onboarding de David. |
| Back-end | **Node.js + NestJS + TypeScript** | Même langage que le front (TypeScript) → mutualisation des compétences dans une équipe réduite, montée en compétence plus rapide de Jonathan et bascule front/back facilitée en cas d'absence ; structure imposée par NestJS (modules, injection de dépendances) qui limite les dérives dans un projet à délai serré ; validation des entrées native (`class-validator`) utile pour la sécurité. |
| Base de données | **PostgreSQL** (managée chez l'hébergeur) | Modèle relationnel adapté aux commandes/factures (intégrité, transactions ACID nécessaires pour la comptabilité) ; sauvegardes et réplication gérées par l'hébergeur. |
| ORM | **Prisma** | Migrations versionnées, typage bout-en-bout avec TypeScript, réduit les erreurs de requêtes. |
| Authentification | JWT (access token courte durée) + refresh token en cookie **httpOnly / Secure / SameSite=Strict** | Évite l'exposition du token en `localStorage` (protection XSS) ; gestion de rôles (visiteur connecté, commercial, comptabilité, administrateur) par un système de rôles/permissions (RBAC) au niveau de l'API. |
| Paiement | **Stripe** (Checkout + Payment Intents + Webhooks) | Imposé par le client ; aucune donnée bancaire ne transite ni n'est stockée sur nos serveurs (scope PCI-DSS SAQ A) ; les webhooks Stripe déclenchent les changements de statut de commande et les emails associés. |
| Contenu statique (CGV, mentions légales, À propos, actualités) | Module de gestion de contenu **développé dans le back-office NestJS** (plutôt qu'un CMS tiers séparé) | Évite d'ajouter et de maintenir un second système (coût, sécurité, empreinte serveur supplémentaire non souhaitable en éco-conception) ; suffisant pour le volume de contenu d'une TPE. |
| Emails transactionnels | **Brevo** (ex-Sendinblue, société française, hébergement UE) | Envoi des emails de suivi de commande (confirmation, paiement, expédition, etc.) ; conformité RGPD facilitée (hébergement UE, DPA disponible). |
| Export comptable | Génération **CSV** à la demande depuis le back-office comptabilité | Format demandé pour l'intégration dans le logiciel comptable existant. |

### Pourquoi ne pas partir sur une solution "boîte" (WooCommerce/PrestaShop/Shopify) ?

Ces solutions auraient pu réduire le temps de développement de la boutique de base, mais elles rendent plus coûteuse et plus fragile l'implémentation des workflows métier spécifiques demandés (rôles différenciés commercial/comptabilité/administrateur, export comptable CSV sur mesure, transmission des commandes à la logistique). Le choix décrit ci-dessus reste néanmoins réévaluable en cours de cadrage si le budget venait à se resserrer davantage.

## 1.3 Nom de domaine et hébergement

- **Nom de domaine** : réservation de `lasocketterie.fr` (extension prioritaire pour la confiance d'une clientèle française/UE et le référencement local) et de `lasocketterie.com` à titre défensif (redirection vers le `.fr`). Activation du DNSSEC et du Whois privacy.
- **Hébergement** : hébergeur **basé dans l'Union européenne, engagé sur les énergies renouvelables**, cohérent avec la démarche d'éco-conception et avec le RGPD (résidence des données en UE) — par exemple Scaleway ou Infomaniak.
  - Un environnement **staging** (recette) strictement identique à la production, pour valider chaque livraison avant mise en ligne.
  - Base de données managée avec sauvegardes automatiques quotidiennes (rétention 30 jours) et test de restauration périodique.
  - Stockage des images produits sur un espace objet (S3-compatible) associé à un CDN, pour soulager le serveur applicatif et réduire les temps de chargement (SEO + éco-conception : formats d'image modernes WebP/AVIF, compression, lazy-loading).
  - Certificats TLS via Let's Encrypt (renouvellement automatique), HTTPS forcé sur tout le site.

## 1.4 Services tiers

| Service | Usage | Point d'attention |
|---|---|---|
| Stripe | Paiement carte, gestion des remboursements | Coût variable en % du chiffre d'affaires (cf. estimation des coûts) |
| Brevo | Emails transactionnels (statuts de commande) | Hébergement UE, DPA à signer |
| Matomo (auto-hébergé) | Statistiques d'audience respectueuses de la vie privée | Alternative à Google Analytics : pas de transfert de données hors UE, cohérent RGPD |
| Axeptio ou Tarteaucitron.js | Gestion du consentement aux cookies | Solution française/open-source, conforme CNIL |
| Sentry | Suivi des erreurs applicatives en production | Alerting en cas d'incident |
| GitHub / GitHub Actions | Hébergement du code, intégration et déploiement continus | Voir §1.6 |

## 1.5 Sécurité

- **Transport** : HTTPS obligatoire (redirection automatique), en-têtes de sécurité (CSP, HSTS, X-Content-Type-Options, X-Frame-Options).
- **Authentification** : mots de passe hashés (Argon2), politique de mot de passe minimale, verrouillage/limitation du débit (rate limiting) sur les endpoints de connexion pour limiter le bruteforce.
- **Autorisation** : contrôle d'accès par rôle (RBAC) vérifié côté API à chaque requête (jamais uniquement côté front).
- **Données** : validation systématique des entrées (`class-validator`), requêtes paramétrées via l'ORM (protection injection SQL), échappement des sorties (protection XSS), protection CSRF sur les formulaires sensibles.
- **Paiement** : aucune donnée de carte bancaire ne transite par nos serveurs (Stripe Elements / Checkout hébergé) → réduit fortement le périmètre d'audit PCI-DSS.
- **Secrets** : variables d'environnement séparées par environnement, jamais commitées (`.env` dans `.gitignore`, secrets gérés via le coffre-fort de l'hébergeur/CI).
- **Dépendances** : mise à jour régulière et automatisée (Dependabot/Renovate), audit de vulnérabilités (`npm audit`) intégré à la CI.
- **RGPD** : minimisation des données collectées, durée de conservation définie, parcours d'accès/rectification/suppression des données personnelles depuis le compte client, registre des traitements, DPA signés avec les sous-traitants (Stripe, Brevo, hébergeur).
- **Sauvegardes** : sauvegardes quotidiennes chiffrées, testées périodiquement.

## 1.6 Organisation du suivi et du partage du code

- **Dépôt Git privé** (GitHub) avec protection de la branche `main` (revue obligatoire avant fusion, statut CI vert requis).
- **Workflow simplifié** : branche `main` (production), branche `develop` (recette/staging), branches `feature/xxx` créées depuis `develop` pour chaque user story, fusionnées via *pull request* avec au moins une relecture croisée.
- **Convention de commit** : Conventional Commits (`feat:`, `fix:`, `chore:`...) pour générer un changelog lisible.
- **Intégration et déploiement continus (CI/CD)** via GitHub Actions : lint, tests unitaires, build et audit de sécurité à chaque *pull request* ; déploiement automatique de `develop` sur l'environnement de staging ; déploiement en production déclenché manuellement après validation.
- **Suivi des tâches** : GitHub Projects (Kanban) directement lié aux issues et pull requests du dépôt (cf. §3), pour garder la traçabilité entre une user story, son code et son statut.
- **Documentation** : README technique (installation, variables d'environnement, architecture), documentation d'API générée automatiquement (Swagger), journal des décisions d'architecture (ADR) pour tracer les choix structurants et permettre au Lead Developer de reprendre le contexte à son retour.

## 1.7 Grandes lignes du contrat de maintenance

À l'issue de la mise en production, un contrat de **Tierce Maintenance Applicative (TMA)** est proposé au client, reconductible annuellement :

- **Maintenance corrective** : correction des anomalies bloquantes sous 24h (jour ouvré), anomalies mineures sous 72h.
- **Maintenance préventive/sécurité** : veille et application mensuelle des correctifs de sécurité et mises à jour de dépendances.
- **Maintenance évolutive** : banque d'heures mensuelle (8h/mois incluses dans le forfait) pour des évolutions mineures ; au-delà, devis au TJM en vigueur.
- **Supervision** : monitoring de disponibilité (uptime) et suivi des erreurs applicatives (Sentry), sauvegardes vérifiées.
- **Modalités** : forfait mensuel, engagement 12 mois reconductible tacitement, résiliable avec préavis de 2 mois ; heures non consommées non reportables (ou reportables à hauteur de 30 %, à négocier).

## 1.8 Point de vigilance identifié

La police de caractères utilisée pour le logo (Stadio Now Display) a été trouvée sous forme de **version d'essai** sur un site tiers. Avant toute mise en production, il est nécessaire de vérifier et, le cas échéant, d'acquérir une **licence commerciale** en règle auprès de la fonderie éditrice, faute de quoi l'utilisation du logo/de la police sur un site marchand exposerait le client à un risque juridique. Ce point est budgété en §5 et doit être remonté au directeur dès son retour.

## 1.9 Risques projet

Le directeur de La Socketterie entretient une relation personnelle avec notre directeur (parties de golf régulières, épouses amies d'enfance). Cette proximité est un atout pour la relation commerciale, mais elle représente aussi un **risque de gouvernance de projet** : elle peut faciliter des demandes informelles transmises hors du circuit officiel (directement entre directeurs, en dehors du backlog), avec un risque de dérive du périmètre ou de pression à traiter en urgence une demande non priorisée, au détriment du planning validé.

**Mesure de mitigation** : toute demande du client, quel que soit le canal par lequel elle arrive (y compris directement au directeur), doit être formalisée en user story, ajoutée au backlog et priorisée selon le même processus que les autres demandes avant d'être engagée. Ceci protège à la fois le respect des échéances (tournage / diffusion) et la qualité du livrable, et évite d'exposer la relation personnelle entre les deux directeurs à un différend professionnel.
