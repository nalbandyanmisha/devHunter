# DevHunter Monorepo

This monorepo contains both the frontend and backend for the DevHunter project, managed as Git submodules and run together using Docker Compose.

## 🧱 Project Structure

```
devHunter/
├── frontend/          # React app (submodule)
├── backend/           # Express app (submodule)
└── docker-compose.yml
```

## 🚀 Getting Started

### 1. Clone with Submodules

Clone the monorepo and initialize the submodules:

```bash
git clone --recurse-submodules <repo-url>
cd devHunter
```

If you already cloned without submodules:

```bash
git submodule update --init --recursive
```

### 2. Start with Docker Compose

```bash
docker-compose up --build
```

This builds and starts both the frontend and backend.

- Frontend: <http://localhost:3000>  
- Backend: <http://localhost:3001>

### 3. Stop

Use `Ctrl + C` to stop the servers.

To clean up:

```bash
docker-compose down
```

## 🔧 Development Notes

- Changes in source files trigger hot reload automatically inside Docker.
- You can continue working inside each submodule as usual.

## ✅ Requirements

- Docker  
- Docker Compose  
- Git
