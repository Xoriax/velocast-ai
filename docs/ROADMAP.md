# ROADMAP — VéloCast AI

VéloCast AI est une PWA et une API qui calculent des itinéraires vélo optimisés par un **confort-score** (sécurité/confort) en combinant OSM/Leaflet, météo temps réel, open data d’accidents, et disponibilité des vélos (GBFS).

## Objectifs
- Démontrer des compétences **full-stack** (Next.js + Express), **data/ETL**, et **ML**.
- Code public, licence **Non-Commercial**.
- Stack 100% **outils gratuits**.

## Périmètre (v1)
- **Front (PWA)** : Next.js (TS), Tailwind, Leaflet, manifest/service worker.
- **API** : Express (TS), validation Zod, endpoints: `/routes`, `/score`, `/weather`, `/gbfs`, `/admin`.
- **DB** : MySQL (Prisma) pour référentiels; MongoDB (Mongoose) pour séries temporelles (météo/GBFS).
- **Data/ETL** : ingestion OSM (extraits), météo (fournisseur gratuit), accidents (open data), GBFS.
- **Scoring v1** : rule-based combinant segments OSM + météo + historique incidents.
- **Tests/CI** : Vitest/Jest, ESLint/Prettier, GitHub Actions (lint, test, build).
- **Docs & Demo** : README, Roadmap, guides d’installation, exemples d’appels d’API.

## Hors périmètre (v1)
- Authentification avancée, multi-tenants, ML deep learning (prévu v2).

---

## Phases & Deliverables

### Phase B — Front PWA (Next.js + Tailwind + Leaflet)
**Deliverables**
- Scaffold Next.js (apps/web), PWA (manifest + SW), base Leaflet (carte, tuile OSM).
- Page `Itinéraire` avec saisie départ/arrivée, affichage du tracé (mock API).
**Issues clés**
- #<à compléter> Scaffold Next.js
- #<à compléter> Tailwind + design tokens
- #<à compléter> PWA (manifest + service worker)
- #<à compléter> Carte Leaflet + géoloc
**Critères d’acceptation**
- Build prod OK, PWA installable, carte visible et fonctionnelle.

### Phase C — Backend API (Express + Zod)
**Deliverables**
- Scaffold Express (apps/server), routes `/health`, `/routes`, `/score`, `/weather`, `/gbfs`.
- Validation Zod, gestion erreurs, logs, CORS, rate limit (basique).
**Issues clés**
- #<à compléter> Scaffold Express + Zod
- #<à compléter> Routing & error middleware
- #<à compléter> Rate limit + CORS
**Critères**
- Tests unitaires OK, OpenAPI (YAML) minimal.

### Phase D — DB & ORM (Prisma + MySQL / Mongoose + MongoDB)
**Deliverables**
- Schéma Prisma (référentiel segments, points d’intérêt), migrations.
- Schéma Mongoose (observations temps réel GBFS, météo).
**Issues clés**
- #<à compléter> Prisma schema + migrations
- #<à compléter> Mongoose models (time-series)
**Critères**
- Migrations OK, connexions DB paramétrées via `.env`.

### Phase E — Data & ETL
**Deliverables**
- Scripts ingestion (Python/Node) : OSM extrait, météo (API gratuite), accidents (open data), GBFS.
- Planification simple (npm script/cron local).
**Issues clés**
- #<à compléter> ETL OSM (extrait)
- #<à compléter> ETL météo
- #<à compléter> ETL accidents
- #<à compléter> ETL GBFS
**Critères**
- Données persistées, logs d’exécution, volumes maîtrisés.

### Phase F — Scoring & ML v1
**Deliverables**
- Score rule-based (pondérations réglables).
- Notebook ML (baseline) pour recalibrer pondérations (si données suffisantes).
**Issues clés**
- #<à compléter> Implémentation score v1
- #<à compléter> Notebook baseline (ml/)
**Critères**
- Score calculé en < 300 ms pour un itinéraire urbain moyen.

### Phase G — QA, Tests, Perf, Sécu
**Deliverables**
- Tests intégration front/back, Lighthouse ≥ 85, sécurité basique (headers, input validation).
**Issues clés**
- #<à compléter> Tests intégration
- #<à compléter> Optim perf front (Lighthouse)
**Critères**
- Pipeline CI vert, score Lighthouse OK.

### Phase H — Release & Docs
**Deliverables**
- Scripts `pnpm` unifiés, guide d’installation, changelog, version `v1.0.0`.
**Issues clés**
- #<à compléter> Release notes
- #<à compléter> README final
**Critères**
- Tag `v1.0.0`, demo fonctionnelle.

---

## Gestion de projet

**Labels**
- `type:*` (feature, bug, docs, data/etl, ml, infra)  
- `area:*` (web, api, db)  
- `priority:*` (urgent, high, normal)

**Priorisation**
- `Urgent > High > Normal`, et `Size` (1,2,3,5,8) pour la complexité.

**Définition de Done (DoD)**
- Code mergé en `main`, tests passants, docs mises à jour, CI verte.

**Risques / Mitigations**
- Quotas API météo/GBFS → cache local, backoff.
- Qualité des données accidents → validation et outliers.
- Perf routing → limiter la zone, pagination segments.

**Non-objectifs (v1)**
- Monétisation, comptes utilisateurs, backoffice complet.

---

## Liens utiles
- `.env.example`
- OpenAPI (à venir)
- Board : GitHub Project “VéloCast AI — Delivery Board”