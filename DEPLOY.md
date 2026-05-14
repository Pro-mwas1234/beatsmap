# Deploying BeatMaps to Koyeb

This guide explains how to deploy the BeatMaps application to [Koyeb](https://www.koyeb.com).

## Prerequisites

- A Koyeb account (sign up at https://app.koyeb.com/signup)
- The Koyeb CLI installed (`brew install koyeb/tap/koyeb` or download from https://www.koyeb.com/docs/cli/install)
- Git installed

## Quick Deploy Options

### Option 1: Deploy via GitHub (Recommended)

1. **Push your code to GitHub**
   ```bash
   git add .
   git commit -m "Initial commit"
   git remote add origin <your-github-repo-url>
   git push -u origin main
   ```

2. **Deploy from Koyeb Dashboard**
   - Go to https://app.koyeb.com
   - Click "Create Service"
   - Select "Deploy from Git"
   - Connect your GitHub repository
   - Koyeb will automatically detect the Dockerfile and deploy

### Option 2: Deploy via Koyeb CLI

1. **Login to Koyeb**
   ```bash
   koyeb login
   ```

2. **Create an app and deploy**
   ```bash
   # Create a new app
   koyeb app create beatmaps

   # Deploy the service
   koyeb service create beatmaps --app beatmaps --dockerfile ./Dockerfile --port 80:http
   ```

3. **Or use the configuration file**
   ```bash
   koyeb deploy
   ```

### Option 3: Deploy via Docker

If you prefer to build and push the Docker image yourself:

1. **Build the Docker image**
   ```bash
   docker build -t your-registry/beatmaps:latest .
   ```

2. **Push to your container registry** (Docker Hub, GHCR, etc.)
   ```bash
   docker push your-registry/beatmaps:latest
   ```

3. **Deploy to Koyeb**
   ```bash
   koyeb service create beatmaps --app beatmaps --image your-registry/beatmaps:latest --port 80:http
   ```

## Configuration

The deployment uses the following configuration:

- **Port**: 80 (HTTP)
- **Regions**: Frankfurt (fra), Washington DC (was), San Jose (sjc)
- **Scaling**: 1 instance (can be adjusted)
- **Health Check**: Path `/` every 30 seconds

You can modify these settings in `koyeb.yaml` or via the Koyeb dashboard.

## Accessing Your App

Once deployed, Koyeb will provide you with a URL like:
```
https://beatmaps-xxxxx.koyeb.app
```

Your BeatMaps application will be accessible at this URL.

## Updating Your Deployment

### Via GitHub
Simply push new commits to your repository, and Koyeb will automatically redeploy.

### Via CLI
```bash
koyeb deploy
```

## Notes

- This is a static HTML application served via nginx
- No database or backend services are required
- The app uses browser geolocation for navigation features
- Music files are loaded locally by the user through the browser

## Troubleshooting

If you encounter issues:

1. Check the build logs in the Koyeb dashboard
2. Verify the Dockerfile builds locally: `docker build -t test .`
3. Ensure port 80 is correctly configured
4. Check that `beatmaps.html` is in the root directory

## Support

For Koyeb-specific issues, refer to:
- [Koyeb Documentation](https://www.koyeb.com/docs)
- [Koyeb Community](https://community.koyeb.com)
