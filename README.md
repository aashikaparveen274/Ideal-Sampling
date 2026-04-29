# Ideal, Natural, & Flat-top -Sampling
# Aim
Write a simple Python program for the construction and reconstruction of ideal, natural, and flattop sampling.
# Tools required
Python

Libraries: NumPy, Matplotlib, SciPy
# Algorithm

# Ideal Sampling (Impulse Sampling)

1.Start

2.Define the time range t

3.Generate the original signal x(t) (e.g., sine wave)

4.Choose a sampling frequency fs

5.Calculate sampling interval Ts=1/fs

6.Select discrete sampling points at intervals of Ts

7.Extract signal values at those points

8.Represent samples as impulses (using stem plot)

9.Display the waveform

10.Stop

# Natural Sampling

1.Start

2.Define the time range t

3.Generate the original signal x(t)

4.Choose sampling frequency fs

5.Generate a periodic pulse train

6.Multiply the signal with the pulse train

7.Obtain the naturally sampled signal

8.Plot the waveform

9.Display the result

10.Stop

# Flat-top Sampling (Sample and Hold)

1.Start

2.Define the time range t

3.Generate the original signal x(t)

4.Choose sampling frequency fs

5.Calculate step size based on sampling interval

6.Sample the signal at regular intervals

7.Hold each sampled value constant until the next sample

8.Generate staircase (flat-top) waveform

9.Plot and display the signal

10.Stop

# Program
# Ideal
```
import numpy as np
import matplotlib.pyplot as plt

# Time axis
fs = 1000
t = np.linspace(0, 1, fs)

# Original signal
f = 5
x = np.sin(2 * np.pi * f * t)

# Sampling frequency
fs_sample = 50
Ts = 1 / fs_sample

# Ideal sampling (impulse-like)
sample_points = np.arange(0, 1, Ts)
sampled_values = np.sin(2 * np.pi * f * sample_points)

# Plot
plt.figure()
plt.plot(t, x, label="Original Signal")
plt.stem(sample_points, sampled_values, linefmt='r-', markerfmt='ro', basefmt='k-')
plt.title("Ideal Sampling")
plt.legend()
plt.show()
```
# Natural
```
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import square

# Time axis
fs = 1000
t = np.linspace(0, 1, fs)

# Original signal
f = 5
x = np.sin(2 * np.pi * f * t)

# Sampling frequency
fs_sample = 50

# Pulse train (natural sampling)
pulse = (square(2 * np.pi * fs_sample * t, duty=0.2) + 1) / 2

# Natural sampled signal
natural_sample = x * pulse

# Plot
plt.figure()
plt.plot(t, x, label="Original Signal")
plt.plot(t, natural_sample, label="Natural Sampling", color='red')
plt.title("Natural Sampling")
plt.legend()
plt.show()
```
# Flat-top
```
import numpy as np
import matplotlib.pyplot as plt

# Time axis
fs = 1000
t = np.linspace(0, 1, fs)

# Original signal
f = 5
x = np.sin(2 * np.pi * f * t)

# Sampling frequency
fs_sample = 50
step = int(fs / fs_sample)

# Flat-top sampling
flat_top = np.zeros_like(t)

for i in range(0, len(t), step):
    flat_top[i:i+step] = x[i]

# Plot
plt.figure()
plt.plot(t, x, label="Original Signal")
plt.plot(t, flat_top, label="Flat-top Sampling", color='green')
plt.title("Flat-top Sampling")
plt.legend()
plt.show()
```
# Output Waveform
<img width="741" height="567" alt="image" src="https://github.com/user-attachments/assets/9eeb8c23-9ba8-4446-9d9b-9690f9fcfcb4" />
<img width="732" height="561" alt="image" src="https://github.com/user-attachments/assets/5c1d433f-7282-4f40-ac4c-b9f9309a949d" />
<img width="747" height="560" alt="image" src="https://github.com/user-attachments/assets/6187fe43-5de9-4307-a289-819bd0443ccf" />


# Results
The experiment was successfully carried out using Python to generate and analyze ideal, natural, and flat-top sampling techniques.
