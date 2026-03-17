# Proxy Nginx pour VPS Canada (138.197.140.123)

Proxy Nginx déployé sur Google Cloud Run pour rediriger le trafic TCP vers le VPS au Canada.

## Configuration
- **VPS cible** : `138.197.140.123:443`
- **Port d'écoute du proxy** : `8080`
- **Région VPS** : Canada (physique)
- **Région Cloud Run** : `northamerica-northeast1` (Montréal) – alignée géographiquement
- **Type de proxy** : TCP Stream (Layer 4) avec keepalive
- **Usage** : Tunnel pour Xray/3x-ui (VPN)

## Déploiement
```bash
gcloud run deploy canada-proxy \
  --source . \
  --platform managed \
  --region northamerica-northeast1 \
  --allow-unauthenticated \
  --port 8080 \
  --memory 256Mi \
  --cpu 1 \
  --timeout 3600 \
  --service-account mboka-kitoko@project-35c16924-9301-4126-9f5.iam.gserviceaccount.com
