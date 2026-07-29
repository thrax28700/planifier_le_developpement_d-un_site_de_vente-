# La Socketterie — Planification du développement du site

Dossier de cadrage et de planification du site vitrine + boutique en ligne de **La Socketterie**, rédigé en tant que développeur full-stack en charge de l'organisation du projet pendant l'absence du Lead Developer.

## Contenu

Le livrable se trouve dans [`livrable/`](livrable/) :

| Fichier | Contenu |
|---|---|
| `01-description-technique.md` | Choix technologiques, domaine/hébergement, services tiers, sécurité, RGPD, organisation Git/CI-CD, contrat de maintenance, risques projet |
| `02-user-stories.md` | Tableau des user stories (MoSCoW, estimation en jours) |
| `03-kanban.md` | Colonnes du tableau Kanban et photo d'exemple |
| `04-gantt.md` | Diagramme de Gantt (Mermaid, en jours ouvrés) et répartition des ressources |
| `05-estimation-couts.md` | Chiffrage détaillé (ressources humaines, technique, maintenance) |
| `livrable-la-socketterie.html` | Version consolidée et mise en forme des cinq sections ci-dessus, imprimable en PDF |

## Organisation Git

- `main` : version validée du livrable
- `develop` : intégration des sections avant validation finale
- `feature/*` : une branche par section du livrable, fusionnée dans `develop` puis dans `main`

Cette organisation reflète celle préconisée pour le futur développement du site (cf. §1.6 de la description technique).
