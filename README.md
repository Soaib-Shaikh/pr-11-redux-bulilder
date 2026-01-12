# Redux User CRUD Application

A modern React + Redux Toolkit-based User Management System that handles all CRUD operations (Create, Read, Update, Delete).

---

## 📋 Project Overview

This project is a **User Management System** where you can:
- ✅ Add new users (Create)
- ✅ View all users list (Read)
- ✅ Update user information (Update)
- ✅ Delete users (Delete)

This application uses **Redux Toolkit** for state management and fetches data from **JSON Server**.

---

## 🛠️ Technology Stack

| Technology | Description |
|------------|-------------|
| **React** | JavaScript library for building user interfaces |
| **Redux Toolkit** | Simplified state management for Redux |
| **Redux Thunk** | Handles asynchronous API calls |
| **Vite** | Fast build tool and dev server |
| **Axios** | HTTP client for making requests |
| **Bootstrap 5** | CSS framework for styling |
| **JSON Server** | Mock REST API server |
| **React Router** | Client-side routing for navigation |

---

## ✨ Key Features

### 1. **User Signup/Registration** 📝
- Users can register with their information
- Form validation for data input

### 2. **User List View** 👥
- Display all registered users
- Show user details in a table format

### 3. **User Update** ✏️
- Edit existing user information
- Save updated data to database

### 4. **User Delete** 🗑️
- Remove users from the database

### 5. **Header Navigation** 🏠
- Easy navigation between different pages

---

## 🔄 How Redux Thunk Works

### What is Redux Thunk?
Redux Thunk is middleware that enables Redux to handle **asynchronous operations** (like API calls).

### How It Works:

```
User Dispatches Action
        ↓
Redux Thunk Middleware intercepts it
        ↓
Async Operation (API Call) is executed
        ↓
Response is received
        ↓
Data is sent to Redux Reducer
        ↓
State is updated
        ↓
Component receives new state
        ↓
UI re-renders
```

### Redux Data Flow in Your App:
1. **Dispatch Action** → `dispatch(getAllUsers())`
2. **Async Thunk** → Makes API call
3. **API Response** → Data comes back
4. **Reducer Updates** → State is updated
5. **Component Re-renders** → UI updates

---

## 📁 Project Structure

```
redux-user-crud/
├── src/
│   ├── app/
│   │   └── store.js              # Redux Store Configuration
│   ├── features/
│   │   └── user/
│   │       └── userSlice.js       # User Actions & Reducers
│   ├── api/
│   │   └── apiIntance.js          # Axios Instance Configuration
│   ├── components/
│   │   ├── Header.jsx             # Navigation Component
│   │   ├── Signup.jsx             # User Registration Form
│   │   └── ViewUser.jsx           # User List & Edit View
│   ├── App.jsx                    # Main App Component
│   ├── main.jsx                   # Entry Point
│   └── index.css                  # Global Styles
├── db.json                        # JSON Server Database
├── package.json                   # Project Dependencies
├── vite.config.js                 # Vite Configuration
├── eslint.config.js               # ESLint Rules
└── README.md                      # This File
```

---

## 🚀 Installation Guide

### Step 1: Clone/Download the Project
```bash
# If cloning from Git
git clone <https://github.com/Soaib-Shaikh/pr-11-redux-bulilder.git>
cd redux-user-crud
```

### Step 2: Install Dependencies
```bash
# Using npm
npm install

# Using bun (faster)
bun install

# Using yarn
yarn install
```

### Step 3: Start JSON Server (Database)
```bash
# Run in a separate terminal
npx json-server --watch db.json --port 5000
```

### Step 4: Start Development Server
```bash
# Run in another terminal
npm run dev
# or
bun run dev
```

**Application will open at:** `http://localhost:5173`

---

## 📦 Available Commands

```bash
# Start development server
npm run dev

# Build for production
npm run build

# Check code quality with ESLint
npm run lint

# Preview production build
npm run preview

# Start JSON Server (in separate terminal)
npx json-server --watch db.json --port 5000
```

---

## 🔧 Configuration Files

### `vite.config.js`
Vite build tool configuration for fast bundling and HMR

### `eslint.config.js`
ESLint rules for maintaining code quality

### `db.json`
JSON Server database file - stores all user data

