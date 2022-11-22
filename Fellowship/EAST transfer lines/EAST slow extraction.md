# EAST slow extraction
See [[East Slow Extraction Eliott]] for my notes.

## Resources

* OP webtools, beam documentation (Oliver):
    * EAST cycle: https://wikis.cern.ch/display/PSOP/EAST+-+2018
    * Slow extraction: https://wikis.cern.ch/display/PSOP/Slow+extraction

* EAST slow extraction presentation (Ron):
    * https://wikis.cern.ch/display/PSOP/EAST+-+2018?preview=/103443159/103446077/Ron%20presentation.pdf

* Ions to EAST:
    * https://indico.cern.ch/event/602774/ (Marc)
  
* The new slow extraction system of the CERN PS: C. Steinbach, H, Stucki, and M. Thivent:
    * https://cds.cern.ch/record/251171/files/CM-P00059524.pdf

* Simulation of the PS slow extraction 62 with the MAD program: F. Galluccio et al.
    * https://cds.cern.ch/record/193857/files/198901534.pdf

* Beam optics at resonant extraction septa: C. Steinbach (CERN-PS-92-22-OP)
    * 3rd European Particle Accelerator Conference, Berlin, Germany, 24 - 28 Mar 1992, pp.857-859
    * https://cds.cern.ch/record/235950

* Optical design of a synchrotron with optimisation of the slow extraction for hadron therapy: M. Benedikt's thesis (CERN-THESIS-2000-022)
    * http://cds.cern.ch/record/450847
    
## Basics

* Proton beam extracted at 24 GeV/c
* Slow extraction on third-integer Q_x = 6.333 or 3Q_x = 19
* Momentum spread of the stack: $\Delta p/p$ quoted as 0.3%. Heiko dug out a tomoscope analysis after the bunch rotation giving $\Delta p /p|_\textrm{max} = \pm 0.3$%:

