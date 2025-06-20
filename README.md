# 🚀 Smart Task Manager

A lightweight yet powerful task manager built using **Node.js + Express.js (backend)** and **MongoDB (database)** with a clean HTML, CSS, and JavaScript frontend. It supports full CRUD operations through a RESTful API.

---

## 🔗 Features

* ✅ Add tasks with a title and description
* 📋 View all tasks
* 🔄 Mark tasks as complete/incomplete
* 🗑️ Delete tasks
* 🔗 Interact via frontend UI or REST API

---

## 🛠 Tech Stack

| Component | Technology                       |
| --------- | -------------------------------- |
| Frontend  | HTML, CSS, JavaScript, Bootstrap |
| Backend   | Node.js, Express.js              |
| Database  | MongoDB with Mongoose ODM        |

---

## 📦 APIs & Their Functionality

### 1. **GET /api/tasks**

* **Description**: Fetches all tasks from the database
* **Response**:

```json
[
  {
    "_id": "666abc123",
    "title": "Read a book",
    "description": "Finish chapter 4",
    "completed": false
  }
]
```

---

### 2. **POST /api/tasks**

* **Description**: Adds a new task to the database
* **Request Body**:

```json
{
  "title": "Buy groceries",
  "description": "Milk, eggs, bread",
  "completed": false
}
```

* **Response**:

```json
{
  "_id": "666def456",
  "title": "Buy groceries",
  "description": "Milk, eggs, bread",
  "completed": false
}
```

---

### 3. **PUT /api/tasks/\:id**

* **Description**: Toggles the completion status of a task
* **Request Body**:

```json
{
  "completed": true
}
```

* **Response**: Updated task object

---

### 4. **DELETE /api/tasks/\:id**

* **Description**: Deletes a task by its ID
* **Response**:

```json
{
  "message": "Task deleted successfully"
}
```

---

## 📃 Database Used: MongoDB

We use **MongoDB Atlas** for cloud database storage and **Mongoose** for object modeling.

### 🔌 Integration in `server.js`:

```js
const mongoose = require('mongoose');
mongoose.connect(process.env.MONGO_URI)
  .then(() => console.log("MongoDB connected"))
  .catch((err) => console.error("Connection failed:", err));
```

### 🧱 Sample Mongoose Schema:

```js
const taskSchema = new mongoose.Schema({
  title: String,
  description: String,
  completed: Boolean
});
module.exports = mongoose.model("Task", taskSchema);
```

---

## ⚙️ How to Run the Server Locally

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/task-manager-app.git
cd task-manager-app
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Create `.env` File

Add your MongoDB connection URI:

```
MONGO_URI=your_mongo_connection_string
PORT=5000
```

### 4. Start the Server

```bash
node server.js
# or
nodemon server.js
```

Server runs at: `http://localhost:5000`

---

## 💻 How to Run the Frontend 

1. Open `index.html` in your browser
2. Or use Live Server in VSCode 

The frontend connects to the API via `fetch()` calls to `http://localhost:5000/api/tasks`

---

## 📬 How to Interact with the API

### ➕ Add a Task

```bash
curl -X POST http://localhost:5000/api/tasks \
  -H "Content-Type: application/json" \
  -d '{"title":"Study","description":"Revise Node.js","completed":false}'
```

### 📋 View All Tasks

```bash
curl http://localhost:5000/api/tasks
```

### ✅ Toggle Completion

```bash
curl -X PUT http://localhost:5000/api/tasks/<task_id> \
  -H "Content-Type: application/json" \
  -d '{"completed":true}'
```

### 🗑️ Delete a Task

```bash
curl -X DELETE http://localhost:5000/api/tasks/<task_id>
```

---

## 👍 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.

---
