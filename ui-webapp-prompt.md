# Template de Projet : Application Web Full-Stack React + FastAPI

## 🎯 INSTRUCTIONS POUR CLAUDE CODE (À LIRE EN PREMIER)

**AVANT de générer quoi que ce soit**, tu dois avoir une conversation interactive avec l'utilisateur pour bien comprendre son besoin. Suis ce processus étape par étape :

### Phase 1 : Informations de base (OBLIGATOIRE)

Commence par demander les informations essentielles en utilisant l'outil `AskUserQuestion` :

**Question unique initiale :** Demande le titre du projet et une description courte.

Format attendu de la réponse utilisateur :
- Titre : [nom du projet]
- Description : [1-3 phrases décrivant l'objectif principal]

### Phase 2 : Raisonnement itératif sur le data model (OBLIGATOIRE)

**IMPORTANT** : Active le mode de raisonnement étape par étape pour cette phase.

À partir de la description, tu dois **raisonner** pour identifier :

1. **Entités principales du data model**
   - Analyse la description pour déduire les entités métier
   - Exemple : "gestion de tâches" → entités : User, Task, Project
   - Exemple : "suivi de commandes" → entités : Customer, Order, Product

2. **Attributs de chaque entité**
   - Raisonne sur les champs logiques pour chaque entité
   - Pense aux relations (one-to-many, many-to-many)
   - Identifie les champs obligatoires vs optionnels

3. **Présente ton analyse** sous forme de schéma :
   ```
   📊 Data Model proposé :

   Entité 1 : [Nom]
   - champ1 : [type] (description)
   - champ2 : [type] (description)
   - relation avec Entité 2

   Entité 2 : [Nom]
   - champ1 : [type] (description)
   ...
   ```

4. **Demande validation** : "Ce data model correspond-il à ton besoin ? Faut-il ajouter/modifier des entités ou des champs ?"

### Phase 3 : Raisonnement sur les pages et fonctionnalités (OBLIGATOIRE)

**Toujours en mode raisonnement**, déduis les pages nécessaires :

1. **Analyse des pages requises**
   - Pour chaque entité, identifie les opérations CRUD nécessaires
   - Raisonne sur les pages de liste, détail, création, édition
   - Pense aux pages transversales (dashboard, recherche, statistiques)

2. **Présente l'architecture des pages** :
   ```
   📁 Pages React prévues :

   1. HomePage (/)
      - Description : [page d'accueil, dashboard, etc.]
      - Composants clés : [liste des composants]

   2. [EntityList]Page (/entities)
      - Description : Liste des [entités] avec filtres
      - Fonctionnalités : recherche, tri, pagination
      - Appels API : GET /api/entities

   3. [EntityDetail]Page (/entities/:id)
      - Description : Détails et édition d'une [entité]
      - Fonctionnalités : affichage, modification, suppression
      - Appels API : GET/PUT/DELETE /api/entities/:id

   4. Create[Entity]Page (/entities/new)
      - Description : Création d'une nouvelle [entité]
      - Appels API : POST /api/entities

   [... autres pages selon le contexte]
   ```

3. **Identifie les endpoints API** correspondants :
   ```
   🔌 Endpoints API prévus :

   Entité 1 :
   - GET    /api/entity1           → Liste toutes les entités
   - POST   /api/entity1           → Crée une entité
   - GET    /api/entity1/:id       → Récupère une entité
   - PUT    /api/entity1/:id       → Modifie une entité
   - DELETE /api/entity1/:id       → Supprime une entité

   [Endpoints supplémentaires si nécessaire]
   - GET    /api/entity1/:id/related → Récupère les relations
   - POST   /api/search             → Recherche avancée
   ```

4. **Demande validation** : "Cette architecture de pages répond-elle à tes besoins ? Faut-il ajouter ou retirer des pages ?"

### Phase 4 : Challenge et optimisations (OBLIGATOIRE)

Après validation du modèle et des pages, **analyse et challenge** :

1. **Vérifie l'adéquation de la stack React + FastAPI**
   - ✅ Adapté pour : applications CRUD, dashboards, APIs REST classiques
   - ⚠️ Limitations : temps réel intensif (considérer WebSocket), calculs lourds côté client
   - ❌ Inadapté si : [cas spécifiques détectés]

2. **Propose des améliorations contextuelles** :
   - Pagination si > 100 items par entité
   - Base de données SQLite/PostgreSQL selon le volume
   - Authentification JWT si multi-utilisateurs
   - Gestion des rôles si permissions différenciées
   - Upload de fichiers si détecté dans les besoins
   - Export CSV/Excel si beaucoup de données
   - Tests unitaires pour API critique
   - Logging/monitoring si application professionnelle

3. **Questions de clarification** (si nécessaire) :
   - "J'ai remarqué [X], as-tu besoin de [Y] ?"
   - "Pour [use case], veux-tu que j'ajoute [feature] ?"

### Phase 5 : Validation du plan final (OBLIGATOIRE)

Présente un plan complet et détaillé :

```
📋 Plan de projet pour [NOM_PROJET]

🎯 Objectif : [résumé en 1 phrase de la description]

📊 Data Model :
[Reprendre le schéma validé de la Phase 2]

🏗️ Architecture technique :
- Backend : FastAPI avec [précisions : base de données, auth, etc.]
- Frontend : React avec React Router, Bootstrap
- Stockage : [en mémoire / SQLite / PostgreSQL]
- Authentification : [oui/non, méthode]

📁 Pages React (détaillées) :
[Reprendre l'architecture validée de la Phase 3]

🔌 Endpoints API (complets) :
[Reprendre les endpoints de la Phase 3]

✨ Améliorations incluses :
- [Amélioration 1] : [justification]
- [Amélioration 2] : [justification]
- ...

📦 Livrables :
- Structure complète du projet
- Backend FastAPI fonctionnel avec tous les endpoints
- Frontend React avec toutes les pages
- Docker (dev + prod)
- Makefile pour simplifier les commandes
- README exhaustif

✅ Checklist de validation :
- [ ] Data model complet et cohérent
- [ ] Toutes les pages nécessaires identifiées
- [ ] Endpoints API couvrant tous les use cases
- [ ] Améliorations pertinentes proposées

Est-ce que ce plan te convient ? Veux-tu ajouter/modifier quelque chose avant que je commence la génération ?
```

### Phase 6 : Génération (SEULEMENT APRÈS VALIDATION)

Une fois que l'utilisateur a **explicitement validé** le plan (réponse "oui", "ok", "valide", etc.), tu peux commencer à générer le projet en suivant les spécifications techniques ci-dessous.

**RAPPEL** : Ne commence JAMAIS la génération sans validation explicite du plan.

---

## Objectif
Créer une application web moderne avec interface utilisateur React et API backend FastAPI, prête pour le développement et le déploiement Docker.

## Stack Technique

### Backend
- **FastAPI** ^0.115.6 : Framework API REST moderne et performant
- **Uvicorn** ^0.34.0 : Serveur ASGI avec hot-reload
- **Pydantic** ^2.10.5 : Validation de données et modèles
- **Python** 3.9+ avec **uv** pour la gestion des dépendances

### Frontend
- **React** ^19.2.0 : Bibliothèque UI avec hooks
- **Vite** ^7.2.4 : Build tool rapide avec HMR
- **React Router** ^7.9.6 : Navigation SPA
- **Bootstrap** ^5.3.8 + **React Bootstrap** ^2.10.10 : Framework CSS et composants
- **Node.js** 18+ avec npm

### DevOps
- **Docker** avec multi-stage builds
- **docker-compose** pour orchestration (dev + prod)
- **Makefile** pour commandes standardisées
- **nginx** pour servir le frontend en production

## Structure du Projet

```
{{PROJECT_NAME}}/
├── backend/              # API FastAPI
│   ├── __init__.py
│   ├── main.py          # Application FastAPI principale
│   ├── models.py        # (optionnel) Modèles Pydantic
│   ├── routes/          # (optionnel) Routes modulaires
│   ├── Dockerfile       # Image backend Python
│   └── README.md        # Documentation backend
├── ui/                  # Application React
│   ├── src/
│   │   ├── main.jsx     # Point d'entrée React
│   │   ├── App.jsx      # Composant racine avec Router
│   │   ├── App.css
│   │   ├── index.css
│   │   ├── pages/       # Pages/routes de l'application
│   │   ├── components/  # Composants réutilisables
│   │   ├── services/    # Services API (api.js)
│   │   └── assets/      # Images, icônes, etc.
│   ├── public/          # Fichiers statiques
│   ├── index.html       # Template HTML
│   ├── Dockerfile       # Image frontend (build + nginx)
│   └── nginx.conf       # Configuration nginx
├── .dockerignore
├── .gitignore
├── .env.local           # Variables d'environnement (dev)
├── docker-compose.yml   # Configuration Docker production
├── docker-compose.dev.yml # Configuration Docker développement
├── Makefile             # Commandes de développement
├── package.json         # Dépendances et scripts npm
├── package-lock.json
├── pyproject.toml       # Configuration Python et dépendances
├── uv.lock              # Lock file uv
├── vite.config.js       # Configuration Vite
├── eslint.config.js     # Configuration ESLint
└── README.md            # Documentation projet
```

## Fichiers de Configuration à Créer

### 1. `pyproject.toml`
```toml
[project]
name = "{{PROJECT_NAME}}"
version = "0.1.0"
description = "{{PROJECT_DESCRIPTION}}"
readme = "README.md"
requires-python = ">=3.9"
dependencies = [
    "fastapi>=0.115.6",
    "uvicorn[standard]>=0.34.0",
    "python-multipart>=0.0.20",
    "pydantic>=2.10.5",
]

[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"

[tool.hatch.build.targets.wheel]
packages = ["backend"]

[tool.uv]
dev-dependencies = []
```

### 2. `package.json`
```json
{
  "name": "{{PROJECT_NAME}}",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint .",
    "preview": "vite preview"
  },
  "dependencies": {
    "bootstrap": "^5.3.8",
    "react": "^19.2.0",
    "react-bootstrap": "^2.10.10",
    "react-dom": "^19.2.0",
    "react-router-dom": "^7.9.6"
  },
  "devDependencies": {
    "@eslint/js": "^9.39.1",
    "@types/react": "^19.2.5",
    "@types/react-dom": "^19.2.3",
    "@vitejs/plugin-react": "^5.1.1",
    "eslint": "^9.39.1",
    "eslint-plugin-react-hooks": "^7.0.1",
    "eslint-plugin-react-refresh": "^0.4.24",
    "globals": "^16.5.0",
    "vite": "^7.2.4"
  }
}
```

### 3. `vite.config.js`
```javascript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  server: {
    proxy: {
      '/api': {
        target: 'http://localhost:8000',
        changeOrigin: true,
      }
    }
  },
  build: {
    outDir: 'build',
  }
})
```

### 4. `.env.local`
```
VITE_API_URL=http://localhost:8000
```

### 5. `Makefile` (avec commandes standardisées)
Inclure les commandes suivantes :
- `make install` : Installe backend + frontend
- `make dev` : Lance backend ET frontend ensemble
- `make backend` : Lance uniquement backend
- `make frontend` : Lance uniquement frontend
- `make build` : Build frontend pour production
- `make clean` : Nettoie les fichiers générés
- `make docker-build` : Construit les images Docker
- `make docker-up` : Lance les conteneurs (production)
- `make docker-dev` : Lance les conteneurs (développement)
- `make docker-down` : Arrête les conteneurs
- `make docker-logs` : Affiche les logs Docker
- `make help` : Affiche l'aide avec couleurs

## Patterns de Code

### Backend : Structure FastAPI

```python
from fastapi import FastAPI, HTTPException
from fastapi.middleware.cors import CORSMiddleware
from pydantic import BaseModel
from typing import List, Optional

app = FastAPI(title="{{PROJECT_NAME}} API", version="1.0.0")

# CORS pour permettre les requêtes depuis le frontend
app.add_middleware(
    CORSMiddleware,
    allow_origins=["http://localhost:5173"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)

# Modèles Pydantic
class Item(BaseModel):
    id: int
    name: str
    # ... autres champs

# Routes
@app.get("/")
def read_root():
    return {
        "message": "Bienvenue sur l'API {{PROJECT_NAME}}",
        "version": "1.0.0",
        "status": "running"
    }

@app.get("/api/items", response_model=List[Item])
def get_items():
    # Logique métier
    pass
```

### Frontend : Service API

Créer `ui/src/services/api.js` :

```javascript
const API_BASE_URL = import.meta.env.VITE_API_URL || 'http://localhost:8000';

export const api = {
  async get(endpoint) {
    const response = await fetch(`${API_BASE_URL}${endpoint}`);
    if (!response.ok) throw new Error(`HTTP error! status: ${response.status}`);
    return response.json();
  },

  async post(endpoint, data) {
    const response = await fetch(`${API_BASE_URL}${endpoint}`, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(data),
    });
    if (!response.ok) throw new Error(`HTTP error! status: ${response.status}`);
    return response.json();
  },

  async put(endpoint, data) {
    const response = await fetch(`${API_BASE_URL}${endpoint}`, {
      method: 'PUT',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(data),
    });
    if (!response.ok) throw new Error(`HTTP error! status: ${response.status}`);
    return response.json();
  },

  async delete(endpoint) {
    const response = await fetch(`${API_BASE_URL}${endpoint}`, {
      method: 'DELETE',
    });
    if (!response.ok) throw new Error(`HTTP error! status: ${response.status}`);
    return response.json();
  },
};
```

### Frontend : Structure App.jsx

```javascript
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
import NavBar from './components/NavBar';
import HomePage from './pages/HomePage';
// Importer d'autres pages...

function App() {
  return (
    <Router>
      <NavBar />
      <Routes>
        <Route path="/" element={<HomePage />} />
        {/* Ajouter d'autres routes */}
      </Routes>
    </Router>
  );
}

export default App;
```

### Frontend : Composant NavBar avec Bootstrap

```javascript
import { Navbar, Nav, Container } from 'react-bootstrap';
import { Link } from 'react-router-dom';

function NavBar() {
  return (
    <Navbar bg="dark" variant="dark" expand="lg">
      <Container>
        <Navbar.Brand as={Link} to="/">{{PROJECT_NAME}}</Navbar.Brand>
        <Navbar.Toggle aria-controls="basic-navbar-nav" />
        <Navbar.Collapse id="basic-navbar-nav">
          <Nav className="ms-auto">
            <Nav.Link as={Link} to="/">Accueil</Nav.Link>
            {/* Ajouter d'autres liens */}
          </Nav>
        </Navbar.Collapse>
      </Container>
    </Navbar>
  );
}

export default NavBar;
```

## Docker Configuration

### `backend/Dockerfile`
```dockerfile
FROM python:3.11-slim

WORKDIR /app

# Installer uv
RUN pip install uv

# Copier les fichiers de dépendances
COPY pyproject.toml uv.lock ./

# Installer les dépendances
RUN uv sync --frozen

# Copier le code source
COPY backend ./backend

# Exposer le port
EXPOSE 8000

# Lancer l'application
CMD ["uv", "run", "uvicorn", "backend.main:app", "--host", "0.0.0.0", "--port", "8000"]
```

### `ui/Dockerfile` (multi-stage)
```dockerfile
# Stage 1: Build
FROM node:18-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY ui ./ui
COPY vite.config.js ./
COPY eslint.config.js ./
COPY .env.local ./

RUN npm run build

# Stage 2: Production avec nginx
FROM nginx:alpine

COPY --from=build /app/build /usr/share/nginx/html
COPY ui/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

### `ui/nginx.conf`
```nginx
server {
    listen 80;
    server_name localhost;

    root /usr/share/nginx/html;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }

    location /api {
        proxy_pass http://backend:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

### `docker-compose.yml` (production)
```yaml
version: '3.8'

services:
  backend:
    build:
      context: .
      dockerfile: backend/Dockerfile
    ports:
      - "8000:8000"
    environment:
      - PYTHONUNBUFFERED=1

  frontend:
    build:
      context: .
      dockerfile: ui/Dockerfile
    ports:
      - "80:80"
    depends_on:
      - backend
```

### `docker-compose.dev.yml` (développement avec hot-reload)
```yaml
version: '3.8'

services:
  backend:
    build:
      context: .
      dockerfile: backend/Dockerfile
    ports:
      - "8000:8000"
    volumes:
      - ./backend:/app/backend
    command: uv run uvicorn backend.main:app --host 0.0.0.0 --port 8000 --reload

  frontend:
    image: node:18-alpine
    working_dir: /app
    ports:
      - "5173:5173"
    volumes:
      - .:/app
    command: sh -c "npm install && npm run dev -- --host"
    environment:
      - VITE_API_URL=http://localhost:8000
```

## README.md Structure

Le README doit inclure :
1. Description du projet
2. Structure du projet (arborescence)
3. Prérequis (Python 3.9+, Node 18+, uv)
4. Installation rapide avec Makefile
5. Commandes disponibles (make help)
6. Lancement manuel (sans Makefile)
7. Build pour production
8. Déploiement Docker (prod + dev)
9. Technologies utilisées
10. Configuration (variables d'environnement, CORS)

## .gitignore
```
# Python
__pycache__/
*.py[cod]
.venv/
*.egg-info/

# Node
node_modules/
build/
dist/

# Vite
.vite/

# Environment
.env.local
.env.*.local

# IDE
.vscode/
.idea/

# OS
.DS_Store
```

## Instructions de Génération pour Claude Code

1. **Créer la structure de dossiers** complète
2. **Générer tous les fichiers de configuration** avec les contenus ci-dessus
3. **Créer le backend** :
   - `backend/main.py` avec FastAPI de base
   - Modèles Pydantic adaptés au use case
   - Routes API REST complètes
   - CORS configuré
4. **Créer le frontend** :
   - Structure React avec Router
   - Composant NavBar avec Bootstrap
   - Service API centralisé
   - Pages adaptées au use case
   - Styles CSS cohérents
5. **Configurer Docker** :
   - Dockerfiles optimisés
   - docker-compose pour dev et prod
   - nginx correctement configuré
6. **Makefile complet** avec toutes les commandes
7. **README exhaustif** et bien structuré

## Checklist Finale

- [ ] Projet démarre avec `make install && make dev`
- [ ] Backend accessible sur http://localhost:8000
- [ ] Frontend accessible sur http://localhost:5173
- [ ] API docs disponibles sur http://localhost:8000/docs
- [ ] Navigation React Router fonctionne
- [ ] Appels API fonctionnels
- [ ] Docker build réussit : `make docker-build`
- [ ] Docker prod fonctionne : `make docker-up`
- [ ] Docker dev avec hot-reload : `make docker-dev`
- [ ] README complet et à jour
- [ ] .gitignore configuré
- [ ] ESLint configuré