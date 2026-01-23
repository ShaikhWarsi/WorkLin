# Render Yjs Server Configuration Guide

## Current Issues in Your Render Dashboard

Your `worklin-yjs-server` service has incorrect settings. Here's what needs to be fixed:

## ✅ Required Changes

### 1. Root Directory
**Current**: `src`  
**Should be**: `yjs-server`

**Why**: The Yjs server files are in the `yjs-server` folder, not `src`.

### 2. Build Command
**Current**: `npm install; npm run build`  
**Should be**: `npm install`

**Why**: The Yjs server doesn't have a build step - it's a simple Node.js server that just needs dependencies installed.

### 3. Start Command
**Current**: `npm start`  
**Status**: ✅ **CORRECT** (no change needed)

**Why**: The `package.json` in `yjs-server` has `"start": "node server.js"` which is correct.

## 📋 Complete Correct Settings

Go to your Render dashboard → `worklin-yjs-server` → Settings → Build & Deploy:

| Setting | Value |
|---------|-------|
| **Root Directory** | `yjs-server` |
| **Build Command** | `npm install` |
| **Start Command** | `npm start` |
| **Branch** | `main` |

## 🔧 Step-by-Step Fix

1. Go to: https://dashboard.render.com
2. Click on your service: `worklin-yjs-server`
3. Go to **Settings** tab
4. Scroll to **Build & Deploy** section
5. Update these fields:

   **Root Directory:**
   - Click **Edit** next to "Root Directory"
   - Change from `src` to `yjs-server`
   - Click **Save**

   **Build Command:**
   - Click **Edit** next to "Build Command"
   - Change from `npm install; npm run build` to `npm install`
   - Click **Save**

6. Click **Manual Deploy** → **Deploy latest commit**

## ✅ Verification

After deploying, check the logs. You should see:
```
✅ Yjs server running on port 1234
📡 WebSocket URL: ws://localhost:1234
```

Your WebSocket URL will be:
- **Local**: `ws://localhost:1234`
- **Production**: `wss://worklin-yjs-server.onrender.com`

## 🔗 Next Steps

After the server is running:

1. Get your WebSocket URL: `wss://worklin-yjs-server.onrender.com`
2. Add to your `.env` file:
   ```env
   VITE_YJS_WEBSOCKET_URL=wss://worklin-yjs-server.onrender.com
   ```
3. Restart your local dev server if running
4. Test real-time collaboration!

---

**Note**: The Yjs server is separate from the main WorkLin app. This service only handles WebSocket connections for real-time collaboration.
