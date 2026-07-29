# 5. Estimation du coût

Tous les montants sont exprimés **hors taxes (HT)**.

## 5.1 Méthodologie

La comptabilité n'étant pas disponible pour ce chiffrage, les rémunérations de référence sont issues des données publiques **Indeed.fr** (salaires moyens observés en France, juillet 2026). Un **Taux Journalier Moyen (TJM) chargé** est calculé ainsi :

> TJM chargé = (salaire brut annuel de référence ÷ 218 jours travaillés/an) × coefficient de charges patronales

Le coefficient retenu est de **1,45** pour les salariés classiques (charges patronales moyennes en France), et de **1,10** pour les alternants (les contrats d'apprentissage bénéficient d'exonérations de charges importantes). Pour les freelances, le TJM de marché (déjà "chargé" par construction) est utilisé directement, dans la limite contractuelle de 5 jours chacun.

## 5.2 Coût des ressources humaines

| Ressource | Profil | Référence salariale annuelle (Indeed.fr) | TJM chargé | Jours mobilisés (cf. Gantt) | Coût total |
|---|---|---|---:|---:|---:|
| Moi-même | Développeur full-stack (pilotage projet) | 45 036 € | 300 € | 90 j | **27 000 €** |
| Lead Developer | Développeur senior (arbitrages ponctuels au retour) | ≈ 50 000 € | 330 € | 10 j | **3 300 €** |
| David | Alternant, front-end (80 %) | 17 244 € | 90 € | 60 j | **5 400 €** |
| Jonathan | Alternant, back-end (80 %) | 17 244 € | 90 € | 56 j | **5 040 €** |
| Jack | UI/UX designer | 46 691 € | 305 € | 12 j | **3 660 €** |
| Rose | UI/UX designer | 46 691 € | 305 € | 12 j | **3 660 €** |
| Omar | Freelance développeur (intégration Stripe) | TJM marché ≈ 530 €/j | 530 € | 5 j (plafond contractuel) | **2 650 €** |
| Fred | Freelance développeur (audit sécurité) | TJM marché ≈ 530 €/j | 530 € | 5 j (plafond contractuel) | **2 650 €** |
| Directeur | Validations, relation client | ≈ 100 884 €/an (directeur de PME, secteur services) | 670 € | 6 j (temps cumulé sur 4 mois) | **4 020 €** |
| **Sous-total ressources humaines** | | | | **257 j** | **57 380 €** |

## 5.3 Coûts techniques (première année)

| Poste | Détail | Coût annuel |
|---|---|---:|
| Noms de domaine | `lasocketterie.fr` + `.com` (défensif) | 35 € |
| Hébergement | Serveur applicatif + base managée + staging, stockage objet + CDN images | 1 450 € |
| Email transactionnel | Brevo (statuts de commande) | 240 € |
| Supervision | Sentry (suivi des erreurs) | 312 € |
| Outillage design | Figma (Jack, Rose, durée du projet) | 120 € |
| Licence police de caractères | Licence commerciale à acquérir pour Stadio Now Display (logo) | 100 € *(one-shot, cf. §1.8)* |
| **Sous-total technique** | | **2 257 €** |

*Non inclus car variable et proportionnel au chiffre d'affaires : la commission Stripe (≈ 1,5 % + 0,25 € par transaction carte européenne).*

## 5.4 Contrat de maintenance (TMA)

| Poste | Détail | Coût annuel |
|---|---|---:|
| Forfait maintenance | 8 h/mois incluses (corrective + sécurité + supervision), au-delà TJM 350 €/j | 3 600 € |

## 5.5 Synthèse

| Poste | Montant HT |
|---|---:|
| Ressources humaines (développement) | 57 380 € |
| Coûts techniques (1ère année) | 2 257 € |
| Contrat de maintenance (1ère année) | 3 600 € |
| **Sous-total** | **63 237 €** |
| Marge pour aléas (10 %, équipe junior à 80 %, délai contraint) | 6 324 € |
| **TOTAL ESTIMÉ (1ère année)** | **≈ 69 600 € HT** |

## 5.6 Sources

- [Salaire développeur full stack (H/F) — Indeed.fr](https://fr.indeed.com/career/d%C3%A9veloppeur-full-stack/salaries)
- [Salaire UI/UX designer (H/F) — Indeed.fr](https://fr.indeed.com/career/ui%2Fux-designer/salaries?hl=fr)
- [Salaire apprenti développeur (H/F) — Indeed.fr](https://fr.indeed.com/career/apprenti-d%C3%A9veloppeur/salaries)
- [TJM freelance développeur fullstack 2026 — FreelanceMention](https://freelancemention.fr/blog/tjm-freelance-developpeur-fullstack/)
- [Salaire chef d'entreprise / directeur de PME — Indeed.fr](https://fr.indeed.com/conseils-carrieres/remuneration-salaire/combien-gagne-chef-entreprise)
