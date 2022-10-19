# 750 and 400 MeV per nucleon

Ramp produit en croix avec le ratio du vieux et nouveaux momentum proton 

750 MeV/u c'est 5.392 GeV proton equivalent, see [[Current scaling for Ions]]

## Spill correction

We see two peaks and those can be corrected with LEQ

![[Pasted image 20221017162750.png]]

## Spill optimisation (intensity reduction and length increase) Tuesday 18.10.22

* [ ] try to reduce XSE strength
* [ ] try to do a local bump on TPS15
* [ ] try to reduce extracted intensity by changing QX_LEQ  (degraded extraction, tune kept a bit further from the resonance)


Reduced the intensity by using the bump 23 in the opposite direction. Kicking away from the septum.
Think about the ramp on POPS and the radial position of the beam during the ramping of POPS

PyLSA to grab BSW23 flat top values

We have to lower SMH57 because the beam crashes back on the septum blade. This is because with ions we bypass SEH23 (it has foils which would strip the beam) and so the bump is much closer to the blade.

### Summary of spill improvement
A quick update on the work we’ve done yesterday with Marc on the 750 and 500 MeV beams.  
  
**Spill shape**

-   We’ve doubled the length of each of these spills, they are now around 400 ms long.
-   The homogeneity of the spill has been improved, we removed the large spikes, and it is now looking more like a rectangular spill. There’s still some variation spill to spill and noise during extraction but if we take tens of minutes of beam, we should see it average out.

**Spill intensity**

-   Marc and Matthew had the clever idea of creating a bump in 23 (a zone used for proton extraction but not for ion extraction) and increase its height until the beam scrapes the aperture. This loses particles without changing the overall parameters of the beam as the emittance in H (controlled by the slow extraction scheme) and V are unaffected. The extraction can be kept the same.
-   The Intensity can be controlled by increasing or decreasing the bump height. If there is no bump, then the full intensity is transmitted, whereas increasing the bump height increases the number of particles that are shaven by the side walls which reduces the intensity.
-   A slight change in the tune function (QX_LEQ) is needed to keep a rectangular spill but this is easy to correct.
-   From the XSEC measurement we observed a decrease in amplitude of the signal (whatever this correlate to) from 10’000 to 1’000

I’ve recorded some data of the XSEC and the BXSCINT and I’ll make some plots for documentation and for the weekly beam update.  
  
I suggest we start with the 750 MeV and 500 MeV at full intensity to make sure we see the beams on the downstream instruments before degrading the intensity.  
  
Perhaps we could discuss on Friday the order of beams and the access to install the degrader. I would suggest:

1.  750 MeV for 30 min – 1h
2.  750 MeV at 2-3 lower intensity steps – 20 min per step ( + Time to change bump height and correct spill shape)
3.  500 MeV for 30 min – 1h
4.  500 MeV at 2-3 lower intensity steps – 20 min per step ( + Time to change bump height and correct spill shape)
5.  Access + Install degrader (40 min ?)
6.  Repeat 1-4

  
This would already be packed schedule and doesn’t account for POPS trips or other beam downtime.