![](https://codimd.web.cern.ch/uploads/upload_9c47b5f5b6bed5a8c87f512a82678756.png)

* Stop-band width quoted as 0.1%

* Extraction:
    * PFW (figure of 8 loop) set to zero
    * PWF D and F used to force $Q_x = 6.2$ and $\zeta_x = -0.9$
    * Switch on bumps, quadrupoles, sextupoles and septa
        * Quadrupoles:
            * Add $Q_x$ of 0.13 which gives Qh = 6.33
            * Increase $\beta_x$ and make dispersion small at SEH23
            * Make dispersion big and positive at SMH57
        * Sextupoles: 
            * Add $\zeta_x$ of 0.4 which gives $\zeta_x = -0.5$
            * Control the ‘stability triangle’ size and the ‘spiral step’ (phase space kick)
        * Bumps: approach beam to the different septa
        * Septa: (SES23, SMH57, SMH61)
    * Hardt condition looks like it was imposed during the design: interesting to check this!

## Extraction equipment

* PE.SEH23, Septum electrostatic SS23 on inside of machine:
    * Parameters from Jan Borburgh (by email 7 June 2019):
        * Gap width: 17 mm
        * Field: 10 MV/m
        * Septum thickness: 100 um Mo foil, 
        * Apparent thickness < 200 um 
        * Length: 800 mm
        * $\int E dL = 8 MV$
        * Deflection angle $\approx$ 8 MV/ 25.6 GV  = 0.31 mrad
        * 800 mm long, 0.1 mm thick Mo foil. Longitudinally made from 4 or so foils. 
        * From TIMBER: Anode UP = 71.2 mm, Cathode = 86.3 mm, angle = 2.14 mrad
            * ![](https://codimd.web.cern.ch/uploads/upload_18304572627ca80b080613508023584a.png)

* PE.SMH57, Septum magnetic, under vacuum on inside of machine
    * Parameters from Jan Borburgh:
        * Lphysical: 850 mm
        * Gap height: 25 mm
        * Gap width between conductors: ~30 mm
        * Lmagnetic: 828 mm
        * I=9871 A
        * B.dl = 411 mT.m
        * Bo= 496 mT
        * Blade UP = 72.1 mm, angle = -0.4 mrad
        * Newer values:
            * I nominal 9300 A
            * B.dl nominal: 378 mT.m
            * Leak field: 0.4% @ 5 mm

* PE.SMH61, Septum magnetic, outside vacuum
    * Parameters from Jan Borburgh:
        * $I = 2350$ A
        * $B_0 = 4750$ G
        * $\int B dL =  0.247$ Tm
        * Leak field @ 20 mm: 0.6.10-3
* PE.BSW23, slow bump for PE.SEH23 (bumpers in SS19 and SS27)
* PE.BSW57, slow bump (bumpers in SS53, SS59, SS61 and SS
* PR.QSE, slow extraction quadrupoles in SS29 and SS87
    * It looks like the QSE's are voluntarily misaligned by +-15 mm
        * Nota Bene from Marine:
        `Les deux quadripôles sont décentrés radialement, de 15 mm à l’extérieur pour Q29 et de 15 mm vers l’intérieur pour Q87, afin de corriger l’orbite réelle du faisceau, déformée par rapport à l’orbite nominale. En effet, le tune horizontal avant le démarrage du “spill” étant 6.21, les bumps 23 et 57 ne sont plus exactement à l/2 donc la trajectoire du faisceau ne se referme pas sur l’orbite nominale. Cet effet affecte la trajectoire sur toute la circonférence de la machine.`
* PR.XSE, sextupoles slow extraction, two in SS01 and one in SS07

(check sextupole positions in figure below, look incorrect)
![](https://codimd.web.cern.ch/uploads/upload_65415ddbbee0ab037f46e4f1b9c042a0.png)

* Extraction sequence:
    * SS61 = (SMH61, BSW61) ![](https://codimd.web.cern.ch/uploads/upload_3005048ef00cc5b8c8013e8fb81e989e.png)
    * MU61
    * SS62 = (empty) ![](https://codimd.web.cern.ch/uploads/upload_735f540e2ca300d7c7d08697b51fe9e1.png)
    * MU62 (stray)
    * SS63 = (includes quad F61.MQNCL007, type Q74) ![](https://codimd.web.cern.ch/uploads/upload_349a338583fa3ce0af0092ded6276455.png)
    * MU63 (stray?)
    * BTV12 - corrector (F61.MCXCE013) ![](https://codimd.web.cern.ch/uploads/upload_be2a50b7ab367c212c1e1f851cbef387.png)
    * quad (F61.MQNEL014, type Q120), corrector (F61.MCXCE015) ![](https://codimd.web.cern.ch/uploads/upload_dd98cf16fa0c3b1bbbb55eb0c97ec137.png)
    * quad (F61.MQNEF021), dipole (F61.MQNEF021) ![](https://codimd.web.cern.ch/uploads/upload_b4af6a6bbb42bbff8a31645a20f0bfc0.png)
    * 2 dipoles (F61.MQNEF021) **HANDOVER POINT** ![](https://codimd.web.cern.ch/uploads/upload_118576c34b2e2084355c7ca8b3786d8c.png)
    * ![](https://codimd.web.cern.ch/uploads/upload_7c656efe4a0b48c0366eef53193d1207.JPG)
    * ![](https://codimd.web.cern.ch/uploads/upload_d05add1c93bb1009d53b185836961f1a.png)

# Stray fields geometry for extraction

## Main unit PR.BHU62 (drawing: PS_LM___0135):
![](https://codimd.web.cern.ch/uploads/upload_ba36c863a2da26adff022da19f71cec9.png)

## Straight Section SS62 (drawing: PS_LM___0136):
![](https://codimd.web.cern.ch/uploads/upload_3aebe24cf030bea87e8bb14f2b8f5a2d.png)

## Main unit PR.BHT63 (drawing: PS_LM___0137):
![](https://codimd.web.cern.ch/uploads/upload_59303adf805b4467ad477da12e4e6f34.png)

## Straight Section SS63 (drawing: PS_LM___0136):
![](https://codimd.web.cern.ch/uploads/upload_4916af7ddd18f1e7fa53b0ab1776d7af.png)

## Compare to Main unit PR.BHU16 (Same type as MU62) (drawing: PS_LM___0043):
![](https://codimd.web.cern.ch/uploads/upload_5c280a1982c4f7f52fde792b47dfda11.png)

# Handover point decision:

            Minutes from meeting on 30 October 2019
            Present: Klaus, Johannes, Lau, Eva, Alexander, Matthew, Brennan
            Excused: Wolfgang

            · A 27 cm offset has been found between the beginning of F61 (according to the model used to simulate this line) and the corresponding MU in the PS
            · In the model presently used the starting point of F61 is an arbitrary point which is close to the MU but does not correspond to any physical object
            · The first physical object in F61 where real survey data are available is the first quadrupole Q74
            · It is decided that this quadrupole will be used as physical reference point
            · ABT propose that they take over the responsibility for simulating the slow extraction from the PS towards the East Area including the first part of F61 up to the entry plane of bending magnet MBXHD025 (attention, names will change in the future)
            · From this handover point onwards EN-EA will be responsible for the simulation of the line

# Instrumentation

* Beam losses at 23, 57, 61, 63
* Mini Toposcope 57 (soft/hardware improvements needed) ?

* Info after discussion with Jocelyn Tan (7 July 2020):
    * Spill measurement (LSD now refurbished to BCGA23):

             · F61 Longitudinal Spill Detector (LSD) refurbished (now BCGA)
             · Volume of N2 gas, collect photons (gas instead of plastic), 2 scintillators working in co-incidence to remove background noise
             · Dedicated acquisition chain, uncalibrated single (for now)
             · Sampling rate limited by the PMT tube up to 1 MHz
             · Old spill monitor was very slow (~1 ms sampling)
             · Being installed in 10 days, location immediately after MBXHD025 
             ·  Same FESA class used for scintillators in NA secondary lines

    * SEM (XSEC):

            · SEM's already installed in East Area are identicaly to North Area devices: responsibility now given to Federico's team
            · Calibrated with  fast BCT (now upgraded with former Linac2 device) to calibrate
            · Might be fast enough to give reliable spill quality signal at lower frequencies

* BTV's:
    *  ![](https://codimd.web.cern.ch/uploads/upload_adcfc15dad90a90c6cc77e4dfe361760.png)



# Parameters from measurements

* Reference parameters extracted from measurements at the beginning of the spill $C = 1050$ ms.
* Measurements had the beam bunched but the ramp on the main units ON, which may explain some of the variations observed on the flat-top.
* See PS repo for measurements:
    * https://gitlab.cern.ch/acc-models/acc-models-ps/-/blob/master/scenarios/east/EAST2_chromaticity_measurement.md

## Flat top with PFW only

* Tune: $Q_x(C=1050~\textrm{ms}) = 6.22$ ![](https://codimd.web.cern.ch/uploads/upload_f5c1a3cdaf0c1cd1c53b2f5c07d47604.png)

* Chromaticity, $Q_x(C=1050~\textrm{ms}) = -10.0$ ![](https://codimd.web.cern.ch/uploads/upload_042d0165dc5a93b514c70cd35128c8ba.png)

* Non-linear chromaticity $Q''_x(C=1050~\textrm{ms}) = -180$ ![](https://codimd.web.cern.ch/uploads/upload_958ccd6276d332a6ef1ccadb9f355756.png)


* Following values matched in MADX:

        /**********************************************************************************
         *       Values given in repo at FT (with PFW and no XSE or QSE)
         *
         * Values based on non-linear chromaticity measurement along the cycle 
         * recorded on 01.11.2018
        ***********************************************************************************/

        ! Qx = 0.22395 + -10.0177*x + -178.26411*x^2
        Qx := 0.22395;
        Qxp := -10.0177;
        Qxp2 := -178.26411;

        ! Qy = 0.28702 + -2.18663*x + 48.4114*x^2
        Qy := 0.28702;
        Qyp := -2.18663;
        Qyp2 := 48.4114;
        
## Flat top with PFW and XSE:

* Tune, $Q_x(C=1050~\textrm{ms}) = 6.23$ ![](https://codimd.web.cern.ch/uploads/upload_b078bca4308cc15299fc6e8c9b308cdc.png)
    * XSE makes a very small perturbation to the tune 

* Chromaticity, $Q'_x(C=1050~\textrm{ms}) = -3.5$ ![](https://codimd.web.cern.ch/uploads/upload_83915853d4c155d1df246f846db0114f.png)
    * Large dispersion at XSE causes a very large perturbation to the chromaticity

* Non-linear chromaticity, $Q''_x(C=1050~\textrm{ms}) = -250$ ![](https://codimd.web.cern.ch/uploads/upload_b6cd68eb89119e3ab7045371a9f90274.png)

## Flat top with PFW, XSE and QSE:

* Tune, $Q_x(C=1050~\textrm{ms}) = 0.315$ ![](https://codimd.web.cern.ch/uploads/upload_a5f5123bcc010921e30759ca351a3a0c.png)
    

* Chromaticity: $Q'_x(C=1050~\textrm{ms}) = -3.5$ ![](https://codimd.web.cern.ch/uploads/upload_29f60645671106f69f9e6226438686b6.png)
    * QSE does not affect the chromaticity

* Non-linear chromaticity, $Q''_x(C=1050~\textrm{ms}) = -100$![](https://codimd.web.cern.ch/uploads/upload_d023db9565144319a63d64a286a2793d.png)

## Extracted beam profile (PR.SMH57: located about 8 cm upstream of SMH57)

* From Stephane Burger:
    * "The grid on the screen where the beam is has 5x5mm (in reality 7x5mm but installed at 45 degrees which makes it 5x5mm)."
    * The thicker lines on the left side of the screen represent the 3mm thickness of the septum blade.
    * ![](https://codimd.web.cern.ch/uploads/upload_2a70e991b3f119831578a21fe00d23e2.jpg)
    * Approximate beam size = 15 (H) x 5 (V) mm ![](https://codimd.web.cern.ch/uploads/upload_aa8959173477a35e286863193511e95a.png)

## Simulations

* With model matched to measurements (PFW only) I match the XSE strength to give $Q_x' = -3.5$ and then the QSE for resonance at DP = 0 
    * **Optics to be better defined/optimised later**

    * ![](https://codimd.web.cern.ch/uploads/upload_d3dd76557ff5f54cc98f420e7337efd8.png)
    * ![](https://codimd.web.cern.ch/uploads/upload_7814544bf8f3dd2b958e5ae749ff972b.png)
    * ![](https://codimd.web.cern.ch/uploads/upload_edb49b2924861ea247cd6ccdeb8fb13a.png)
    * ![](https://codimd.web.cern.ch/uploads/upload_c708879dff8a9a05b016076e0950d6b6.png)

* Rematching the tune using the QSE's has a minimal effect on the optics

* Settings used to track and generate the PTC maps:

        /**********************************************************************************
        *                             SBENDs and MULTIPOLES in MUs
        ***********************************************************************************/

        k1_f               =      0.05705266952 ;
        k1_d               =     -0.05711581728 ;
        k2_f               =                  0 ;
        k2_d               =                  0 ;
        mpk2               =     -0.01858039299 ;
        mpk2_j             =      0.03934772381 ;
        mpk3_f             =      0.05812457857 ;
        mpk3_d             =      -0.1320148496 ;

        /**********************************************************************************
        *                                    PFW and F8L
        ***********************************************************************************/

        pfwk1_f            =   -0.0001009094244 ;
        pfwk1_d            =    5.894593051e-05 ;
        pfwk2_f            =    -0.002222356465 ;
        pfwk2_d            =    -0.003987126033 ;
        pfwk3_f            =      -0.3425892323 ;
        pfwk3_d            =       0.3331200184 ;
        f8lk1              =                  0 ;

        /**********************************************************************************
        *                                    Injection dipoles
        ***********************************************************************************/

        kbsw26             =                  0 ;
        kbsw40             =                  0 ;
        kbsw41             =                  0 ;
        kbsw42             =                  0 ;
        kbsw43             =                  0 ;
        kbsw44             =                  0 ;

        /**********************************************************************************
        *                                    Extraction dipoles
        ***********************************************************************************/

        kbsw12             =                  0 ;
        kbsw14             =                  0 ;
        kbsw20             =                  0 ;
        kbsw22             =                  0 ;
        kbsw23             =    -0.001574679218 ;
        kbsw57             =     0.000829955906 ;

        /**********************************************************************************
        *                                      Quadrupoles
        ***********************************************************************************/

        kf                 =                  0 ;
        kd                 =                  0 ;
        kqse               =       0.1379634524 ;
        kqke16             =                  0 ;
        kqlb               =                  0 ;

        /**********************************************************************************
        *                                       Sextupoles
        ***********************************************************************************/

        kxno39             =                  0 ;
        kxno55             =                  0 ;
        kxno               =                  0 ;
        kxse               =        1.278381613 ;

        /**********************************************************************************
        *                                       Octupoles
        ***********************************************************************************/

        kono39             =                  0 ;
        kono55             =                  0 ;
        kodn               =                  0 ;

# Maptrack benchmarking

* 2 sector maps from SEH23 to SMH57, and from SMH57 to SEH23:
    * 2nd order: ![](https://codimd.web.cern.ch/uploads/upload_17b8b854444183952ec1c9f128f612bf.png)

    * 3rd order: ![](https://codimd.web.cern.ch/uploads/upload_5465be0b6b4b5be4e22264f733f8e87f.png)
 
  * 4th order: ![](https://codimd.web.cern.ch/uploads/upload_77c8e9bb5fe9c1ee27b8c3f4122eb54b.png)
  
  * 5th order:
![](https://codimd.web.cern.ch/uploads/upload_795bd6430810da8cfff65be0ca704743.png)

# First simulations with maptrack/pycollimate

## Protons

* No scattering, nominal settings: good results, spiral step at SMH57 is roughly 22 mm and a bit larger than in the SMH57 screenshot above (could trim the bump higher, systematic scans to be looked at later):
    * See eastSXtrackSimple.ipynb



| ![](https://codimd.web.cern.ch/uploads/upload_25a66ef11de17a2470507c6b5829966b.png) | ![](https://codimd.web.cern.ch/uploads/upload_10dac8a17d18e6987c6244cb4c7ac4ae.png) | 
| -------- | -------- | 
| ![](https://codimd.web.cern.ch/uploads/upload_d3f4ddf19437a1b198694e8a3b5aeb52.png)| ![](https://codimd.web.cern.ch/uploads/upload_5e97a5bfe9f1c79bdfd584816f457a04.png)
 | 
| ![](https://codimd.web.cern.ch/uploads/upload_2fc0491753959b27969b5b23b88d1d0a.png)| ![](https://codimd.web.cern.ch/uploads/upload_b413a74c470619f79d4d30acb78d1dc6.png)
 | 
| ![](https://codimd.web.cern.ch/uploads/upload_86bb018c457d8495ae86b287611e507d.png)| ![](https://codimd.web.cern.ch/uploads/upload_516317576e8531c1553b28e3f96e4502.png)
 | 
| ![](https://codimd.web.cern.ch/uploads/upload_84825afc6b3f1d8a6b30cd0faf0f57bd.png)| ![|1000](https://codimd.web.cern.ch/uploads/upload_ed69232086788ef228efaad7f102141a.png)
 | 
| ![](https://codimd.web.cern.ch/uploads/upload_e69d03aed4d18d867dc774fb3336f4d9.png)| ![](https://codimd.web.cern.ch/uploads/upload_951e84a9319d5e983569f32f6b50f5fa.png)
 | 



* Checking impact on circulating beam emittance (vertical beam size):
 ![](https://codimd.web.cern.ch/uploads/upload_ce1f74513640ac2d6c1bdbd229e07780.png)


### Spiral Step


## Ions

* No scattering, nominal settings but with BSW23 bump OFF and SEH23 retracted: good results, spiral step at SMH57 is roughly 30 mm (could trim the bump higher, systematic scans to be looked at later):
    * See eastSXtrackSimpleIons.ipynb

![](https://codimd.web.cern.ch/uploads/upload_3ab2729f71c4d5401abbb853ae9b58bd.png)
![](https://codimd.web.cern.ch/uploads/upload_651a9b828e75d8c4eaac61242335fbb0.png)
![](https://codimd.web.cern.ch/uploads/upload_540fa4ab80c2affaa7604024d01a2cc0.png)
![](https://codimd.web.cern.ch/uploads/upload_38dfeb8424a2ac6b80b5cac9cd0f0f5e.png)
![](https://codimd.web.cern.ch/uploads/upload_3e064efc186f2dfb7539f5b490242392.png)





# Stopband width

Nominal parameters quoted as maximum momentum spread of $\pm0.3\%$ with a stopband width of 0.1%

A quick check was performed in the nominal extraction scenario, validating the result at the extraction point (a uniform momentum spread of $\pm0.3$% was launched):

| ![](https://codimd.web.cern.ch/uploads/upload_92ffb77ad62f5dfffbe97e1517fcc225.png) | ![](https://codimd.web.cern.ch/uploads/upload_a58db4b5d16e1bb417b2f6430ccea7be.png)  |
| ---- | -- |
| ![](https://codimd.web.cern.ch/uploads/upload_0bddbc8c75169d52c231c667550ccaaf.png) | ![](https://codimd.web.cern.ch/uploads/upload_a11984526e1e46c2ecd276bcde2ed79f.png)
 |

**Comment:** this is a static simulation (no ramp) showing the optics of a single stopband width, the dispersion function is not correct when considering the entire momentum stack

The dispersion becomes very smooth with COSE when randomised over the entire momentum spread in the waiting stack. The result below uses a momentum spread equal to the stop band width to increase the number of particles extracted. The momentum spread of the extracted beam is artifically increased with a convolution with a uniform distribution. This result is to be verified with a MADX tracking simulation of the entire spill/ramp. In the SPS this was demonstrated as a good approximation.

| ![](https://codimd.web.cern.ch/uploads/upload_c435b8a858bb5313eabd646aabe26e02.png) | ![](https://codimd.web.cern.ch/uploads/upload_4f4105a42382f7a40e13fc1ef6c423dd.png) |
| - | - |
|  ![](https://codimd.web.cern.ch/uploads/upload_dc5fee496ef1fd5d3318cb826fa9640b.png) | ![](https://codimd.web.cern.ch/uploads/upload_e1c719e6cc336b418820bf06fec018e6.png) |

# Beam parameters for handover

* Warning: no MU stray field implemented yet!

* The dispersive contribution to the beam size is small in both planes. To be checked!

Immediately upstream of Q74:

| $\beta_x$ [m] | $\alpha_x$ | $\beta_y$ [m] | $\alpha_y$ | $D_x$ [m] |$D'_x$ [mrad]| $D_y$ [m] | $D'_y$ |
| - | - | - | - | - | -| - | - |
| 82.4 | -11.1| 33.2 | 0.28 | 0.13 | 0.02 | 0 | 0 |

* Iteration needed on F61 line geometry and implementation of optics in repository.

# MD Planning 2021

* Info after discussion with Johannes Bernhard and Nikos Charitonidis (8 July 2020):

        * New beam dump now available for setting up extraction:
            * First dipole can switch to different destinations inc, dump
            * Full extraction intensity now possible for set-up
                * Limit is about 6e10 protons for a usual supercycle composition (40ish seconds) (RP limits are the constraint)
                * Usual operation intensity is a few 1e10 (can go higher) maybe few 1e11 with reduced duty factor
            * New timings introduced per destination
            * Dynamic switching between destination is not so easy:
                (i) hysteresis effects in switching magnet might cause issues for parallel MD's (we will try during commissioning to check dynamic switching and constraints)
                (ii) dedicated MD on Wednesday as usual (many users setting up anyway)
                    * We can lock polarity of switch to send beam to the dump whislt access is on-going in East Area
    
        * New BLM’s available in F61 to guide set-up

        * SX to the dump will be possible in 2021 before secondary lines are up towards the end of year (delays due to COVID)  
        * Possible to do tests on operational beam while extraction to IRRAD and CHARM (e.g. application of RF structure)
        
        * Ions:
            * Solution will be to SX over the SMH only (SEH bump off)
            * Check number of ions measured by CHARM per spill
            * Check vacuum window specification
             
        * Simulations
             * Include aperture of Q74 (74 mm diameter)



# Stripping in SEH23: Pb54+ 

## Input from Gamma Factory team

* Discussion with Felx Kroeger, Thomas Stoehlker, Guenter Weber (17 July 2020):
    * felix.kroeger@uni-jena.de
    * T.Stoehlker@gsi.de
    * G.Weber@gsi.de

            * Ionisation cross-section most important at high energy (above a GeV/nucleon) and relatively constant with energy
            * Expect a range of charge states and ~ 5-6 electrons remaining for Pb54+ on two 25 um foils
            * Cross-sections accurate to a factor two so some difference would be expected
            * Check precision on foil thickness with septa team 
            * Data for high energy cross-sections is scarce and any data that can be attained is of relvance: stripping efficiency infered from the extraction efficiency would be interesting
            * Exit window of F61 could be interesting for gathering data on stripping efficiencies

![](https://codimd.web.cern.ch/uploads/upload_e23c8e37a425a72287d20bb8f2edfa4a.png)

* Post meeting correspondance with Felix: `Please find attached the plot (Picture 1) showing the charge state distribution for lead ions (starting at Pb54+) colliding with an Al foil at 5900 MeV/u. As discussed the scarce experimental data in this energy range lets us expect a probable shift of the charge state distribution to the left (see Picture 2 showing 2 variants of calculations taking into account the experimental findings), which however can only be determined better the more experimental data is available.`
* ![|875](https://codimd.web.cern.ch/uploads/upload_9a65215cd0d233c721a40951a81a4eb0.jpg)
* ![|950](https://codimd.web.cern.ch/uploads/upload_91a6032cd7567c06dbd11b486f3b4c0b.jpg)

**Clearly the ions will be almost fully stripped in SEH23**

## Charge state acceptance in the PS

* Increasing the charge state reduces the rigidity of the beam:
    * Highly charged ions will be bent to the inside of the machine
    
        $\frac{(B\rho)_1}{(B\rho)_0} = \frac{\Delta(B\rho) + (B\rho)_0}{(B\rho)_0} = \frac{p_1}{p_0}\frac{q_0}{q_1}=\frac{q_0}{q_1}$ where $p_1=p_0$ across the foils
    
* For fully stripped ions the rigidity will reduced by $\frac{q_0}{q_1} = \frac{54}{84} = 0.66$

* In MADX, the Twiss would simply need perturbing by $\textrm{DELTAP} = 1 - \frac{q_0}{q_1}$

* Even the loss of a single electron in passing the SEH23 would lead to beam loss on the PS aperture between the SEH23 and SMH57
    * DELTAP = $1 - 54/55$ = 1.8 %
    * Initial conditions shown by the markers, launched downstream of SEH23:
    ![|1000](https://codimd.web.cern.ch/uploads/upload_a9f8a28982e66df751460bbdad1231ff.png)

![|1000](https://codimd.web.cern.ch/uploads/upload_d98ca9f05f3998637e5323940b18a689.png)

![|1000](https://codimd.web.cern.ch/uploads/upload_57719e072d1a677292b6b74d226c0267.png)



* Losses expected in MU24/25/26, large amplitude in SS26 (PI.SMH26)

# Checking SEH23 foil scattering: protons

* Using pycollimate `Collimator` object with protons (Al with 25 $\mu$m thickness)
* Check pycollimate routine (all scattering processes vs. multiple Coulomb scattering):
    * Source term is generated at SEH23 and at 24 GeV/c (used for all $p_0$ in plots below). MCS becomes important below about 5 GeV/c 
    * ![|950](https://codimd.web.cern.ch/uploads/upload_57f8dbd2ec8712b8c8e9dfbdf69bfe8a.png)
    * ![|950](https://codimd.web.cern.ch/uploads/upload_957eac2dfe2512bb0136bd9dcd30e294.png)
    * Rare events (large-angle scattering etc.) introduce noise. 
    * ![|925](https://codimd.web.cern.ch/uploads/upload_30ef1707d163347d3d871c4bfa54aa41.png)

* Compute emittance growth through 2 foils:
    * Impact of foils is small at all energies (scaled intial source distribution by $1/(\beta_{rel}\gamma_{rel}$):
    * ![|900](https://codimd.web.cern.ch/uploads/upload_628065e9e861612bc18e97aa3c6ece9c.png)

# Maximum spill length (example from DIRAC in T8 from 2011

* Oliver stated RMS of MPS and septum at limit with 600 ms spill: 

![](https://codimd.web.cern.ch/uploads/upload_8c7b711c7e88b35aa2e3ec7cba24bf9b.png)

![](https://codimd.web.cern.ch/uploads/upload_3d6f92bc8334bb3bc2b4a8cb5a622398.png)


# Investigating the Hardt Condition

* Tracking a few particles that are off momentum but located on the edge of their separatrix, centred on their dispersive orbit (dispersion extracted from the Twiss file)
* To note: the resonance is ramped up through the momentum spread from below, give 
    * $\delta_p > 0$ and $Q' < 0$ therefore $\delta Q < 0$
    * This is important as it rotates the stable triangle by 180 degrees depending on how the resonance is approached

* Comment: Dispersion vector at the SEH23 is in the wrong direction (D,D') = (+,-) **We need to flip the sign of the chromaticity to achieve the Hardt condition at the SEH23!**

![|950](https://codimd.web.cern.ch/uploads/upload_79b8bdfebbd9c312e38b0c244ee3beec.png)

* Standard theory (explained nicely by M. Benedikt):

![|850](https://codimd.web.cern.ch/uploads/upload_19768a434f67ecbb0df7a360cb64745e.png)


![|925](https://codimd.web.cern.ch/uploads/upload_e5df1c06920821168593674a3340bb27.png)

![|825](https://codimd.web.cern.ch/uploads/upload_41670faf1718c6ce23bfcce46b01f4fc.png)


![|925](https://codimd.web.cern.ch/uploads/upload_5b289f88c9087cff12acb4fb82cc237e.png)

* In the PS case separatrix arm C is cut, $\alpha_0 = 420$ deg and $\Delta\mu = 140$ deg: 
    * $\alpha_0 - \Delta\mu = 280$ deg

## Computation of Q' for HArdt Condition 

* Imagining that I could adjust the virtual sextupole location and change $\Delta\mu$:

![|925](https://codimd.web.cern.ch/uploads/upload_0c35d20ad200a7774bfaacc6e62ea414.png)

**It looks like I am missing a phase of $\pi$ or a minus sign (related to the polarity at which particles approach resonance and the flip of the stable triangle at the virtual sextupole)**

* THe Hardt condition appears fulfilled for $Q' = +2.5$ in this case, not the negative!

## Computation of the Virtual Sextupole

* Computation of the virtual sextupole in the machine and phase advance of septa
* Reference phase is 'PS$START'
* Virtual sextupole is located somewhere inside and towards the second half of MU01 (inside PR.DHZ01.B)

### Nominal case ($Q' < 0 = -2.5$)

Driving term from XSE's only | Driving term from all sextpole components (inc. main units SBEND and MULTIPOLE elements)
- | -
![|975](https://codimd.web.cern.ch/uploads/upload_9592efd3302574144794241fec818082.png) | ![](https://codimd.web.cern.ch/uploads/upload_385ff2365db0560c9262da56adc6c9e8.png)

### Flipped chromaticity ($Q' > 0 = +2.5$): strong sextupole components in PFW


Driving term from XSE's only | Driving term from all sextpole components (inc. main units SBEND and MULTIPOLE elements)
- | -
![](https://codimd.web.cern.ch/uploads/upload_d54e579f216366bc8bf5884c62ce0b8c.png) | ![](https://codimd.web.cern.ch/uploads/upload_0399de2be2cda2ed429c3a0e4f435675.png)

Even with very strong sextupole components in the PFW the resonant driving term stays stable

## At the SEH23

### Nominal Phase space ($\delta_p > 0$)

$Q' < 0= 2.5$ | ![](https://codimd.web.cern.ch/uploads/upload_b92abd3c442bf436b76e3bf8cd0e7f3c.png) | $(D_n, D'_n) = (0.751, -0.126)$
 ------ | -------- | --------   
$Q' > 0= 2.5$ | ![](https://codimd.web.cern.ch/uploads/upload_6cd2e9619ddb68987564eaa28aa159ee.png)| $(D_n, D'_n) = (0.741, -0.1098)$


### Normalised phase compared with modified chromaticity

|  | $Q' > 0= 2.5$ | $Q' < 0= -2.5$ |
| -------- | -------- | -------- |
| PE.SEH23.UP | $(D_n, D'_n) = (0.741, -0.1098)$ | $(D_n, D'_n) = (0.751, -0.126)$ |
| $\delta_p > 0$ | ![](https://codimd.web.cern.ch/uploads/upload_a12480467878564353e5ad0e30ae98bf.png)| ![](https://codimd.web.cern.ch/uploads/upload_ac083da8bff0408f8d3372f92331058f.png) 
|  $\delta_p < 0$      | ![](https://codimd.web.cern.ch/uploads/upload_e1a7eb1937ad0461fd23375f718321b0.png)  |  ![](https://codimd.web.cern.ch/uploads/upload_dba53a1231300fc4a5eb58a488a86351.png)|

* Comment: the Hard Condition is met with positive chromaticity with the optics as given at the SEH23


## At the SMH57

### Nominal Phase space ($\delta_p > 0$ and $Q' < 0$)

$Q' < 0= 2.5$ | ![](https://codimd.web.cern.ch/uploads/upload_4f3c0fc1cd6c7bc611b5a57197edeeba.png)| $(D_n, D'_n) = (0.751, -0.126)$
 ------ | -------- | --------   
$Q' > 0= 2.5$ | ![](https://codimd.web.cern.ch/uploads/upload_16f18868e813e9a04ced19e2c09db023.png)| $(D_n, D'_n) = (0.741, -0.1098)$


### Normalised phase compared with modified chromaticity

|  | $Q' > 0 = 2.5$ | $Q' < 0 = -2.5$ |
| -------- | -------- | -------- |
| PE.SMH57.UP | $(D_n, D'_n) = (0.741, -0.1098)$ | $(D_n, D'_n) = (0.751, -0.126)$ |
| $\delta_p > 0$ | ![](https://codimd.web.cern.ch/uploads/upload_83df6a5ecdd41f7345c9530b85e4566c.png)  |![](https://codimd.web.cern.ch/uploads/upload_d4c8149980124be3f38d00e317cd6b96.png) |
|  $\delta_p < 0$      |  ![](https://codimd.web.cern.ch/uploads/upload_416e50e61d99170d32fd17aefba520cb.png)  |   ![](https://codimd.web.cern.ch/uploads/upload_f6877d9afcc625181bde46b0377f69c5.png)  |

* Comment: Steinbach explains that the optics is perturbed with the QSE's to increase the beta function at both septa. The gap opening in maximised when the dispersion at the SEH is small but large at the SMH. Discussion of this found in the referene at the top of the page.

## At the Virtual Sextupole

### Normalised phase space

* Rotating back the SEH23 phase space by 138 degrees to the virtual sextupole with a linear trasnformation

|  | $Q' > 0 = 2.5$ | $Q' < 0 = -2.5$ |
| -------- | -------- | -------- |
| Virtual 6pole | $(D_n, D'_n) = (0.741, -0.1098)$ | $(D_n, D'_n) = (0.751, -0.126)$ |
| $\delta_p > 0$ | ![](https://codimd.web.cern.ch/uploads/upload_39130697bb64df9b447cab9486ca42c8.png) | ![](https://codimd.web.cern.ch/uploads/upload_d7c9b5ff0a2c0bec8105728a3c1f87a5.png) |
|  $\delta_p < 0$      |  ![](https://codimd.web.cern.ch/uploads/upload_ff6a7517a00a5284f1c787a094b8ebf5.png)  |  ![](https://codimd.web.cern.ch/uploads/upload_5a5d028353cdb88582b7baeb26dcffd5.png)  |


* I should run a tracking to check the phase space at the location of the virtual sextupole.

 ## Simulation comparison 

| $Q' < 0 = 2.5$ | $Q' > 0 = -2.5$ |
| -------- | -------- | 
![](https://codimd.web.cern.ch/uploads/upload_10dac8a17d18e6987c6244cb4c7ac4ae.png) | ![](https://codimd.web.cern.ch/uploads/upload_e902bb089772a834782e1111bad55fee.png) |
 ![](https://codimd.web.cern.ch/uploads/upload_5e97a5bfe9f1c79bdfd584816f457a04.png)  | ![](https://codimd.web.cern.ch/uploads/upload_64786baa007fee286b137a7c82838131.png) |
![](https://codimd.web.cern.ch/uploads/upload_b413a74c470619f79d4d30acb78d1dc6.png) | ![](https://codimd.web.cern.ch/uploads/upload_95a6db664a142e457ced74c61a5a63bf.png)
 ![](https://codimd.web.cern.ch/uploads/upload_516317576e8531c1553b28e3f96e4502.png) | ![](https://codimd.web.cern.ch/uploads/upload_eb4323325282d66ae6e244e56b880585.png)
 ![](https://codimd.web.cern.ch/uploads/upload_ed69232086788ef228efaad7f102141a.png) | ![](https://codimd.web.cern.ch/uploads/upload_c041cf61cc0e14c1c071fc2ca358418a.png)
![](https://codimd.web.cern.ch/uploads/upload_951e84a9319d5e983569f32f6b50f5fa.png) | ![](https://codimd.web.cern.ch/uploads/upload_492790aba106b6ddc0cfd7a60ce96a37.png)
 

 * **Opening at SMH57 is reduced when implementing the Hardt condition at SEH23**
 
# Check QSE voluntary misalignment

## Closed-orbit perturbation

* No apparent closure of the bump created by an equal and opposite misalignments of the QSE magnets (SEG23 and SMH57 locations shown with  black lines):

![|1000](https://codimd.web.cern.ch/uploads/upload_e510d8ef42bc7d798e6753e7784789dd.png)

* Actually, misaligning both quads makes the closed-orbit oscillation worse: large oscillations of 5 - 8 mm
* The offsets were probably implemented emprically and I would guess evolved over time as the closed-orbit changed and aperture bottlenecks appeared

* Check with misalignement in the same direction:

![|1000](https://codimd.web.cern.ch/uploads/upload_51900377cd0a95cf8ce139fbc662048a.png)

# Aperture

## Reference (QSE's on axis)

* Envelope of all three arms separatrix arms plotted with the extracted beam (between SEH23 and SMH57) with the aperutre model (provided by Alex)

* **Comments**:
    * SX envelope approaches aperture in SS09 and upstream in Main Unit 09
    * No aperture bottlenecks at SQE29 and QSE87 locations

![](https://codimd.web.cern.ch/uploads/upload_fab0c772e5e8afafe863782d6a311e8b.png)

## QSE29 -15 mm

![|975](https://codimd.web.cern.ch/uploads/upload_e946fe2fdc21d879e6121f1de7bccea2.png)

* Makes the bottleneck in SS09 slightly worse

## QSE87 +15 mm

![|975](https://codimd.web.cern.ch/uploads/upload_63f8dd22e5f6babe2ca8f74aa717cee8.png)

* Makes the bottleneck in SS09 slightly worse

## QSE29 and 87 +-15 mm

![|975](https://codimd.web.cern.ch/uploads/upload_04fc5070408ab6dac8ea7ba50a5cdb48.png)

# Implementation of AutoSPILL

* Discussion with Alex, Denis, Oliver and Verena (1 September 2020):

        * Input required by AutoSPILL to linearise decay of BCT decay, by increasing/decreasing rate of tune sweep:
            * SX timing event
            * BCT during the spill
            * LSA momentum parameter
        * Comment: A delay of ~ 200 ms after SX start event needed before beam is extracted (for RF gymnastics etc)
        * Things to be done:
            * PFW ->  make-rule needed for the EAST case with only 2 circuits during SX, perhaps we need a specific function generator for EAST, tbc.
            * Denis has already linked QSE and XSE to momentum, magnetic septa to be added
        * Timeline: dry run test without beam -> November?

* Post-meeting follow-up, Alex noticed that in an old drawing of SS01, an air-quadrupole (element number 3) was used for 50 Hz compensation. This part of the SS is still empty, so the space could be re-used, if required.

![|975](https://codimd.web.cern.ch/uploads/upload_937c069627dd557f8e1ac4558385dee1.png)


# Optics checks

From Marine's document:

L’optimisation du processus d’éjection lente (minimisation des pertes et haute efficacité) impose des contraintes sur l’optique du faisceau à l’emplacement des 2 septa.

A l’emplacement du septum électrostatique, il serait intéressant de minimiser les pertes en superposant  les séparatrices des différentes énergies. Cette méthode, proposée par W.Hardt pour la machine LEAR et décrite dans la note , impose la relation:

$8 \pi Q'_h /S  + D_{n1} \cos{\phi_1} - D'_{n1}\sin{\phi_1} = 0$ (A3)

avec:
$Q'_h = \eta_h Q_h$


$D_{n1}, D’_{n1}$: coefficients normalisés de dispersion au premier septum
$\phi_1$: angle de phase bétatronique entre le sextupôle équivalent et le premier septum

A l’emplacement du septum magnétique, il faut remplir une condition similaire pour optimiser l’éjection. Même si le faisceau extrait présente une émittance nulle à l’emplacement du premier septum (la contrainte à l’emplacement du premier septum est vérifiée), du fait que le deuxième septum n’est pas dans la même section que le premier et que, généralement, le transfert n’est pas achromatique, la position des particules du faisceau extrait au deuxième septum va dépendre de leur énergie. Ainsi, deux particules d’énergies différentes et se trouvant en $Xa1 = Xb1$ au premier septum se trouveront en deux positions différentes au deuxième septum: $Xa2 \neq Xb2$.

 
Pour optimiser la séparation au deuxième septum, la chromaticité et la dispersion sont ajustées afin que la position de la séparation soit indépendante de l’énergie (cela revient à: $Xa2 = Xb2$). 

La condition à satisfaire est:

$ + D_{n2} \sin{\phi_1} - D'_{n1}\sin{\phi_2} = 8 \pi Q'_h /S \sin(\phi_2 - \phi_1)$ (A4)

avec:
Qh’ = h * Qh 	
Dn2, D’n2: coefficients normalisés de dispersion au deuxième septum
$\phi_2$: angle de phase bétatronique entre le sextupôle et le deuxième septum 

Un choix approprié des paramètres de dispersion Dn1, D’n1, Dn2, D’n2  (au moyen de la position et de la force des quadripôles) et de la chromaticité Qh’ (au moyen de la position et de la force des sextupôles) permet THEORIQUEMENT de satisfaire les deux conditions (A3)  et (A4) exprimées ci-dessus.

Cependant, pour le PS, du fait que les deux septa sont du même côté de la machine, les conditions (A3)  et (A4) n’ont pas pu être remplies toutes les deux. **Seule, la condition (A4) est satisfaite. On a renoncé à l’optimisation des pertes au septum électrostatique au prix d’environ 0.5% de pertes supplémentaires.**

Pour remplir la condition (A4), il faut appliquer une chromaticité Qh’ assez grande pour limiter la dispersion d’énergie du faisceau extrait, ce qui implique que la valeur du bras gauche de l’équation (A4) soit la plus haute possible. Comme les deux septa sont du même côté de l’orbite fermée, il faut appliquer une faible dispersion horizontale au premier septum et une grande au deuxième septum.`


# Check stopband width

# LSA parameters available in LSA
PS MOMENTUM function : **PSBEAM/MOMENTUM**

Quadrupole function (Q29 & Q87) : **logical.PR.QSE** (k)-> PR.QSE (FGC I) normalized with momemtum
Sextupole function (X01 & X07): **logical.PR.XSE** (k)-> PR.XSE (FGC I) normalized with momemtum

Bumper23 (SS19,27) : **logical.PE.BSW23** (k)-> PE.BSW23 (FGC I) normalized with momemtum
Bumper57 (SS53,59,61,67) : **logical.PE.BSW57** (k) -> PE.BSW57 (FGC I) normalized with momemtum

Beam Current Transformer (SS34): PR.BCT (class BCTDCPS)

Default start timing is PE2X.MC-CTML (there is around 100ms following this timing for the rising edge of different function)

Concerning SMH57 and SMH61, pre-LS2 there was only a scalar value available to program the current. -> PC migrated to FGC_63 during LS2, we should be able to create a function normalized with momentum now. (tbc with TE-EPC)

[](http://elogbook.cern.ch/eLogbook/attach_reader?attach_id=2026496)


# Misalignment of vacuum chamber downstream MU61

9th September 2020

*FYI, attached a pic from the EAST extraction chamber at the downstream end of MU61. The offset between the two parts of the chamber is probably around 3 mm, and there doesn’t seem to be any possibility to fix this now. Jose will try to push the chamber up a bit, let’s see. With the limited instrumentation we have for the extracted beam that’s really a shame, I hope it won’t cause too much of a problem. It seems it has already been like that in the past, but looking at the old 3D image from this section, it didn’t seem that severe. Cheers, Alex*

![](https://codimd.web.cern.ch/uploads/upload_01c3624b2beea854d6404e5a397e8718.jpeg)


# Restart 2021

## Resources

PFW, QSE tune scan: https://docs.google.com/spreadsheets/d/1yXRERGp3AKFule6cgC_ScqV8oP0UmbzF25OV1Hqtmdg/edit#gid=0
First tune, chroma meas: https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3315857
EAST optics studies July 5th: 
https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3342505

https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3342508

https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3342514

https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3342608

Setting PFW values correctly, July 5th: https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3342525

Chroma meas: July 7th
https://logbook.cern.ch/elogbook-server/GET/showEventInLogbook/3343113



## Commissioning Measurements

| Measurement | Cycle Type | Studies | Date(s) | Comment   |     
| - |-|-|-|-|
| Q on FT  (PFW-MAIN OFF) |   *PILOT   | B ramp ON/OFF | 8/7/21  | Tune drift when ramping |          
| Q' (PFW-MAIN OFF) |   *PILOT   |  B ramp ON/OFF  | TO DO | Check optics variation|   
| Flatten Q-slope with PFW (PFW-MAIN OFF) |   *PILOT   |  B ramp ON/OFF  | TO DO | Measyre Q' variation|  
 | Q on FT with PFW-MAIN ON  |   SE61_Studies   |   B ramp ON/OFF   |  TODO | Compare with PFW-MAIN OFF, flatten? |   

*PILOT = **PILOT_24GeV_PFW_Studies_CloneType**
*SE61_Studies (TEST type not MD!)


### Before SX

* Tune and chromaticity measurements (could use LHC pilot beam with lower intensity):
    * Beam bunched, RF ON, no ramp on B
    * Different configs: bare, PFW, PFW + XSE, PFW + QSE, PFW + XSE + QSE
        * All functions must be constant in time
    * **Repeat with Bdot on POPS**: check scaling/ramping of optics and VAR

* Octupole studies

* RF channelling first tests

### With SX

* setup...
* Correct radial positioning


# EAST Commissioning tasks

## Check beam position in Q74

* Scan Q74 strength and measure beam movement on BTV012: find the centre of the quadrupole




