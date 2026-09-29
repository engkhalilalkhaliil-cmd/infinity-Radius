# InfinityNet — One-Click Run on Windows / VS Code

## Requirements
1. Install Docker Desktop for Windows and start it.
2. Install VS Code.
3. Open this project folder in VS Code.

## One-click run
1. Open **Run and Debug** (`Ctrl+Shift+D`).
2. Select **InfinityNet ▶ Run**.
3. Press **F5** or click the green ▶ button.
4. VS Code runs `docker compose up -d --build` and opens `http://localhost:8080`.

## First run
The first run may take several minutes because Docker builds the images and installs dependencies.

## Stop
Use the Docker Desktop UI, or run this in the VS Code terminal:

```powershell
docker compose down
```

## If Docker is not running
Start Docker Desktop first. Verify with:

```powershell
docker --version
docker compose version
```

## Useful checks

```powershell
docker compose ps
docker compose logs --tail=100 manager
```

Dashboard:

`http://localhost:8080`

Health:

`http://localhost:8080/health`
