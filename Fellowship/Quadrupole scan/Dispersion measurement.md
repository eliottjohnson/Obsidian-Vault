# Radial steering for dispersion measurement
Delta momentum before extraction and after extraction and change by a few % not to disturb the extraction

I think the parameter to change is PA.FREV-SD
Can you still do a dispersion measurement if the beam isn't centered in the quadrupole being scanned ?

$D=\frac{\Delta x}{\frac{\Delta p}{p}}$

We want to change the revolution frequency $\frac{\Delta f}{f}= -\eta\frac{\Delta p}{p} = -(\frac{1}{\gamma^{2}_{tr}} - \frac{1}{\gamma^{2}})\frac{\Delta p}{p}$

$\eta$ can be found in MAD-X by running a twiss

Marche à suivre in Accelerator Physics by S.Y. Lee p.137:
$$ D = \frac{\Delta x}{\frac{\Delta p}{p}}$$

and $$ \frac{\Delta p}{p} = -\frac{\Delta f}{\eta f} $$

$$ D = \frac{\Delta x}{-\frac{\Delta f}{\eta f}} = -\eta f_{0} \frac{\Delta x_{co}}{\Delta f_{0}}$$ this assume linearily because I replaced $\delta$ by $\Delta$

Where $x_{co}$ is the closed orbit, $f_{0}$ is the revolution frequency, $\eta$ is the phase-slip factor. The momentum of the beam is varied by changing the rf frequency.

![](https://codimd.web.cern.ch/uploads/upload_a4b419d2d9fb2d4e65b74dd6d2c6c0e6.png)

Basically, the Dispersion at a certain location is the slope of the change of position $\Delta x$ as a function of the change in frequency $\Delta f$. So if I do a fit of position as a function of frequency at each BTVs multiplied by $-\eta f_{0}$ I can get the Dispersion function at that location ($D(x_{BPM}$).

Then to check I can compare the Dispersion in MAD-X with my measurements like in the second plot.

WorkingSet -> LONGITUDINAL -> CPS:LL_H8H16 -> PAS.GSRPOS to change the frequency. This is an array so maybe grab java object and then change it.

PA.FREV-SED to monitor the frequency change
Also you can look at the sampler: Sampler -> BCT + ... @ CO -> PA.FREV-SD
![](https://codimd.web.cern.ch/uploads/upload_89fcfbe387712b961de0c5017cd5921e.png)

Pay attention that the first sample acquires at 150 ms
![](https://codimd.web.cern.ch/uploads/upload_3202f494e2b833fd88ffa9e318eb3a1e.png)

Dispersion measurement
|     |     |
| --- | --- |
| ![](https://codimd.web.cern.ch/uploads/upload_657b0b641fc386310289041aed0cea2f.png)    | ![](https://codimd.web.cern.ch/uploads/upload_3d27a6e3cb129ceb7e62cb10907eb132.png)    |

![](https://codimd.web.cern.ch/uploads/upload_4d18cfeae16747b878c125ab15b840d7.png)

![](https://codimd.web.cern.ch/uploads/upload_40542f51d930b1e823479f9167111d97.png)
![](https://codimd.web.cern.ch/uploads/upload_e459d49171aee9bf0cb4020bf93a234d.png)
![](https://codimd.web.cern.ch/uploads/upload_4f47b5099ab8c57ef9143b11173011dd.png)
![](https://codimd.web.cern.ch/uploads/upload_a2850dd245310f7a2bdf1a41e3e96940.png)


