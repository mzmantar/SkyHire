# SkyHire - AI-Powered Aviation Recruitment Platform

<div align="center">

**Revolutionizing Aviation Recruitment with Artificial Intelligence**

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

## 🌟 Overview

**SkyHire** is a comprehensive AI-powered recruitment platform specifically designed for the aviation industry. It combines cutting-edge artificial intelligence, natural language processing, and real-time communication to streamline the hiring process for airlines, aviation companies, and cabin crew candidates.

### 🎯 Mission

Transform aviation recruitment by providing intelligent matching, automated CV analysis, AI-powered interview simulations, and personalized career coaching - all in a unified platform.

## ✨ Key Features

### 🤖 AI-Powered Interview Simulator
- **Real-time voice interview** using Google Gemini 2.5 Flash Live API
- Natural conversation with an aviation-specialized AI recruiter
- Instant feedback on communication skills, confidence, and relevance
- Behavioral questions based on scenarios for cabin crew positions
- Bidirectional audio with native audio support

### 📄 Intelligent CV Analyzer
- Advanced OCR technology with CRAFT and PaddleOCR
- Automatic extraction of personal information, education, experience, and skills
- NER (Named Entity Recognition) for structured data extraction
- Support for multiple CV formats (PDF, images)
- Intelligent matching with job requirements

### 💼 Smart Job Matching
- AI-powered job recommendation engine
- Skill-based matching algorithm
- Compatibility score for each position
- Real-time job alerts and notifications
- Application tracking system

### 💬 Career Coach Chatbot
- AI assistant powered by Google Gemini
- Personalized career advice for aviation professionals
- Interview preparation tips and techniques
- CV optimization recommendations
- Cabin crew career FAQ

### 🔐 Complete Authentication System
- Secure JWT-based authentication
- Role-based access control (Candidate/Recruiter)
- Profile management and customization
- Ready social login integration

### 📊 Real-time Chat and Networking
- Real-time messaging powered by Socket.io
- Direct communication between recruiters and candidates
- Professional networking features
- Group conversations and notifications

### 📈 Analytics and Dashboard
- Comprehensive candidate dashboard
- Application status tracking
- Interview performance metrics
- Recruiter analytics for hiring decisions

## 🏗️ Architecture

SkyHire follows a modern **microservices architecture** with multiple Node.js and Python backend services orchestrated with Docker Compose.

```
┌─────────────────────────────────────────────────────────────┐
│               Frontend Servers (Nginx)                      │
│  ┌──────────────────────┬──────────────────────────────┐   │
│  │   Main Frontend      │    Live Interview Server     │   │
│  │      (Port 80)       │         (Port 81)            │   │
│  └──────────────────────┴──────────────────────────────┘   │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              API Gateway (Port 5000)                        │
│              Routing & Load Balancing                       │
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
- **React** - Modern UI library
- **Nginx** - Production web server
- **Socket.io Client** - Real-time communication
- **Axios** - HTTP client

### Backend Services
- **Node.js 20** - Runtime environment
- **Express.js** - Web framework
- **MongoDB 7.0** - NoSQL database
- **Socket.io** - WebSocket server
- **JWT** - Secure authentication
- **Mongoose** - MongoDB ODM
- **Docker & Docker Compose** - Containerization

### AI & Python Services
- **Google Gemini 2.5 Flash** - Live AI audio for interviews
- **Google Gemini Pro** - Career coaching chatbot
- **FastAPI** - High-performance Python API framework
- **PaddleOCR** - OCR for CV analysis
- **CRAFT** - Text detection
- **spaCy** - NER for CV extraction

### DevOps & Tools
- **Docker** - Container platform
- **Docker Compose** - Multi-container orchestration
- **Git** - Version control
- **Nginx** - Web server and reverse proxy

## 🚀 Quick Start

### Prerequisites

- **Docker Desktop** installed and running
- **Git** for version control
- **Google Gemini API Key** (for AI features)

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/mzmantar/SkyHire.git
cd SkyHire
```

2. **Configure Environment Variables**

Create a `.env` file at the root with the following variables:

