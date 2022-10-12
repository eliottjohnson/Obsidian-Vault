# Emittance calculation of the extracted slow beam

From the PROTON-ION MEDICAL MACHINE STUDY (PIMMS)PART I document:

$$ E_{x, stack} \left(\frac{\Delta p}{p}\right)_{stack}T_{rev} = E_{x, spill} \left(\frac{\Delta p}{p}\right)_{spill}T_{spill}$$

$$ E_{x, spill} = \frac{E_{x, stack} \left(\frac{\Delta p}{p}\right)_{stack}T_{rev}}{\left(\frac{\Delta p}{p}\right)_{spill}T_{spill}}$$

* $T_{rev} = \frac{628}{3\cdot10^{8}} = 2.09\cdot10^{-6}  \text{[s]}$

* $T_{spill} = 400\cdot10^{-3} \text{[s]}$

* $\left(\frac{\Delta p}{p}\right)_{stack} \approx 1.71\cdot10^{-3}$

* $E_{x, stack} \approx 16.18 \text{[mm mrad]}$
https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3536208

The momentum spread of the spill depends on the sextupole strength and the chromaticity:

$$ \pi E_{x,stack} = \frac{48\sqrt{3}Q'^{2}\left(\frac{\Delta p}{p}\right)_{spill}^{2}\pi^{2}}{S^{2}}$$

$$ \left(\frac{\Delta p}{p}\right)_{spill} = \sqrt{\frac{E_{x,stack}S^{2}}{48\sqrt{3}Q'^{2}\pi}}$$

* $Q_{x}' \approx -1.25$
https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3343113

The sextupole strength is the sum of all sextupole in the machine called the virtual strength:
$$S = S_{virtual} = \sum{S\cdot e^{2i\mu}}$$
$$ S_{virtual} = \sum{\frac{1}{2}\beta_{x}^{\frac{3}{2}}\cdot l_{s}\cdot k'\cdot e^{2i\mu}} $$

where $k'$ is the normalised sextupole gradient

$$k' = \frac{1}{|B\rho|}\left(\frac{d^2B_{z}}{dx^{2}}\right)$$

and $l_{s}$ is the effective magnetic length of a sextupole [m].

* $S_{virtual} = 123.1 [m^{-3}]$
https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3343113

$$\left(\frac{\Delta p}{p}\right)_{spill} = \sqrt{\frac{16.18\cdot(123.1)^{2}}{48\sqrt{3}(-1.25)^{2}\pi}} \approx 24.5$$

In the end:

$$ E_{x, spill} = \frac{16.18\cdot1.71\cdot10^{-3}\cdot 2.09\cdot10^{-6}}{24.5\cdot 400\cdot10^{-3}} = 5.9\cdot10^{-9}$$
