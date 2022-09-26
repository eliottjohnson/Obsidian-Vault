# Emittance blow-up

Theory on emittance growth:
* [Sources of emittance growth D. Mohl](https://cds.cern.ch/record/941314/files/p245.pdf)
* [Sources of emittance growth CAS powerpoint by M. Giovannozzi](https://cas.web.cern.ch/sites/default/files/lectures/trieste-2005/giovannozzi-final.pdf)
* [Particle Data Group PDG Passage of Particles Through Matter](https://pdg.lbl.gov/2020/reviews/rpp2020-rev-passage-particles-matter.pdf)

Matthew wrote a code for the BGI gas scattering
[BGI gas scattering code](https://gitlab.cern.ch/mfraser/ps-injection-matching-analysis/-/blob/master/BGI_gas_scattering.ipynb)

Small script to get the order of magnitude of the air scattering
[Source code: scattering_on_air.ipynb](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/scattering_on_air.ipynb)

Residual gas act as a distributed thin scatterer. Pure nitrogen (N2) at pressure P has radiation length $L_{rad,N2}=327m$ The thickness traversed by the beam in time $t$ is $L=β_{p}ct$

$\theta_{rms} = \frac{13.6 MeV/c}{p\beta_{c}}q_{p} \sqrt{ \frac{L}{L_{rad}} } (1+\delta_{corr})$
$\Delta\epsilon_{k\sigma} = \frac{1}{2}(k\theta_{rms})^{2}\beta_{x}$

[Review of formulas for relativistic motion](https://uspas.fnal.gov/materials/12MSU/rellect.pdf)
-   $\beta_{rel}=\frac{v}{c}$
-   $\gamma_{rel}=\frac{1}{\sqrt{1-\beta^{2}}}$
-   $E_{total}=E_{rest}+T$
-   $\gamma=\frac{E_{tot}}{E_{rest}}$
-   $E_{total}=\gamma m_{0}c^{2}$
-   $p=\gamma m_{0} \beta c$

$\Delta\epsilon_{k\sigma} = \frac{1}{2}k^{2}q^{2}(\frac{14\cdot10^{-3}}{p\beta_{rel}})^2\beta_{x}\frac{L}{L_{rad}}$ with energies in units of GeV

$L_{rad}=\frac{L_{rad0}}{P/760}$

### Mattermost discussion from Andreas with length where beam travels through air
![[air region in T8.png]]
-   The last 50cm of "Drift_1"
-   From the downstream end of "F61.BCTF022" to 30cm downstream of "F61.MBXHD025"
-   From the downstream end of "Drift37" to "T08.BPM073"
-   4.11m upstream of "T08.BPM080" to "T08.BPM092"
-   From 15cm upstream of "T08.XION94" all the way until the CHARM dump

![[emittance_blow_up.png]]

Some other things to try:
* [ ] recalculate the $\beta$ after the scattering as $\beta=\frac{<x^{2}>}{\epsilon_{x}}$ 
* [ ] Calculate $\beta$ at every tiny length, maybe 10 cm

Maybe look again into these two formulas for analytical results
![[Pasted image 20220816143143.png]]


### Dipole kicks
You can also use dipole kick as a montecarlo

pycollimate has this function
$p.randn()\cdot\theta_{rms} = \theta_{i}$

$\sigma=\sqrt{\beta\epsilon}$


### Look at this code found in the gitlab
https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/5c41750652d4e7f0782838fc4a6a010a2662eae5/ps_extraction/tt2tt10_pb82_q26/line/fe_pb_strip_match.madx
```python
 thetascatt_rms = 13.6 * ZSCAT/((beam->beta)*(beam->pc)*1000) * sqrt(L/csi0) * (1+0.038*log(L/csi0));
 value, thetascatt_rms;! Scattering angle, caused by the stripper
 value, beam->beta, beam->pc, sqrt(L/csi0);
```