```env
# JWT Configuration
JWT_SECRET=your_jwt_secret_here
JWT_EXPIRE=7d

# Google Gemini API
GEMINI_API_LIVE_TOKEN=your_gemini_api_key_here
CHATBOT_TOKEN=your_gemini_api_key_here

# MongoDB Configuration
MONGODB_URI=mongodb://mongodb:27017/skyhire

# Environment
NODE_ENV=production

# Service Ports
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

# Upload Configuration (CV Service)
UPLOAD_PATH=./uploads/cv
MAX_FILE_SIZE=5242880
```

3. **Start All Services with Docker Compose**
```bash
docker-compose up -d
```

This command will:
- Build all Docker images
- Start all microservices
- Create necessary networks and volumes
- Initialize MongoDB

4. **Verify All Services Are Running**
```bash
docker-compose ps
```

You should see all services with status `Up`.

5. **Access the Application**

- **Main Frontend**: http://localhost
- **Interview Interface**: http://localhost:81
- **API Gateway**: http://localhost:5000
- **Chatbot API**: http://localhost:8000
- **MongoDB**: mongodb://localhost:27017

## 📁 Project Structure

```
skyhire-docker/
├── docker-compose.yml           # All services orchestration
├── Dockerfile                   # Main Dockerfile (Docker-in-Docker)
├── .env                         # Environment variables (to create)
├── .gitignore                   # Git ignored files
├── README.md                    # This documentation
│
├── api-gateway/                 # API Gateway & routing
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│       └── server.js
│
├── auth-service/                # Authentication & authorization
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
├── user-service/                # User profile management
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│
├── job-service/                 # Job listings & applications
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│
├── cv-service/                  # CV management
│   ├── Dockerfile
│   ├── package.json
│   ├── src/
│   └── uploads/
│
├── cv_parser/                   # CV parsing service (OCR + NER)
│   ├── api/                     # Node.js API
│   │   ├── Dockerfile
│   │   ├── package.json
│   │   └── server.js
│   ├── python-service/          # Python FastAPI service
│   │   ├── Dockerfile
│   │   └── server.py
│   ├── input/                   # CV input folder
│   ├── models/                  # OCR models (CRAFT, etc.)
│   └── src/                     # Python source code
│
├── chat-service/                # Real-time messaging
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│       ├── server.js
│       ├── controllers/
│       ├── models/
│       ├── routes/
│       └── sockets/
│
├── interview-service/           # Interview sessions
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│       ├── server.js
│       ├── controllers/
│       ├── models/
│       ├── routes/
│       └── sockets/
│
├── interviewToken-service/      # Gemini token generation
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│       ├── app.js
│       └── authgen.js
│
├── chatbot-api/                 # Career Coach Chatbot API
│   ├── Dockerfile
│   ├── main.py                  # FastAPI application
│   ├── requirements.txt
│   ├── cabin_docs.json          # Business documentation
│   └── README.md
│
├── notifications-service/       # Notification service
│   ├── Dockerfile
│   ├── package.json
│   └── src/
│
├── frontend-server/             # Main Frontend Server (Nginx)
│   ├── Dockerfile
│   └── public-html/
│       ├── index.html
│       ├── static/
│       └── skyrecruiter/
│
└── live-interview-server/       # Live Interview Server (Nginx)
    ├── Dockerfile
    └── public-html/
        ├── index.html
        └── static/
```

## 🔧 Services

### Main Services

| Service | Port | Description | Tech Stack |
|---------|------|-------------|-----------------|
| **Frontend Server** | 80 | Main web application (Nginx) | Nginx + React |
| **Live Interview Server** | 81 | Live interview interface (Nginx) | Nginx + React |
| **API Gateway** | 5000 | Routes requests to microservices | Express.js |
| **Auth Service** | 5001 | JWT authentication & authorization | Express + JWT |
| **User Service** | 5007 | User profiles & connections | Express + MongoDB |
| **Job Service** | 5005 | Job listings & applications | Express + MongoDB |
| **CV Service** | 5003 | CV upload & management | Express + Multer |
| **CV Parser API** | 5010 | CV parsing API (Node.js) | Express |
| **CV Python Service** | 8000 | OCR/NER parsing service (Python) | FastAPI + PaddleOCR |
| **Chat Service** | 5002 | Real-time messaging | Socket.io |
| **Interview Service** | 5004 | Interview sessions | Express + Socket.io |
| **Interview Token** | 5008 | Gemini token generation | Express + @google/genai |
| **Chatbot API** | 8000 | Career coach chatbot API | FastAPI + Gemini |
| **Notifications** | 5006 | Push notifications | Express + MongoDB |
| **MongoDB** | 27017 | Database | MongoDB 7.0 |

