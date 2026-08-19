# 🏙️ NYC Airbnb Room Type Predictor

A machine learning project that predicts the **room type of an Airbnb listing in New York City** using listing information such as location, price, reviews, minimum nights, and availability.

The project takes the model beyond a Jupyter Notebook by serving the trained model through a **FastAPI API** and connecting it to a simple web interface.

---

## 📌 Project Overview

The goal of this project is to build a multiclass classification model that predicts one of three Airbnb room types:

* **Entire home/apt**
* **Private room**
* **Shared room**

The project covers the complete machine learning workflow:

**Data → EDA → Preprocessing → Model Training → Evaluation → Saved Model → FastAPI → Web Interface**

---

## 📊 Dataset

The project uses the **New York City Airbnb Open Data** dataset.

The dataset contains information about Airbnb listings, including:

* Latitude & Longitude
* Neighbourhood
* Neighbourhood group
* Price
* Minimum nights
* Number of reviews
* Reviews per month
* Number of listings owned by the host
* Availability
* Room type

**Target variable:** `room_type`

---

## 🤖 Machine Learning

I experimented with multiple classification algorithms and compared their performance before selecting the final model.

The project includes:

* Exploratory Data Analysis
* Missing-value handling
* Numerical feature preprocessing
* Categorical feature encoding
* Train/test split
* Model comparison
* Cross-validation
* Hyperparameter tuning
* Feature importance analysis

The final model is a **Random Forest Classifier** integrated into a preprocessing pipeline.

The complete pipeline is saved using **Joblib**, allowing the same preprocessing steps used during training to be applied when making predictions.

---

## ⚙️ How It Works

```text
                    Airbnb Listing Data
                            │
                            ▼
                    Data Preprocessing
                            │
              ┌─────────────┴─────────────┐
              ▼                           ▼
       Numerical Features          Categorical Features
              │                           │
              └─────────────┬─────────────┘
                            ▼
                     ML Pipeline
                            │
                            ▼
                  Random Forest Model
                            │
                            ▼
                    Saved Model (.pkl)
                            │
                            ▼
                       FastAPI
                            │
                            ▼
                     Web Interface
                            │
                            ▼
              Room Type + Probabilities
```

---

## 🚀 FastAPI Backend

The trained model is exposed through a FastAPI backend.

### Endpoint

```text
POST /predict
```

The API receives listing information, validates the input using **Pydantic**, sends the data through the saved ML pipeline, and returns the predicted room type along with prediction probabilities.

Example response:

```json
{
  "Predicted_room_type": "Private room",
  "Probability": [0.21, 0.74, 0.05]
}
```

The probability values represent the model's estimated probability for each class.

---

## 🖥️ Frontend

A simple HTML, CSS, and JavaScript interface is included to interact with the API.

Users can enter listing information such as:

* Location
* Neighbourhood
* Price
* Minimum nights
* Reviews
* Reviews per month
* Host listing count
* Availability

The frontend sends the data to the FastAPI backend and displays the prediction.

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

| File                                        | Purpose                                           |
| ------------------------------------------- | ------------------------------------------------- |
| `nyc_airbnb_room_type_classification.ipynb` | EDA, preprocessing, model training and evaluation |
| `Model_Pipeline.pkl`                        | Saved preprocessing + trained model pipeline      |
| `main.py`                                   | FastAPI backend and prediction endpoint           |
| `index.html`                                | Frontend structure                                |
| `style.css`                                 | Frontend styling                                  |
| `script.js`                                 | Frontend/API interaction                          |
| `requirements.txt`                          | Python dependencies                               |

---

## 💻 Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/sufipvt/NYC-AIRBNB.git
cd NYC-AIRBNB
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it on Windows:

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

The API will run at:

```text
http://127.0.0.1:8000
```

FastAPI's interactive documentation is available at:

```text
http://127.0.0.1:8000/docs
```

### 5. Use the frontend

Open `index.html` in your browser and enter the Airbnb listing details to generate a prediction.

---

## 📚 What I Learned

This project helped me understand how an ML model can move beyond experimentation in a notebook and become an actual application.

Key takeaways:

* Building a complete ML classification workflow
* Working with numerical and categorical data
* Creating reusable Scikit-learn pipelines
* Model evaluation and tuning
* Saving and loading trained models
* Building prediction APIs with FastAPI
* Validating API inputs with Pydantic
* Connecting a frontend to an ML backend

The main lesson was that **training the model is only one part of building an ML application**. The model also needs to be packaged, served, and connected to something that can actually use it.



## 👨‍💻 Author

**Sufiyan Rizvi**

