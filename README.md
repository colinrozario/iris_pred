
# Iris Flower Prediction (Streamlit)

This project contains a simple Streamlit web application that predicts the species of an Iris flower based on four numeric measurements (sepal length, sepal width, petal length, petal width). The app trains a RandomForestClassifier on the classic scikit-learn Iris dataset and displays the predicted class and probability.

---

## Features ✅

- Simple UI built with `streamlit`.
- Trains a `RandomForestClassifier` on the fly using scikit-learn's built-in Iris dataset.
- Interactive sliders for the four input features in the sidebar.
- Shows predicted species and prediction probabilities.

---

## Files

- `iris_pred.py` - main Streamlit app. This trains the classifier and exposes an interactive UI.

---

## Install dependencies

Install needed libraries using pip. Either use `requirements.txt` (if you add one), or the one-liner below:

```powershell
pip install streamlit scikit-learn pandas
```

---

## Run the app 🚀

Start the Streamlit development server from the project directory:

```powershell
streamlit run iris_pred.py
```

Open the URL printed to your terminal (usually http://localhost:8501) in your browser. Use the sidebar sliders to change the input values and see the predictions update in real time.

If port 8501 is busy, you can set a different port:

```powershell
streamlit run iris_pred.py --server.port 8502
```

---

## How it works — quick summary 💡

1. The app uses scikit-learn's `load_iris` dataset (no external data file).
2. A `RandomForestClassifier` is trained in the app on the full dataset (X and y from `load_iris`).
3. The four slider values from the sidebar are assembled into a DataFrame and used to call `predict` and `predict_proba`.
4. The chosen label and its probability are displayed below the sliders.

Note: the model is trained every time the app runs — this is fine for demo/personal use but for production you would train and save a model (for example with `joblib`) and then load it.

---

## Tips & Troubleshooting ⚠️

- If Streamlit doesn’t show updates after changing sliders: try reloading the browser page or running the app with `streamlit run iris_pred.py --logger.level debug` to view logs.
- If you want to save the trained model, add a small script or extend `iris_pred.py` using `joblib.dump(clf, 'model.joblib')` and load with `joblib.load('model.joblib')`.
- For Windows PowerShell, if `streamlit` command is not found after venv activation, make sure your PATH includes `\.venv\Scripts` and/or use the Python -m form:

```powershell
.\.venv\Scripts\python -m streamlit run iris_pred.py
```

### Fix for "ModuleNotFoundError: No module named 'sklearn'"

If you get an error saying `No module named 'sklearn'` (or `ModuleNotFoundError` referencing `sklearn`), do the following:

1. Add a `requirements.txt` to your repository containing required packages. For example:

```
streamlit
scikit-learn
pandas
```

2. If you're running locally, install dependencies with pip:

```powershell
pip install -r requirements.txt
```

3. If deploying on Streamlit Cloud, push the `requirements.txt` to your repo and redeploy — Streamlit Cloud installs the packages listed there during deployment.

4. The app has an import check; if scikit-learn is missing the app will show a readable message instead of crashing. If the message persists after you have added `requirements.txt`, re-check logs in Streamlit Cloud (Manage app → Logs) or verify which environment your app runs in.

---

## Contributing 🤝

This is a small demo project; contributions are welcome. You might add:

- A `requirements.txt` file with pinned package versions
- A saved model and load-once pattern instead of training on every start
- Unit tests for helper functions
