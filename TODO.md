# TODO for nginx-middleware-mysql Project

- [x] Create main directory nginx-middleware-mysql and subdirectories middleware and nginx
- [x] Create package.json in middleware/
- [x] Create server.js in middleware/
- [x] Create Dockerfile in middleware/
- [x] Create default.conf in nginx/
- [x] Create Dockerfile in nginx/
- [x] Create docker-compose.yml in nginx-middleware-mysql/
- [x] Run docker compose build
- [ ] Run docker compose up -d
- [ ] Verify containers are running with 'docker ps' or 'docker compose ps'
- [ ] Check container status:
  - [ ] mysql container should be running
  - [ ] middleware container should be running
  - [ ] nginx container should be running
- [ ] Test application:
  - [ ] Visit http://localhost or run: curl http://localhost/
  - [ ] Should see "Hello from middleware! (container: ...)"
- [ ] Check logs if needed:
  - [ ] docker compose logs -f nginx
  - [ ] docker compose logs -f middleware
  - [ ] docker compose logs -f mysql

## Testing Steps

1. Start containers:
   - Run: `docker compose up -d`
2. Verify containers are running:
   - Run: `docker compose ps`
   - Or: `docker ps`
3. Check container status:
   - Ensure mysql, middleware, and nginx containers are listed and healthy
4. Test application:
   - Open browser and visit: http://localhost
   - Or run: `curl http://localhost`
   - You should see: "Hello from middleware! (container: ...)"

Next steps — commands to run now
1. Restart Docker Desktop (apply DNS/daemon changes).
2. Build images:
   - docker compose build
3. Start services:
   - docker compose up -d
4. Check status:
   - docker compose ps
   - docker ps
5. Test the app:
   - curl http://localhost/
   - open http://localhost in a browser
6. If anything fails, check logs:
   - docker compose logs -f
   - docker compose logs -f nginx middleware mysql
7. Common fixes:
   - If image pull fails: docker pull node:16 nginx:alpine mysql:5.7
   - If DNS issues persist: ensure c:\Users\91940\.docker\daemon.json contains DNS entries (8.8.8.8, 1.1.1.1), restart Docker
   - If authentication required: docker login
   - If build context / COPY errors: confirm files exist under middleware/ and nginx/ and compose build context is correct

If you run the commands above and paste any errors or logs that look wrong, I will help you debug the exact failure.
  - docker pull nginx:alpine
- If DNS still fails:
  - Temporarily change Windows DNS (Network Adapter → IPv4 → DNS) to 8.8.8.8 / 1.1.1.1 and restart Docker.
  - As last resort only: add hosts entry mapping the failing hostname to an IP you verified from a working network (edit C:\Windows\System32\drivers\etc\hosts) — avoid permanent hosts edits unless you know the IP is stable.
- After connectivity is fixed:
  - docker compose build
  - docker compose up -d
  - docker ps
  - curl http://localhost

Notes:
- Changing `daemon.json` requires Docker restart to take effect.
- If you are behind a corporate proxy / VPN, configure Docker Desktop proxy settings or disconnect VPN while pulling.

Next Steps:
- [ ] Run docker compose build again
- [ ] If build succeeds, run docker compose up -d
- [ ] Test the application at http://localhost
- [ ] If you see "failed to solve: failed to compute cache key: failed to copy" errors:
  - [ ] Check Docker daemon DNS config (`c:\Users\91940\.docker\daemon.json`)
  - [ ] Restart Docker Desktop after changes
  - [ ] Set Windows network adapter DNS to 8.8.8.8 and 1.1.1.1
  - [ ] Disconnect VPN/proxy if possible
  - [ ] Try: docker pull node:alpine
  - [ ] If pull fails, it's a network/DNS issue, not a Dockerfile problem
  - [ ] If pull works, try: docker compose build

## How to commit nginx-middleware-mysql folder to GitHub

1. Open a terminal and navigate to your project folder:
   ```
   cd ~/Desktop/docker-demo/nginx-middleware-mysql
   ```
2. Initialize a git repository (if not already done):
   ```
   git init
   ```
3. Add all files:
   ```
   git add .
   ```
4. Commit your changes:
   ```
   git commit -m "Initial commit for nginx-middleware-mysql project"
   ```
5. Create a new repository on GitHub (via the website).
6. Link your local repo to GitHub:
   ```
   git remote add origin https://github.com/<your-username>/<your-repo-name>.git
   ```
7. Push your code:
   ```
   git push -u origin master
   ```
   (or use `main` if your default branch is `main`)

**Note:** Replace `<your-username>` and `<your-repo-name>` with your actual GitHub username and repository name.
