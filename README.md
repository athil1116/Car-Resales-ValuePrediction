# Car-Resales-ValuePrediction
This project uses machine learning to predict the resale value of a car based on features such as age, mileage, fuel type, transmission, and ownership history. By training regression models on a cleaned dataset, the system provides accurate price estimates, helping buyers and sellers make informed decisions in the used car market.
apply regression models to accurately predict car prices.

📂 Dataset
Imported using pandas.

Initial data checks included:

Checking for missing values using .isna().sum().

Inspecting data types with .dtypes.

🧹 Data Cleaning & Preprocessing
Dropping Columns:

NewPrice column was dropped due to 90% missing values.

An unnamed index column was also removed.

Handling Text in Numeric Columns:

Columns like Mileage, Engine, and Power contained units (e.g., km/kg, cc, bhp).

Used .str.replace() to remove units:

python
Copy
Edit
df['Mileage'] = df['Mileage'].str.replace(' km/kg', '')
Converted cleaned strings to numeric using .astype(float).

Handling Missing Values:

Remaining missing values were filled using:

.fillna() with mean, median, or mode, depending on the column type.

Encoding Categorical Features:

Applied LabelEncoder to convert object-type columns into numerical values.

Feature Selection:

Input features: X

Target variable: y (Car resale price)

Feature Scaling:

Used MinMaxScaler() to normalize features to a common scale:

python
Copy
Edit
from sklearn.preprocessing import MinMaxScaler
scaler = MinMaxScaler()
X_scaled = scaler.fit_transform(X)
📈 Model Training
Train/Test Split:

Used train_test_split() from scikit-learn.

80% training data, 20% testing:

python
Copy
Edit
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X_scaled, y, test_size=0.2, random_state=42)
Linear Regression:

Trained a Multiple Linear Regression model.

Used r2_score to evaluate performance.

Model did not achieve good accuracy.

K-Nearest Neighbors (KNN) Regression:

Switched to KNeighborsRegressor due to better suitability for the dataset.

Trained and tested using the same split.

Achieved better r2_score than Linear Regression.

📊 Evaluation
Performance measured using r2_score.

KNN outperformed Linear Regression on this dataset.
