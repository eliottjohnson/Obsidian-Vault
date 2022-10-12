#### Beam size through tracking

* Next thing I can is track a [[Particle distributions]] and look at their distribution at the SEM-Grid.

![](https://codimd.web.cern.ch/uploads/upload_0c0bb585e4c078e564de4efc1b2267c2.png)



### Beam size through distribution

[Source code: kick_response_old_btp_model_beam_size.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_injection/bt3btp_lhcindiv/stitched/jmad/kick_response_old_btp_model_beam_size.ipynb)

I want to track a [[Particle distributions]] through the field map at injection for different POPS

I send a distribution of particle (always the same with a random seed)

![](https://codimd.web.cern.ch/uploads/upload_fe63f934495f6910984cbc807487a007.png)

![](https://codimd.web.cern.ch/uploads/upload_8bd1e59e39bd55c2a5845c25da84bb9e.png)

Although at first to save computation time I'll only launch a few

![](https://codimd.web.cern.ch/uploads/upload_d6dfc47104dfa244bd57b486d83bba9e.png)

Then as they exit the field map, I look again at the distribution and calculate the standard deviation.

![](https://codimd.web.cern.ch/uploads/upload_a5fd2a95b68fdd8cdb4847256fb67c64.png)

![](https://codimd.web.cern.ch/uploads/upload_2812557a492aea31b3455382b5acf612.png)

Remarks: 
We see the ellipse has an angle, meaning particles that particles that are are on the outside of the ring have less angle than the ones on the inside of the ring. This makes sense as particles that are on the inside of the ring in the initial distribution will feel more the magnetic field and thus be more bent.

![](https://codimd.web.cern.ch/uploads/upload_5d22ef326d7c86886db2c8cdb28eac2b.png)

![](https://codimd.web.cern.ch/uploads/upload_de719e71a80dccae758ee4fbc661c1b3.png)

As with the old model, the mean position of the beam gets more on the inside of the ring with POPS and the beam size gets larger with POPS (as the particles are more scattered depending on their initial location).

With the field map we can create a [[Multipole component model from injection]]. The first thought are in [[Comparing with old BTP model]].
