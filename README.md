# csms_genie
GENIE splines with CSMS cross-sections for high energy neutrino deep inelastic scattering (DIS) interactions.

## Background


### Native GENIE cross-section splines
The native GENIE cross-section that this work was based on was obtained using the following command in GENIE 2.8.6:
```
gmkspl -p 12,-12,14,-14,16,-16 -t 1000080160,1000010010 -e 1000 -o 'native_genie.xml' -n 500
```
### Default GENIE neutrino interaction channels
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

Cross-sections of the channels marked with an asterisk(&ast;) were modified in this cross-section spline package.

### Cross-section modifications


## Prerequisites
This set of GENIE with CSMS cross-section splines was developed and tested with GENIE 2.8.6. on <whatever the fend archi is>. 

## Getting started
Download and unpack the GENIE splines with CSMS cross-section found at https://github.com/plt109/csms_genie/blob/master/full_package_conjoined_v9b.tar.gz at your desired path(e.g. /path_to_GENIE/GENIE_2_8_6/data/xsec/), and proceed with generating GENIE events with the splines.

### Example to generate events using GENIE splines with CSMS cross-sections
For generating 5000 muon neutrino on water events with a flat flux from 60-210 GeV:
```
gevgen -n 5000 -e 60,210 -f '1' -p 14 --cross-sections /path_to_spline/full_package_conjoined_v9b.xml -t 1000080160[0.8879],1000010010[0.1121]
```

## Cross-check plots
### test
![](https://github.com/plt109/csms_genie/blob/master/figures/numu/p_multi_numu.png)

### Checking distribution of multiplicity and kinematic variables of stable daughter particles
blah

The full collection of the cross-check plots can be found in:
https://github.com/plt109/csms_genie/tree/master/figures

## Author
Pueh Leng Tan, 5 February 2019

## References
Details of the CSMS cross-sections calculations can be found at:
https://arxiv.org/abs/1106.3723v2

Cross-section values for neutrino and anti-neutrino Neutral Current (NC) and Charged Current (CC) interactions on proton, neutron, and isoscalar targets were obtained from:
http://www-pnp.physics.ox.ac.uk/~cooper/neutrino/
