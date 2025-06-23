import pandas as pd

# Load the dataset
df = pd.read_csv("C:\Users\ASUS\Downloads\Titanic-Dataset.csv")  # Replace with your actual file path

# Drop unwanted columns
df.drop(['Ticket', 'Cabin'], axis=1, inplace=True)

# Handle missing values
df['Age'].fillna(df['Age'].median(), inplace=True)
df['Embarked'].fillna(df['Embarked'].mode()[0], inplace=True)

# Encode categorical columns
df['Sex'] = df['Sex'].map({'male': 0, 'female': 1})
df['Embarked'] = df['Embarked'].map({'C': 0, 'Q': 1, 'S': 2})

# Save the cleaned data
df.to_csv('Cleaned_Titanic.csv', index=False)

# Preview cleaned data
print(df.head())
