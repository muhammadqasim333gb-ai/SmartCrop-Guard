# SmartCrop Guard

SmartCrop Guard is a full-stack plant disease detection web application with multilingual support, user accounts, image upload or camera capture, disease detection, treatment recommendations, severity scoring, and scan history.

## Stack
- Frontend: HTML, CSS, JavaScript
- Backend: Node.js, Express
- Database: MySQL
- Machine Learning: TensorFlow, Pandas, Plotly
- Machine Learning script: `ml/detect.py`
- Deployment target: AWS

## Available Pages
- `index.html` — Landing page with detection, recommendations, and charts
- `signup.html` — User signup page
- `login.html` — User login page
- `history.html` — Scan history for logged-in users
- `about.html` — About SmartCrop Guard
- `howto.html` — Usage guide

## Setup
1. Install backend dependencies:
   ```bash
   npm install
   ```
2. Install Python dependencies:
   ```bash
   python3 -m pip install -r requirements.txt
   ```
3. Create a `.env` file with database and Firebase service account settings:
   ```env
   DB_HOST=localhost
   DB_USER=root
   DB_PASSWORD=yourpassword
   DB_NAME=plant_app
   PORT=3000
   FIREBASE_SERVICE_ACCOUNT={"type":"service_account",...}
   OPENAI_API_KEY=your_openai_api_key
   ```
4. Start the backend server:
   ```bash
   npm start
   ```
5. Install frontend dependencies and run the React app (optional):
   ```bash
   cd frontend
   npm install
   npm run dev
   ```
6. Open the app at `http://localhost:3000` for the Express site or `http://localhost:5173` for the frontend dev server.

## Docker Deployment

SmartCrop Guard now includes container support for production-like portability.

- Build the app image:
  ```bash
  npm run docker:build
  ```
- Start the full stack with MySQL using Docker Compose:
  ```bash
  npm run docker:up
  ```
- Stop the services:
  ```bash
  npm run docker:down
  ```

The app is exposed on `http://localhost:3000` and the database is available at `mysql://root:example@localhost:3306/plant_app`.

> Tip: place `.env` values in a local `.env` file and never commit secrets.

If you want to use Google authentication, fill in the Firebase config values in `frontend/src/firebase.js` and set up a Firebase project with Google Sign-In enabled.

## Features
- Signup and login with MySQL-backed user records
- Image upload or camera capture for instant crop disease detection
- AI-powered Help page for crop disease advice and treatment guidance
- Severity classification: mild, moderate, severe
- Treatment recommendations and prevention tips
- Scan history saved to MySQL for each logged-in user
- English and Urdu language selection
- Responsive, nature-friendly animated interface
- Local file-storage fallback when MySQL is unavailable
- Detection cache for identical image uploads to speed repeated scans
- Container-ready deployment with `Dockerfile` and `docker-compose.yml`

## Notes
- `ml/detect.py` now uses TensorFlow for detection and can auto-train a small demo model from synthetic crop-style examples when no saved model exists.
- You can also run `python ml/detect.py train <data_dir>` to train from a labeled image dataset.
- To deploy on AWS, provision Node.js and MySQL resources and set the `.env` variables accordingly.
