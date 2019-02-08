# csms_genie
Native GENIE splines with Cooper-Sarkar-Mertsch-Sarkar (CSMS) neutrino cross-sections for high energy neutrino deep inelastic scattering (DIS) interactions.

## Background
The largest source of uncertainties in calculating neutrino cross-sections at high energies is the uncertainties on the parton distribution functions (PDFs) of the nucleon. 

CSMS neutrino cross-section is an updated prediction of high energy neutrino and anti-neutrino charged current (CC) and neutral current (NC) DIS cross-sections using the Dokshitzer–Gribov–Lipatov–Altarelli–Parisi (DGLAP) formalism of next-to-leading-order (NLO) Quantum Chromodynamics (QCD) and using the HERAPDF1.5 PDF fits.

This modified GENIE neutrino cross-section spline package attempts to incorporate the CSMS DIS neutrino cross-sections into the native GENIE neutrino cross-section splines. 

### Modifications to native GENIE cross-section splines
This neutrino cross-section spline package is designed such that the user can just download the spline package, specify this spline package .xml file to be used using the '--cross-sections' flag while generating events in GENIE, and GENIE will generate the neutrino events according to:

- Native GENIE neutrino cross-section for neutrino energies below 70 GeV
- A mixture of native GENIE neutrino cross-section and CSMS cross-section in the transition region from 70-200 GeV
- Pure CSMS cross-sections from 200-1000 GeV. CSMS cross-section for neutrino energies above 1000 GeV is not included in this spline package, but can be included should there be a demand for it.

The total charged current cross-section as a function of incoming neutrino energy for the various neutrino flavours on Hydrogen-1 and Oxygen-16 is show in the figure below:
![](https://github.com/plt109/csms_genie/blob/master/figures/xsec/nu_cc.png)
Zooming in to the transition and CSMS region, the modified GENIE cross-section deviates from the CSMS cross-section values by <10% at the 70 GeV and dropping down to <2% in the pure CSMS region:
![](https://github.com/plt109/csms_genie/blob/master/figures/xsec/nu_cc_zoomed.png)

The full collection of plots showing native GENIE cross-sections overlaid with CSMS cross-sections can be found in:
https://github.com/plt109/csms_genie/tree/master/figures/xsec

### Native GENIE neutrino cross-section region
The native GENIE cross-section that this work is based on is obtained using the following command in GENIE 2.8.6:
```
gmkspl -p 12,-12,14,-14,16,-16 -t 1000080160,1000010010 -e 1000 -o 'native_genie.xml' -n 500
```

## Transition region
In the transition region from 70-200 GeV, the native GENIE neutrino cross-section tapers off linearly while the CSMS cross-section is introduced linearly. This treatment minimises ripples in cross-section splines when GENIE interpolates from the cross-section splines using cubic splining.

## Pure CSMS neutrino cross-section region
CSMS neutrino cross-sections are calculated for $Q^2>1GeV^2$ so that perturbative QCD methods can be reliably used. CSMS neutrino cross-section values are not only available for neutrino energies <50 GeV as this region would have contributions from $Q^2<1GeV$. Details of the CSMS cross-sections calculations can be found at:
https://arxiv.org/abs/1106.3723v2


Decided to introduce CSMS fully >200 GeV because BLAH.

Left the tau neutrino cross-sections untouched because BLAH.


### Default GENIE neutrino interaction channels
GENIE will use the following event generators when the list of event generators to be used is not specified:
- Charged current quasi-elastic scattering (QEL-CC)
- Neutral current quasi-elastic scattering (QEL-NC)
- Charged current baryon resonance production (RES-CC)
- Neutral current baryon resonance production (RES-NC)
- Charged current deep inelastic scattering (DIS-CC) &ast;
- Neutral current deep inelastic scattering (DIS-NC) &ast;
- Charged current coherent neutrino-nucleus scattering (COH-CC)
- Neutral current coherent neutrino-nucleus scattering (COH-NC)
- Charged current deep inelastic charm production (DIS-CC-CHARM) &ast;
- Charged current deep quasi-elastic charm production (QEL-CC-CHARM)
- Neutrino-electron elastic scattering (NUE-EL)
- Inverse muon decay (IMD)
- Inverse muon decay (IMD-ANH)

Cross-sections of only the channels marked with an asterisk(&ast;) are modified in this cross-section spline package.

## Prerequisites
This set of GENIE with CSMS cross-section splines was developed and tested with GENIE 2.8.6. on Red Hat Linux. 

## Getting started
Download GENIE splines with CSMS cross-section found at https://github.com/plt109/csms_genie/blob/master/full_package_conjoined_v9b.tar.gz

Extract the .tar.gz file to your desired path(e.g. /path_to_GENIE/GENIE_2_8_6/data/xsec/). 
```
tar -zxvf full_package_conjoined_v9b.tar.gz -C /path_to_GENIE/GENIE_2_8_6/data/xsec/
```

full_package_conjoined_v9b.tar.gz contains the following files:
- Read me description file: README.txt
- Cross-section XML spline file: full_package_conjoined_v9b.xml (MD5 = df86ee7afdef52e02ad591618332edc5)

This cross-section XML spline file must be specified when generating events using GENIE.

### Example to generate events using GENIE splines with CSMS cross-sections
To generate 5000 events in each of which a 300 GeV muon neutrino interacts with water(88.79% O16, 11.21% H1):
```
gevgen -n 5000 -e 300 -p 14 --cross-sections /path_to_spline/full_package_conjoined_v9b.xml -t 1000080160[0.8879],1000010010[0.1121]
```

## Cross-check plots
### Multiplicity distribution checks
Checking the distribution of multiplicities of the stable daughter particles
![](https://github.com/plt109/csms_genie/blob/master/figures/numu/p_multi_numu.png)
![](https://github.com/plt109/csms_genie/blob/master/figures/numu/ap_multi_numu.png)

### Kinematics distribution checks
Checking the distribution of the 4-momentum components of the stable daughter particles
![](https://github.com/plt109/csms_genie/blob/master/figures/numu/e_numu.png)
![](https://github.com/plt109/csms_genie/blob/master/figures/numu/px_numu.png)
![](https://github.com/plt109/csms_genie/blob/master/figures/numu/py_numu.png)
![](https://github.com/plt109/csms_genie/blob/master/figures/numu/pz_numu.png)

The full collection of the cross-check plots can be found in:
https://github.com/plt109/csms_genie/tree/master/figures

## Author
Pueh Leng Tan, 5 February 2019
