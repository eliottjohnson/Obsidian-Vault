## Plan for 5-day ion run

Concerning the 5-day CHIMERA ion run, we need to start getting specific about the related test plan. My proposal for the first ~12h would be the following. We can use this email thread (and, of course, this week’s CHIMERA meeting) to continue discussing about it and extend the schedule further.

In terms of beam conditions, the baseline should be to run with 3 different PS energies (1 GeV/n, 750 MeV/n and 650 MeV/n) and varying intensity, through the RFKO technique. In principle other parameters such as the beam spatial profile and spill time profile will not be (intentionally) altered. Therefore, the main elements we will be changing, in addition to the energy and the intensity, will be the degrader and devices under test.

The first few hours of the beam time (e.g. 2 to 5:30 PM – all times are very tentative, of course) should be devoted to characterizing the three energies and varying intensity, as per the “standard”  beam instruments, making sure they are logging adequately, are set to the correct values (e.g. gain, voltage, etc.). This could in principle be done without the DUTs (diode and three SRAMs) in place, to spare them from some fluence during the setup, and to really focus our efforts on the beam instruments.

Then (5:30 – 9 PM), we could move in the Montrac with the DUTs, hoping this operation does not require an access, now that there will be no other users (i.e. racks, extra cable chains) in CHARM. And, we would test all four of them sequentially, for all energies, and perhaps 2 or 3 intensities each. Each irradiation will be short, but of course, 3 energies x 2 intensities x 4 DUTs is already = to 24 runs.

Then (9 PM – 2 AM), we would hopefully be able to access and place a degrader thickness which would ideally give us 3 new energies, one per each PS energy. We would therefore repeat all measurements already introduced above.

After that, we could perhaps leave a longer run over night, to e.g. accumulate statistics on the Renesas memory.

And, that would basically bring us to the access of Thursday morning, during which we could either change to a second degrader thickness, or to another set of DUTs. Or, something also potentially interesting could be to do a “degrader scan”, i.e. progressively adding thickness up to the point we reach the range of the beam and fully stop the primary ions, which would hence also be an indirect measurement of the beam energy.  

What do you think about this initial proposal?

After that, Friday would of course be fully devoted to the ESA tests, and possibly at least a part of Saturday as well, in case they need to collect more data. But, depending on whether ESA are interested in long runs, we could still have the night for “ourselves”. And, this would anyway leave us at least Saturday night and Sunday as backup (e.g. for extra tests) and for the optics measurements by Eliott, of course.

Looking forward to your feedback and extra ideas!!

Nominal:

**Pb54_3BP_2021_06_09_NOMINAL_3600ms_V1**


### General rule:

* Changing elements:
	* Energy
	* Intensity
	* Degrader
	* Device under test

* Not changing:
	* Beam size = not altered
	* Spill length = not altered

### Wednesday 23

* Set up the three energies
	* 1 GeV/n
	* 750 MeV/n
	* 650 MeV/n
* Vary the intensity (RFKO)

14:00 - 17:30:
* Characterization of the beam energy and varying intensity
* Make sure instruments are logging
* Set the gain to correct values
	* XSEC (gain = HIGH)
	* MWPC (voltage)
* DUT:
	* Empty (no diode, no 3 SRAMS to spare fluence)

17:30 - 21:00:
* Move the MONTRAC with DUT:
	* Diode
	* 3 SRAMs
* Test all 4 equipment sequentially
	* For all 3 energy
	* 2-3 intensities
	* 3 energies x 2 intensities x 4 DUTs is already = to 24 runs
	* placed in different spots on the frame (i.e., not stacked as it was during the 26th of oct) and that we would move the frame in the x, y remotely

* 21:00 - 02:00:
	* Access to place a degrader of specific thickness:
		* This will create three new energies
	* Repeat all measurements


### Thursday 24

02:00 - 08:00:
* Long run during the night to accumulate statistics on the Renesas memory

Access
08:00:
* Change degrader thickness
* Another set of DUT
* Degrader scan:
	* Progressively adding thickness up to the point where we fully stop the primary ions (= measurement of beam energy)
* Compare degraded energy with primary energy (energy spread, fragmentation)

### Friday 25

* ESA Test
* Nights:
  * Available for our own measurements

### Saturday 26

* ESA Test
* Nights:
  * Available for our own measurements

### Sunday 27

```mermaid
gantt

    title ESA Run

    dateFormat  HH-mm

    axisFormat %H:%M

  

    section Wednesday

    Setup three energies, characterization of the beam energy and varying intensity with RFKO: 14-00, 3h

    1000 MeV/u HIGH :14-00, 30m

    1000 MeV/u LOW :14-30, 30m

    750 MeV/u HIGH :15-00, 30m

    750 MeV/u LOW :15-30, 30m

    650 MeV/u HIGH : 16-00, 30m

    650 MeV/u LOW : 16-30, 30m

  

    Montrac movements: 17-30, 210m

  

    Diode: 17-30, 45m

    1000 MeV/u HIGH: 17-30, 7m

    1000 MeV/u LOW: 17-37, 7m

    750 MeV/u HIGH: 17-45, 7m

    750 MeV/u LOW: 17-52, 7m

    650 MeV/u HIGH: 18-00, 7m

    650 MeV/u LOW: 18-07, 7m

  
  

    SRAM 1: 18-15, 45m

    1000 MeV/u HIGH: 18-15, 7m

    1000 MeV/u LOW: 18-22, 7m

    750 MeV/u HIGH: 18-30, 7m

    750 MeV/u LOW: 18-37, 7m

    650 MeV/u HIGH: 18-45, 7m

    650 MeV/u LOW: 18-52, 7m

  

    SRAM 2: 19-00, 45m

    1000 MeV/u HIGH: 19-00, 7m

    1000 MeV/u LOW: 19-07, 7m

    750 MeV/u HIGH: 19-15, 7m

    750 MeV/u LOW: 19-22, 7m

    650 MeV/u HIGH: 19-30, 7m

    650 MeV/u LOW: 19-37, 7m

  

    SRAM 3: 19-45, 45m

    1000 MeV/u HIGH: 19-45, 7m

    1000 MeV/u LOW: 19-52, 7m

    750 MeV/u HIGH: 20-00, 7m

    750 MeV/u LOW: 20-07, 7m

    650 MeV/u HIGH: 20-15, 7m

    650 MeV/u LOW: 20-22, 7m

  

    Degrader installation : 21-00, 3h

  

    section Thursday

    Degrader installation: 00-00, 2h

  

    Long run during the night to accumulate statistics on the Renesas memory: 02-00, 6h

  

    Degrader scan: 08-00, 12h

    Access degrader: 08-00, 1h

    Another set of DUT, compare degraded energy: 09-00, 3h

  

    Access degrader: 12-00, 1h

  

    Access degrader: 15-00, 1h

  

    Access degrader: 18-00, 1h

  

    section Friday

    ESA Test: 08-00, 10h

    CHIMERA MD: 18-00, 6h

  

    section Saturday

    CHIMERA MD: 00-00, 8h

    ESA Test: 08-00, 10h

    CHIMERA MD: 18-00, 6h

  

    section Sunday

  

    TBD: 00-00, 24h
```

three energies

2 on one spare on energies single user

1 chimera cycle per 30 sec

One energie and move table

2 order of magnitude higher Lower and lower intensity