### `package.json`
Project dependencies and npm scripts

---

## 💡 Redux Store Setup

```javascript
// app/store.js
import { configureStore } from "@reduxjs/toolkit";
import userReducer from "../features/user/userSlice.js"

const store = configureStore({
    reducer : {
        users : userReducer  // users slice
    }
})

export default store;
```

---

## 🔌 API Endpoints

This application uses the following REST API endpoints:

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/users` | Fetch all users |
| POST | `/users` | Create a new user |
| PATCH | `/users/:id` | Update a user by ID |
| DELETE | `/users/:id` | Delete a user by ID |

---

## 📝 Database Schema (db.json)

```json
{
  "users": [
    {
      "id": 1,
      "name": "John Doe",
      "email": "john@example.com",
      "phone": "9876543210",
      "city": "Delhi"
    },
    {
      "id": 2,
      "name": "Jane Smith",
      "email": "jane@example.com",
      "phone": "9876543211",
      "city": "Mumbai"
    }
  ]
}
```

---

## 🎯 How to Use the Application

### 1. **Open Home Page**
- Navigate to `http://localhost:5173`

### 2. **Add a New User**
- Go to Signup page
- Fill in user details (name, email, phone, city)
- Click "Sign Up" button
- User will be added to the database

### 3. **View All Users**
- Click on "View Users" or "Users List"
- See all registered users in a table

### 4. **Edit a User**
- Click Edit button next to a user
- Modify the information
- Click Save to update

### 5. **Delete a User**
- Click Delete button next to a user
- User will be removed from the database

---

## 🐛 Troubleshooting

### JSON Server won't start?
```bash
# Port 5000 might be in use by another service
# Try running on a different port:
npx json-server --watch db.json --port 5001

# Then update your API instance URL in src/api/apiIntance.js
```

### API Connection Error?
- Verify JSON Server is running
- Check if `src/api/apiIntance.js` has the correct API URL
- Ensure the port numbers match (default: 5000)

### Dependencies won't install?
```bash
# Clear npm cache
npm cache clean --force

# Remove node_modules and package-lock.json
rm -rf node_modules package-lock.json

# Reinstall dependencies
npm install
```

### Port 5173 already in use?
```bash
# Vite will automatically use next available port
# Check terminal output for the actual URL
# Or manually specify port:
npm run dev -- --port 3000
```

---

## 📚 Complete CRUD Operations

### Create (POST)
```javascript
dispatch(createUser({
  name: "John Doe",
  email: "john@example.com",
  phone: "9876543210",
  city: "Delhi"
}))
```

### Read (GET)
```javascript
dispatch(getAllUsers())
```

### Update (PATCH)
```javascript
dispatch(updateUser({
  id: 1,
  name: "Jane Doe",
  email: "jane@example.com",
  phone: "9876543211",
  city: "Mumbai"
}))
```

### Delete (DELETE)
```javascript
dispatch(deleteUser(1))
```

---

## 🔗 Useful Resources

- **Redux Toolkit Documentation**: https://redux-toolkit.js.org/
- **React Documentation**: https://react.dev/
- **Vite Documentation**: https://vitejs.dev/
- **JSON Server**: https://github.com/typicode/json-server
- **Axios Documentation**: https://axios-http.com/
- **Bootstrap Documentation**: https://getbootstrap.com/

---

## 🎓 Learning Outcomes

By working with this project, you'll learn:
- ✅ State management with Redux Toolkit
- ✅ Asynchronous operations with Redux Thunk
- ✅ React hooks (useState, useEffect, useDispatch, useSelector)
- ✅ REST API integration with Axios
- ✅ Component-based architecture
- ✅ React Router for navigation
- ✅ Form handling and validation

---

## 📄 License

This project is created for learning and educational purposes.

---

## 🚀 Getting Started Checklist

- [ ] Clone/download the repository
- [ ] Install dependencies with `npm install`
- [ ] Start JSON Server with `npx json-server --watch db.json --port 5000`
- [ ] Start development server with `npm run dev`
- [ ] Open browser and go to `http://localhost:5173`
- [ ] Create a new user via signup
- [ ] View all users
- [ ] Edit a user
- [ ] Delete a user

---

**Last Updated:** January 2026
**Version:** 1.0.0
