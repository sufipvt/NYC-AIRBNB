# 🏙️ NYC Airbnb Room Type Predictor

A machine learning application that predicts the **room type of an Airbnb listing in New York City** based on features such as location, price, reviews, minimum nights, and availability.

The project covers the complete workflow from **data analysis and model training to API development, frontend integration, and deployment**.

## 🌐 Live Demo

**Frontend:**
https://nyc-airbnb-1-9me0.onrender.com

**Backend API:**
https://nyc-airbnb-80qd.onrender.com

**API Documentation:**
https://nyc-airbnb-80qd.onrender.com/docs

---

## 🎯 Project Goal

The goal is to build a multiclass classification model that predicts one of three Airbnb room types:

* **Entire home/apt**
* **Private room**
* **Shared room**

The application allows a user to enter listing information and receive a predicted room type along with the model's probability for each class.

---

## 📊 Dataset

The project uses the **New York City Airbnb Open Data** dataset.

The dataset contains information about Airbnb listings, including:

* Latitude and longitude
* Neighbourhood
* Neighbourhood group
* Price
* Minimum nights
* Number of reviews
* Reviews per month
* Host listing count
* Availability
* Room type

**Target variable:** `room_type`

---

## 🤖 Machine Learning

The project follows a complete supervised machine learning workflow:

* Exploratory Data Analysis
* Data cleaning
* Missing-value handling
* Feature preprocessing
* Numerical feature scaling
* Categorical feature encoding
* Train/test split
* Model comparison
* Cross-validation
* Hyperparameter tuning
* Model evaluation
* Feature importance analysis

The final model uses a **Random Forest Classifier** inside a Scikit-learn preprocessing pipeline.

The complete pipeline is saved using **Joblib** and reused by the backend for predictions.

---

## ⚙️ Project Workflow

```text
Airbnb Dataset
      ↓
Data Cleaning & EDA
      ↓
Feature Preprocessing
      ↓
Model Training & Evaluation
      ↓
Random Forest Pipeline
      ↓
Saved Model
      ↓
FastAPI Backend
      ↓
Frontend
      ↓
Room Type Prediction
```

---

## 🔌 FastAPI Backend

The trained model is served through a **FastAPI** backend.

### Main Endpoint

```text
POST /predict
```

The API:

1. Receives listing information
2. Validates the input using **Pydantic**
3. Passes the data through the saved ML pipeline
4. Generates the prediction
5. Returns the predicted room type and class probabilities

Example response:

```json
{
  "Predicted_room_type": "Private room",
  "Probability": [0.21, 0.74, 0.05]
}
```

The probability values represent the model's predicted probability for each room-type class.

### Interactive API Documentation

FastAPI automatically provides interactive API documentation:

https://nyc-airbnb-80qd.onrender.com/docs

---

## 🖥️ Frontend

The project includes a simple web interface built with:

* HTML
* CSS
* JavaScript

Users can enter details such as:

* Location
* Neighbourhood
* Price
* Minimum nights
* Number of reviews
* Reviews per month
* Host listing count
* Availability

The frontend sends the data to the deployed FastAPI backend and displays the prediction.

---

## 🛠️ Tech Stack

### Machine Learning

* Python
* Pandas
* NumPy
* Scikit-learn
* Joblib
* Matplotlib
* Seaborn

### Backend

* FastAPI
* Pydantic
* Uvicorn

### Frontend

* HTML
* CSS
* JavaScript

### Deployment

* Render

---

## 📁 Project Structure

```text
NYC-AIRBNB/
│
├── nyc_airbnb_room_type_classification.ipynb
├── Model_Pipeline.pkl
│
├── main.py
│
├── index.html
├── style.css
├── script.js
│
├── requirements.txt
├── runtime.txt
└── .gitignore
```

### Key Files

| File                                        | Description                                                 |
| ------------------------------------------- | ----------------------------------------------------------- |
| `nyc_airbnb_room_type_classification.ipynb` | Data analysis, preprocessing, model training and evaluation |
| `Model_Pipeline.pkl`                        | Saved preprocessing and ML model pipeline                   |
| `main.py`                                   | FastAPI backend and prediction endpoint                     |
| `index.html`                                | Frontend structure                                          |
| `style.css`                                 | Frontend styling                                            |
| `script.js`                                 | Frontend and API interaction                                |
| `requirements.txt`                          | Project dependencies                                        |

---

## 🚀 Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/sufipvt/NYC-AIRBNB.git
cd NYC-AIRBNB
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

On Windows:

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Start the FastAPI server

```bash
uvicorn main:app --reload
```

The backend will be available at:

```text
http://127.0.0.1:8000
```

API documentation:

```text
http://127.0.0.1:8000/docs
```

### 5. Open the frontend

Open `index.html` in your browser and enter the Airbnb listing details.

---

## 📚 What I Learned

This project helped me understand how to take a machine learning model from experimentation to a usable application.

Key takeaways:

* Building a complete ML classification workflow
* Working with numerical and categorical features
* Creating reusable Scikit-learn pipelines
* Model comparison and hyperparameter tuning
* Saving and loading trained models
* Building APIs with FastAPI
* Validating inputs with Pydantic
* Connecting a frontend with an ML backend
* Deploying an ML application using Render

The main lesson was that **training a model is only one part of an ML project**. The model also needs to be packaged, served through an API, connected to an interface, and deployed so that it can actually be used.

---

## 🔮 Future Improvements

* Add automated API tests
* Dockerize the application
* Improve model monitoring
* Experiment with additional classification models
* Add model versioning
* Improve the frontend experience
* Set up automated deployment/CI

---

## 👨‍💻 Author

**Sufiyan Rizvi**

GitHub: https://github.com/sufipvt

---

## 📜 License

This project is intended for educational and portfolio purposes.
