---
layout: default
title: "Spectra of benchmark detached eclipsing binary stars"
permalink: /spectra
---

## Spectra of benchmark detached eclipsing binary stars

This web page is a collection of spectra for stars in eclipsing binary systems for which the effective temperature has been measured directly from the its angular diameter and bolometric flux, i.e.

> $$ T_{\rm eff} = (4F_{\rm bol}  \theta/\sigma_{\rm SB})^{1/4},$$

where $\sigma_{\rm SB}$ is the Stefan-Boltzmann constant and $$\theta = 2\,R_{\star}/d$$ is the angular diameter of a star of radius $$R_{\star}$$ at distance $$d$$.
The full method is described in [Miller, Maxted and Smalley, 2020](https://ui.adsabs.harvard.edu/abs/2020MNRAS.497.2899M/abstract).


**N.B.** these are spectra of one star in the binary system with zero or negligible contribution from the companion star.

Individual spectra for a star in an eclipsing binary can be obtained by one of the following methods ...

#### Eclipse
Spectrum of the larger star in a binary obtained during a total eclipse when the smaller companion is completely hidden.
#### EBLM
EBLM systems are eclipsing binaries where the F-/G-type primary star has a very low-mass M-dwarf companions. The flux from the companion in the optical spectrum is negligible ($$\approx 0.2$$% or less).
#### Corrected
Spectra where the flux contribution from the fainter star has been removed using synthetic spectra. This works well for systems where the flux ratio is $$\approx 1$$% or less, e.g. near-infrared spectra of EBLM systems.
#### Disentangled
Extraction of the individual spectra from a set of combined spectra using the spectral disentangling method by Simon & Sturm (1994) (or some other method).

##### Note on disentangled spectra
The disentagled spectra are computed so that their sum after the appropriate radial velocity shifts have been applied gives the best least-squares fit to the observed spectra, and so that the flux ratio matches the value expected based on the light curve analysis.
Errors in normalisation for the input spectra result in some parts of the disentangled spectrum not having the correct flux ratio. This can be seen as one spectrum being too high in some wavelength regions and the other spectrum being too low in the same wavelength regions. This problem is worse for noisy echelle spectra near the ends of the echelle orders.

If you have a better estimate of what the flux ratio, $$R$$, should be in the some part of the spectrum then you should proceed as follows 

1. Calculate
 - $$f_1$$ = average flux in disentangled spectrum of star 1,
 - $$f_2$$ = average flux in disentangled spectrum of star 2.

2. Calculate the constant $$C$$ such that $$R = (f_2 + C)/(f_1 - C)$$, so $$C = (R\times f_1 - f_2) /(1+R)$$

3. Create new spectra
 - new_spectrum$$_1$$ = old_spectrum$$_1$$ - $$C$$
 - new_spectrum$$_2$$ = old_spectrum$$_2$$ + $$C$$


### List of stars
- [AI Phe, F7 V + K0 IV](#ai_phezip)
- [EBLM J0113+31 A, G0 V](#eblm_j011331_azip)
- HD 22064, F2V
- CPD-54 810, F5 IV + F6 V
- EBLM J0608-59A, G0 V
- BEBOP-3_A, F9 V


#### AI_Phe.zip
The folder `uves/` contains 4 spectra of AI Phe B obtained with the red (arm R$$\approx$$100,000) and blue arm (R$$\approx$$80,000) of the UVES spectrograph during the total eclipse of the F7V companion. The raw data were reprocessed using version 6.1.8 of the UVES pipeline and renormalized using the algorithm described in [Borisov et al., 2023](https://ui.adsabs.harvard.edu/abs/2023ApJS..266...11B/abstract). 

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
 - log $g = 4.002 \pm 0.001$
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
|U (Johnson) | 9.406 ±       0.020 | 1984ApJ...282..748H | 0.446 ± 0.020 | 1988A&A...196..128A | 9.806 ± 0.025 | 10.680± 0.039|
|B (Johnson) | 9.254 ± 0.014 | 1984ApJ...282..748H | 0.727 ± 0.011 | 1988A&A...196..128A | 9.847 ± 0.016 | 10.193± 0.017|
|V (Johnson) | 8.578 ± 0.013 | 1984ApJ...282..748H | 1.011 ± 0.009 | 1988A&A...196..128A | 9.337 ± 0.014 | 9.325 ± 0.014|
|R (Johnson) | 7.994 ± 0.014 | 1984ApJ...282..748H | 1.198 ± 0.024 | 1988A&A...196..128A | 8.849 ± 0.018 | 8.652 ± 0.017|
|I (Johnson) | 7.612 ± 0.020 | 1984ApJ...282..748H | 1.406 ± 0.023 | 1988A&A...196..128A | 8.565 ± 0.019 | 8.195 ± 0.018|
|J (2MASS) | 7.301 ± 0.023 | 2003yCat.2246....0C | 1.658 ± 0.023 | 2020MNRAS.497.2899M | 8.362 ± 0.025 | 7.813 ± 0.024|
|H (2MASS) | 6.935 ± 0.034 | 2003yCat.2246....0C | 2.012 ± 0.010 | 2019A&A...632A..31G | 8.132 ± 0.034 | 7.373 ± 0.034|
|Ks (2MASS) | 6.819 ± 0.026 | 2003yCat.2246....0C | 2.076 ± 0.030 | 2020MNRAS.497.2899M | 8.039 ± 0.028 | 7.246 ± 0.026|

References
- Maxted et al., 2020
- Miller et al., 2020


### EBLM_J0113+31_A.zip
