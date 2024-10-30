### Name: KARTHIKEYAN R
### Reg.NO:212222240046
### Date:
# Ex.No: 08     MOVING AVERAGE MODEL AND EXPONENTIAL SMOOTHING
### AIM:
To implement Moving Average Model and Exponential smoothing Using Python.
### ALGORITHM:
1. Import necessary libraries
2. Read the electricity time series data from a CSV file,Display the shape and the first 20 rows of
the dataset
3. Set the figure size for plots
4. Suppress warnings
5. Plot the first 50 values of the 'Value' column
6. Perform rolling average transformation with a window size of 5
7. Display the first 10 values of the rolling mean
8. Perform rolling average transformation with a window size of 10
9. Create a new figure for plotting,Plot the original data and fitted value
10. Show the plot
11. Also perform exponential smoothing and plot the graph
### PROGRAM:
```
# Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
import warnings

# Read the gold price time series data
df = pd.read_csv('Gold Price.csv')  # Path to your dataset
print("Dataset Shape:", df.shape)
print(df.head(5))  # Display the first 5 rows

# Convert the 'Price' column to numeric, handling any errors
df['Price'] = pd.to_numeric(df['Price'], errors='coerce')

# Suppress warnings
warnings.filterwarnings("ignore")

# Set figure size for plots
plt.figure(figsize=(12, 6))

# Plot the first 50 values of the 'Price' column
df['Price'][:50].plot()
plt.title("First 50 Values of Gold Prices")
plt.show()

# Perform rolling average transformation with a window size of 5
df['Rolling_Mean_5'] = df['Price'].rolling(window=5).mean()

# Display the first 10 values of the rolling mean
print(df[['Price', 'Rolling_Mean_5']].head(10))

# Perform rolling average transformation with a window size of 10
df['Rolling_Mean_10'] = df['Price'].rolling(window=10).mean()

# Create a new figure for plotting original data and fitted values
plt.figure(figsize=(12, 6))

# Plot the original data and fitted values
plt.plot(df['Price'], label='Original Data')
plt.plot(df['Rolling_Mean_5'], label='Rolling Mean (Window=5)', color='blue')
plt.plot(df['Rolling_Mean_10'], label='Rolling Mean (Window=10)', color='red')

# Add title and labels
plt.title('Moving Average on Gold Prices')
plt.legend()
plt.show()

# Exponential Smoothing
df['Exponential_Smoothing'] = df['Price'].ewm(span=5, adjust=False).mean()

# Plot the exponential smoothing along with the original data
plt.figure(figsize=(12, 6))
plt.plot(df['Price'], label='Original Data')
plt.plot(df['Exponential_Smoothing'], label='Exponential Smoothing (span=5)', color='black')

plt.title('Exponential Smoothing on Gold Prices')
plt.legend()
plt.show()

```

### OUTPUT:
![image](https://github.com/user-attachments/assets/1c3921f3-4dc7-44bb-b369-3c28451b3af0)
![image](https://github.com/user-attachments/assets/76018bdf-dd51-4602-a119-668dded6f0c2)
![image](https://github.com/user-attachments/assets/1c1d1ae5-b471-44fe-9115-26653dab33ff)
#### Moving Average
![image](https://github.com/user-attachments/assets/ad4fc8e3-6605-4ee9-b990-66980292e3a7)
#### Exponential Smoothing
![image](https://github.com/user-attachments/assets/a92f1dd5-0c2e-422b-b64d-744fcd25d7ce)


### RESULT:
Thus we have successfully implemented the Moving Average Model and Exponential smoothing using python.
