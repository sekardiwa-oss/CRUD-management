# Task Manager — Full-Stack CRUD App

A full-stack task management application built with:
- **Backend:** Node.js, Express, MongoDB (Mongoose)
- **Frontend:** React (Vite), Axios
- **Features:** Create, Read, Update, Delete tasks with status, priority, and due dates.

---

## Project Structure
```
taskmanager/
├── backend/
│   ├── models/Task.js
│   ├── routes/tasks.js
│   ├── server.js
│   ├── package.json
│   └── .env
└── frontend/
    ├── src/
    │   ├── components/TaskForm.jsx
    │   ├── components/TaskList.jsx
    │   ├── components/TaskItem.jsx
    │   ├── App.jsx
    │   ├── main.jsx
    │   ├── api.js
    │   └── index.css
    ├── index.html
    ├── vite.config.js
    └── package.json
```

---

## Prerequisites
- **Node.js** (v18+) and npm installed
- **MongoDB** installed locally OR a free MongoDB Atlas cluster (cloud)

---

## 1. Backend Setup

```bash
cd taskmanager/backend
npm install
```

### Configure MongoDB connection
Edit the `.env` file:
```
PORT=5000
MONGO_URI=mongodb://localhost:27017/taskmanager
```
- If using **MongoDB Atlas**, replace `MONGO_URI` with your Atlas connection string, e.g.:
  ```
  MONGO_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/taskmanager
  ```

### Start MongoDB locally (if using local DB)
```bash
mongod
```
(Or just ensure your MongoDB service is running.)

### Run the backend server
```bash
npm start
```
You should see:
```
MongoDB connected successfully
Server running on port 5000
```

The API is now available at `http://localhost:5000/api/tasks`.

---

## 2. Frontend Setup

Open a **new terminal window**:

```bash
cd taskmanager/frontend
npm install
npm run dev
```

Vite will start the dev server (usually at `http://localhost:3000`). Open that URL in your browser.

---

## 3. Using the App
- Fill in the form (title required) and click **Add Task** to create a task.
- Tasks appear as cards below, filterable by status (All / Pending / In Progress / Completed).
- Click **Edit** to modify a task, **Delete** to remove it.
- Use the status dropdown on each card to quickly update progress.

---

## API Endpoints (Backend)

| Method | Endpoint           | Description          |
|--------|---------------------|----------------------|
| GET    | `/api/tasks`        | Get all tasks        |
| GET    | `/api/tasks/:id`    | Get a single task    |
| POST   | `/api/tasks`        | Create a new task    |
| PUT    | `/api/tasks/:id`    | Update a task        |
| DELETE | `/api/tasks/:id`    | Delete a task        |

### Example task object
```json
{
  "title": "Finish report",
  "description": "Complete quarterly report",
  "status": "pending",
  "priority": "high",
  "dueDate": "2026-06-20"
}
```

---

## Troubleshooting
- **"Failed to fetch tasks"**: Ensure the backend (`npm start` in `/backend`) is running on port 5000.
- **MongoDB connection error**: Confirm `mongod` is running locally, or that your Atlas connection string/IP whitelist is correct.
- **Port conflicts**: Change `PORT` in `backend/.env` and update `API_URL` in `frontend/src/api.js` accordingly.
