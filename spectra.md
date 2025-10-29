## Spectra of benchmark detached eclipsing binary stars

This web page is a collection of spectra for stars in eclipsing binary systems for which the effective temperature has been measured directly from the its angular diameter and bolometric flux, i.e.
$$ T_{\rm eff} = (4F_{\rm bol}  \theta/\sigma_{\rm SB})^{1/4},$$
where $\sigma_{\rm SB}$ is the Stefan-Boltzmann constant and $\theta = 2\,R_{\star}/d$ is the angular diameter of a star of radius $R_{\star}$ at distance $d$.
The full method is described in [Miller, Maxted and Smalley, 2020](https://ui.adsabs.harvard.edu/abs/2020MNRAS.497.2899M/abstract).


**N.B.** these are spectra of one star in the binary system with zero or negligible contribution from the companion star.

Individual spectra for a star in an eclipsing binary can be obtained by one of the following methods ...

#### Eclipse
Spectrum of the larger star in a binary obtained during a total eclipse when the smaller companion is completely hidden.
#### EBLM
EBLM systems are eclipsing binaries where the F-/G-type primary star has a very low-mass M-dwarf companions. The flux from the companion in the optical spectrum is negligible ($\approx 0.2$% or less).
#### Corrected
Spectra where the flux contribution from the fainter star has been removed using synthetic spectra. This works well for systems where the flux ratio is $\approx 1$% or less, e.g. near-infrared spectra of EBLM systems.
#### Disentangled
Extraction of the individual spectra from a set of combined spectra using the spectral disentangling method by Simon & Sturm (1994) (or some other method).

##### Note on disentangled spectra
The disentagled spectra are computed so that their sum after the appropriate radial velocity shifts have been applied gives the best least-squares fit to the observed spectra, and so that the flux ratio matches the value expected based on the light curve analysis.
Errors in normalisation for the input spectra result in some parts of the disentangled spectrum not having the correct flux ratio. This can be seen as one spectrum being too high in some wavelength regions and the other spectrum being too low in the same wavelength regions. This problem is worse for noisy echelle spectra near the ends of the echelle orders.

If you have a better estimate of what the flux ratio, $R$, should be in the some part of the spectrum then you should proceed as follows 

1. Calculate
 - $f_1$ = average flux in disentangled spectrum of star 1,
 - $f_2$ = average flux in disentangled spectrum of star 2.

2. Calculate the constant $C$ such that $R = (f_2 + C)/(f_1 - C)$, so $C = (R\times f_1 - f_2) /(1+R)$

3. Create new spectra
 - new_spectrum$_1$ = old_spectrum$_1$ - $C$
 - new_spectrum$_2$ = old_spectrum$_2$ + $C$


### List of stars
- [AI Phe, F7 V + K0 IV](#AI_Phe.zip)
- [EBLM J0113+31 A, G0 V](#EBLM_J0113+31_A.zip)
- HD 22064, F2V
- CPD-54 810, F5 IV + F6 V
- EBLM J0608-59A, G0 V
- BEBOP-3_A, F9 V


### AI_Phe.zip
The folder `uves/` contains 4 spectra of AI Phe B obtained with the red (arm R$\approx$100,000) and blue arm (R$\approx$80,000) of the UVES spectrograph during the total eclipse of the F7V companion. The raw data were reprocessed using version 6.1.8 of the UVES pipeline and renormalized using the algorithm described in [Borisov et al., 2023](https://ui.adsabs.harvard.edu/abs/2023ApJS..266...11B/abstract). 

There is a glitch due to poor order tracing/profile fitting around 610 nm. This appears to be due to a spurious absorption feature at 616.0 - 616.5 nm that can be seen in the spectra extracted using the "linear" mode of the uves pipeline (`uves/FLUX_SCI_POINT_REDU_L...fits`).
The format of the data is described [here](https://archive.eso.org/cms/eso-archive-news/release-of-uves-echelle-science-data-products.html). These spectra can be read directly into [iSpec](https://www.blancocuaresma.com/s/iSpec/manual/usage/basics).

The zip file also contains the result of disentangling 36 spectra obtained with the HARPS spectrograph together with the UVES spectra obtained in eclipse. The disentangling algorithm has been updated so that the spectra taken in eclipse determine the flux ratio in each order. This works better than estimating the flux ratio in the order from the light curve results, particularly in the far blue end of the spectrum. The disantangling also accounts for the different signal-to-noise in each spectrum using inverse variance weighting on a per-spectrum basis.

The disentangling is done in short sections correpsonding to HARPS echelle orders. Several iterations are used to remove outliers, estimate the noise, and ensure that the normalisation of the input spectra is consistent, The spectra of the two components of AI Phe are then "stitched" to generate spectra in the following wavelengh ranges:

- violet: 379.0- 449.1
- blue: 464.5 - 530.4
- green: 533.8 - 559.0
- yellow: 568.7 - 615.9
- red: 616.6 - 663.0

These sections correspond to the overlap between the HARPS spectra and the useable parts of the UVES spectra. If you spot problems with any features then you can check the spectra provided order-by-order in the folder `output/` to see if it is problem with the order stitching, e.g. there is problem with the stitching of orders 97 and 98 due to a feature at the edges of these orders near 627.5 nm. There are not many such cases that I could see from a quick inspection. The UVES spectra extracted using "linear" mode were used for the disentangling in the wavelength range 602.4 - 627.2 nm.
The spectra include orders where there are telluric features, (e.g. order 97). The disentangled spectra look ok, but I have not done any extensive testing to check how accurate the line depths are recovered in these regions.

The format of the disentangled spectra is suitable for use with [iSpec](https://www.blancocuaresma.com/s/iSpec/manual/usage/basics).


##### AI Phe A, F7 V
 - T$_{\rm eff} = 6199 \pm 33$ K
 - $\log g = 4.002 \pm 0.001$
 - Mass $ = 1.1938 \pm 0.0008 M_{\odot}$
 - Radius $ = 1.8050 \pm 0.0022 R_{\odot}$

##### AI Phe B, K0 IV
 - T$_{\rm eff} = 5094 \pm 27$ K
 - $\log g  = 3.598 \pm 0.001$
 - Mass  $ = 1.2438 \pm 0.0008 M_{\odot}$
 - Radius $ = 2.9332 \pm 0.0023 R_{\odot}$

##### Photometry
The following table gives the combined magnitude of the binary system, the flux ratio in that band from the light curve analysis, and the individual magnitudes of the two stars calculated from these input values.

Band | Magnitude | Source | Flux ratio (B/A) | Ref. | mA | mB|
|----|-----------|--------|------------------|------|----|----|
|U (Johnson) | 9.406 $\pm$ 0.020 | 1984ApJ...282..748H | 0.446 $\pm$ 0.020 | 1988A&A...196..128A | 9.806 $\pm$ 0.025 | 10.680$\pm$ 0.039|
|B (Johnson) | 9.254 $\pm$ 0.014 | 1984ApJ...282..748H | 0.727 $\pm$ 0.011 | 1988A&A...196..128A | 9.847 $\pm$ 0.016 | 10.193$\pm$ 0.017|
|V (Johnson) | 8.578 $\pm$ 0.013 | 1984ApJ...282..748H | 1.011 $\pm$ 0.009 | 1988A&A...196..128A | 9.337 $\pm$ 0.014 | 9.325 $\pm$ 0.014|
|R (Johnson) | 7.994 $\pm$ 0.014 | 1984ApJ...282..748H | 1.198 $\pm$ 0.024 | 1988A&A...196..128A | 8.849 $\pm$ 0.018 | 8.652 $\pm$ 0.017|
|I (Johnson) | 7.612 $\pm$ 0.020 | 1984ApJ...282..748H | 1.406 $\pm$ 0.023 | 1988A&A...196..128A | 8.565 $\pm$ 0.019 | 8.195 $\pm$ 0.018|
|J (2MASS) | 7.301 $\pm$ 0.023 | 2003yCat.2246....0C | 1.658 $\pm$ 0.023 | 2020MNRAS.497.2899M | 8.362 $\pm$ 0.025 | 7.813 $\pm$ 0.024|
|H (2MASS) | 6.935 $\pm$ 0.034 | 2003yCat.2246....0C | 2.012 $\pm$ 0.010 | 2019A&A...632A..31G | 8.132 $\pm$ 0.034 | 7.373 $\pm$ 0.034|
|Ks (2MASS) | 6.819 $\pm$ 0.026 | 2003yCat.2246....0C | 2.076 $\pm$ 0.030 | 2020MNRAS.497.2899M | 8.039 $\pm$ 0.028 | 7.246 $\pm$ 0.026|

References
- Maxted et al., 2020
- Miller et al., 2020


### EBLM_J0113+31_A.zip

##### J0113+31_FIES.fits
Average FIES optical spectrum (R$\approx$46,000). Flux from the M-dwarf companion is negligible (<0.1 %).
##### J0113+31_SPIRou.fits
Average SPIRou spectrum (R$\approx$75,000) after subtraction of a model M-dwarf spectrum to correct for the flux contribution from the M-dwarf companion ($\approx$0.5 %)

- T$_{\rm eff} = 6124 \pm 40$ K
- $\log g  = 4.148 \pm 0.006$
- Mass $ = 1.029 \pm 0.025 M_{\odot}$
- Radius $ = 1.417 \pm 0.014 R_{\odot}$
- \[Fe/H\] $\approx -0.3 \pm 0.1$

#### Photometry
See [Maxted et al. (2022)](https://ui.adsabs.harvard.edu/abs/2022MNRAS.513.6042M/abstract) Table 7

#### References
- [Maxted et al., 2022](https://ui.adsabs.harvard.edu/abs/2022MNRAS.513.6042M/abstract)


### HD_22064_A.zip
The file hd22064_apogee.txt contains the average APOGEE spectrum (R≈22,500) of the primary after subtraction of a model M-dwarf spectrum to correct for the flux contribution from the M-dwarf companion (≈4.4 %). This file can be read directly into iSpec.
The file hd22064_apogee.csv contains the same spectrum in CSV format plus the reconstructred spectrum described in Maxted, 2023. N.B. Broad spectral features such as absorption lines due to hydrogen are badly affected by the processing steps leading to the production of these spectra. In particular, the cores of the hydrogen Brackett absorption lines are not accurate and should not be used for analysis.


Teff = 6763 ± 39 K
log g (cgs) = 4.184 ± 0.006
Mass = 1.345 ± 0.031 M⊙
Radius = 1.554 ± 0.014 R⊙
[Fe/H] ≈ −0.05 ± 0.15
Photometry
See Maxted et al. (2023) Table 10
References
Maxted, 2023
CPD-54_810.zip
Disentangled <a href="https://www.eso.org/sci/facilities/lasilla/instruments/feros.html", target="_blank">FEROS</a> spectra for both components over the wavelength range 495.1 − 580.2 nm.
The format of the disentangled spectra is suitable for use with iSpec.

The 5 original FEROS spectra are included in the zip file. As can be seen, these are spectra are quite noisy and badly affected by outliers in a some wavelength regions. Several post-processing steps were required to obtain a consistent normalisation between the spectra so there are some regions where the flux ratio may not be very accurate (see note on disentangling). The disentangling process is quite sensitive to outliers so some line profiles may be badly distorted by an outlier in one of the input spectra. It is recommended to check the raw spectra if you are not able to get a good fit to some of the spectral features or find strange abundances based on only a few lines.

The format of the raw data is described here. These spectra can also be read directly into iSpec, but the wavelength scale is Å so remember to apply the mathematical expression waveobs/10 to get wavelengths in nm.


### CPD-54 810 A, F5 IV
Teff = 6462 ± 43 K
log g (cgs) = 3.984 ± 0.001
Mass = 1.309 ± 0.005 M⊙
Radius = 1.929 ± 0.003 R⊙
[Fe/H] ≈ −0.0 ± 0.2 </ul>
CPD-54 810 B, F6 V
Teff = 6331 ± 43 K
log g (cgs) = 4.330 ± 0.003
Mass = 1.090 ± 0.003 M⊙
Radius = 1.182 ± 0.004 R⊙
Photometry
The following table gives the combined magnitude of the binary system, the flux ratio in that band from the light curve analysis, and the individual magnitudes of the two stars calculated from these input values.
N.B. Magnitudes for both stars in other photometric bands can be estimated from the analysis described in Miller et al. (2022). This will take some effort, but can be done if someone can make good use of the results.


Band	Magnitude	Source	Flux ratio (B/A)	Ref.	mA	mB
B (Tycho)	10.971 ± 0.049	2000A&A...355L..27H	0.330 ± 0.001	2022MNRAS.517.5129M	11.28 ± 0.05	12.48 ± 0.05
V (Tycho)	10.560 ± 0.047	2000A&A...355L..27H	0.341 ± 0.001	2022MNRAS.517.5129M	10.88 ± 0.05	12.05 ± 0.05
I (Gunn-i)	9.922 ± 0.03	2005yCat.2263....0D	0.352 ± 0.001	2022MNRAS.517.5129M	10.25 ± 0.03	11.38 ± 0.03
References
Miller et al., 2022
EBLM_J0608-59_A.zip
J0608-59_ESPRESSO.fits
Average ESPRESSO optical spectrum (R≈140,000). Flux from the M-dwarf companion is negligible (<0.2 % average in Gaia RP band).

Teff = 6031 ± 56 K
log g (cgs) = 4.24 ± 0.01
Mass = 1.098 ± 0.018 M⊙
Radius = 1.321 ± 0.017 R⊙
[Fe/H] ≈ −0.01 ± 0.05
Photometry
See Maxted et al. (2024) Table 1
References
Maxted et al., 2024
BEBOP-3_A.zip
BEBOP-3_SOPHIE.fits
Average SOPHIE optical spectrum (R≈75,000). Flux from the M-dwarf companion is negligible (≈0.2 % average in Gaia RP band).

Teff = 6065 ± 44 K
log g (cgs) = 4.190 ± 0.004
Mass = 1.084 ± 0.026 M⊙
Radius = 1.386 ± 0.010 R⊙
[Fe/H] ≈ −0.02 ± 0.10
Photometry
See Maxted et al. (2025) Table 4
References
Maxted et al., 2025
