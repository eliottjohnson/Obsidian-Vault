# East Slow Extraction Eliott

See [[EAST slow extraction]] for Matthew notes.
See [[East Area optics measurements]] for optics measurements.

![](https://codimd.web.cern.ch/uploads/upload_12a52038950a39150716bb60a96400ca.png)

## Sign comparison with septums

[Source code: slow_extraction_trajectory.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/59171358f877af9d5a0737caebca5b31fb73283b/ps_extraction/east-fast-extraction/Check%20scripts/slow_extraction_trajectory.ipynb)

Electrostatic septum SEH23 sign comparison
![](https://codimd.web.cern.ch/uploads/upload_412e3839063d7247aa4dec7b425ddb2b.png)

Septum SMH57 and SMH61 sign analysis
![](https://codimd.web.cern.ch/uploads/upload_7faf3f39fec228d843e2f1dea43acaa3.png)

## Excursion in Main units during a slow extraction

![](https://codimd.web.cern.ch/uploads/upload_79bb3d1b5f201737ac6c2f29931b14f8.png)


Just a confirmation that you need to kick positive with both magnetic septums to be outside of the ring at MU62
![](https://codimd.web.cern.ch/uploads/upload_11567ce1af9ddc3758baac615b8c2bc5.png)


With or without tune on resonance (19/3)

![](https://codimd.web.cern.ch/uploads/upload_a043b6630ddb314251bf7dd84ae8144b.png)

![](https://codimd.web.cern.ch/uploads/upload_9aa38d69b37029b4bb694026430e9100.png)

What we can tell is that only MU62 and MU63 are in the stray fields.

[Source code: slow_extraction_main_unit_excursion.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/ea116248c12b5ef497958727e02b7a56d7030a6f/ps_extraction/east-fast-extraction/Check%20scripts/slow_extraction_main_unit_excursion.ipynb)

### I made a mistake, I should have done four turns instead of three
Also now I'm tracking four particles at the edge of the phase space

![](https://codimd.web.cern.ch/uploads/upload_b7657c909a5c2e49e900ca4e3d5f2e30.png)

![](https://codimd.web.cern.ch/uploads/upload_725b1167ba0a7a8a5ddb3fe136af8e41.png)

![](https://codimd.web.cern.ch/uploads/upload_9417f8bab36007e4ea3840a08303bf1f.png)

It looks like my tune matching is wrong.
![](https://codimd.web.cern.ch/uploads/upload_1893b548ba2ace0cb037a1d3dcee9282.png)

The plots below are made with a particles that is in the middle of the initial conditions.

![](https://codimd.web.cern.ch/uploads/upload_250c4e641b251c9a9c4444cb4bfb7fb9.png)

![](https://codimd.web.cern.ch/uploads/upload_8e2cdc57897e74ecaa8c8c055fcb9fee.png)

![](https://codimd.web.cern.ch/uploads/upload_7acdc1d384d9a2ba8105b27173b34889.png)

![](https://codimd.web.cern.ch/uploads/upload_bd82eb51f482f56f8308def2db03789b.png)

## Pycollimate, maptrack

To install pycollimate go to the [pycollimate gitlab](https://gitlab.cern.ch/fvelotti/pycollimate)

* clone the repo: ``` git clone https://gitlab.cern.ch/fvelotti/pycollimate.git```
* Using SWAN's terminal >_ ``` cd ``` to location of clone
* ```git checkout east ``` as there is a modified version of the code
* ```python setup.py build_ext --inplace ```
* ```python setup.py install --user```


[Matthew's repo on EAST Studies](https://gitlab.cern.ch/mfraser/east-studies)

[Script to produce these phase space plots](https://gitlab.cern.ch/mfraser/east-studies/-/blob/master/simulations/preliminary/eastSXtrackSimple.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_730fba23283cdc401b5510678c6c24ba.png)

I select my points that are in the corners of the phase space outside of the septum

![](https://codimd.web.cern.ch/uploads/upload_0ed601489516eb874b30295e042de4e9.png)


After doing 4 turns in MADX with seh23 off
![](https://codimd.web.cern.ch/uploads/upload_98ea33c234b93de6b3a3f1a3946c6971.png)

Small bug because the twiss outputs I think at the end of SEH23

![](https://codimd.web.cern.ch/uploads/upload_dffa194abe8c1a75efa832811b01b975.png)

Entry of SEH23. After 3 turns the particles are not quite on the pycollimate map.
![](https://codimd.web.cern.ch/uploads/upload_1aa3971814382599a63df97f792a824a.png)

![](https://codimd.web.cern.ch/uploads/upload_4823ddfa6e4bb0396023a4b41b53e761.png)


![](https://codimd.web.cern.ch/uploads/upload_c7f306050d18814242eb18a694a66dd4.png)


Slow extraction during the last turn with all three septums on and four points of phase space plot.
![](https://codimd.web.cern.ch/uploads/upload_76ced57d1d1ced1953a98e80c4856eee.png)


![](https://codimd.web.cern.ch/uploads/upload_5575681e2500956ca1c50a173684b3c6.png)


![](https://codimd.web.cern.ch/uploads/upload_1be2adfadc71bc54b149f702e79e3e7e.png)

![](https://codimd.web.cern.ch/uploads/upload_b1976628cd70a8d5937ac6f4b94bf944.png)

![](https://codimd.web.cern.ch/uploads/upload_52dfc1ab3fcaf9e888035c9680b0c612.png)

![](https://codimd.web.cern.ch/uploads/upload_fad33794bd3e8fb4ea3e337d409a07c4.png)

![](https://codimd.web.cern.ch/uploads/upload_08398dd99e65064693f075b45d6ba4c2.png)

![](https://codimd.web.cern.ch/uploads/upload_eb228f6985715d5a05b2bbb9c4c4f2b6.png)

![](https://codimd.web.cern.ch/uploads/upload_78f3f6e8201a42bc7138276e31b5a217.png)

![](https://codimd.web.cern.ch/uploads/upload_0aa870024f2dfb07d3c1205e17b2522a.png)

### Comparing my slow extraction with the maptrack script

|||
:-------------------------:|:-------------------------:
![](https://codimd.web.cern.ch/uploads/upload_92cd0ed3f53f34fdf1916e0312183e49.png) | ![](https://codimd.web.cern.ch/uploads/upload_ff8fd9740fe8318d5d5fa6d39ee0993a.png)
![](https://codimd.web.cern.ch/uploads/upload_d441da3dcff618efa4f5bcbc5cd752f2.png) |

### If we kick positive with SEH23 (instead of negativ)
We don't jump the septum in smh57
|||
:-------------------------:|:-------------------------:
| ![](https://codimd.web.cern.ch/uploads/upload_fb70f7d570288bab14d11f95b6b7bb8a.png) | ![](https://codimd.web.cern.ch/uploads/upload_ba8fa4d89083e4636d8a00df4b3d7909.png) |

### Septum SMH57 position in Timber
![](https://codimd.web.cern.ch/uploads/upload_862ad7e43ca87802e1a75a4580d99125.png)

![](https://codimd.web.cern.ch/uploads/upload_59fb79068baceeff905ff69ded72fbca.png)

you don't have this information for SMH61 in Timber

![](https://codimd.web.cern.ch/uploads/upload_021fd2861afd713c6c547a6b3feb795c.png)

![](https://codimd.web.cern.ch/uploads/upload_9fd308d61ccefab82a10e2bde681f85c.png)

![](https://codimd.web.cern.ch/uploads/upload_54841266c942376645bf60b2910e01ff.png)

[EDMS SHM61](https://edms.cern.ch/ui/#!master/navigator/document?D:100524897:100524897:subDocs)

In smartteam search for PR.SD61

![](https://codimd.web.cern.ch/uploads/upload_5b4988f69c76832c7f8ed3aed95b267e.png)


![](https://codimd.web.cern.ch/uploads/upload_45e4300ff6eeaf097b7b783549b71e53.png)

![](https://codimd.web.cern.ch/uploads/upload_1a7808f39d66409650bc4424faa9976a.png)

On this top view you see that the vacuum pipe splits just after the quadrupole

![](https://codimd.web.cern.ch/uploads/upload_6a5fe3c37c343a982034e716cf02e807.png)

![](https://codimd.web.cern.ch/uploads/upload_028effe18055a1d8bccf570db974b9bd.png)

Some few rough number at the middle of the septum61

![](https://codimd.web.cern.ch/uploads/upload_8c975792d6b2b6c6d9562ca6f7fdebfb.png)


![](https://codimd.web.cern.ch/uploads/upload_99babaaa82d71eb846f00ed1b50010e1.png)

![](https://codimd.web.cern.ch/uploads/upload_03cde5373668e0663c45d048525647ca.png)

![](https://codimd.web.cern.ch/uploads/upload_b67fa46358663b6594964b43710b16db.png)

## Matching resonant tune

```
H-tune: 6.33, H-Chroma: -1.241
V-Tune: 6.33, V-Chroma: -0.242

k1prpfwf: 0.000339
k1prpfwd: -0.00055
k2prpfwf: 0.005584
k2prpfwd: -0.016767
```

which gives these tunes:
```
print(header["q1"],header["q2"])
6.3233037066 6.2188868141
```

![](https://codimd.web.cern.ch/uploads/upload_d85a976e6d3b5d6b0ec882584f318807.png)

[Source code: fast_extraction_three_turns.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_extraction/east-fast-extraction/Check%20scripts/fast_extraction_three_turns.ipynb)
![](https://codimd.web.cern.ch/uploads/upload_db8d42e724b52a57b5ac827f9b54aca3.png)

![](https://codimd.web.cern.ch/uploads/upload_4f9a49670fb0ddb7c8c551fa9e196f6e.png)


# Polarity of SMH57

https://edms.cern.ch/ui/#!master/navigator/document?D:101051143:101051143:subDocs

As pointed out by Eliott and his studies of the East extraction trajectory, Jan B confirms that the SMH57 defects the beam back towards its own blade.

This is quite unusual… but needed to get the beam out and into the SMH61 aperture even though SMH57 is on the inside of the machine.


<img src="https://codimd.web.cern.ch/uploads/upload_4be2f5ecd83800031b98907a7124a31e.png" alt="drawing" width="300"/>
See also [[Sign comparison with septums]]

# Fast extraction tune comparison

[Source code: fast_extraction_three_turns.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/EliottBranch/ps_extraction/east-fast-extraction/Check%20scripts/fast_extraction_three_turns.ipynb)

![](https://codimd.web.cern.ch/uploads/upload_d06a12d38031572987c8a301cc5e4db4.png)

![](https://codimd.web.cern.ch/uploads/upload_5cb363fa377aac658b56e1a6da3a0f2a.png)


Alex logbook entry on Q 6.1 and 6.36:
https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3444509

Denis's logbook entry on trying Q 6.1
https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3526256

Settings I think we should try where I optimize the beam with pybobqa

KFA71 : 527 kV
SMH57 : 7962 A

[Source code (permalink): fast_extraction_three_turns.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/5ae26c98d52c55f51323c69e143822ff53119089/ps_extraction/east-fast-extraction/Check%20scripts/fast_extraction_three_turns.ipynb)
![](https://codimd.web.cern.ch/uploads/upload_1e1961f321a14a30b67b873de05d9586.png)

[Logbook entry](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3527584)

```
EAST_FAST_22

Best tune without losses is Qh=6.15
SMH57=7900A
KFA71=520Kv

We see the beam in F61 ! Thank you Eliott !
```

[Logbook entry](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3527710)
![](https://codimd.web.cern.ch/uploads/upload_473c0eeaf2fb2fc874105140c19d9f5e.png)

[Logbook entry](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3527744)
![](https://codimd.web.cern.ch/uploads/upload_1c1f1a0d1b89a91f481ef815ed4b1754.png)


* [x] Add beam size to the fast extraction
    * [x] Add several sigma of beam size
* [x] Look at the shape of the beam wether it's focusing or defocusing
* [x] Plot the slow extracted beam 2 points that stay in the machine to see the opening
    * [x] See where the gap opens open up
    * [x] See the angle
* [ ] Look into the aperture model to see what the finger is in the main unit
    * [ ] Go in the Excel sheet and look to which finger the corresponds to
* [ ] Keep in mind the QSE misalignement (for slow extraction)
* [ ] Keep in mind the High Energy correctors (HE)
* [ ] Check the tomoscope measurement for sige, momentum spread during kick response
* [ ] Check chromaticity with the measurements
* [ ] Ask OP to measure chromaticity for 6.1 tune

* [ ] Scan the tune through a loop
    * [ ] write down the phase advance mu
    * [ ] delta mu between kfa71 and smh57
    * [ ] As a function of tune, the phase advance will oscillate
    * [ ] Maybe it's not exactly 6.1 maybe, 6.101

* [ ] Measurement with the BPM
    * [ ] Before and after the kick (last trajectory)
    * [ ] Check the difference (delta) between after kick and before kick
    * [ ] If tune Qx = 6.36, check the last three turns
    * [ ] Take aquisition on the BPM at different tunes
    * [ ] Set up TMS (Trajectory Measurement System) aquiring at extraction (not possible for slow because beam is debunched)
    * [ ] Grab all the important parameters
        * [ ] High Energy correctors (HE) (Working set, Ring, multipole)
            ![](https://codimd.web.cern.ch/uploads/upload_d3711b4317a0d9cb10081c8b3f9bbf8c.png)
        * [ ] Grab the K also
            ![](https://codimd.web.cern.ch/uploads/upload_0759db711bda97d8d878e62643d3956e.png)

        * [ ] Bumpers
        * [ ] XSE
        * [ ] QSE
        * [ ] Septums

* [ ] [Grabbing script](https://gitlab.cern.ch/mfraser/qse-alignment/-/blob/master/checkEAST_QSE.py) needs
    * [x] Change this line to BBB    ``` #bpmPS_data_temp, bpmPS_data['header'] = bpmPS.getTrajectoryBBB()
        bpmPS_data_temp, bpmPS_data['header'] = bpmPS.getOrbit()```
    * [x] [cern-general-device repo](https://gitlab.cern.ch/abt-optics-and-code-repository/commissioning-tools/cern-general-devices/-/tree/master/cern_general_devices)

![](https://codimd.web.cern.ch/uploads/upload_a93b1332a208fe8a6aa7b5a547c38bb8.png)

Not enough turn number

![](https://codimd.web.cern.ch/uploads/upload_3b2a7d1c812e6f35f6f3d91941b1df49.png)

[Source code: BPM_tune.py](https://gitlab.cern.ch/eljohnso/quad-scan-east/-/blob/master/BPM_tune.py)

Start of a turn is around 42, so when you look at a turn it resets at 42

Keep in mind this is with data at Qx=6.15 and sim is at 6.1


[Source code permalink: fast_extraction_three_turns.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/8aa47a1a834c84474af77eefd0b4fba18efa86ab/ps_extraction/east-fast-extraction/Check%20scripts/fast_extraction_three_turns.ipynb)
![](https://codimd.web.cern.ch/uploads/upload_8345198a134773ccbf18708eb4cc61af.png)

![](https://codimd.web.cern.ch/uploads/upload_1fea031bf30515504ea96ce33cac4ae8.png)

![](https://codimd.web.cern.ch/uploads/upload_212b10d08318e3bf36f132b596c55722.png)

![](https://codimd.web.cern.ch/uploads/upload_bc1b6b1c67ba164b1f153c8a748f9195.png)

Phase advance and tune
![](https://codimd.web.cern.ch/uploads/upload_19bf9704b6995c09189ecfc3299923ae.png)



![](https://codimd.web.cern.ch/uploads/upload_292915f1a5d98fcba08e5431e6b40987.png)

![](https://codimd.web.cern.ch/uploads/upload_1d885cf6c3e708194423fb91d9760b14.png)

# SMH57
[[SMH57]]


# BPM in T8
[[BPMs in T8]]

# Optimizer East

## Slow extraction

[Logbook entry SMH57 and SMH61 alignement](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3527758)

![](https://codimd.web.cern.ch/uploads/upload_8c0a1923e50e1619f0197f5758530514.png)

[Logbook entry SEH23 Alignment](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3527839)

![](https://codimd.web.cern.ch/uploads/upload_877915b5450075b7ef46e27a48429c02.png)

[Logbook entry SMH57 alignment](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3527880)

Change the angle of the septum SMH57
![](https://codimd.web.cern.ch/uploads/upload_af829a8168e0875ba8c709769039bf6b.png)

[Logbook entry septa killed](https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3527973)

Keep in mind that perhaps the optimizer should act on the REF.TABLE.FUNCLIST instead of the CCV.

``` Since the septa had very different values between CCV and REF.TABLE.FUNCLIST, the beam might have been killed during the afternoon if the septa changed mode, for some reason ```

## Fast optimiser

It should act (**actors**) on:
* Bumper BSW57
* Kicker KFA71
* SMH57 strenght, position and angle
* SMH61

Note: septa positions and angles are in OP-SPEC: CPS:SEPTA-POSITION

It should **minimise**:
* All BLMs
    * In particular around the extraction region 57-63
* Minimise $\Delta$ Intensity