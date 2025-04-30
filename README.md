# EXP.NO.9-Simulation-of-Pulse-Code-Modulation


## AIM:
To Simulate of PCM using Python.

## SOFTWARE REQUIRED:
Google Collab

## ALGORITHM:
1. Generate an analog signal (e.g., sine wave).
2. Sample the signal at regular intervals (sampling).
3. Quantize the sampled values to the nearest levels (quantization).
4. Convert the quantized values into binary code (encoding).
5. Plot the:
    Original analog signal
    Sampled signal
    Quantized signal
    Encoded PCM output
   
## PROGRAM:
```
# PCM import matplotlib.pyplot as plt
import numpy as np
import matplotlib.pyplot as plt
# Parameters
sampling_rate = 5000  # Sampling rate (samples per second)
frequency = 50  # Frequency of the message signal (analog signal)
duration = 0.1  # Duration of the signal in seconds
quantization_levels = 16  # Number of quantization levels (PCM resolution)

# Generate time vector
t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

# Generate message signal (analog signal)
message_signal = np.sin(2 * np.pi * frequency * t)

# Generate clock signal (sampling clock) with higher frequency than before
clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))  # Increased clock frequency to 200 Hz

# Quantize the message signal
quantization_step = (max(message_signal) - min(message_signal)) / quantization_levels
quantized_signal = np.round(message_signal / quantization_step) * quantization_step

# Simulate the PCM modulated signal (digital representation)
pcm_signal = (quantized_signal - min(quantized_signal)) / quantization_step
pcm_signal = pcm_signal.astype(int)

# Plotting the results
plt.figure(figsize=(12, 10))

# Plot message signal
plt.subplot(4, 1, 1)
plt.plot(t, message_signal, label="Message Signal (Analog)", color='blue')
plt.title("Message Signal (Analog)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

# Plot clock signal (higher frequency)
plt.subplot(4, 1, 2)
plt.plot(t, clock_signal, label="Clock Signal (Increased Frequency)", color='green')
plt.title("Clock Signal (Increased Frequency)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

# Plot PCM modulated signal (quantized)
plt.subplot(4, 1, 3)
plt.step(t, quantized_signal, label="PCM Modulated Signal", color='red')
plt.title("PCM Modulated Signal (Quantized)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

# Plot 'PCM Demodulation'
plt.subplot(4, 1, 4)
plt.plot(t, quantized_signal, label="Signal Demodulation", color='purple', linestyle='--')
plt.title("Signal Without Demodulation")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

plt.tight_layout()
plt.show()
```

## OUTPUT:
![PCM OUTPUT](https://github.com/user-attachments/assets/77bae5ba-d55a-42e6-8f71-b704bc6ec0dc)


## RESULT:

Two distinct analog signals (50Hz and 120Hz) are successfully generated and quantized.
Their PCM representations are calculated and visualized.
A time-division multiplexed PCM signal is constructed by interleaving PCM values from both signals.
The output plots demonstrate:
Clear quantization of both signals.
Proper interleaving of PCM values for transmission in a multiplexed form.
A visual representation of how TDM works with PCM for efficient digital signal transmission.
