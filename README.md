# PyXRFPower

PyXRFPower is a graphical user interface (GUI) designed to allow one to quickly estimate element-dependent spatial resolutions of scanning fluorescence X-ray microscopy (SFXM) images acquired at synchrotron light source beamlines via power spectral density (PSD) analysis [1].

# GUI Features

- Elemental image and 2D PSD visualization
- A plot window capable of displaying azimuthally averaged PSD profiles for up to **ten** different elements simultaneously
- Isotropic and anisotropic (i.e. $x$ and $y$) spatial resolutions $\delta_{\mathrm{res}}$ and $\delta_{\mathrm{res},x}$ and $\delta_{\mathrm{res},y}$, respectively

# OS and File Requirements

Mac, Linux, and Windows systems are all supported.

Currently, HDF5 and MBLANK Matlab files (see [2]) are supported; <ins>**however**</ins>: 
- For HDF5 files, because synchrotron light sources can store data differently (i.e. have different file structures), if the synchrotron of interest is not available, please contact <benjaminroter2026@u.northwestern.edu> and provide a sample file so the structure can be included.
- If using a separate Matlab file structure, please send an email request along with a sample file to have that structure included.

# Introduction

The 2D PSD for a particular element can be found via

```math
\text{2D PSD} \equiv S\left(u_{x}, u_{y}\right) = \mathcal{F}\left\{\sqrt{I\left(x, y\right)}\right\}^{*}\mathcal{F}\left\{\sqrt{I\left(x, y\right)}\right\} = \left|\mathcal{F}\left\{\sqrt{I\left(x, y\right)}\right\}\right|^{2}.
```
- $u_{x}, u_{y} \equiv x$, $y$ spatial frequencies extending out to $1/\left(2\Delta_{x}\right), 1/\left(2\Delta_{y}\right)$
  - $\Delta_{x}$, $\Delta_{y} \equiv x$, $y$ pixel sizes
- $I \equiv$ fluorescence intensity

2D PSDs can be averaged over an arbitrary number of circles to produce azimuthally averaged PSDs $S\left(u_{r}\right).$
 - $u_{r} \equiv$ radial spatial frequency

Spatial resolution can be estimated by fitting power law signal decays and noise floors relative to the frequency $u_{\mathrm{res}}$ at which the signal and noise meet ("knee frequency" $u_{\mathrm{knee}}$); however, because there is approximately equal mixing of signal and noise at $u_{r}$, finding $u_{\mathrm{res}}$ corresponding to an SNR greater than one, i.e. corresponding to a multiplicative factor greater than one, will dilute the contributions to resolution from noise.

Half-pitch/half-period spatial resolution $\delta_{\mathrm{res}}$ for an isotropic beam can be estimated as

```math
\delta_{\mathrm{res}} = \frac{1}{2u_{\mathrm{res}}}.
```

For an anisotropic beam, $u_{\mathrm{res}} \rightarrow u_{\mathrm{res},x}, u_{\mathrm{res},y} \therefore \delta_{\mathrm{res}} \rightarrow \delta_{\mathrm{res},x}, \delta_{\mathrm{res},y}$.

# Installation

1. Install [Anaconda](http://continuum.io/downloads)
2. Clone this repository
3. Create an appropriate `conda` environment in a command line and activate it:

```
$ cd <path to PyXRFPower directory>
$ conda env create -f base_env.yml --name pyxrfpwr
$ conda activate pyxrfpwr
```

4. Invoke PyXRFPower:

```
$ python pyxrfpwr_launcher.py
```

# Additional Documentation

A manual for how to use PyXRFPower can be found inside the PyXRFPower repository: `pyxrfpwr_im.docx`  

More details about PSD analysis can be found in a manuscript currently being drafted.

# Contact

Having trouble using PyXRFPower, noticing bugs, or have recommandations for new features? Please contact <benjaminroter2026@u.northwestern.edu>.

# References

[1] J. Deng, D. J. Vine, S. Chen, Q. Jin., Y. S. G. Nashed, T. Peterka, S. Vogt, and C. Jacobsen, Sci. Rep. **7**, 445 (2017).  
[2] A. M. Crawford, A. Deb, and J. E. Penner-Hahn, J. Synchrotron Radiat. 26, 497 (2019).