### AI Services

| Service | Description | AI Model |
|---------|-------------|-----------|
| **Interview Simulator** | Real-time voice AI interview | Gemini 2.5 Flash Live API |
| **Career Coach** | Conversational career advisor | Gemini Pro |
| **CV Analyzer** | OCR + NER extraction | CRAFT + PaddleOCR + spaCy |
| **Job Matching** | Skill-based recommendations | Custom ML algorithm |

## 🤖 AI Features

### 1. AI Interview Simulator (SkyRecruiter)

The crown jewel of SkyHire - a real-time AI recruiter powered by Google Gemini Live API.

**Features:**
- Natural real-time voice conversation
- Specialized aviation recruiter persona
- Behavioral and situational questions
- Instant performance feedback
- Audio recording capabilities
- Scoring on clarity, confidence, and relevance

**Technology:**
- Google Gemini 2.5 Flash with native audio support
- WebRTC for audio streaming
- Custom prompt engineering for aviation context
- Real-time transcription and analysis

**Usage:**
```
1. Navigate to http://localhost:81
2. Click "Start Interview"
3. Allow microphone access
4. The AI recruiter will greet you and begin asking questions
```

### 2. CV Analyzer with OCR

Intelligent CV analysis using state-of-the-art OCR and NER technologies.

**Capabilities:**
- Extract personal information (name, email, phone)
- Analyze educational history with dates and degrees
- Identify professional experience and responsibilities
- Extract skills and certifications
- Language proficiency detection
- Aviation-specific keyword recognition

**Tech Stack:**
- CRAFT for text detection
- PaddleOCR for text recognition
- spaCy NER for entity extraction
- Custom training on 500+ aviation CVs

### 3. Career Coach Chatbot

AI-powered career advisor using Gemini Pro.

**Features:**
- Interview preparation advice
- CV writing guidance
- Career path recommendations
- Salary negotiation tips
- Company research assistance
- Aviation industry insights

**Example Interactions:**
```
User: "How should I prepare for a cabin crew interview?"
Coach: "Great question! For cabin crew interviews, focus on..."

User: "What skills are most important for flight attendants?"
Coach: "The top skills airlines look for include..."
```

### 4. Smart Job Matching

ML-based job recommendation system.

**Algorithm:**
- TF-IDF vectorization of job descriptions and CVs
- Cosine similarity scoring
- Skills gap analysis
- Experience level matching
- Location and salary preferences
- Career progression recommendations

## 📚 Documentation

### Quick Links

- **Main Frontend:** http://localhost
- **Interview Interface:** http://localhost:81
- **API Gateway:** http://localhost:5000
- **Chatbot API:** http://localhost:8000
- **MongoDB:** mongodb://localhost:27017

### Main API Endpoints

- **API Health Check:** `GET http://localhost:5000/api/health`
- **Interview Token Service:** `GET http://localhost:5008/token`
- **Chatbot API:** `POST http://localhost:8000/chat`

## 🧪 Testing

### Backend Services Testing
```bash
# Check all running containers
docker-compose ps

# Check logs for specific service
docker-compose logs -f api-gateway
docker-compose logs -f interview-token-service
docker-compose logs -f chatbot-api

# Test specific services
curl http://localhost:5000/api/health
curl http://localhost:5008/token
curl http://localhost:8000/docs  # FastAPI documentation
```

### Interview Simulator Testing
```bash
# 1. Start backend services
docker-compose up -d

# 2. Verify all services are running
docker-compose ps

# 3. Access http://localhost:81
# 4. Click "Start Interview" and test with your microphone
```

