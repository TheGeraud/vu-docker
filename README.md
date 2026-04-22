# 🚀 Vue.js App — Dockerized & Deployed on AWS

Application Vue.js 3 containerisée avec Docker et déployée sur AWS EC2 via Amazon ECR.

## 📐 Architecture

GitHub Push
│
▼
GitHub Actions (CI/CD)
│
├─ Build image Docker (multi-stage)
│
├─ Push image → Amazon ECR
│
└─ Deploy → AWS EC2

## 🛠️ Stack technique

| Technologie | Rôle |
|---|---|
| **Vue.js 3** | Framework frontend |
| **Vite** | Build tool |
| **Docker** | Containerisation (multi-stage build) |
| **Nginx** | Serveur web de production |
| **GitHub Actions** | Pipeline CI/CD |
| **Amazon ECR** | Registre d'images Docker |
| **AWS EC2** | Hébergement de l'application |

## 🐳 Lancer en local avec Docker

```bash
# Cloner le repo
git clone https://github.com/TheGeraud/vu-docker.git
cd vu-docker

# Build et lancer avec Docker Compose
docker-compose up --build

# L'app est accessible sur http://localhost:80
```

## ⚙️ Lancer sans Docker (développement)

```bash
# Installer les dépendances
npm install

# Lancer en mode développement
npm run dev

# Build de production
npm run build
```

## 🔄 Pipeline CI/CD

Le pipeline GitHub Actions automatise les étapes suivantes à chaque push sur `main` :

1. Build de l'image Docker (multi-stage : Node.js → Nginx)
2. Authentification à Amazon ECR
3. Push de l'image sur ECR
4. Déploiement sur l'instance EC2

> Les credentials AWS sont stockés dans les **GitHub Secrets** — aucune clé n'est exposée dans le code.

## 📁 Structure du projet

vu-docker/
├── .github/
│   └── workflows/        # Pipeline CI/CD GitHub Actions
├── src/                  # Code source Vue.js
├── public/               # Assets statiques
├── Dockerfile            # Build multi-stage (Node → Nginx)
├── docker-compose.yml    # Orchestration locale
├── nginx.conf            # Configuration Nginx production
└── vite.config.js        # Configuration Vite

## 💡 Ce que j'ai appris

- Mettre en place un **build Docker multi-stage** pour optimiser la taille de l'image
- Configurer un **pipeline CI/CD complet** de GitHub vers AWS
- Utiliser **Amazon ECR** comme registre privé d'images
- Sécuriser les credentials AWS avec les **GitHub Secrets**
- Configurer **Nginx** comme reverse proxy en production

## 🔧 Améliorations futures

- [ ] Ajouter des tests automatisés dans le pipeline
- [ ] Mettre en place un load balancer AWS
- [ ] Ajouter un certificat SSL (HTTPS)
- [ ] Monitorer avec AWS CloudWatch
