# Discrete-Fourier-Transform

In the main direction of the flow contributes to the turbulence at different scales. First, to calculate the $\text{E}_{11}(\text{k})$, the streamwise fluctuating velocity signal (i.e., no matter H-W or generated dataset) at a specific wall-normal elevation, is segmented into signals with the spatial length scale of $12\delta$. This length is the largest resolved length scale in the spectrum and represents the scale of very large-scale motions (VLSMs)\citep{kim1999very, zhou1999mechanisms, Guala06, balakumar2007large}. For time-resolved datasets, such as H-W and Sonic, the Taylor frozen hypothesis is employed to switch from the temporal domain to the spatial domain for the signal segmentation(i.e., $\text{x} = \overline{\text{U}}t$). The number of segments $\text{M} \in \mathbb{N}$, after chopping the $\text{u}^{\prime}$ signal into segments of length $12\delta$, is $\text{M} = \left\lfloor \frac{\text{L}}{12\delta} \right\rfloor$, where $\text{L}$ is the length of the entire signal. Each segmented $12\delta$ signal, has $\text{N}= \left\lceil \frac{12\delta}{\Delta x} \right\rceil\in \mathbb{N}$ number of samples. The streamwise velocity power spectrum density for each segmented signal is given by discrete Fourier analysis:

$$
E_{11_m}(k)\,\left[\frac{m^3}{s^2}\right]
= 
\frac{\Delta x}{N\,G}
\left|
\sum_{n=0}^{N-1}
w(n)\,u'(n)\,
e^{-j\,\frac{2\pi n}{N}\,k}
\right|^2
$$

\begin{equation}
    \text{E}_{11_{m}}(\text{k})[\frac{\text{m}^3}{\text{s}^2}] = \frac{\Delta x}{\text{N}\text{G}} \left| \sum_{n=0}^{\text{N}-1} w(n)\text{u}^{\prime}(n) e^{-j\frac{2\pi n}{\text{N}}\text{k}} \right|^2
    \label{PSD}
\end{equation}

\[
\text{where } \text{k} = \{0,1,\dots,\text{N-1}\} \text { and } m = \{1,2,\dots,\text{M}\}
\]

To avoid energy leakage from one wavenumber bin to the neighboring bins, the Hann window function, $w(n)$, is used, and $\text{G} = \frac{1}{\text{N}} \sum_{n=0}^{\text{N}-1} w(n)^2$ is the window power normalization factor. The ensemble average of all segmented signals is $\overline{\text{E}_{11}}(\text{k})=\frac{1}{\text{M}}\sum_{m=1}^{\text{M}}\text{E}_{11_{m}}(\text{k})$. To have single-sided power spectrum density

\[
 \overline{\text{E}_{11}}_{\text{single-sided}}(\text{k})=2\overline{\text{E}_{11}}(\text{k})\quad \text{for } \text{k}
 = \{1,2,\dots,\left\lceil \frac{\text{N}}{2} \right\rceil-1\}
\]

\[
 \overline{\text{E}_{11}}_{\text{single-sided}}(\text{k})=\overline{\text{E}_{11}}(\text{k})\quad \text{for } \text{k} = \{0,\left\lceil \frac{\text{N}}{2} \right\rceil\}
\]

in which $\text{k}=0$ corresponds to the mean of the signal which is zero (i.e., $\overline{\text{u}^{\prime}(n)}=0\xrightarrow{}\overline{\text{E}_{11}}_{\text{single-sided}}(0)=0$), and $\text{k}=\left\lceil \frac{\text{N}}{2}\right\rceil$ corresponds to Nyquist wavenumber. The set of wavenumbers, $\text{k}_{1}=\frac{\text{k}2\pi}{\text{N}\Delta x}$, starts from $\text{k}=1\xrightarrow{}\text{k}_1 = 2\pi / 12\delta$ and continues up to $\text{k}=\left\lceil \frac{\text{N}}{2}\right\rceil\xrightarrow{}\text{k}_1 = \pi/\Delta x$, which corresponds to the Nyquist wavenumber in the single-sided spectrum. For brevity we will denote $\overline{\text{E}_{11}}_{\text{single-sided}}(\text{k})$ by $\text{E}_{11}(\text{k})$. Finally, $\text{E}_{11}(\text{k})$ is scaled ($\text{C}\times\text{E}_{11}(\text{k})$) such that  ,the area under the curve of $\text{C}\times\text{E}_{11}(\text{k})$ vs $\text{k}_{1}$ is equal to streamwise velocity variance:
\[
\text{C}\sum_{\text{k}=1}^{\left\lceil \frac{\text{N}}{2}\right\rceil} \text{E}_{11}(\text{k}) \, \frac{\text{k}2\pi}{\text{N}\Delta x} = \overline{\text{u}^{\prime 2}}[\frac{\text{m}^{2}}{\text{s}^{2}}]\xrightarrow{}\text{C} = \frac{\overline{\text{u}^{\prime 2}}}{\sum_{\text{k}=1}^{\left\lceil \frac{\text{N}}{2}\right\rceil} \text{E}_{11}(\text{k}) \, \frac{\text{k}2\pi}{\text{N}\Delta x}}\in \mathbb{R}
\]