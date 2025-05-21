Here's a complete `README.md` file for your **React + Django Portfolio Website** with navigation that doesn’t reload the page. It includes **all setup steps and commands** for both frontend and backend.

---

```markdown
# React + Django Portfolio Website

This is a simple portfolio website built using **React** (frontend) and **Django** (backend). It includes multiple pages (`Home`, `About`, `Skills`, `Contact`) and a navigation bar that allows switching pages **without reloading** using React Router.

---

## 📁 Project Structure

```

myportfolio/
│
├── backend/        ← Django Project
└── frontend/       ← React Project

````

---

## 🚀 Backend (Django)

### 1. Create Django Project

```bash
cd myportfolio
django-admin startproject backend
cd backend
python3 -m venv venv
source venv/bin/activate
pip install django djangorestframework
````

### 2. Enable CORS in `backend/settings.py`

```python
INSTALLED_APPS = [
    ...
    'corsheaders',
    'rest_framework',
]

MIDDLEWARE = [
    'corsheaders.middleware.CorsMiddleware',
    ...
]

CORS_ORIGIN_WHITELIST = [
    'http://localhost:3000',
]
```

### 3. Migrate and Run Server

```bash
python manage.py migrate
python manage.py runserver 8080
```

Server will run at: [http://localhost:8080](http://localhost:8080)

---

## 🌐 Frontend (React)

### 1. Create React App

```bash
cd ../
npx create-react-app frontend
cd frontend
```

### 2. Install React Router

```bash
npm install react-router-dom
```

### 3. Create Pages

Inside `frontend/src`, create:

* `Home.js`
* `About.js`
* `Skills.js`
* `Contact.js`

Each file should contain:

```jsx
import React from 'react';

function Home() {
  return <h1>This is the Home Page</h1>;
}

export default Home;
```

(Replace `Home` with `About`, `Skills`, `Contact` for each file accordingly.)

---

### 4. Configure Routing and Navbar in `App.js`

```jsx
import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';
import Home from './Home';
import About from './About';
import Skills from './Skills';
import Contact from './Contact';

function App() {
  return (
    <Router>
      <nav style={{ padding: '10px', background: '#eee' }}>
        <Link to="/" style={{ margin: '10px' }}>Home</Link>
        <Link to="/about" style={{ margin: '10px' }}>About</Link>
        <Link to="/skills" style={{ margin: '10px' }}>Skills</Link>
        <Link to="/contact" style={{ margin: '10px' }}>Contact</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/skills" element={<Skills />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </Router>
  );
}

export default App;
```

---

### 5. Fix File Watcher Error (if any)

If you get this error:

```
ENOSPC: System limit for number of file watchers reached
```

Run the following:

```bash
sudo nano /etc/sysctl.conf
```

Add this line at the end:

```
fs.inotify.max_user_watches=524288
```

Then:

```bash
sudo sysctl -p
sudo reboot  # optional, for safety
```

---

### 6. Start React Development Server

```bash
npm start
```

App will open at: [http://localhost:3000](http://localhost:3000)

---

## ✅ Features

* React SPA navigation (no page reloads)
* Separate React and Django codebases
* Ready to be extended with API integration

---

## 🛠 Next Steps

* Add CSS for layout and styles
* Connect backend APIs (skills, contact form)
* Deploy with Nginx + Gunicorn + build React app

---

## 📌 Notes

* React runs at `http://localhost:3000`
* Django runs at `http://localhost:8080`

```

---

Let me know if you'd like this `README.md` saved as a downloadable file or extended with backend API integration instructions!
```
