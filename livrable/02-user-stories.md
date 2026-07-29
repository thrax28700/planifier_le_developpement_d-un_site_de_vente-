# 2. User stories

Priorité selon la méthode MoSCoW : **Must** (indispensable), **Should** (important), **Could** (souhaitable). Estimation en jours-développeur (ordre de grandeur, hors validation/relecture).

## Épopée A — Pages publiques & contenu (visiteur non connecté)

| ID | Rôle | User story | Priorité | Est. (j) |
|---|---|---|---|---|
| A1 | Visiteur | En tant que visiteur, je veux consulter les pages À propos, CGV et Mentions légales afin de connaître l'entreprise et ses conditions. | Must | 2 |
| A2 | Visiteur | En tant que visiteur, je veux consulter les articles d'actualité de la marque afin de suivre sa vie et son actualité. | Should | 3 |
| A3 | Visiteur | En tant que visiteur, je veux utiliser un formulaire de contact afin de poser une question à l'entreprise. | Must | 2 |
| A4 | Visiteur | En tant que visiteur, je veux naviguer sur le site depuis mon mobile, ma tablette ou mon ordinateur afin d'avoir une expérience adaptée à mon support. | Must | 5 |
| A5 | Porteur de projet | En tant que porteur de projet, je veux que le site soit bien référencé sur les moteurs de recherche afin que les visiteurs découvrent la marque. | Must | 4 |

## Épopée B — Boutique / Catalogue

| ID | Rôle | User story | Priorité | Est. (j) |
|---|---|---|---|---|
| B1 | Visiteur | En tant que visiteur, je veux parcourir le catalogue par catégorie afin de trouver facilement un produit. | Must | 5 |
| B2 | Visiteur | En tant que visiteur, je veux consulter la fiche détaillée d'un produit (photos, tailles, prix, description) afin de décider de l'achat. | Must | 4 |
| B3 | Visiteur | En tant que visiteur, je veux rechercher un produit par mot-clé afin de gagner du temps. | Should | 3 |
| B4 | Visiteur | En tant que visiteur, je veux filtrer les produits par taille, couleur ou prix afin d'affiner ma recherche. | Should | 3 |

## Épopée C — Panier & commande

| ID | Rôle | User story | Priorité | Est. (j) |
|---|---|---|---|---|
| C1 | Visiteur | En tant que visiteur, je veux ajouter un ou plusieurs articles à mon panier afin de préparer ma commande. | Must | 3 |
| C2 | Visiteur | En tant que visiteur, je veux modifier les quantités ou retirer un article de mon panier afin d'ajuster ma commande. | Must | 2 |
| C3 | Visiteur | En tant que visiteur, je veux voir le récapitulatif de mon panier (sous-total, livraison, total) afin de connaître le montant exact à payer. | Must | 2 |
| C4 | Visiteur | En tant que visiteur, je dois créer un compte ou me connecter afin de pouvoir valider ma commande. | Must | 3 |
| C5 | Client connecté | En tant que client connecté, je veux choisir un mode de livraison parmi ceux proposés afin d'adapter la livraison à mes besoins. | Must | 2 |
| C6 | Client connecté | En tant que client connecté, je veux payer ma commande par carte bancaire via Stripe afin de la finaliser en toute sécurité. | Must | 5 |
| C7 | Client connecté (UE) | En tant que client résidant dans l'Union européenne, je veux pouvoir commander où que je sois en UE afin d'accéder à la boutique depuis mon pays. | Must | 3 |

## Épopée D — Compte client

| ID | Rôle | User story | Priorité | Est. (j) |
|---|---|---|---|---|
| D1 | Visiteur | En tant que visiteur, je veux créer un compte avec mon email et un mot de passe afin d'accéder aux fonctionnalités réservées aux clients. | Must | 3 |
| D2 | Client connecté | En tant que client connecté, je veux modifier mes informations personnelles (adresse, email, mot de passe) afin de les maintenir à jour. | Must | 2 |
| D3 | Client connecté | En tant que client connecté, je veux consulter l'historique de mes commandes afin de suivre mes achats passés. | Must | 3 |
| D4 | Client connecté | En tant que client connecté, je veux télécharger mes factures afin de les conserver. | Must | 2 |
| D5 | Client | En tant que client, je veux réinitialiser mon mot de passe en cas d'oubli afin de retrouver l'accès à mon compte. | Must | 2 |

## Épopée E — Notifications

| ID | Rôle | User story | Priorité | Est. (j) |
|---|---|---|---|---|
| E1 | Client | En tant que client, je veux recevoir un email à chaque changement de statut de ma commande (validée, payée, en préparation, expédiée) afin de suivre son avancement. | Must | 3 |

