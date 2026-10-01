# ⚽ GamePlan AI

### AI-Powered Football Set-Piece Analysis, Optimization & Simulation

**GamePlan AI** is a full-stack football analytics platform developed as a Final Year Project to assist players, coaches, and analysts in designing and evaluating set-piece strategies.

The platform combines **AI/ML-based tactical analysis, player-position optimization, set-piece simulation, and interactive visualization** into a single web application.

It supports both **corner kicks and free kicks**, allowing users to analyze tactical strategies, optimize player positioning, and simulate different set-piece scenarios.

---

## 🚀 Key Features

### 🎯 Analyze Set Pieces

Analyze available football set-piece strategies and retrieve tactical insights such as:

* Primary receiver
* Shot confidence
* Tactical decision
* Decision reasoning
* Available strategies

The frontend communicates with the backend through dedicated API endpoints for retrieving and analyzing strategies.

### 🧠 Optimize Player Positioning

The **Optimize Player Positioning (OPP)** service evaluates player positions and returns optimized tactical arrangements.

It supports:

* Corner-kick positioning
* Free-kick positioning
* Optimized player locations
* Primary receiver identification
* Shot confidence
* Tactical insights

### 🎬 Simulate Strategies

The **Simulation (SIM)** service allows users to interactively place players and generate set-piece simulations.

The system supports:

* Corner-kick simulation
* Free-kick simulation
* Interactive player placement
* Ball trajectory visualization
* Player movement visualization
* Animated tactical scenarios

### 🔐 Authentication System

GamePlan AI includes a dedicated authentication API supporting:

* User registration
* User login
* JWT verification
* User profiles
* Logout
* Password changes
* Protected frontend routes

Authentication is integrated with the React frontend through dedicated login, signup, and authentication utility components.

---

## 🏗️ System Architecture

GamePlan AI is structured as a multi-service full-stack application:

```text
                         ┌──────────────────────┐
                         │    React Frontend    │
                         │      Port 3000       │
                         └──────────┬───────────┘
                                    │
                    ┌───────────────┼────────────────┐
                    │               │                │
                    ▼               ▼                ▼
             ┌────────────┐  ┌────────────┐  ┌────────────┐
             │    Auth    │  │   Corner   │  │  Free Kick │
             │    API     │  │  Kick API  │  │    API     │
             │  Port 5002 │  │  Port 5000 │  │  Port 5001 │
             └─────┬──────┘  └──────┬─────┘  └──────┬─────┘
                   │                │                │
                   ▼                ▼                ▼
              Authentication   Tactical/ML      Set-Piece
                 Layer          Processing       Simulation
```

### Services

| Service            |   Port | Purpose                                    |
| ------------------ | -----: | ------------------------------------------ |
| React Frontend     | `3000` | Web application and user interface         |
| Corner Kick API    | `5000` | Corner analysis, optimization & simulation |
| Free Kick API      | `5001` | Free-kick positioning & simulation         |
| Authentication API | `5002` | Registration, login & JWT authentication   |

The repository includes documentation describing the API connections and complete multi-server startup process.

---

## 🧩 Application Routes

The frontend contains several major application areas:

```text
/login
/signup
/
/services
/analyze-set-piece
/optimize-player-positioning
/simulate-strategies
```

Protected application routes require authentication.

---

## 🔌 API Architecture

### Authentication API

```text
GET  /api/auth/health
POST /api/auth/register
POST /api/auth/login
GET  /api/auth/verify
GET  /api/auth/profile
POST /api/auth/logout
POST /api/auth/change-password
```

### Corner Kick API

```text
GET  /api/health
POST /api/optimize
POST /api/simulate
POST /api/corner/left
POST /api/corner/right
GET  /api/strategies
GET  /api/strategy/<filename>
```

### Free Kick API

```text
GET  /api/freekick/health
POST /api/freekick/position
POST /api/freekick/simulate
```

These APIs are connected directly to the corresponding React services for tactical analysis, positioning optimization, and simulation.

---

## 🛠️ Technology Stack

### AI / Machine Learning

* Python
* PyTorch
* PyTorch Geometric
* Machine Learning
* Tactical Optimization
* Simulation

### Backend

* Flask
* Flask-CORS
* Python REST APIs
* JWT Authentication
* bcrypt

### Frontend

* React
* React Router
* JavaScript
* Chart.js

### Development

* Git
* GitHub
* REST API architecture
* Multi-service application architecture

