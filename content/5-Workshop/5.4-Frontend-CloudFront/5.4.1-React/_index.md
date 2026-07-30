---
title: "Build the React Dashboard"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.4.1. </b> "
---

#### Scaffold the app

```bash
cd frontend
npm create vite@latest .   # choose React
npm install
npm install axios recharts react-router-dom
```

#### API service

`src/services/api.js`:

```javascript
import axios from "axios";

const API_URL = "https://<api-id>.execute-api.ap-southeast-1.amazonaws.com/dev";

export const getStudents = () => axios.get(`${API_URL}/students`);
export const getPredictions = () => axios.get(`${API_URL}/predictions`);
export const predictRisk = (f) => axios.post(`${API_URL}/predict`, f);
export const createStudent = (s) => axios.post(`${API_URL}/students`, s);
export const updateStudent = (id, u) => axios.put(`${API_URL}/students/${id}`, u);
export const deleteStudent = (id) => axios.delete(`${API_URL}/students/${id}`);
```

#### Dashboard sections 

The dashboard is organized as a decision-support tool:

- **KPI cards** — total students, at-risk students, average exam score, average attendance.
- **Risk distribution** — pie chart (at-risk vs. safe).
- **High-risk table** — the students needing intervention.
- **Students page** — search, filter, pagination, and CRUD actions.
- **Predict page** — on-demand risk prediction without saving.

Before the ML endpoint exists, you can use temporary mock risk logic so the full frontend flow can be tested end-to-end; it is replaced by real predictions in section 5.5.

![Dashboard overview]( /fcj-workshop-template/images/5-Workshop/5.4-Frontend-CloudFront/dashboard.png)

#### Run locally

```bash
npm run dev
# http://localhost:5173
```
