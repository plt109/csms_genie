# csms_genie
GENIE splines with CSMS cross-sections for high energy neutrino deep inelastic scattering (DIS) interactions.

## Background


### Native GENIE cross-section splines
The native GENIE cross-section that this work was based on was obtained using the following command in GENIE 2.8.6:
```
gmkspl -p 12,-12,14,-14,16,-16 -t 1000080160,1000010010 -e 1000 -o 'native_genie.xml' -n 500
```

## Getting started

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
Pueh Leng Tan, 2019

## References
Details of the CSMS cross-sections calculations can be found at:
https://arxiv.org/abs/1106.3723v2

Cross-section values for neutrino and anti-neutrino Neutral Current (NC) and Charged Current (CC) interactions on proton, neutron, and isoscalar targets were obtained from:
http://www-pnp.physics.ox.ac.uk/~cooper/neutrino/
