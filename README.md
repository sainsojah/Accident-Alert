# Accident-Alert
accident alert dashboard 
# AccidentAlert Dashboard

Real-time dashboard for ESP32 accident alerts (G‑force severity). Uses Firebase Realtime Database and Leaflet map.

## Deploy on Render

1. Push this repo to GitHub.
2. Log into [Render](https://render.com) → **New Static Site**.
3. Connect your GitHub repo.
4. Set **Build Command** to: `./render-build.sh`
5. Set **Publish Directory** to: `.` (a single dot)
6. Under **Environment Variables**, add your Firebase config (from Firebase Console → Project settings → General → Your apps → Realtime Database config):
   - `FIREBASE_API_KEY`
   - `FIREBASE_AUTH_DOMAIN`
   - `FIREBASE_DATABASE_URL` (e.g., `https://your-project-default-rtdb.firebaseio.com`)
   - `FIREBASE_PROJECT_ID`
   - `FIREBASE_STORAGE_BUCKET`
   - `FIREBASE_MESSAGING_SENDER_ID`
   - `FIREBASE_APP_ID`
7. Click **Create Static Site**.

Your dashboard will be live at `https://your-app.onrender.com`

## Firebase Realtime Database Setup

1. In Firebase Console, create a Realtime Database in **test mode** (for development).
2. Structure: The dashboard listens at `/alerts`. Each alert should have:
   ```json
   {
     "id": "ALT-001",
     "lat": 19.0760,
     "lng": 72.8777,
     "impact": "critical",   // or "moderate", "minor"
     "resolved": false,
     "dispatched": false,
     "timestamp": 1682697600000,
     "device": "ESP32-SIM7600",
     "gForce": "2.5"
   }
