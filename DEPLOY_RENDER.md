# Deploy Voicebox on Render

This repo is packaged as a single Docker web service. The container builds the
React web app, starts the FastAPI backend, and serves both from one public URL.

## 1. Push this repo to your GitHub account

If this is still pointing to the upstream project, fork it first or create your
own GitHub repo and push these changes there.

```powershell
gh auth login
gh repo fork jamiepine/voicebox --clone=false
git remote set-url origin https://github.com/<your-username>/voicebox.git
git add Dockerfile render.yaml DEPLOY_RENDER.md
git commit -m "Add Render deployment configuration"
git push origin main
```

## 2. Create the Render Blueprint

Open this URL after replacing `<your-username>`:

```text
https://dashboard.render.com/blueprint/new?repo=https://github.com/<your-username>/voicebox
```

Render will read `render.yaml`, build the Docker image, and publish a web URL.

## 3. Important production note

Voicebox downloads large AI model files and uses a lot of memory. The free plan
is enough to test whether the service builds and boots, but real public usage
will likely need a paid Render plan and persistent storage for model cache/data.
