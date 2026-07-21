### Code Examples for Logistic Regression

This document provides detailed code examples for implementing logistic regression using Python and scikit-learn. Each example is fully annotated to help you understand the steps involved.

#### Loading and Exploring Data
```python
import pandas as pd
from sklearn.datasets import load_breast_cancer

# Load dataset
data = load_breast_cancer()
df = pd.DataFrame(data.data, columns=data.feature_names)
df['target'] = data.target

# Explore data
print(df.head())
print(df.describe())
```

#### Preprocessing Data
```python
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

# Split data into features and target
X = df.drop('target', axis=1)
y = df['target']

# Scale features
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# Split data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X_scaled, y, test_size=0.2, random_state=42)
```

#### Training the Model
```python
from sklearn.linear_model import LogisticRegression

# Train model
model = LogisticRegression()
model.fit(X_train, y_train)
```

#### Evaluating the Model
```python
from sklearn.metrics import confusion_matrix, accuracy_score, precision_score, recall_score

# Predict on test set
y_pred = model.predict(X_test)

# Evaluate model
conf_matrix = confusion_matrix(y_test, y_pred)
accuracy = accuracy_score(y_test, y_pred)
precision = precision_score(y_test, y_pred)
recall = recall_score(y_test, y_pred)

print(f'Confusion Matrix:\n{conf_matrix}')
print(f'Accuracy: {accuracy:.2f}')
print(f'Precision: {precision:.2f}')
print(f'Recall: {recall:.2f}')
```

#### Handling Imbalanced Data
```python
from sklearn.utils import class_weight

# Compute class weights
class_weights = class_weight.compute_class_weight('balanced', classes=np.unique(y_train), y=y_train)

# Train model with class weights
model = LogisticRegression(class_weight={0: class_weights[0], 1: class_weights[1]})
model.fit(X_train, y_train)
```

For more detailed explanations and best practices, refer to [Core Concepts](references/core_concepts.md) and [Practical Guide](references/practical_guide.md).