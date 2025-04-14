# Taniya-Mittal-Task-5
<br>
Here  extraction insights using visual and statistical exploration.
<br>
The titanic dataset is a classic for exploration.
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
