# Discrete-Fourier-Transform

In the main direction of the flow contributes to the turbulence at different scales. First, to calculate the $E_{11}(k)$, the streamwise fluctuating velocity signal (i.e., no matter H-W or generated dataset) at a specific wall-normal elevation, is segmented into signals with the spatial length scale of $12\delta$. This length is the largest resolved length scale in the spectrum and represents the scale of very large-scale motions (VLSMs)\citep{kim1999very, zhou1999mechanisms, Guala06, balakumar2007large}. For time-resolved datasets, such as H-W and Sonic, the Taylor frozen hypothesis is employed to switch from the temporal domain to the spatial domain for the signal segmentation(i.e., $x = \overline{U}t$). The number of segments $M \in \mathbb{N}$, after chopping the $u^{\prime}$ signal into segments of length $12\delta$, is $M = \left\lfloor \frac{L}{12\delta} \right\rfloor$, where $L$ is the length of the entire signal. Each segmented $12\delta$ signal, has $N= \left\lceil \frac{12\delta}{\Delta x} \right\rceil\in \mathbb{N}$ number of samples. The streamwise velocity power spectrum density for each segmented signal is given by discrete Fourier analysis:<br>

$E_{11_{m}}(k)[\frac{m^3}{s^2}] = \frac{\Delta x}{NG}|\sum_{n=0}^{N-1} w(n)u^{\prime}(n) e^{-j\frac{2\pi n}{N}k}|^2$


$\text{where } k = \{0,1,\dots,N-1\} \text { and } m = \{1,2,\dots,M\}$

To avoid energy leakage from one wavenumber bin to the neighboring bins, the Hann window function, $w(n)$, is used, and $G = \frac{1}{N} \sum_{n=0}^{N-1} w(n)^2$ is the window power normalization factor. The ensemble average of all segmented signals is $\overline{E_{11}}(k)=\frac{1}{M}\sum_{m=1}^{M}E_{11_{m}}(k)$. To have single-sided power spectrum density:<br>

$\overline{E_{11_{single-sided}}}(k)=2\overline{E_{11}}(k)\quad \text{for } k
 = \{1,2,\dots,\left\lceil \frac{N}{2} \right\rceil-1\}$

$\overline{E_{11_{single-sided}}}(k)=\overline{E_{11}}(k)\quad \text{for } k = \{0,\left\lceil \frac{N}{2} \right\rceil\}$

in which $k=0$ corresponds to the mean of the signal which is zero (i.e., $\overline{u^{\prime}(n)}=0\xrightarrow{}\overline{E_{11_{single-sided}}}(0)=0$), and $k=\left\lceil \frac{N}{2}\right\rceil$ corresponds to Nyquist wavenumber. The set of wavenumbers, $k_{1}=\frac{k2\pi}{N\Delta x}$, starts from $k=1\xrightarrow{}k_1 = 2\pi / 12\delta$ and continues up to $k=\left\lceil \frac{N}{2}\right\rceil\xrightarrow{}k_1 = \pi/\Delta x$, which corresponds to the Nyquist wavenumber in the single-sided spectrum. For brevity we will denote $\overline{E_{11_{single-sided}}}(k)$ by $E_{11}(k)$. Finally, $E_{11}(k)$ is scaled ($C\times E_{11}(k)$) such that  ,the area under the curve of $C\times E_{11}(k)$ vs $k_{1}$ is equal to streamwise velocity variance:

$C\sum_{k=1}^{\left\lceil \frac{N}{2}\right\rceil} E_{11}(k) \, \frac{k2\pi}{N\Delta x} = \overline{u^{\prime 2}}[\frac{m^{2}}{s^{2}}]\xrightarrow{}C = \frac{\overline{u^{\prime 2}}}{\sum_{k=1}^{\left\lceil \frac{N}{2}\right\rceil} E_{11}(k) \, \frac{k2\pi}{N\Delta x}}\in \mathbb{R}$