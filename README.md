# VéloCast AI — Assistant vélo (PWA + API)
Itinéraires vélo optimisés par **confort-score** : combine OSM/Leaflet, météo temps réel, open data d’accidents, et disponibilité vélos (GBFS). Monorepo : frontend Next.js (TS), backend Express (TS), ETL/ML Python. 100% outils gratuits.
Voir /docs pour la roadmap.## Monorepo
- apps/web : Next.js (TS) PWA + Leaflet
- apps/server : Express (TS) + Prisma (MySQL) + Mongoose (MongoDB)
- ml : Notebooks / entraînement modèle (scikit-learn)
- data : raw/processed pour ETL
