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

```
