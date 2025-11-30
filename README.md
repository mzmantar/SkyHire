# 🚀 SkyHire - Plateforme de Recrutement Aéronautique Alimentée par l'IA

<div align="center">

**Révolutionner le Recrutement Aéronautique avec l'Intelligence Artificielle**

[![Node.js](https://img.shields.io/badge/Node.js-20-green.svg)](https://nodejs.org/)
[![Docker](https://img.shields.io/badge/Docker-Compose-2496ED.svg)](https://www.docker.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-7.0-47A248.svg)](https://www.mongodb.com/)
[![Python](https://img.shields.io/badge/Python-3.11-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100-009688.svg)](https://fastapi.tiangolo.com/)
[![Google Gemini](https://img.shields.io/badge/Gemini-2.5_Flash-4285F4.svg)](https://ai.google.dev/)

</div>

## 📋 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Architecture](#-architecture)
- [Technologies](#-technologies)
- [Getting Started](#-getting-started)
- [Project Structure](#-project-structure)
- [Services](#-services)
- [AI Features](#-ai-features)
- [Documentation](#-documentation)
- [Contributing](#-contributing)
- [License](#-license)

## 🌟 Aperçu

**SkyHire** est une plateforme de recrutement complète alimentée par l'IA, spécialement conçue pour l'industrie aéronautique. Elle combine l'intelligence artificielle de pointe, le traitement du langage naturel et la communication en temps réel pour rationaliser le processus d'embauche pour les compagnies aériennes, les entreprises aéronautiques et les candidats au personnel de cabine.

### 🎯 Mission

Transformer le recrutement aéronautique en fournissant une correspondance intelligente, une analyse automatique de CV, des simulations d'entretien alimentées par l'IA et un coaching de carrière personnalisé - le tout dans une plateforme unifiée.

## ✨ Fonctionnalités Clés

### 🤖 Simulateur d'Entretien Alimenté par l'IA
- **Entretien vocal en temps réel** utilisant Google Gemini 2.5 Flash Live API
- Conversation naturelle avec un recruteur IA spécialisé en aéronautique
- Retour instantané sur les compétences en communication, la confiance et la pertinence
- Questions comportementales basées sur des scénarios pour les postes de personnel de cabine
- Audio bidirectionnel avec support audio natif

### 📄 Analyseur de CV Intelligent
- Technologie OCR avancée avec CRAFT et PaddleOCR
- Extraction automatique des informations personnelles, de l'éducation, de l'expérience et des compétences
- NER (Named Entity Recognition) pour l'extraction de données structurées
- Support de plusieurs formats de CV (PDF, images)
- Correspondance intelligente avec les exigences du poste

### 💼 Correspondance d'Emploi Intelligente
- Moteur de recommandation d'emplois alimenté par l'IA
- Algorithme de correspondance basé sur les compétences
- Score de compatibilité pour chaque poste
- Alertes et notifications d'emploi en temps réel
- Système de suivi des candidatures

### 💬 Chatbot Coach de Carrière
- Assistant IA alimenté par Google Gemini
- Conseils de carrière personnalisés pour les professionnels de l'aéronautique
- Conseils et techniques de préparation aux entretiens
- Recommandations d'optimisation de CV
- FAQ sur les carrières du personnel de cabine

### 🔐 Système d'Authentification Complet
- Authentification sécurisée basée sur JWT
- Contrôle d'accès basé sur les rôles (Candidat/Recruteur)
- Gestion et personnalisation du profil
- Intégration de connexion sociale prête

### 📊 Chat et Réseautage en Temps Réel
- Messagerie en temps réel alimentée par Socket.io
- Communication directe entre recruteurs et candidats
- Fonctionnalités de réseautage professionnel
- Conversations de groupe et notifications

### 📈 Analytiques et Tableau de Bord
- Tableau de bord candidat complet
- Suivi de l'état des candidatures
- Métriques de performance des entretiens
- Analytiques recruteur pour les décisions d'embauche

## 🏗️ Architecture

SkyHire suit une architecture moderne de **microservices** avec plusieurs services backend Node.js et Python orchestrés avec Docker Compose.

```
┌─────────────────────────────────────────────────────────────┐
│               Serveurs Frontend (Nginx)                      │
│  ┌──────────────────────┬──────────────────────────────┐   │
│  │  Frontend Principal  │  Serveur d'Entretien Live    │   │
│  │      (Port 80)       │       (Port 81)              │   │
│  └──────────────────────┴──────────────────────────────┘   │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              API Gateway (Port 5000)                         │
│              Routage & Équilibrage de Charge                 │
└────────┬──────────┬──────────┬──────────┬──────────┬────────┘
         │          │          │          │          │
    ┌────▼────┐┌───▼────┐┌───▼────┐┌───▼────┐┌────▼─────┐
    │  Auth   ││  User  ││  Job   ││   CV   ││Interview │
    │ Service ││Service ││Service ││Service ││  Service │
    │  :5001  ││ :5007  ││ :5005  ││ :5003  ││  :5004   │
    └─────────┘└────────┘└────────┘└────────┘└──────────┘
         │          │          │          │          │
    ┌────▼────┐┌───▼────┐┌───▼────┐┌───▼────┐┌────▼─────┐
    │  Chat   ││ Notif. ││CV Parser││Interview││ Chatbot  │
    │ Service ││Service ││ Service ││  Token  ││   API    │
    │  :5002  ││ :5006  ││ :5010   ││  :5008  ││  :8000   │
    └─────────┘└────────┘└────────┘└─────────┘└──────────┘
         │          │          │          │          │
         └──────────┴──────────┴──────────┴──────────┘
                    │
              ┌─────▼─────┐
              │  MongoDB  │
              │   :27017  │
              └───────────┘
```

## 💻 Technologies

### Frontend
- **React** - Bibliothèque UI moderne
- **Nginx** - Serveur web pour production
- **Socket.io Client** - Communication en temps réel
- **Axios** - Client HTTP

### Backend Services
- **Node.js 20** - Environnement d'exécution
- **Express.js** - Framework web
- **MongoDB 7.0** - Base de données NoSQL
- **Socket.io** - Serveur WebSocket
- **JWT** - Authentification sécurisée
- **Mongoose** - ODM pour MongoDB
- **Docker & Docker Compose** - Containerisation

### Services IA & Python
- **Google Gemini 2.5 Flash** - IA audio en direct pour les entretiens
- **Google Gemini Pro** - Chatbot de coaching de carrière
- **FastAPI** - Framework API Python haute performance
- **PaddleOCR** - OCR pour l'analyse de CV
- **CRAFT** - Détection de texte
- **spaCy** - NER pour l'extraction de CV

### DevOps & Outils
- **Docker** - Plateforme de conteneurs
- **Docker Compose** - Orchestration multi-conteneurs
- **Git** - Contrôle de version
- **Nginx** - Serveur web et proxy inverse

## 🚀 Démarrage Rapide

### Prérequis

- **Docker Desktop** installé et en cours d'exécution
- **Git** pour le contrôle de version
- **Clé API Google Gemini** (pour les fonctionnalités IA)

### Installation

1. **Cloner le dépôt**
```bash
git clone https://github.com/mzmantar/SkyHire.git
cd SkyHire
```

2. **Configurer les Variables d'Environnement**

Créez un fichier `.env` à la racine avec les variables suivantes :

```env
# Configuration JWT
JWT_SECRET=votre_secret_jwt_ici
JWT_EXPIRE=7d

# API Google Gemini
GEMINI_API_LIVE_TOKEN=votre_cle_api_gemini_ici
CHATBOT_TOKEN=votre_cle_api_gemini_ici

# Configuration MongoDB
MONGODB_URI=mongodb://mongodb:27017/skyhire

# Environnement
NODE_ENV=production

# Ports des Services
API_GATEWAY_PORT=5000
AUTH_SERVICE_PORT=5001
CHAT_SERVICE_PORT=5002
CV_SERVICE_PORT=5003
INTERVIEW_SERVICE_PORT=5004
JOB_SERVICE_PORT=5005
NOTIFICATIONS_SERVICE_PORT=5006
USER_SERVICE_PORT=5007
INTERVIEW_TOKEN_SERVICE_PORT=5008
CV_PARSER_SERVICE_PORT=5010
FRONT_SERVER_PORT=80
INTERVIEW_SERVER_PORT=81

# Configuration Upload (Service CV)
UPLOAD_PATH=./uploads/cv
MAX_FILE_SIZE=5242880
```

3. **Démarrer tous les Services avec Docker Compose**
```bash
docker-compose up -d
```

Cette commande va :
- Construire toutes les images Docker
- Démarrer tous les microservices
- Créer les réseaux et volumes nécessaires
- Initialiser MongoDB

4. **Vérifier que tous les services sont en cours d'exécution**
```bash
docker-compose ps
```

Vous devriez voir tous les services avec le statut `Up`.

5. **Accéder à l'Application**

- **Frontend Principal** : http://localhost
- **Interface d'Entretien** : http://localhost:81
- **API Gateway** : http://localhost:5000
- **API Chatbot** : http://localhost:8000
- **MongoDB** : mongodb://localhost:27017

## 📁 Structure du Projet

```
skyhire-docker/
├── docker-compose.yml           # Orchestration de tous les services
├── Dockerfile                   # Dockerfile principal (Docker-in-Docker)
├── .env                         # Variables d'environnement (à créer)
├── .gitignore                   # Fichiers Git à ignorer
├── README.md                    # Cette documentation
│
├── api-gateway/                 # API Gateway & routage
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│       └── server.js
│
├── auth-service/                # Authentification & autorisation
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│       ├── server.js
│       ├── config/
│       ├── controllers/
│       ├── middleware/
│       ├── models/
│       └── routes/
│
├── user-service/                # Gestion des profils utilisateurs
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│
├── job-service/                 # Offres d'emploi & candidatures
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│
├── cv-service/                  # Gestion des CV
│   ├── Dockerfile
│   ├── package.json
│   ├── src/
│   └── uploads/
│
├── cv_parser/                   # Service d'analyse de CV (OCR + NER)
│   ├── api/                     # API Node.js
│   │   ├── Dockerfile
│   │   ├── package.json
│   │   └── server.js
│   ├── python-service/          # Service Python FastAPI
│   │   ├── Dockerfile
│   │   └── server.py
│   ├── input/                   # Dossier d'entrée des CV
│   ├── models/                  # Modèles OCR (CRAFT, etc.)
│   └── src/                     # Code source Python
│
├── chat-service/                # Messagerie en temps réel
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│       ├── server.js
│       ├── controllers/
│       ├── models/
│       ├── routes/
│       └── sockets/
│
├── interview-service/           # Sessions d'entretien
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│       ├── server.js
│       ├── controllers/
│       ├── models/
│       ├── routes/
│       └── sockets/
│
├── interviewToken-service/      # Génération de tokens Gemini
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│       ├── app.js
│       └── authgen.js
│
├── chatbot-api/                 # API Chatbot Coach de Carrière
│   ├── Dockerfile
│   ├── main.py                  # FastAPI application
│   ├── requirements.txt
│   ├── cabin_docs.json          # Documentation métier
│   └── README.md
│
├── notifications-service/       # Service de notifications
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│
├── frontend-server/             # Serveur Frontend Principal (Nginx)
│   ├── Dockerfile
│   └── public-html/
│       ├── index.html
│       ├── static/
│       └── skyrecruiter/
│
└── live-interview-server/       # Serveur d'Entretien Live (Nginx)
    ├── Dockerfile
    └── public-html/
        ├── index.html
        └── static/
```

## 🔧 Services

### Services Principaux

| Service | Port | Description | Stack Technique |
|---------|------|-------------|-----------------|
| **Frontend Server** | 80 | Application web principale (Nginx) | Nginx + React |
| **Live Interview Server** | 81 | Interface d'entretien en direct (Nginx) | Nginx + React |
| **API Gateway** | 5000 | Route les requêtes vers les microservices | Express.js |
| **Auth Service** | 5001 | Authentification JWT & autorisation | Express + JWT |
| **User Service** | 5007 | Profils utilisateurs & connexions | Express + MongoDB |
| **Job Service** | 5005 | Offres d'emploi & candidatures | Express + MongoDB |
| **CV Service** | 5003 | Upload & gestion des CV | Express + Multer |
| **CV Parser API** | 5010 | API d'analyse de CV (Node.js) | Express |
| **CV Python Service** | 8000 | Service d'analyse OCR/NER (Python) | FastAPI + PaddleOCR |
| **Chat Service** | 5002 | Messagerie en temps réel | Socket.io |
| **Interview Service** | 5004 | Sessions d'entretien | Express + Socket.io |
| **Interview Token** | 5008 | Génération de tokens Gemini | Express + @google/genai |
| **Chatbot API** | 8000 | API du chatbot coach de carrière | FastAPI + Gemini |
| **Notifications** | 5006 | Notifications push | Express + MongoDB |
| **MongoDB** | 27017 | Base de données | MongoDB 7.0 |

### Services IA

| Service | Description | Modèle IA |
|---------|-------------|-----------|
| **Simulateur d'Entretien** | Entretien vocal IA en temps réel | Gemini 2.5 Flash Live API |
| **Coach de Carrière** | Conseiller de carrière conversationnel | Gemini Pro |
| **Analyseur de CV** | Extraction OCR + NER | CRAFT + PaddleOCR + spaCy |
| **Correspondance d'Emploi** | Recommandations basées sur les compétences | Algorithme ML personnalisé |

## 🤖 Fonctionnalités IA

### 1. Simulateur d'Entretien IA (SkyRecruiter)

Le joyau de SkyHire - un recruteur IA en temps réel alimenté par l'API Google Gemini Live.

**Fonctionnalités :**
- ✅ Conversation vocale naturelle en temps réel
- ✅ Persona de recruteur aéronautique spécialisé
- ✅ Questions comportementales et situationnelles
- ✅ Retour instantané sur la performance
- ✅ Capacités d'enregistrement audio
- ✅ Notation sur la clarté, la confiance et la pertinence

**Technologie :**
- Google Gemini 2.5 Flash avec support audio natif
- WebRTC pour le streaming audio
- Ingénierie de prompt personnalisée pour le contexte aéronautique
- Transcription et analyse en temps réel

**Utilisation :**
```
1. Accédez à http://localhost:81
2. Cliquez sur "Démarrer l'entretien"
3. Autorisez l'accès au microphone
4. Le recruteur IA vous accueillera et commencera à poser des questions
```

### 2. Analyseur de CV avec OCR

Analyse intelligente de CV utilisant des technologies OCR et NER de pointe.

**Capacités :**
- Extraire les informations personnelles (nom, email, téléphone)
- Analyser l'historique éducatif avec dates et diplômes
- Identifier l'expérience professionnelle et les responsabilités
- Extraire les compétences et certifications
- Détection de la maîtrise des langues
- Reconnaissance de mots-clés spécifiques à l'aéronautique

**Stack Technologique :**
- CRAFT pour la détection de texte
- PaddleOCR pour la reconnaissance de texte
- spaCy NER pour l'extraction d'entités
- Entraînement personnalisé sur 500+ CV aéronautiques

### 3. Chatbot Coach de Carrière

Conseiller de carrière alimenté par l'IA utilisant Gemini Pro.

**Fonctionnalités :**
- Conseils de préparation aux entretiens
- Conseils de rédaction de CV
- Recommandations de parcours professionnel
- Conseils de négociation salariale
- Assistance à la recherche d'entreprises
- Perspectives sur l'industrie aéronautique

**Exemples d'Interactions :**
```
Utilisateur : "Comment dois-je me préparer pour un entretien de personnel de cabine ?"
Coach : "Excellente question ! Pour les entretiens de personnel de cabine, concentrez-vous sur..."

Utilisateur : "Quelles compétences sont les plus importantes pour les agents de bord ?"
Coach : "Les principales compétences recherchées par les compagnies aériennes incluent..."
```

### 4. Correspondance d'Emploi Intelligente

Système de recommandation d'emplois basé sur le ML.

**Algorithme :**
- Vectorisation TF-IDF des descriptions de poste et des CV
- Score de similarité cosinus
- Analyse des lacunes en compétences
- Correspondance du niveau d'expérience
- Préférences de localisation et de salaire
- Recommandations de progression de carrière

## 📚 Documentation

### Liens Rapides

- **Frontend Principal :** http://localhost
- **Interface d'Entretien :** http://localhost:81
- **API Gateway :** http://localhost:5000
- **API Chatbot :** http://localhost:8000
- **MongoDB :** mongodb://localhost:27017

### Endpoints API Principaux

- **Vérification de santé API :** `GET http://localhost:5000/api/health`
- **Service de tokens d'entretien :** `GET http://localhost:5008/token`
- **API Chatbot :** `POST http://localhost:8000/chat`

## 🧪 Tests

### Test des Services Backend
```bash
# Vérifier tous les conteneurs en cours d'exécution
docker-compose ps

# Vérifier les logs d'un service spécifique
docker-compose logs -f api-gateway
docker-compose logs -f interview-token-service
docker-compose logs -f chatbot-api

# Tester des services spécifiques
curl http://localhost:5000/api/health
curl http://localhost:5008/token
curl http://localhost:8000/docs  # Documentation FastAPI
```

### Test du Simulateur d'Entretien
```bash
# 1. Démarrer les services backend
docker-compose up -d

# 2. Vérifier que tous les services sont en cours d'exécution
docker-compose ps

# 3. Accéder à http://localhost:81
# 4. Cliquer sur "Démarrer l'entretien" et tester avec votre microphone
```

### Test de l'Analyseur de CV
```bash
# Uploader un CV via l'interface web
# Ou utiliser l'API directement
curl -X POST http://localhost:5010/parse \
  -F "file=@/path/to/cv.pdf"
```

## 🐳 Commandes Docker

```bash
# Démarrer tous les services
docker-compose up -d

# Démarrer avec reconstruction
docker-compose up -d --build

# Voir les logs de tous les services
docker-compose logs -f

# Voir les logs d'un service spécifique
docker-compose logs -f <nom-du-service>
# Exemples:
docker-compose logs -f api-gateway
docker-compose logs -f interview-token-service
docker-compose logs -f chatbot-api

# Arrêter tous les services
docker-compose down

# Arrêter et supprimer les volumes
docker-compose down -v

# Voir les conteneurs en cours d'exécution
docker ps

# Voir tous les conteneurs (y compris arrêtés)
docker ps -a

# Redémarrer un service spécifique
docker-compose restart <nom-du-service>

# Reconstruire un service spécifique
docker-compose build <nom-du-service>

# Voir l'utilisation des ressources
docker stats

# Nettoyer les ressources inutilisées
docker system prune -a
```

## 🔐 Variables d'Environnement

### Fichier .env Principal
```env
# Configuration JWT
JWT_SECRET=votre_cle_secrete_ici
JWT_EXPIRE=7d

# API Google Gemini
GEMINI_API_LIVE_TOKEN=votre_cle_api_gemini
CHATBOT_TOKEN=votre_cle_api_gemini

# MongoDB
MONGODB_URI=mongodb://mongodb:27017/skyhire

# Environnement
NODE_ENV=production

# Ports des Services
API_GATEWAY_PORT=5000
AUTH_SERVICE_PORT=5001
CHAT_SERVICE_PORT=5002
CV_SERVICE_PORT=5003
INTERVIEW_SERVICE_PORT=5004
JOB_SERVICE_PORT=5005
NOTIFICATIONS_SERVICE_PORT=5006
USER_SERVICE_PORT=5007
INTERVIEW_TOKEN_SERVICE_PORT=5008
CV_PARSER_SERVICE_PORT=5010
FRONT_SERVER_PORT=80
INTERVIEW_SERVER_PORT=81

# Configuration Upload
UPLOAD_PATH=./uploads/cv
MAX_FILE_SIZE=5242880
```

### Obtenir une Clé API Gemini

1. Accédez à [Google AI Studio](https://aistudio.google.com/app/apikey)
2. Connectez-vous avec votre compte Google
3. Créez une nouvelle clé API
4. Copiez la clé et ajoutez-la à votre fichier `.env`

## 🐛 Dépannage

### Problème : Les services ne démarrent pas

**Solution :**
```bash
# Vérifier que Docker est en cours d'exécution
docker info

# Redémarrer Docker Desktop
# Puis redémarrer les services
docker-compose down
docker-compose up -d --build
```

### Problème : "Aucun token généré"

**Solution :**
- Vérifiez `GEMINI_API_LIVE_TOKEN` dans `.env`
- Vérifiez les logs du service de tokens : `docker-compose logs interview-token-service`
- Régénérez la clé API sur https://aistudio.google.com/app/apikey
- Redémarrez le service : `docker-compose restart interview-token-service`

### Problème : Échec de connexion à MongoDB

**Solution :**
```bash
# Vérifier que MongoDB est en cours d'exécution
docker-compose ps | findstr mongo

# Redémarrer MongoDB
docker-compose restart mongodb

# Vérifier les logs MongoDB
docker-compose logs mongodb
```

### Problème : Le simulateur d'entretien ne répond pas

**Solution :**
- Autorisez l'accès au microphone dans les paramètres du navigateur
- Utilisez Chrome ou Edge (meilleur support WebRTC)
- Vérifiez la console du navigateur (F12) pour les erreurs
- Vérifiez la génération de token : `curl http://localhost:5008/token`
- Redémarrez le service d'entretien : `docker-compose restart interview-service`

### Problème : Le chatbot ne répond pas

**Solution :**
```bash
# Vérifier les logs du chatbot
docker-compose logs chatbot-api

# Vérifier que la clé API Gemini est correcte
# Tester l'endpoint directement
curl http://localhost:8000/docs
```

### Problème : Port déjà utilisé

**Solution :**
```bash
# Voir les processus utilisant un port spécifique (exemple : 5000)
netstat -ano | findstr :5000

# Arrêter le processus ou changer le port dans .env
# Puis redémarrer les services
docker-compose down
docker-compose up -d
```

### Problème : Erreurs de build Docker

**Solution :**
```bash
# Nettoyer le cache Docker
docker system prune -a

# Reconstruire tout depuis zéro
docker-compose down -v
docker-compose build --no-cache
docker-compose up -d
```

## 🤝 Contribution

Nous accueillons les contributions ! Veuillez suivre ces étapes :

1. Forkez le dépôt
2. Créez une branche de fonctionnalité (`git checkout -b feature/NouvelleFonctionnalite`)
3. Committez vos changements (`git commit -m 'Ajout d'une nouvelle fonctionnalité'`)
4. Poussez vers la branche (`git push origin feature/NouvelleFonctionnalite`)
5. Ouvrez une Pull Request

### Directives de Développement

- Suivez les meilleures pratiques Node.js et Python
- Écrivez des tests pour les nouvelles fonctionnalités
- Mettez à jour la documentation
- Suivez les messages de commit conventionnels
- Assurez-vous que les builds Docker réussissent
- Testez localement avant de pousser

### Configuration Git

```bash
# Configurer votre nom d'utilisateur et email
git config --global user.name "Votre Nom"
git config --global user.email "votre.email@example.com"

# Vérifier la configuration
git config --global --list
```

## 📝 Licence

Ce projet est sous licence MIT. Voir le fichier `LICENSE` pour plus de détails.

## 🙏 Remerciements

- **Google Gemini API** pour fournir des capacités IA de pointe
- **MongoDB** pour la solution de base de données robuste
- **Docker** pour simplifier le déploiement
- **Communauté Open Source** pour les outils et bibliothèques incroyables
- **FastAPI** pour le framework Python haute performance
- **Node.js & Express** pour l'écosystème backend solide

## 📞 Support

Pour toute question ou problème :
- Ouvrez une issue sur GitHub
- Consultez la documentation
- Vérifiez les logs Docker pour les erreurs

## 🚀 Améliorations Futures

- [ ] Authentification OAuth2 (Google, LinkedIn)
- [ ] Analyse avancée et rapports
- [ ] Application mobile (React Native)
- [ ] Support multilingue
- [ ] Intégration avec les ATS (Applicant Tracking Systems)
- [ ] Recommandations de formation personnalisées
- [ ] Intégration de vidéoconférence
- [ ] Tests A/B pour l'optimisation du recrutement

---
