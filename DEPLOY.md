# Deployment Instructions

You asked to deploy to **Vercel**, but Vercel is designed for static sites and serverless functions. It **does not support** the persistent WebSocket connections required for this app (Socket.io) on their free tier, and your room data would be lost frequently.

**We recommend deploying to Render (it's free and works perfectly for this app).**

## Option 1: Deploy to Render (Recommended)

1. Push your code to a GitHub repository.
2. Go to [dashboard.render.com](https://dashboard.render.com/).
3. Click **New +** -> **Web Service**.
4. Connect your GitHub repository.
5. Render will automatically detect the `render.yaml` file I created and set everything up.
6. Click **Create Web Service**.

## Option 2: Deploy to Glitch (Easiest for testing)

1. Go to [glitch.com](https://glitch.com/).
2. Click **New Project** -> **Import from GitHub**.
3. Paste your repository URL.
4. It will start running immediately.

## Why not Vercel?
- Vercel functions "sleep" after a few seconds.
- When they sleep, all WebSocket connections are cut.
- The "rooms" stored in memory (`const rooms = {}`) are deleted every time the function sleeps.
- Your users would constantly get disconnected and lose sync.