### CV Analyzer Testing
```bash
# Upload a CV via web interface
# Or use API directly
curl -X POST http://localhost:5010/parse \
  -F "file=@/path/to/cv.pdf"
```

## 🐳 Docker Commands

```bash
# Start all services
docker-compose up -d

# Start with rebuild
docker-compose up -d --build

# View logs for all services
docker-compose logs -f

# View logs for specific service
docker-compose logs -f <service-name>
# Examples:
docker-compose logs -f api-gateway
docker-compose logs -f interview-token-service
docker-compose logs -f chatbot-api

# Stop all services
docker-compose down

# Stop and remove volumes
docker-compose down -v

# View running containers
docker ps

# View all containers (including stopped)
docker ps -a

# Restart specific service
docker-compose restart <service-name>

# Rebuild specific service
docker-compose build <service-name>

# View resource usage
docker stats

# Clean up unused resources
docker system prune -a
```

## 🔐 Environment Variables

### Main .env File
```env
# JWT Configuration
JWT_SECRET=your_secret_key_here
JWT_EXPIRE=7d

# Google Gemini API
GEMINI_API_LIVE_TOKEN=your_gemini_api_key
CHATBOT_TOKEN=your_gemini_api_key

# MongoDB
MONGODB_URI=mongodb://mongodb:27017/skyhire

# Environment
NODE_ENV=production

# Service Ports
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

# Upload Configuration
UPLOAD_PATH=./uploads/cv
MAX_FILE_SIZE=5242880
```

### Getting Gemini API Key

1. Go to [Google AI Studio](https://aistudio.google.com/app/apikey)
2. Sign in with your Google account
3. Create a new API key
4. Copy the key and add it to your `.env` file

## 🐛 Troubleshooting

### Issue: Services won't start

**Solution:**
```bash
# Verify Docker is running
docker info

# Restart Docker Desktop
# Then restart services
docker-compose down
docker-compose up -d --build
```

### Issue: "No token generated"

**Solution:**
- Check `GEMINI_API_LIVE_TOKEN` in `.env`
- Check token service logs: `docker-compose logs interview-token-service`
- Regenerate API key at https://aistudio.google.com/app/apikey
- Restart service: `docker-compose restart interview-token-service`

### Issue: MongoDB connection failed

**Solution:**
```bash
# Check if MongoDB is running
docker-compose ps | findstr mongo

# Restart MongoDB
docker-compose restart mongodb

# Check MongoDB logs
docker-compose logs mongodb
```

### Issue: Interview simulator not responding

**Solution:**
- Allow microphone access in browser settings
- Use Chrome or Edge (better WebRTC support)
- Check browser console (F12) for errors
- Check token generation: `curl http://localhost:5008/token`
- Restart interview service: `docker-compose restart interview-service`

### Issue: Chatbot not responding

**Solution:**
```bash
# Check chatbot logs
docker-compose logs chatbot-api

# Verify Gemini API key is correct
# Test endpoint directly
curl http://localhost:8000/docs
```

### Issue: Port already in use

**Solution:**
```bash
# View processes using specific port (example: 5000)
netstat -ano | findstr :5000

# Stop the process or change port in .env
# Then restart services
docker-compose down
docker-compose up -d
```

### Issue: Docker build errors

**Solution:**
```bash
# Clean Docker cache
docker system prune -a

# Rebuild everything from scratch
docker-compose down -v
docker-compose build --no-cache
docker-compose up -d
```

## 🙏 Acknowledgments

- **Google Gemini API** for providing cutting-edge AI capabilities
- **MongoDB** for robust database solution
- **Docker** for simplifying deployment
- **Open Source Community** for amazing tools and libraries
- **FastAPI** for high-performance Python framework
- **Node.js & Express** for solid backend ecosystem

## 🚀 Future Enhancements

- [ ] OAuth2 authentication (Google, LinkedIn)
- [ ] Advanced analytics and reporting
- [ ] Mobile application (React Native)
- [ ] Multi-language support
- [ ] ATS (Applicant Tracking Systems) integration
- [ ] Personalized training recommendations
- [ ] Video conferencing integration
- [ ] A/B testing for recruitment optimization

---