## Épopée F — Back-office Équipe commerciale

| ID | Rôle | User story | Priorité | Est. (j) |
|---|---|---|---|---|
| F1 | Équipe commerciale | En tant que membre de l'équipe commerciale, je veux créer, modifier et publier un article de la boutique afin de tenir le catalogue à jour. | Must | 5 |
| F2 | Équipe commerciale | En tant que membre de l'équipe commerciale, je veux consulter la liste des commandes et leur statut afin de suivre l'activité de la boutique. | Must | 3 |
| F3 | Équipe commerciale | En tant que membre de l'équipe commerciale, je veux éditer les informations d'une commande validée afin de les transmettre à la logistique pour colisage et étiquetage. | Must | 3 |
| F4 | Équipe commerciale | En tant que membre de l'équipe commerciale, je veux marquer une commande comme expédiée une fois informé par la logistique afin de déclencher l'email de suivi au client. | Must | 2 |
| F5 | Équipe commerciale | En tant que membre de l'équipe commerciale, je veux consulter et gérer la fiche d'un client afin de répondre à ses demandes. | Should | 3 |

## Épopée G — Back-office Comptabilité

| ID | Rôle | User story | Priorité | Est. (j) |
|---|---|---|---|---|
| G1 | Comptabilité | En tant que membre de la comptabilité, je veux consulter la liste des commandes et factures afin de suivre l'activité financière. | Must | 2 |
| G2 | Comptabilité | En tant que membre de la comptabilité, je veux modifier une facture afin de corriger une erreur avant export. | Should | 2 |
| G3 | Comptabilité | En tant que membre de la comptabilité, je veux exporter les commandes/factures au format CSV sur une période donnée afin de les intégrer dans le logiciel comptable. | Must | 3 |

## Épopée H — Administrateur

| ID | Rôle | User story | Priorité | Est. (j) |
|---|---|---|---|---|
| H1 | Administrateur | En tant qu'administrateur, je veux créer, modifier et désactiver les comptes internes (commercial, comptabilité) afin de gérer les accès au back-office. | Must | 3 |
| H2 | Administrateur | En tant qu'administrateur, je veux paramétrer les catégories de produits afin d'organiser le catalogue. | Must | 2 |
| H3 | Administrateur | En tant qu'administrateur, je veux paramétrer les modes de livraison disponibles (transporteurs, tarifs, zones UE) afin d'adapter l'offre logistique. | Must | 3 |
| H4 | Administrateur | En tant qu'administrateur, je veux gérer les paramètres techniques du site (SEO, informations société) afin de garder le site conforme et à jour. | Must | 3 |
| H5 | Administrateur | En tant qu'administrateur, je veux gérer le contenu des pages statiques et des articles d'actualité afin de garder le site vitrine à jour sans intervention développeur. | Must | 4 |
| H6 | Administrateur | En tant qu'administrateur, je veux disposer de toutes les fonctionnalités commerciales et comptables afin de superviser le fonctionnement global du site. | Must | 2 |

## Épopée I — Sécurité, légal, RGPD

| ID | Rôle | User story | Priorité | Est. (j) |
|---|---|---|---|---|
| I1 | Visiteur | En tant que visiteur, je veux être informé et donner mon consentement sur l'usage des cookies afin que mes droits soient respectés (RGPD/CNIL). | Must | 2 |
| I2 | Client | En tant que client, je veux pouvoir demander l'accès, la rectification ou la suppression de mes données personnelles afin d'exercer mes droits RGPD. | Must | 3 |
| I3 | Administrateur | En tant qu'administrateur, je veux que les mots de passe et données sensibles soient protégés (hash, HTTPS, sauvegardes) afin de garantir la sécurité des comptes. | Must | 3 |

## Épopée J — Technique, SEO, performance, éco-conception

| ID | Rôle | User story | Priorité | Est. (j) |
|---|---|---|---|---|
| J1 | Porteur de projet | En tant que porteur de projet, je veux que chaque page publique soit optimisée pour le référencement (balises, sitemap, données structurées) afin d'améliorer la visibilité du site. | Must | 4 |
| J2 | Porteur de projet | En tant que porteur de projet, je veux que le site respecte les principes d'éco-conception (poids des pages, images optimisées, sobriété du design) afin de limiter son empreinte environnementale. | Should | 3 |
| J3 | Porteur de projet | En tant que porteur de projet, je veux que le site soit testé sur les principaux navigateurs et tailles d'écran afin de garantir une expérience homogène. | Must | 3 |

**Total des user stories : 39 — Effort brut cumulé : ≈ 108 jours-développeur** (ce total sert de base à la répartition des tâches du diagramme de Gantt, réparti entre plusieurs ressources en parallèle — cf. §4).