The project's API documentation specifically identifies Flask, Flask-CORS, PyTorch, PyTorch Geometric, bcrypt, PyJWT, React, React Router, and Chart.js among its core dependencies.

---

## 📁 Project Structure

```text
gameplanai_fyp/
│
├── backend/
│   └── hassaa/
│       └── data/
│           ├── api_server.py
│           ├── freekick_api.py
│           └── requirements.txt
│
├── database/
│   ├── auth_api.py
│   └── requirements.txt
│
├── frontend/
│   └── src/
│       ├── components/
│       │   ├── Login.js
│       │   ├── Signup.js
│       │   ├── SIM-Service.js
│       │   ├── OPP-Service.js
│       │   └── ASP-Service.js
│       └── utils/
│           └── auth.js
│
├── API_CONNECTIONS.md
├── start_all_servers.bat
├── start_all_servers.sh
├── test_api_connections.py
├── test_api_flow.py
├── test_signup.py
├── test_simple.py
└── vercel.json
```

The current GitHub repository contains separate `backend`, `database`, and `frontend` components, along with startup scripts, API tests, API documentation, and Vercel configuration.

---

## ⚙️ Running the Project

### 1. Clone the Repository

```bash
git clone https://github.com/HassaanUllahKhan11/gameplanai_fyp.git
cd gameplanai_fyp
```

### 2. Start All Services

#### Windows

```bash
.\start_all_servers.bat
```

#### Linux / macOS

```bash
chmod +x start_all_servers.sh
./start_all_servers.sh
```

The startup scripts are designed to launch the required services in separate terminal windows.

### 3. Manual Startup

#### Authentication API

```bash
cd database
python auth_api.py
```

#### Free Kick API

```bash
cd backend/hassaa/data
python freekick_api.py
```

#### Corner Kick API

```bash
cd backend/hassaa/data
python api_server.py
```

#### React Frontend

```bash
cd frontend
npm start
```

---

## 🧪 API Testing

The repository includes multiple test scripts for checking API connectivity and application flows.

Run:

```bash
python test_api_connections.py
```

Additional test files include:

```text
test_api_flow.py
test_signup.py
test_simple.py
```

---

## 🔄 How the System Works

A typical user workflow is:

```text
                User
                 │
                 ▼
          Authentication
                 │
                 ▼
           GamePlan AI
                 │
        ┌────────┼─────────┐
        ▼        ▼         ▼
     Analyze   Optimize   Simulate
     Strategy  Position   Strategy
        │        │         │
        └────────┼─────────┘
                 ▼
          Tactical Output
                 │
                 ▼
          Visual Simulation
```

### Example

A user can:

1. Sign into GamePlan AI.
2. Select a set-piece scenario.
3. Analyze available strategies.
4. Request optimized player positioning.
5. Select or modify a tactical setup.
6. Run a simulation.
7. Observe player movement and ball trajectory.
8. Review tactical insights and confidence information.

---

## 💡 What This Project Demonstrates

GamePlan AI demonstrates practical experience across several areas of modern software and AI development:

* End-to-end AI application development
* Machine learning integration
* Graph-based ML tooling with PyTorch Geometric
* REST API development
* React frontend development
* Multi-service backend architecture
* JWT-based authentication
* AI-assisted tactical decision making
* Interactive simulation
* API integration and testing
* Full-stack system design

Rather than being a standalone ML notebook, the project connects the AI/optimization components to a functional web application through multiple APIs.

---

## 🎓 Academic Project

**GamePlan AI** was developed as a **Final Year Project (FYP)**.

The project focuses on applying artificial intelligence and software engineering techniques to football tactical analysis, particularly **set-piece planning, player positioning, and simulation**.

---

## 🔮 Future Improvements

Potential extensions include:

* Real-time match data integration
* Computer vision-based player tracking
* Historical strategy performance analysis
* More advanced tactical optimization
* Larger football event datasets
* Live match scenario analysis
* Cloud-based model serving
* Improved simulation physics
* Automated strategy recommendation
* Coach/analyst dashboards
* Performance benchmarking across strategies

---

## 👨‍💻 Author

**Hassaan Ullah Khan**

BS Data Science
FAST National University of Computer and Emerging Sciences

GitHub:
https://github.com/HassaanUllahKhan11

---

## 📌 Repository

**GamePlan AI — Final Year Project**

https://github.com/HassaanUllahKhan11/gameplanai_fyp

---

⭐ If you find this project interesting, feel free to explore the source code and architecture.
