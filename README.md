# 🏠 HomeValue AI — House Price Prediction

## 1. Project Name

**HomeValue AI — House Price Prediction System**

HomeValue AI is a machine learning-based web application that predicts house prices based on property characteristics such as area, location, bedrooms, bathrooms, property age, and available amenities. It provides an interactive interface built with Streamlit, featuring property comparisons, visualizations, and price insights.

## 2. Problem Statement

Estimating house prices accurately can be challenging because property values depend on several factors, including size, location, property age, and available facilities.

Manual estimation can be time-consuming and inconsistent. HomeValue AI addresses this problem by using machine learning regression models to estimate property prices based on the provided features.

## 3. Solution

HomeValue AI provides an interactive web application that allows users to enter property details and receive an estimated house price.

The application includes:

- House price prediction using a trained regression model.
- Property comparison to evaluate two properties side by side.
- Rule-based explanations describing factors that may influence the estimate.
- Interactive charts and dataset insights.
- Locality-based property comparisons.
- Indian Rupee formatting with Lakh and Crore representations.
- Dynamic house illustrations based on price ranges and selected amenities.
- Dark and light theme support.
- An animated price-reveal interface.

The system is designed for educational and demonstration purposes and does not replace professional property valuation.

## 4. Technologies Used

- **Programming Language:** Python
- **Data Processing:** pandas, NumPy
- **Machine Learning:** scikit-learn, XGBoost
- **Data Visualization:** Matplotlib, Seaborn, Plotly
- **Web Framework:** Streamlit
- **Model Persistence:** joblib
- **Frontend:** HTML, CSS, JavaScript, SVG

## 5. AI Model

The project uses machine learning regression algorithms to estimate house prices.

The models evaluated include:

1. Linear Regression
2. Random Forest Regressor
3. XGBoost Regressor

### Model Evaluation Results

| Model | MAE | RMSE | R² Score |
|---|---:|---:|---:|
| Linear Regression | ~23,479 | ~39,339 | 0.903 |
| Random Forest | ~22,607 | ~38,441 | 0.907 |
| XGBoost | ~20,726 | ~37,015 | 0.914 |

**Best-performing model:** XGBoost Regressor, based on the recorded evaluation results.

- **MAE:** Measures the average absolute difference between actual and predicted prices.
- **RMSE:** Measures prediction errors while assigning greater weight to larger errors.
- **R² Score:** Indicates how well the model explains variation in the target values.

The trained model is saved in `Model/house_price_model.pkl`, with associated information stored in `Model/model_metadata.json`.

