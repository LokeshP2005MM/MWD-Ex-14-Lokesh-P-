# Exp 14 - Fetch Student Details Using an API in React
## NAME: Lokesh P
## REG NO: 2305001015
## Aim
To develop a React application that fetches student details from a public REST API using the `fetch()` method and displays the details dynamically.

## Objectives
- To understand API integration in React.
- To use the `fetch()` method to retrieve data from an API.
- To implement asynchronous operations using `async` and `await`.
- To manage data using the `useState` hook.
- To display student details dynamically.

## Program

### App.jsx

```jsx
import { useState } from "react";
import "./App.css";

function App() {
  const [student, setStudent] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState("");

  async function getStudentDetails() {
    setLoading(true);
    setError("");
    setStudent(null);

    try {
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/users/2"
      );

      if (!response.ok) {
        throw new Error("Failed to fetch student details");
      }

      const data = await response.json();
      data.name = "Lokesh P";
      setStudent(data);

    } catch (err) {
      setError("Unable to load details. Please try again.");

    } finally {
      setLoading(false);
    }
  }

  return (
    <div className="container">
      <h1>Lokesh's Student Management System</h1>

      <p>Click the button to fetch student details from an API.</p>

      <button onClick={getStudentDetails} disabled={loading}>
        {loading ? "Loading..." : "View Details"}
      </button>

      {loading && <p>Fetching data from the API...</p>}

      {error && <p className="error">{error}</p>}

      {student && (
        <div className="student-card">
          <h2>Student Details</h2>
          <p><b>ID:</b> {student.id}</p>
          <p><b>Name:</b> {student.name}</p>
          <p><b>Email:</b> {student.email}</p>
          <p><b>City:</b> {student.address.city}</p>
        </div>
      )}
    </div>
  );
}

export default App;
```

### App.css

```css
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f1f5f9;
}

.container {
  max-width: 600px;
  margin: 60px auto;
  padding: 25px;
  text-align: center;
  background: white;
  border-radius: 12px;
}

h1 {
  color: #15803d;
}

button {
  background: green;
  color: white;
  border: none;
  padding: 12px 22px;
  border-radius: 6px;
  cursor: pointer;
  font-size: 16px;
}

button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.student-card {
  margin-top: 25px;
  padding: 20px;
  background: #dcfce7;
  border-radius: 8px;
  text-align: left;
}

.error {
  color: #dc2626;
}
```

### index.css

```css
body {
  margin: 0;
  font-family: Arial, sans-serif;
}
```

### main.jsx

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.jsx";
import "./index.css";

ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

## Output

The application displays the following details after clicking the View Details button:
<img width="1600" height="656" alt="WhatsApp Image 2026-11-06 at 11 30 25 AM" src="https://github.com/user-attachments/assets/0ca2e984-5ae2-4d72-9cbe-a658bce054bf" />


## Result

Thus, a React application was successfully developed to fetch student details from a public REST API using the `fetch()` method and display the customized student information dynamically.
