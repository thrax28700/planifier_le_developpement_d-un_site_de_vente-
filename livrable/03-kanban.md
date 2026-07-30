# 3. Kanban

## Outil retenu

**GitHub Projects**, directement lié au dépôt de code (chaque carte peut être reliée à une issue et à une pull request), ce qui évite de dupliquer le suivi dans un outil déconnecté du code (cf. §1.6). Alternative équivalente possible : Trello.

**Lien vers la version en ligne** : https://github.com/users/thrax28700/projects/3 (tableau public, lié au dépôt du projet)

À la création du tableau (fin de cadrage), les 42 user stories du §2 y ont été importées sous forme de cartes, toutes placées dans la colonne **Backlog** puisqu'aucun développement n'a encore démarré. La répartition ci-dessous (§"Photo du tableau") est un exemple illustratif de ce à quoi ressemblera le tableau une fois le développement engagé, pas l'état actuel.

## Colonnes

| Colonne | Définition de "prêt à passer à l'étape suivante" |
|---|---|
| **Backlog** | User story rédigée, priorisée, non encore estimée en détail |
| **À faire (sprint)** | User story estimée et affectée à une ressource pour le sprint en cours |
| **En cours** | Développement en cours |
| **En revue / Tests** | Pull request ouverte : relecture de code + tests fonctionnels en recette |
| **Terminé** | Fusionnée sur `develop`, validée en recette, déployable |

## Photo du tableau (exemple à mi-parcours, fin de semaine 6)

| Backlog | À faire (sprint) | En cours | En revue / Tests | Terminé |
|---|---|---|---|---|
| G3 — Export CSV comptabilité | C6 — Paiement Stripe | B1 — Catalogue par catégorie | D1 — Création de compte | A1 — Pages À propos / CGV / Mentions légales |
| H3 — Modes de livraison | C1 — Ajout au panier | F1 — Gestion des articles (back-office) | A3 — Formulaire de contact | Maquettes UI (Jack/Rose) |
| I2 — Droits RGPD (accès/suppression) | B2 — Fiche produit | J1 — SEO technique (sitemap, balises) | | Socle technique (repo, CI/CD, environnements) |
| H5 — Contenu statique / actualités | D3 — Historique commandes | | | Charte graphique validée |
| J2 — Éco-conception (images, poids pages) | | | | Authentification (squelette API) |

*Cette capture illustre l'usage attendu du tableau ; le tableau réel évolue quotidiennement et doit être consulté en ligne pour un état à jour.*