**Model version and license:** The exact XGBoost package version should be verified from the installed environment. XGBoost is an open-source project distributed under the Apache License 2.0. See the [XGBoost repository](https://github.com/dmlc/xgboost) and [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

The reported metrics are based on a synthetic dataset and do not guarantee equivalent accuracy on real-world property data.

## 6. AI Integration

AI is integrated into the project through a trained machine learning regression model.

The application follows this workflow:

1. The user enters property details.
2. The application processes the input features.
3. The trained XGBoost pipeline generates a price prediction.
4. The predicted value is formatted and displayed in Indian Rupees.
5. Rule-based explanations describe relevant property characteristics.
6. Interactive visualizations help users explore property data and compare estimates.

The prediction system uses a trained machine learning model rather than a generative AI API. Any AI-assisted coding used during development should be disclosed according to the applicable project guidelines.

## 7. Installation and Usage

### Prerequisites

- Python 3.10 or a compatible version supported by the project's dependencies.
- pip package installer.
- Git, if cloning the repository.

### Step 1: Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd HomeValue_AI
```

Alternatively, download and extract the repository ZIP file.

### Step 2: Install Dependencies

```bash
pip install -r Streamlit_App/requirements.txt
```

### Step 3: Train the Model (Optional)

If you want to regenerate the dataset and train the models, run:

```bash
python Dataset/generate_dataset.py
python Notebook/train_pipeline.py
```

This process generates the dataset, performs preprocessing and feature engineering, evaluates the regression models, and saves the trained model and related artifacts.

If a compatible trained model and its required files are already included, you can skip retraining.

### Step 4: Run the Application

From the project root directory, execute:

```bash
streamlit run Streamlit_App/app.py
```

Open the local URL shown in the terminal, usually:

`http://localhost:8501`

### Step 5: Use the Application

- Enter the required property details.
- Generate a house price prediction.
- Select **Reveal My Estimate** to view the result.
- Use **Compare Properties** to compare two properties.
- Explore the Insights dashboard.
- Switch between dark and light themes.

### Currency Conversion

The model uses the original price units of the synthetic dataset. The application converts displayed predictions using a fixed conversion rate configured in `Streamlit_App/utils.py`.

The default setting is:

```python
USD_TO_INR = 83
```

This is a demonstration conversion rate and is not updated automatically using live exchange rates.

## 8. Dataset

The project uses a synthetic dataset containing approximately 2,000 generated records. It includes missing values, duplicate rows, and outliers to demonstrate data preprocessing.

### Input Features

| Feature | Description |
|---|---|
| `area_sqft` | Property area in square feet |
| `location` | Property locality |
| `bedrooms` | Number of bedrooms |
| `bathrooms` | Number of bathrooms |
| `age_years` | Property age in years |
| `garage` | Garage availability |
| `garden` | Garden availability |
| `pool` | Swimming pool availability |
| `near_school` | Proximity to a school |
| `distance_to_city_km` | Distance from the city in kilometres |

**Target variable:** `price`

The dataset is intended for learning and demonstration. It does not represent verified property listings or current market prices.

## 9. Project Structure

```text
HomeValue_AI/
├── Dataset/
│   ├── generate_dataset.py
│   ├── house_data.csv
│   └── house_data_cleaned.csv
├── Notebook/
│   └── train_pipeline.py
├── Model/
│   ├── house_price_model.pkl
│   └── model_metadata.json
├── Streamlit_App/
│   ├── app.py
│   ├── utils.py
│   └── requirements.txt
├── Documentation/
│   ├── eda_plots/
│   └── model_comparison_results.csv
└── README.md
```

## 10. Testing and Verification

The following checks were performed during development:

- Python syntax compilation checks for the main application and utility modules.
- Direct testing of utility functions for currency formatting and locality mapping.
- Testing of price explanation and SVG house generation functions.
- Testing of generated HTML, CSS, background animation, and theme styling.
- Code review of the property comparison highlighting implementation.

The complete application was not launched for a live browser-based test in the original build environment because the required packages could not be installed there.

After installing the dependencies, test the application locally to confirm that predictions, property comparisons, charts, animations, and theme switching work correctly.

## 11. License

The project repository does not currently specify a license for the project's own code.

Before distributing the project, add a `LICENSE` file that reflects your intended use and sharing permissions. Review the licenses of third-party libraries separately.

## 12. Demo

**Live Demo:** Add your deployed application URL here, if available.

**Screenshots:** Add screenshots of the prediction interface, property comparison, and Insights dashboard to demonstrate the application's functionality.

## 13. Limitations

- The dataset is synthetic and may not reflect real property market conditions.
- Predictions depend on the training data and model performance.
- The currency conversion uses a fixed rate rather than a live exchange rate.
- Locality descriptions are illustrative.
- Rule-based explanations are not a formal feature-attribution method.
- Predictions should not be treated as professional appraisals or financial advice.

## 14. Academic Integrity and AI Assistance

AI coding tools may be used to assist with development, debugging, and explanations, provided their use is disclosed where appropriate.

Before submitting the project:

- Understand the code you submit.
- Test AI-assisted code before using it.
- Verify the training pipeline and evaluation results.
- Be prepared to explain the preprocessing steps, feature engineering, model selection, and evaluation metrics.
- Do not copy an existing complete project and present it as your own work.

## Conclusion

HomeValue AI demonstrates how machine learning regression models can be integrated into an interactive web application for house price estimation. By combining prediction, property comparison, data visualization, and a user-friendly interface, the project provides a practical demonstration of machine learning and web application development.
