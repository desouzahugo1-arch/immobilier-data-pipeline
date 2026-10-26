# Pipeline de données immobilières (Data Lake)

Pipeline de data engineering de bout en bout : ingestion de données
immobilières brutes dans MinIO (S3), nettoyage, enrichissement par
machine learning, et génération de catalogues traçables.

## Architecture
Sources brutes (JSON/GeoJSON) -> MinIO raw -> curated -> refined

## Pipeline
1. Ingestion des fichiers bruts dans le bucket `immobilier-raw`
2. Estimation de prix (RandomForest, Scikit-learn)
3. Détection d'anomalies (écart prix réel / estimé > 35 %)
4. Score de qualité des images + inventaire (hash SHA-256)
5. Nettoyage et normalisation des catalogues
6. Conversion GeoJSON -> points géographiques

## Stack
Python, Pandas, NumPy, Scikit-learn, MinIO

## Lancer le projet
docker run -p 9000:9000 -p 9001:9001 minio/minio server /data --console-address ":9001"
pip install -r requirements.txt
jupyter notebook
