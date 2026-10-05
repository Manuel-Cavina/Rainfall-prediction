# Rainfall Prediction in the Melbourne Area

## What is this project about?

This project uses historical weather data to answer a simple question:

**Will it rain tomorrow in the Melbourne area?**

It is based on the final assignment from IBM's **Machine Learning with Python** course. It was developed in Google Colab and can also be run in VS Code.

The study uses observations from three weather stations: **Melbourne, Melbourne Airport, and Watsonia**.

## How does it work?

A machine learning model learns patterns from past weather observations, such as temperature, humidity, wind, and pressure.

The value we want to predict is called the **target**. In this dataset, the target is `RainTomorrow`:

- `Yes`: it rained the next day.
- `No`: it did not rain the next day.

Predicting a category is called **classification**. The models also estimate the probability of rain.

## Main steps

| Step | What we do and why |
| --- | --- |
| 1. Explore the data | Check the columns, weather stations, and missing values. |
| 2. Clean the data | Prepare dates and remove unusable records, keeping a record of the reasons. |
| 3. Split the data | Use earlier dates for training and later dates for testing. This helps us evaluate predictions on observations the model has not seen. |
| 4. Prepare the inputs | Fill missing weather values and convert text categories into numbers. Learn these transformations from training data only. |
| 5. Train and compare models | Compare logistic regression and Random Forest using validation periods within the training data. |
| 6. Evaluate predictions | Check the final predictions on the test data, including missed rain and false alarms. |

We also use a **baseline**: a simple model that always predicts the most common training category. It gives us a starting point for comparison.

## Tools

- **Python:** programming language.
- **pandas and NumPy:** organize and process data.
- **Matplotlib and seaborn:** create charts.
- **scikit-learn:** prepare data, train models, and evaluate predictions.
- **Google Colab / VS Code:** run the notebook.

## Project files

| File or folder | Purpose |
| --- | --- |
| `notebooks/` | Contains the `.ipynb` notebook: code, explanations, and charts. |
| `requirements.txt` | Lists the Python libraries needed to run the project. |
| `rainfall_project_outputs/` | Stores exported results and supporting records. |
| `certificates/` | Stores the course certificate. |

Add your downloaded Colab notebook and certificate to their folders; they are not included in this starter package.

## Run in VS Code on Windows

1. Install Python and the **Python** and **Jupyter** extensions in VS Code.
2. Open the project folder and its terminal.
3. Run these commands:

```powershell
py -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
```

The first command creates a separate Python environment for the project. The second installs its libraries.

4. Open the notebook in `notebooks/`.
5. Select `.venv` as the notebook's **kernel** — the Python environment that runs the code.
6. Run the cells in order. Internet access is needed to download the dataset.

If `py` is unavailable, try `python -m venv .venv` for the first command.

In VS Code, skip the final cell that uses `google.colab.files.download`. That cell downloads the results ZIP in Colab; the previous export cell already saves it locally.

## Results and limitations

Results will be added after reviewing the executed notebook. No performance scores are reported yet.

This is an educational project using historical data. Its results do not establish how well it will predict future weather or work in other regions.

## Sources

- [IBM Machine Learning with Python — Coursera](https://www.coursera.org/learn/machine-learning-with-python)
- [Australian weather dataset referenced in the assignment](https://www.kaggle.com/datasets/jsphyg/weather-dataset-rattle-package/)
