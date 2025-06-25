This repository manages the `frontend` and `backend` projects using Git submodules. It also contains high-level configuration files like Docker Compose and CI/CD pipelines.

## Project Structure

```
devHunter/
├── frontend/       # React application
├── backend/        # Express application
└── docker-compose.yml
```

## Submodule Commands

### Clone the Repository with Submodules

```bash
git clone --recurse-submodules <parent-repo-url>
```

### Initialize and Update Submodules

If submodules are not initialized:

```bash
git submodule init
git submodule update
```

### Pull Latest Changes for Submodules

```bash
git submodule update --remote
```

### Push Changes to a Submodule

1. Navigate to the submodule directory:

   ```bash
   cd <submodule-path>
   ```

2. Commit and push changes:

   ```bash
   git add .
   git commit -m "Your commit message"
   git push
   ```

3. Return to the parent repository and update the submodule reference:

   ```bash
   cd ..
   git add <submodule-path>
   git commit -m "Update submodule reference"
   git push
   ```

### Remove a Submodule

1. Delete the submodule entry from `.gitmodules`:

   ```bash
   vim .gitmodules
   ```

2. Remove the submodule directory:

   ```bash
   rm -rf <submodule-path>
   ```

3. Unstage the submodule reference:

   ```bash
   git rm --cached <submodule-path>
   git commit -m "Remove submodule <submodule-path>"
   ```

## Notes

- Use `npm start` in the `frontend` directory to run the React application.
- Use `node index.js` in the `backend` directory to start the Express server.

This repository contains the `frontend` and `backend` projects, along with a shared base Docker image and a `docker-compose.yml` file for managing the development environment.

## Project Structure

```
devHunter/
├── Dockerfile.base       # Shared base Dockerfile for Node.js configuration
├── docker-compose.yml    # Docker Compose configuration for all services
├── frontend/             # React application
│   ├── Dockerfile        # Dockerfile for frontend
│   └── ...
├── backend/              # Express application
│   ├── Dockerfile        # Dockerfile for backend
│   └── ...
```

## Prerequisites

- Install [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/).
- Ensure you have a GitHub account and access to GitHub Container Registry.

## Setup Instructions

### 1. Clone the Repository

```bash
git clone <repo-url>
cd devHunter
```

### 2. Authenticate with GitHub Container Registry

Log in to GitHub Container Registry to pull the shared base image:

```bash
echo "<your-github-token>" | docker login ghcr.io -u <your-github-username> --password-stdin
```

### 3. Run All Services Simultaneously

Use Docker Compose to build and start all services:

```bash
docker-compose up --build
```

### 4. Access the Services

- Frontend: `http://localhost:3000/`
- Backend: `http://localhost:3001/`

### 5. Verify Hot Reload

- **Frontend**: Make changes to the React code in the `frontend` folder. Changes should reflect immediately in the browser.
- **Backend**: Make changes to the Express code in the `backend` folder. Changes should apply immediately without restarting the container.

## Running Services Independently

### Frontend

1. Build the frontend image:

   ```bash
   docker build -f frontend/Dockerfile -t devhunter-frontend ./frontend
   ```

2. Run the frontend container:

   ```bash
   docker run -p 3000:3000 devhunter-frontend
   ```

### Backend

1. Build the backend image:

   ```bash
   docker build -f backend/Dockerfile -t devhunter-backend ./backend
   ```

2. Run the backend container:

   ```bash
   docker run -p 3001:3000 devhunter-backend
   ```

## Notes

- The shared base image (`devhunter-base`) is hosted on GitHub Container Registry.
- Ensure you authenticate with GitHub Container Registry before running services independently.
- Use `docker-compose` for simultaneous execution during development.

## Troubleshooting

- If hot reload doesn't work, ensure the `CHOKIDAR_USEPOLLING=true` environment variable is set for the frontend.
- For backend, ensure `nodemon` is installed and used in the `backend/Dockerfile`.

```
