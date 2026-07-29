# 4. Diagramme de Gantt

Toutes les durées sont exprimées **en jours ouvrés** (week-ends exclus). Date de démarrage retenue à titre d'exemple : lundi 03/08/2026 (à ajuster selon la date réelle de lancement). Deux jalons contractuels structurent le planning :

- **Jalon M1 — "Site présentable"** : vers le jour ouvré 59 (~12 semaines), avec une marge de sécurité avant la limite des 3 mois fixée par le tournage.
- **Jalon M2 — "Site fonctionnel et testé"** : vers le jour ouvré 87 (~17,5 semaines), avant la limite des 4 mois fixée par la diffusion du reportage, suivi d'une semaine d'hypercare.

```mermaid
gantt
    dateFormat  YYYY-MM-DD
    excludes    weekends
    title       Planning La Socketterie — site vitrine + boutique en ligne

    section Cadrage & conception
    Recueil des besoins & spécifications          :done, spec1, 2026-08-03, 5d
    Architecture technique & choix outillage      :done, spec2, after spec1, 3d
    Rédaction user stories & priorisation          :done, spec3, after spec1, 4d
    Mise en place repo Git / CI-CD / environnements:spec4, after spec2, 3d

    section Conception UX-UI
    Wireframes & parcours utilisateurs             :ux1, after spec3, 5d
    Maquettes graphiques haute-fidélité            :ux2, after ux1, 5d
    Validation des maquettes par le client          :milestone, valid1, after ux2, 0d

    section Développement socle
    Authentification & gestion des rôles           :dev1, after valid1, 5d
    Back-office : structure & CMS interne           :dev2, after dev1, 4d
    Intégration front : gabarits & design system    :dev3, after valid1, 6d
    Pages publiques (A propos, CGV, contact, actus) :dev4, after dev3, 5d
    Compte client (création, profil, historique)    :dev8, after dev1, 6d

    section Boutique
    Catalogue produits & catégories                 :dev5, after dev2, 5d
    Fiche produit, recherche & filtres              :dev6, after dev5, 4d
    Panier                                          :dev7, after dev6, 4d

    section Commande & paiement
    Tunnel de commande & choix livraison            :dev9, after dev7, 4d
    Intégration Stripe (paiement + webhooks)        :crit, freelance1, after dev9, 5d
    Emails transactionnels (statuts de commande)    :dev10, after freelance1, 3d
    Factures & export comptable CSV                 :dev11, after dev10, 3d

    section Jalon tournage
    Recette intermédiaire & correctifs              :m1prep, after dev11, 3d
    Site présentable pour le tournage               :milestone, m1, after m1prep, 0d

    section Back-office métier
    Gestion des commandes (équipe commerciale)      :dev12, after m1, 4d
    Gestion des comptes internes (admin)            :dev13, after dev12, 3d
    Paramétrage catégories & livraisons (admin)     :dev14, after dev13, 2d
    Gestion du contenu statique (admin)             :dev15, after dev14, 3d

    section Sécurité, légal, SEO, éco-conception
    Consentement cookies & droits RGPD              :dev16, after dev15, 2d
    Audit sécurité & durcissement                   :crit, freelance2, after dev16, 4d
    SEO technique & données structurées              :dev17, after dev16, 3d
    Optimisation éco-conception & performance       :dev18, after dev17, 2d

    section Recette & mise en production
    Tests fonctionnels multi-supports (UAT client)  :rec1, after dev18, 4d
    Correction des anomalies                        :rec2, after rec1, 2d
    Formation commercial / comptabilité / admin     :rec3, after rec2, 2d
    Mise en production                              :rec4, after rec3, 1d
    Site fonctionnel avant diffusion                :milestone, m2, after rec4, 0d

    section Hypercare
    Surveillance renforcée post-lancement           :hyper1, after rec4, 5d
```

## Répartition des ressources par lot

| Lot | Ressource principale | Appui |
|---|---|---|
| Cadrage & conception | Moi (full-stack, pilotage) | Directeur (validations à distance) |
| UX/UI | Jack, Rose | Directeur (validation client) |
| Développement socle | Jonathan (back), David (front) | Moi (architecture, revue de code) |
| Boutique | David (front), Jonathan (back) | Moi |
| Commande & paiement | Moi + **Omar (freelance, 5 j max)** sur l'intégration Stripe | Jonathan |
| Back-office métier | Jonathan (back), David (front) | Moi |
| Sécurité / SEO / éco-conception | Moi + **Fred (freelance, 5 j max)** sur l'audit sécurité | Jonathan, David |
| Recette & mise en production | Toute l'équipe | Directeur (recette client / UAT) |
| Hypercare | Moi, Jonathan | — |

Le Lead Developer, absent les 3 premières semaines, est prévu en revue d'architecture et validation ponctuelle à son retour (non représenté comme une ligne dédiée dans le planning ci-dessus, car transverse).
