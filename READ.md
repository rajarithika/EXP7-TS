# EXPERIMENT 7: SPECTRAL ANALYSIS, SPECTRAL DENSITY AND TIME-INVARIANT LINEAR FILTERS

**Name:** RAJA RITHIKA M

**Reg. No.:** 2305001029

## 1. Aim

To simulate a time series, calculate its spectral density, perform spectral analysis using the periodogram, and study the effect of a time-invariant linear filter.

## 2. Software Required

- Python 3
- Google Colab or Jupyter Notebook
- NumPy
- Matplotlib
- SciPy

## 3. Procedure

1. Import the required libraries.
2. Generate a time series containing two frequencies and random noise.
3. Plot the original time series.
4. Calculate and plot the periodogram.
5. Identify the dominant frequency.
6. Apply a moving-average filter.
7. Compare the original and filtered time series.
8. Compare the spectral density before and after filtering.

## 4. Program

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import signal

# Generate time points
n = 500
t = np.arange(n)

# Generate time series
np.random.seed(42)
x = (
    np.sin(2 * np.pi * 0.05 * t)
    + 0.5 * np.sin(2 * np.pi * 0.20 * t)
    + 0.3 * np.random.randn(n)
)

# Plot original time series
plt.figure(figsize=(10, 4))
plt.plot(t, x)
plt.title("Original Time Series")
plt.xlabel("Time")
plt.ylabel("Value")
plt.grid(True)
plt.show()

# Calculate periodogram
frequency, power = signal.periodogram(x)

# Plot spectral density
plt.figure(figsize=(10, 4))
plt.plot(frequency, power)
plt.title("Spectral Density")
plt.xlabel("Frequency")
plt.ylabel("Power")
plt.grid(True)
plt.show()

# Find dominant frequency
peak_index = np.argmax(power)
print("Dominant frequency:", frequency[peak_index])

# Apply 5-point moving-average filter
window = 5
filtered = np.convolve(
    x, np.ones(window) / window, mode="same"
)

# Compare original and filtered time series
plt.figure(figsize=(10, 4))
plt.plot(t, x, label="Original")
plt.plot(t, filtered, label="Filtered")
plt.title("Original vs Filtered Time Series")
plt.xlabel("Time")
plt.ylabel("Value")
plt.legend()
plt.grid(True)
plt.show()

# Calculate spectra
f1, p1 = signal.periodogram(x)
f2, p2 = signal.periodogram(filtered)

# Compare spectral densities
plt.figure(figsize=(10, 4))
plt.plot(f1, p1, label="Original")
plt.plot(f2, p2, label="Filtered")
plt.title("Spectral Density: Original vs Filtered")
plt.xlabel("Frequency")
plt.ylabel("Power")
plt.legend()
plt.grid(True)
plt.show()

print("Spectral analysis and filtering completed successfully.")
```

## 5. Expected Output

- Original time-series graph.
<img width="980" height="457" alt="image" src="https://github.com/user-attachments/assets/75c41c92-2daa-40c7-9db5-4f50d8f13f88" />

- Spectral density (periodogram) graph.
<img width="982" height="456" alt="image" src="https://github.com/user-attachments/assets/32f2a3c2-4ceb-40e5-8682-961575401fb4" />

- Printed dominant frequency.
<img width="257" height="17" alt="image" src="https://github.com/user-attachments/assets/15288922-e0be-4e01-b451-2f30229f4d71" />

- Original and filtered time-series comparison graph.
<img width="977" height="462" alt="image" src="https://github.com/user-attachments/assets/0ed1a1c0-02cc-4997-9192-8a9a95c07116" />

- Spectral density comparison graph before and after filtering.
<img width="977" height="488" alt="image" src="https://github.com/user-attachments/assets/f6a561ba-133c-4215-aef4-d6dfc9d90002" />


## 6. Observation

The simulated time series contains two main frequencies, 0.05 and 0.20, along with random noise.

The periodogram shows peaks near the frequencies present in the signal. The moving-average filter smooths the original time series and generally reduces higher-frequency variations.

## 7. Result

Thus, spectral analysis was performed using the periodogram, the dominant frequency was identified, and a moving-average linear filter was applied to compare the original and filtered time series.
