# Taniya-Mittal-Task-5
<br>
Here  extraction insights using visual and statistical exploration.
<br>
The titanic dataset is a classic for exploration.
<br>
<br>
1. Load and Understand the Data
<br>
<br>
import pandas as pd

# Load dataset
df = pd.read_csv('titanic.csv')

# Overview
print(df.head())
print(df.info())
print(df.describe(include='all'))
<br>
<br>
2. Data Cleaning
<br>
<br>
# Check missing values
print(df.isnull().sum())

# Fill missing values
df['Age'].fillna(df['Age'].median(), inplace=True)
df['Embarked'].fillna(df['Embarked'].mode()[0], inplace=True)
df.drop(columns=['Cabin'], inplace=True)  # too many missing

# Convert categorical variables
df['Sex'] = df['Sex'].map({'male': 0, 'female': 1})
df['Embarked'] = df['Embarked'].map({'S': 0, 'C': 1, 'Q': 2})
<br>
<br>
3. Unvariate Analysis
<br>
(a) Survival Count
<br>
import seaborn as sns
import matplotlib.pyplot as plt

sns.countplot(x='Survived', data=df)
plt.title('Survival Count')
plt.show()
<br>
(b) Age Distribution
<br>
sns.histplot(df['Age'], kde=True)
plt.title('Age Distribution')
plt.show()
<br>
(c) Passenger Class
<br>
sns.countplot(x='Pclass', data=df)
plt.title('Passenger Class Distribution')
plt.show()
<br>
<br>
4. Bivariate Analysis
<br>
(a) Survival Rate by Sex
<br>
sns.barplot(x='Sex', y='Survived', data=df)
plt.title('Survival Rate by Sex')
plt.show()
<br>
(b) Age vs Survival
<br>
sns.boxplot(x='Survived', y='Age', data=df)
plt.title('Age Distribution by Survival')
plt.show()
<br>
(c) Correlation Matrix
<br>
corr = df.corr()
sns.heatmap(corr, annot=True, cmap='coolwarm')
plt.title('Correlation Matrix')
plt.show()
<br>
<br>
5. Grouped Statistics
<br>
# Survival by class and sex
survival_stats = df.groupby(['Pclass', 'Sex'])['Survived'].mean().reset_index()
print(survival_stats)

# Average age and fare by survival
print(df.groupby('Survived')[['Age', 'Fare']].mean())
<br>
<br>
6. Key Insights(Example)
<br>
Females had a much higher survival rate than males.
<br>
1st class passengers had a higher survival rate than 2nd and 3rd.
<br>
Younger passengers were more likely to survive.
<br>
Fare tends to be higher among survivors.


