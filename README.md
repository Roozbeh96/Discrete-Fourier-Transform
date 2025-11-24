# Discrete-Fourier-Transform
In the main direction of the flow, energy is distributed across different turbulent scales. To compute the one-dimensional streamwise energy spectrum $E_{11}(k)$, the streamwise fluctuating velocity signal (whether from H-W or a generated dataset) at a specific wall-normal elevation is segmented into chunks of spatial length $12\delta$. This length corresponds to the largest resolved scale in the spectrum and represents the scale of very-large-scale motions (VLSMs).

For time-resolved datasets (H-W, Sonic), the Taylor frozen-turbulence hypothesis is applied to convert the temporal signal into a spatial one using:

$$
x = \overline{U}\, t.
$$

If the total signal length is $L$, then the number of $12\delta$ segments is:

$$
M = \left\lfloor \frac{L}{12\delta} \right\rfloor \in \mathbb{N},
$$

and each segment contains:

$$
N = \left\lceil \frac{12\delta}{\Delta x} \right\rceil \in \mathbb{N}
$$

samples.

The power spectral density for segment $m$ is computed using the discrete Fourier transform:

$$
E_{11_m}(k)\; \left[\frac{\text{m}^3}{\text{s}^2}\right]
= \frac{\Delta x}{NG}
\left|
\sum_{n=0}^{N-1} w(n)\,u'(n)\, e^{-j\frac{2\pi n}{N}k}
\right|^2.
$$

where:

- $k = \{0,1,\dots,N-1\}$
- $m = \{1,2,\dots,M\}$
- $w(n)$ is the Hann window
- $G = \frac{1}{N}\sum_{n=0}^{N-1} w(n)^2$ is the window-power normalization factor

The ensemble-averaged spectrum is:

$$
\overline{E_{11}}(k)
=
\frac{1}{M} \sum_{m=1}^M E_{11_m}(k).
$$

## Single-sided spectrum

To obtain the single-sided PSD:

For wavenumbers $k = 1,2,\dots,\left\lceil N/2 \right\rceil - 1$:

$$
\overline{E_{11}}_{\text{single}}(k) = 2\,\overline{E_{11}}(k).
$$

For the endpoints $k = 0$ and $k = \left\lceil N/2 \right\rceil$:

$$
\overline{E_{11}}_{\text{single}}(k) = \overline{E_{11}}(k).
$$

The mode $k = 0$ corresponds to the mean of the signal, which is zero:

$$
\overline{u'} = 0
\quad \Rightarrow \quad
\overline{E_{11}}_{\text{single}}(0) = 0.
$$

## Wavenumber definition

The physical wavenumber is:

$$
k_1 = \frac{k\,2\pi}{N\,\Delta x}.
$$

Thus, the spectrum begins at:

$$
k_1 = \frac{2\pi}{12\delta},
$$

and extends to the Nyquist wavenumber:

$$
k_1 = \frac{\pi}{\Delta x}.
$$

For brevity, we denote the single-sided spectrum simply as $E_{11}(k)$.

## Variance-preserving scaling

The final spectrum is scaled by a constant $C$ so that the area under $E_{11}(k)$ matches the streamwise velocity variance:

$$
C \sum_{k=1}^{\left\lceil N/2 \right\rceil}
E_{11}(k)\;
\frac{k\,2\pi}{N\Delta x}
= \overline{u'^2}
\;\left[\frac{\text{m}^2}{\text{s}^2}\right].
$$

Therefore, the scaling factor is:

$$
C =
\frac{\overline{u'^2}}
{\displaystyle
\sum_{k=1}^{\left\lceil N/2 \right\rceil}
E_{11}(k)\;
\frac{k\,2\pi}{N\Delta x}
}
\in \mathbb{R}.
$$
