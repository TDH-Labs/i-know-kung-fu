### Code Examples and Prompt Templates

This document provides detailed code snippets and prompt templates for using Gemini 3.5 Flash in various workflows.

#### Image Analysis
```
Look at everything in this image and provide a detailed analysis. Include any relevant steps or actions based on the content.
```

#### Video Understanding
```
Give me the top five insights from this video with exact timestamps. Then find the data table shown around the 23-minute mark and recreate it as a Python chart.
```

#### Document Processing
```
Act as a contract lawyer. Read this entire agreement and flag every hidden fee, automatic renewal clause, and penalty that a client could miss on a first read.
```

#### Structured Data Extraction
```
Extract clean structured data from all these receipts without writing a single line of API code.
```

#### Python Chart Recreation
```python
import matplotlib.pyplot as plt

# Example data
x = [1, 2, 3, 4, 5]
y = [10, 20, 25, 30, 40]

# Plotting the chart
plt.plot(x, y)
plt.xlabel('X-axis')
plt.ylabel('Y-axis')
plt.title('Sample Chart')
plt.show()
```

These examples and templates will help you get started with Gemini 3.5 Flash in your workflows.