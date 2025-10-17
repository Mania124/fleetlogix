# 🚚 FleetLogix — Smart ELD & Route Planner

**FleetLogix** is a full-stack application that helps truck drivers and logistics companies plan routes, manage Hours of Service (HOS), and automatically generate **digital logbooks** (ELD-style) based on trip data and FMCSA rules.

---

## 🧭 Features

- **Trip Planner**
  - Input current, pickup, and dropoff locations.
  - Calculate the best route and estimated trip duration.
- **HOS Logbook Generator**
  - Draws and fills ELD-style daily log sheets.
  - Tracks driving, rest, fueling, and on-duty hours.
- **Compliance Automation**
  - Follows FMCSA 70-hour/8-day property-carrying cycle.
  - Includes required pickup/drop-off and fuel stop times.
- **Map Visualization**
  - Uses free mapping APIs (like OpenRouteService or Mapbox) for routing and visualization.
- **Cloud Architecture**
  - React frontend hosted on Vercel (or AWS Amplify).
  - Django REST API backend deployed on AWS (EC2, Elastic Beanstalk, or Lambda).

---

## 🏗️ Project Structure

```
fleetlogix/
│
├── backend/
│   ├── manage.py
│   ├── requirements.txt
│   ├── Dockerfile
│   ├── docker-compose.yml
│   ├── .env.example
│   ├── fleetlogix_api/
│   │   ├── settings.py
│   │   ├── urls.py
│   │   ├── wsgi.py
│   │   └── asgi.py
│   ├── trips/
│   │   ├── models.py
│   │   ├── serializers.py
│   │   ├── views.py
│   │   ├── urls.py
│   │   └── services/
│   │       ├── route_planner.py
│   │       └── logsheet_generator.py
│   └── users/
│       ├── models.py
│       ├── serializers.py
│       └── views.py
│
├── frontend/
│   ├── src/
│   │   ├── App.jsx
│   │   ├── components/
│   │   │   ├── TripForm.jsx
│   │   │   ├── RouteMap.jsx
│   │   │   ├── LogSheetViewer.jsx
│   │   │   └── SummaryCard.jsx
│   │   ├── hooks/
│   │   │   └── useTripPlanner.js
│   │   ├── services/
│   │   │   └── api.js
│   │   └── styles/
│   │       └── index.css
│   ├── package.json
│   ├── vite.config.js
│   └── Dockerfile
│
└── README.md
```

---

## ⚙️ Tech Stack

| Layer            | Technology                           |
| ---------------- | ------------------------------------ |
| Frontend         | React + Vite + CSS                   |
| Backend          | Django REST Framework                |
| Database         | PostgreSQL                           |
| Map API          | OpenRouteService, Mapbox, or Leaflet |
| Deployment       | Vercel (frontend) + AWS (backend)    |
| Containerization | Docker + docker-compose              |
| Authentication   | JWT or Django Rest Auth              |

---

## 🚀 Setup Instructions

### 1. Backend (Django)

```bash
cd backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
python manage.py migrate
python manage.py runserver
```

### 2. Frontend (React)

```bash
cd frontend
npm install
npm run dev
```

---

## 🧩 Environment Variables

**Backend (.env):**

```
SECRET_KEY=your-secret-key
DEBUG=True
DATABASE_URL=postgres://user:pass@localhost:5432/fleetlogix
MAP_API_KEY=your-map-api-key
```

**Frontend (.env):**

```
VITE_API_URL=https://api.yourdomain.com
VITE_MAP_API_KEY=your-map-api-key
```

---

## 🌍 Deployment

### Frontend (Vercel)

1. Connect your GitHub repo to Vercel.
2. Add environment variables under **Settings → Environment Variables**.
3. Deploy directly from the `frontend/` directory.

### Backend (AWS)

Options:

- **Elastic Beanstalk**
- **EC2 + Nginx + Gunicorn**
- **Lambda + API Gateway**

```bash
docker-compose up --build
```

---

## 🧾 API Endpoints

| Endpoint                    | Method | Description         |
| --------------------------- | ------ | ------------------- |
| `/api/trips/plan/`          | POST   | Create a new trip   |
| `/api/trips/<id>/route/`    | GET    | Fetch route details |
| `/api/trips/<id>/logsheet/` | GET    | Generate log sheet  |
| `/api/users/login/`         | POST   | Authenticate user   |
| `/api/users/register/`      | POST   | Register user       |

---

## 📄 License

[MIT License © 2025 Hezborn Shikuku](LICENCE)
