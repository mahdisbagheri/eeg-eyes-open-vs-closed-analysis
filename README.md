# EEG Signal Analysis: Eyes Open vs Eyes Closed

This project analyzes and compares EEG signals recorded from a single subject under two different conditions: **Eyes Open** and **Eyes Closed**. The analysis includes signal visualization, preprocessing, frequency-domain analysis using FFT, brain-band power estimation, and signal reconstruction using IFFT.

## Dataset

The EEG recordings were obtained from the PhysioNet EEG Motor Movement/Imagery Dataset:

[PhysioNet EEG Motor Movement/Imagery Database](https://physionet.org/content/eegmmidb/1.0.0/?utm_source=chatgpt.com)

Files used in this project:

| File          | Condition   |
| ------------- | ----------- |
| `S001R01.edf` | Eyes Open   |
| `S001R02.edf` | Eyes Closed |

## Objectives

The main goals of this project are:

* Load and inspect EEG recordings from EDF files.
* Extract and analyze the occipital EEG channel (`O1` or `O2`).
* Visualize and compare the first 10 seconds of recordings.
* Apply preprocessing techniques to improve signal quality.
* Perform frequency-domain analysis using Fast Fourier Transform (FFT).
* Compute the power of standard EEG frequency bands.
* Compare brain-band activity between Eyes Open and Eyes Closed conditions.
* Reconstruct the signal using Inverse FFT (IFFT) and evaluate reconstruction accuracy.

## Methodology

### 1. Signal Loading and Visualization

* Load EDF files using MNE-Python.
* Display:

  * Sampling frequency (`sfreq`)
  * Number of samples
  * Channel names
* Select channel `O1` or `O2` for analysis.
* Plot the first 10 seconds of EEG data for both conditions.

### 2. Preprocessing

The following preprocessing steps were applied to both signals:

* DC offset removal (mean subtraction)
* Band-pass filtering between **0.5 Hz and 40 Hz**
* Visualization of the filtered signals

### 3. Frequency-Domain Analysis

#### Fast Fourier Transform (FFT)

For each recording:

* Compute the FFT using `numpy.fft.rfft`
* Generate the frequency axis
* Plot the amplitude spectrum within the range **0–40 Hz**

#### EEG Band Power Estimation

Power was calculated for the following EEG frequency bands:

| Band  | Frequency Range |
| ----- | --------------- |
| Delta | 0.5–4 Hz        |
| Theta | 4–8 Hz          |
| Alpha | 8–12 Hz         |
| Beta  | 12–30 Hz        |
| Gamma | 30–40 Hz        |

<img width="238" height="212" alt="images" src="https://github.com/user-attachments/assets/209ec882-1c51-4720-ad46-c5177735d5c6" />


The band powers for Eyes Open and Eyes Closed conditions were compared using bar charts.

#### Scientific Expectation

The **Alpha band (8–12 Hz)** is expected to exhibit significantly higher power during the **Eyes Closed** condition, particularly in occipital channels.

### 4. Signal Reconstruction

* Reconstruct the EEG signal using `numpy.fft.irfft`
* Compare the reconstructed signal with the original signal
* Evaluate reconstruction accuracy

## Results

Key observations from the analysis:

* EEG activity differs noticeably between Eyes Open and Eyes Closed states.
* The Eyes Closed condition shows stronger Alpha-band activity, consistent with established neuroscience findings.
* FFT successfully reveals the dominant frequency components of the EEG signal.
* IFFT reconstruction closely matches the original signal, validating the frequency-domain transformation process.


