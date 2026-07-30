---
title: "Connect Predictions to the Dashboard"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.5.4. </b> "
---

Replace the temporary mock risk logic with real predictions. Add a `getPredictionsFunction` (`GET /predictions`) that reads `prediction_results`, then join it with `student_records` by `student_id` in the frontend.

```javascript
// merge students with predictions
const predMap = {};
predictions.forEach((p) => { predMap[String(p.student_id)] = p; });
const merged = students.map((s) => {
  const pred = predMap[String(s.student_id)];
  return { ...s, at_risk: pred ? pred.prediction : s.at_risk,
                 probability: pred ? pred.probability : null };
});
```

The dashboard now shows real ML risk levels and probabilities, the Add-Student form runs a live prediction, and the Predict page runs on-demand inference.

![Dashboard with real predictions]( /images/5-Workshop/5.5-ML/dashboard-predictions.png)

Rebuild and redeploy the frontend, then invalidate the CloudFront cache (section 5.4.2).