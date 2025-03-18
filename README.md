import pandas as pd
import seaborn as sns

# Load dataset
df = sns.load_dataset("titanic")
df.head()
import pandas as pd

# Sample DataFrame
df = pd.DataFrame({
    'age': [22, None, 24, 30, None],
    'embarked': ['S', 'C', None, 'Q', 'S'],
    'cabin': ['B42', None, 'C85', 'D56', None]  # Ensure the column exists
})

# Filling missing values correctly
df['age'] = df['age'].fillna(df['age'].median())  # Correct way to fill missing values
df['embarked'] = df['embarked'].fillna(df['embarked'].mode()[0])  # Mode filling correctly

# Check if 'cabin' exists before modifying it
if 'cabin' in df.columns:
    df['cabin'] = df['cabin'].fillna('Unknown')

print(df)
import pandas as pd

# Sample DataFrame (Make sure it has the 'sex' column)
df = pd.DataFrame({
    'age': [22, None, 24, 30, None],
    'embarked': ['S', 'C', None, 'Q', 'S'],
    'sex': ['male', 'female', 'female', None, 'male']  # Ensure 'sex' column exists
})

# Check if 'sex' exists before modifying it
if 'sex' in df.columns:
    df['sex'] = df['sex'].fillna('Unknown')  # Fill missing values safely
else:
    print("Column 'sex' does not exist in the DataFrame!")

print(df)
import pandas as pd
from sklearn.preprocessing import StandardScaler

# Sample DataFrame (Ensure 'fare' exists)
df = pd.DataFrame({
    'age': [22, None, 24, 30, None],
    'fare': [7.25, 71.83, 8.05, 13.00, None]  # Ensure 'fare' column exists
})

# Fill missing values before scaling
df['age'] = df['age'].fillna(df['age'].median())
df['fare'] = df['fare'].fillna(df['fare'].median())

# Initialize StandardScaler
scaler = StandardScaler()

# Check if columns exist before applying transformation
required_cols = ['age', 'fare']
missing_cols = [col for col in required_cols if col not in df.columns]

if not missing_cols:
    df[['age', 'fare']] = scaler.fit_transform(df[['age', 'fare']])
else:
    print(f"Missing columns: {missing_cols}. Please check the DataFrame.")

print(df)
import pandas as pd

# Sample DataFrame (Ensure 'survived' exists)
df = pd.DataFrame({
    'age': [22, 35, 24, 30, 40],
    'fare': [7.25, 71.83, 8.05, 13.00, 20.50],
    'survived': [0, 1, 1, 0, 1]  # Ensure 'survived' column exists
})

# Check if 'survived' is present before dropping it
if 'survived' in df.columns:
    X = df.drop(columns=['survived'])  # Features
    y = df['survived']  # Target variable
else:
    print("Column 'survived' not found in the DataFrame!")

print(X)
print(y)
data_dir = "data/"  # Optional
train_file = "data/train.csv"
test_file = "data/test.csv"
models_dir = "models/"


