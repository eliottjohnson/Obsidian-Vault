# Ion kinetic energy

using Chao's formulas [[Accelerator Physics Theory]]

The rigidity is defined as
$$B\rho = \frac{pc}{q}$$
The total momentum for an ion beam is
$$pc={E_{0}\sqrt{\gamma^{2}-1}}$$
$$pc = E_{0}\sqrt{\left [ \left( \frac{E_{cin}}{E_{0}}+1\right )^{2}-1\right ]}$$
with $E_{0}$ the rest mass of the ion and $\gamma=\frac{E}{E_{0}}=\frac{E_{0}+E_{cin}}{E_{0}} = \frac{E_{cin}}{E_{0}}+1$

The kinetic energy for an ion beam is $E_{cin}=E_{cin\text{ per nucleon}}\cdot A$ where A is the atomic mass number (sum of number of protons and neutrons).

### Example:
if you want a lead ion beam Pb54+ (which means it has 54 charges and 28 $e^{-}$ remain) of isotope A=208 of energy 1 GeV per nucleon the momentum would be:

$$pc = E_{0}\sqrt{\left [ \left( \frac{2\text{ [GeV]}\cdot 208}{E_{0}}+1\right )^{2}-1\right ]}$$
where the rest mass $E_{0}$ of Pb54+ is:

$$m_{Pb54+}= 82\cdot m_{proton} + 126\cdot m_{neutron} + 28\cdot m_{e^{-}} - m_{defect} = 193.74 \frac{GeV}{c^{2}}$$
with the mass defect: $m_{defect}=82\cdot m_{proton} + 126\cdot m_{neutron} + 28\cdot m_{e^{-}} - 208\cdot m_{u}$

with masses from [this source](http://physics.bu.edu/~duffy/sc546_notes10/mass_defect.html):
$$m_{p} = 0.93828 \text{ } GeV/c^{2}$$
$$m_{n} = 0.93957 \text{ } GeV/c^{2}$$
$$m_{e^{-}} = 0.000511 \text{ } GeV/c^{2}$$
$$m_{u} = 0.9315 \text{ } GeV/c^{2}$$

Simple python script to calculate B-field in Amps for a specific Kinetic energy per nucleon: https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/ion_kinetic_energy.ipynb

The other way around

$$E_{cin} = \frac{E_{0}}{208}\sqrt{\left[ \left (\frac{qB\rho}{E_{0}}\right )^{2} - 1\right] +1}$$
