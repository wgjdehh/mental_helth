Mental Health Score
Predicts a "mental health score" (0-10) for students based on their social media use, sleep, study hours, and stress. Trained a regression model on a student survey dataset and wrapped it in a simple form + API.

Not a diagnostic tool. Just a model finding patterns in self-reported habits vs wellbeing. Don't use it to actually assess anyone.

What it does
Fill in a form (age, country, screen time, sleep, stress level, etc.), it runs those through the trained model, and gives back a predicted score. FastAPI backend, plain HTML/CSS/JS frontend, no framework.

Stack
FastAPI + Pydantic on the backend, model loaded with joblib
Vanilla HTML/CSS/JS frontend, no build step
Trained in a Jupyter notebook with pandas + scikit-learn

Files
main.py — API and prediction endpoint
Mental_Health_Model.pkl — the trained model
Student Social Media And Mental Health Impact.csv — training data
ML_Project.ipynb — training/EDA notebook
index.html, style.css, script.js — frontend
requirements.txt — backend deps

API
GET / — health check
POST /predict — takes a student profile, returns a predicted score

About the model
Trained on the included CSV. Countries outside the top few in the dataset get grouped into "Other" before prediction — see top_countries in main.py.

Deployment
Backend on Render (uvicorn main:app --host 0.0.0.0 --port $PORT), frontend as a static site. Update API_BASE in script.js if you point it at your own backend. Render's free tier sleeps when idle, so the first request can be slow.

Limitations
Dataset is self-reported, so treat predictions as a rough signal, not ground truth
Only handles the platforms/countries/stress levels in the dropdowns
No auth, no database — built as a learning project, not production software

Disclaimer
Student project exploring regression on a public dataset. Not clinical or diagnostic. If you're struggling, talk to a real person — a counselor, doctor, or someone you trust.
