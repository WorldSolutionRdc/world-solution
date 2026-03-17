# Proxy Nginx pour VPS Frankfurt (167.99.247.4)

Proxy Nginx déployé sur Google Cloud Run pour rediriger le trafic TCP vers le VPS à Frankfurt.

## Configuration
- **VPS cible** : `167.99.247.4:443`
- **Port d'écoute du proxy** : `8080`
- **Région VPS** : Frankfurt (Allemagne)
- **Région Cloud Run** : `europe-west3` (Frankfurt) – alignée géographiquement
- **Type de proxy** : TCP Stream (Layer 4) avec keepalive
- **Usage** : Tunnel pour Xray/3x-ui (VPN)

## Déploiement
```bash
gcloud run deploy frankfurt-proxy \
  --source . \
  --platform managed \
  --region europe-west3 \
  --allow-unauthenticated \
  --port 8080 \
  --memory 256Mi \
  --cpu 1 \
  --timeout 3600 \
  --service-account mboka-kitoko@project-35c16924-9301-4126-9f5.iam.gserviceaccount.com
