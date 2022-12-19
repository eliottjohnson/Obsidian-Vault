# PS Magnetic Shims

The main discussion is on the [[PS Stray field]] note.

The question is, do we still have shim installed in the extraction lines. If yes, Miro yould add them to the fieldmap.

E-mail from Dominique Bodart on 24.01.2022
```
The shims in 16 and 63 are present, none in the injection region only mumetal around the chamber.
Modelling can teach you where is best efficient to install shims based on their transverse position.

```
# Master Thesis on Shims
[Master thesis on Shims](https://cernbox.cern.ch/index.php/s/AONQ54MYNKGBpAV)

![](https://codimd.web.cern.ch/uploads/upload_74d58a0c26f048e3760c1f32a99d4fcd.png)

Summary of the thesis:
* He uses a new measurement bench with a spare Main Unit PS U17
* Alternating Gradient principle (AG)
    * two half-units, focusing (F), defocusing (D)
    * opposite sign of $\bf{\frac{dB}{dr}}$ the **gradient of induction**, where $B$ is the induction in the aerture gap and $r$ is the radial coordinate in the accelerator bending circle.
![](https://codimd.web.cern.ch/uploads/upload_b00e91bf5462fba5978b989c444cde0e.png)

* Tendency of the beam size to grow if left unfocused.
* Require the field index $n$ (basically, the focusing strength) to be $0<n<1$
$$ n = \frac{r_{0}}{\bf{B_{0}}}\frac{d\bf{B}}{dr} $$
    * $r_{0}$ is the radius of the curvature of the beam
    * $B_{0}$ is the central dipole induction
* If we have **gradient of induction**, particles at different radial distances will **bend more or less**.
    * Big gradient means big difference in forces
* Weak focusing machine have a **constant** gradient.

Alternating Gradient is very good because you gain the advantage of combined focal length in optics:

$$ \frac{1}{f} = \frac{1}{f_{1}} + \frac{1}{f_{2}} - \frac{d}{f_{1}f_{2}} $$

If you have focusing, defocusing (opposite focal lengths), $f_{1}=-f_{2}$, we get $f = \frac{f_{1}^2}{d}>0$ **always positive**.

![](https://codimd.web.cern.ch/uploads/upload_4d2d4347afcdaba402ed2ee413b792c0.png)

* In the horizontal plane, the beam is defocused so you think it's bad, but actually, it's further from the axis in the focusing lens and so it is **focused more strongly**.
* The field index **can now be** $n>1$, which reduces beam size!
* PS: $n=288$
* This is why in the PS, half focusing, half defocussing.

### Magnet measurements

* Dipoles to bend
* Quadrupoles to focus
* Sextupole to correct chromaticity

#### PS Main Unit

![](https://codimd.web.cern.ch/uploads/upload_b2a1de6b3f1983fe017ce3cf4cf5a096.png)


* Made up of 10 adjacent magnets **blocks** of 417 mm long
* Each block is a **C-shape**
* Not straight but curved, with radius $r_{0}=70.0789 m$
* The magnetic length is the physical length of the iron core plus 71.59 mm
* Angle between block are 6.271 mrad for the F-side and 6.295 mrad for the D-side.
* Gaps:
    * 20 mm between F and D
    * 7.775 mm gaps on the F side
    * 9.75 mm gaps on the D side
    * Difference between F and D to adjust number of betatron cycles
* RS UT are used to cancel yoke position
* FDODFOFDODF pattern
![](https://codimd.web.cern.ch/uploads/upload_a4b5999cb9d460f5cb0b07e205b050d9.png)

#### Exciting coils

* One **main coil** wound around top and bottom poles
    * Each main coil consists of two layers called pancakes
        * Pancakes are made from 5 turns of conductor (aluminium)
        * Conductor is rectangular (55 x 38 mm) with water cooling in the center
        * All the coils of the 100 MU are connected in series
        
* Auxiliary windings (correct harmonics)
    * **Figure of eight loop** (**F8**) to change **tune** (quadrupolar component)
        * Doesn't change the chromaticity (integrated bending field)
        * Creates an **opposite** change of the **global field strength** in D and F
        * Increases gradient in one half unit while decreasing in the other
        ![](https://codimd.web.cern.ch/uploads/upload_75d0ce2f343b184c0460c87d1aa7c2ef.png)

        * /!\ my plot: I think it would look something close to this

        ![](https://codimd.web.cern.ch/uploads/upload_72259b0c59db331db6b029dd1e07c087.png)

    * Two **pole-face windings** (**PFW**)
        * One for F and one for D
        * Produce large **quadrupolar** and **sextupolar** field component
        * little effect on dipole component
        * They adjust tune and chromaticity by saturation
        * Can control separately F or D side
        
        ![](https://codimd.web.cern.ch/uploads/upload_96ac14f7c3b2965b31c1883e1fc676ab.png)

![](https://codimd.web.cern.ch/uploads/upload_f084acbe7843884ed043def6ea2f083e.png)

#### Shims

* PS Ring has **short straight sections** for injection/extraction
    * For injection it's ok because we are at low energy
    * For ejection you need to extract with **small angles** to pass the ejection **septum** (thin blade beyond which beam is deflected by electrostatic forces)
    * Small angles means the ejected beam passes close to MU
* **Ejection site 16**
    * "In the D half-unit the ejection particle trajectory passes very close to the central orbit in a region where the field quality is still well controlled, but in the downstream F adjacent half-unit the beam passes beyond the radial position corresponding to maximum field, traversing a strong non-linear fringe field. The gradient seen by the beam has therefore a reversed polarity, like if we had yet another defocussing sector following the already passed D half-unit. This results in very large horizontal beam sizes at the exit of this magnetic unit."
    * ejection first through D close to central orbit, field well know
    * then through F but beyond the radial position of the max field
        * traverses a **non-linear fringe field**
    * The gradient seen by the beam has reversed polarity
        * **Another** Defocussing D after a D
        * $\Rightarrow$ Results in **large horizontal beam size** at the exit
* **Magnetic shims** installed at various radial positions along the 5 blocks **on the F side** to improve the ejection by modelling a **constant field** in the ejection region

* Should improve the optics of the ejected beam through the fringe field

![](https://codimd.web.cern.ch/uploads/upload_9717c269f2cd01e08eb343333cdf44c8.png)

* Metallic shim should **uniform** the flux lines on the ejection path

![](https://codimd.web.cern.ch/uploads/upload_39642ec969ca45820b835ea8196f7369.png)

* Gap between shims reduced to 34 mm
* Shims are **installed at positions 16, 56, 57 and 63** (Note: in 2022 only 16 and 63 ?)
* Master thesis interested in **position 16**
    * Ejection site in the LHC chain
    * Configuration having the greatest influence on the magnetic flux at the central orbit $\Rightarrow$ **affecting the central orbit**
* Shims + ejection vacuum pipe is larger than normal vacuum pipe
    * A thinner figure of eight loop is installed to give more room
    
#### Configurations

* **Normal state**, without shims and without special figure of eight loop
* R type magnet by inverting figure of eight loop current and interchanging the current between the two pole-face-windings
* **Special figure of eight loop**
* Special figure of eight loop + **shims**
    * $\Rightarrow$ see effect on nominal field and fringe field
    
![](https://codimd.web.cern.ch/uploads/upload_c5a28b0d679215bc0b3f43f40b7e62ec.png)

Expected behaviour of a pulsed electromagnet: The change in induction B is **slowed down** with respect to the current due to **Eddy Currents** (current loops) that **opposes** any changes in magnetic field.

![](https://codimd.web.cern.ch/uploads/upload_f1298d5c8e42b70084d7c3868dabec9f.png)

#### Higher order components

* **Gradient** (with respect to x) or **quadrupolar** component $\boldsymbol{G}(x_{j},z)$

$$ \boldsymbol{G}(x_{j},z) = \frac{\Delta\boldsymbol{B}}{\Delta x} = \frac{\boldsymbol{B}(x_{i+1},z) - \boldsymbol{B}(x_{i},z)}{x_{i+1}-x_{i}} $$

$$ x_{j} = \frac{x_{i+1} + x_{i}}{{2}} $$

* **Sextupolar** component:

$$ \boldsymbol{S}(x_{i},z) = \frac{1}{x_{j}-x_{j-1}}\left[ \frac{\boldsymbol{B}(x_{i+1},z) - \boldsymbol{B}(x_{i},z)}{x_{i+1}-x_{i}} - \frac{\boldsymbol{B}(x_{i},z) - \boldsymbol{B}(x_{i-1},z)}{x_{i}-x_{i-1}}  \right] $$

![](https://codimd.web.cern.ch/uploads/upload_bee2ce5046b5828ba9b1afe501bedb33.png)

![](https://codimd.web.cern.ch/uploads/upload_7c77f9fbd6d7472ce20ffb564ccfa3ea.png)

* **Flat** curve is the one with the **shims** installed

![](https://codimd.web.cern.ch/uploads/upload_dec1771fa31e112ac803d1e0d6fc6184.png)

* Remember shims are **only** installed in the **F** section, that why the difference with or without shims is only for z>0.
* Field is lower around x = 0 because it is increase close to the shims

![](https://codimd.web.cern.ch/uploads/upload_3d5b910633d3d68dc3d5b4c44ec2dda5.png)

![](https://codimd.web.cern.ch/uploads/upload_30551543388b589cb1625e6e6015ad7b.png)

### Influence of shims on the PS main magnets
[Influence of shims on the PS main magnets Th. Zickler](http://cds.cern.ch/record/702545/files/sl-note-99-043.pdf)


#### Magnet Unit 16:
Without shims            |  With shims
:-------------------------:|:-------------------------:
![](https://codimd.web.cern.ch/uploads/upload_b1dacc9ffaa64fb4cb4da2d716af0fff.png) | ![](https://codimd.web.cern.ch/uploads/upload_75dc613652bd80c9fc3bde17116d9505.png)

* Figure 1 and Figure 2 show the magnetic flux lines near the central orbit. One can easily see the **redistribution effect** in Figure 2 caused by the shim and also the slightly **lower density** near the **beam orbit**.

![](https://codimd.web.cern.ch/uploads/upload_d3137155e72c05586928b1b97c89a4a9.png)

* Shims at magnet 56 extends over the **whole unit**.
* Block 1 to 5 made of iron plates all around the extraction vacuum chamber
* Block 6 to 10 have iron plates only on top and on the bottom of the square vacuum chamber
* Distance of shim rises linearly, from 218 mm to 465 mm from the center.
* Small flux redistribution
![](https://codimd.web.cern.ch/uploads/upload_c55b483f1b8f89dcc6684c9c5a704b7b.png)


#### Magnet Unit 63:
* almost identical shims as unit 56
* 20 mm more distant from the equilibrium orbit
* extraction beam pipe completely surrounded by iron plates from block 6 to 10
* block 1 to 5 have shimming plates only on top and bottom of the vacuum tube 

![](https://codimd.web.cern.ch/uploads/upload_4ce04b4ffe1e9ae28d5283cfbca322a3.png)

### Additional info

![](https://codimd.web.cern.ch/uploads/upload_3c0a96a35bcabb3db007bbd2ac09ac05.png)



[Shim for ejection 16 - Present State of development (1968)](https://cds.cern.ch/record/2307070/files/MPS-SI-Note-MAE-68-8.pdf)
![](https://codimd.web.cern.ch/uploads/upload_2a557a6ddce8d50226c00813c707dfc6.png)

[Shim for ejection 16 - Summary of results of magnetic model measurements (1969)](https://cds.cern.ch/record/2307072/files/MPS-SI-Note-MAE-69-2.pdf)
![](https://codimd.web.cern.ch/uploads/upload_7636066974e81e9f20eb6ab69ccf00ed.png)



ST0377387_02 a.00 CATIA Product MAGNET UNIT 016 FOR LAYOUT
![](https://codimd.web.cern.ch/uploads/upload_f390c5b34fd7bd3769b61871309d6a70.png)

https://edms.cern.ch/ui/#!master/navigator/external?SMTI137:473353:SMTI137:473353
![](https://codimd.web.cern.ch/uploads/upload_406dc3920f629506551e7843c08ca8df.png)

![](https://codimd.web.cern.ch/uploads/upload_fbbabf74eabb7ffd6c73a651d087bf53.png)

![](https://codimd.web.cern.ch/uploads/upload_4c436e95fceca75ea52fcbf1038b88b4.png)
![](https://codimd.web.cern.ch/uploads/upload_a103b0f8c297ce26e1795842f242bbe2.png)

[Main Unit 16 drawing with shims](https://cernbox.cern.ch/index.php/s/iDD8GhG4lLqPmhe)
![](https://codimd.web.cern.ch/uploads/upload_46cb5637fdafa8d0ab487e2a53eb3288.png)

#### Discussion with Damien Brethoux 25.01.2022

Pour trouver les vieux plans : [DFS/Workspace/o/Old Drawings/Complexe_PS/PS/PS-P](https://dfsweb.web.cern.ch/dfsweb/Services/DFS/DFSBrowser.aspx/Workspaces/o/Old%20Drawings/Complexe_PS/PS/PS-P/)

Coordonnées de l’ancien Q74 :
-	Entrée X=2029.198 ; Y=2193.728 ; Z=2433.660
-	Sortie X=2029.913 ; Y=2193.537 ; Z=2433.660


[MU63 with shims drawing](https://dfsweb.web.cern.ch/dfsweb/Services/DFS/DFSBrowser.aspx/Workspaces/o/Old%20Drawings/Complexe_PS/PS/PS-P/300/PS-P-00353.TIF)

![](https://codimd.web.cern.ch/uploads/upload_3004a4e0b083fb608778412b8c44523f.png)

![](https://codimd.web.cern.ch/uploads/upload_479b22871619427dab3581a77c6ae19c.png)

[ST0505941_01 b.00 CATIA Product MAGNET UNIT 063](https://csviewer.web.cern.ch/document?CDD=false&documentNumber=ST0505941_01&documentVersion=b.00)
![](https://codimd.web.cern.ch/uploads/upload_316afdf86c5250d23f6005f3eee389d6.png)

![](https://codimd.web.cern.ch/uploads/upload_c3552f823d5840c4ebcc6cc1680870f1.jpg)

* Les numéros Smarteam, il existe sous le nom de « blindage magnétique » : ST1308384_01

* Le numéro ST de la Main Unit 63 complète : ST0505941_01

![](https://codimd.web.cern.ch/uploads/upload_78c14607c96f39da527adde6cb3e2f3b.png)

# PS Visit

[Cernbox folder with pictures and videos](https://cernbox.cern.ch/index.php/s/2bwmNZH63xmAWq9)

[Matthew Cernbox folder with pictures](https://cernbox.cern.ch/index.php/apps/files/?dir=/__myshares/photos%20(id%3A431158)&)

## Shims in 16

* Only in the focusing part of the magnet

Extraction 16          |  MU16
:-------------------------:|:-------------------------:
![](https://codimd.web.cern.ch/uploads/upload_735d882a34779cd32674c20d85278d71.png)  | ![](https://codimd.web.cern.ch/uploads/upload_adc3058f56b08ee86ed45cf694fa98d1.png) 
![](https://codimd.web.cern.ch/uploads/upload_59fb0e2a9f4864b1031864b10bccded6.png) | ![](https://codimd.web.cern.ch/uploads/upload_83bbf5d59187e86ca702707a7d5dec02.png)

## Shims in East

* Along the whole MU63

Extraction MU63           |  Entry in MU63
:-------------------------:|:-------------------------:
![](https://codimd.web.cern.ch/uploads/upload_a33d715d06831a03d9bc26fa2f9bbb90.png) | ![](https://codimd.web.cern.ch/uploads/upload_ac6239f80e8154d4ec907046d1f19acc.png)


## Mu metal

E-mail from Jose 31.01.22

* The material is mu-metal (**high permeability**) (SCEM 44.72.60.005.6)
* Thickness 0.5 mm
* Heat treated at 1070°C
* Each shielding is a bit longer so they **overlap 10°** on each side. Usually this overlap is on the top and bottom because was the easiest way to install it, but it was not defined, so other orientations are possible.

* Jose was not in charge of this project, but he was always a bit surprised for the use of **316LN**, for magnetic properties, covered with mu-metal.

    * Vacuum pipe is made of 316LN a stainless steel which is **low magnetic permeable material** (meaning it will allow the magnetic field lines to enter it's space without distorting them)
    * it limits the perturbation of the charged particle beam as it travels through the beam transport tube

Mu-metal           |  wrapped around with overlap
:-------------------------:|:-------------------------:
![](https://codimd.web.cern.ch/uploads/upload_966b279cf7cd4dcd2729598af8be5f98.png) | ![](https://codimd.web.cern.ch/uploads/upload_ad920139e49ded1b1df1baae0d10545c.png)


## STEP files (3D models)

[STEP Files folder](https://cernbox.cern.ch/index.php/s/U6OnZGq5Lz9KTMk)

Software: Autodesk Fusion 360 free license for home use

Main units         |  Shims
:-------------------------:|:-------------------------:
 ![](https://codimd.web.cern.ch/uploads/upload_ad5f956a6320ce9b3926d772884c78d1.png) | ![](https://codimd.web.cern.ch/uploads/upload_ece3448d229adfd58b4a29c11323d2a9.png)
![](https://codimd.web.cern.ch/uploads/upload_cf91a661ce2edfbd1e951235f956f19f.png) | ![](https://codimd.web.cern.ch/uploads/upload_db67844fb2bf5e451e21e108dbdef23c.png)

### MU63 Animation
![](https://codimd.web.cern.ch/uploads/upload_f591b433255c40b98697be68d74cffc6.gif)

### MU16 Animation
![](https://codimd.web.cern.ch/uploads/upload_7499bccb9785f6b6b0899d331f0cc8ce.gif)

### Drawings from STEP files
Main units         |  Shims
:-------------------------:|:-------------------------:
![](https://codimd.web.cern.ch/uploads/upload_13ca4a732299e2f554d0db200bb27c83.png)| ![](https://codimd.web.cern.ch/uploads/upload_6528e878a895f179909d20bd1cf5dcbd.png)
![](https://codimd.web.cern.ch/uploads/upload_c8d81d6a3e3c3a19279045a5880e2849.png) | ![](https://codimd.web.cern.ch/uploads/upload_134ccb8fb651760830250732093707e2.png)

## Comparing the trajectory from MU16 and MU62

compare_trajectory_MU62_MU16.ipynb

Comparison between LHC and East extraction amplitudes to see why we have shims in 16 and not in 62. It looks like at entry in each magnet you have aprox. the same excursion so I don't see why we could put shims in 62.
![](https://codimd.web.cern.ch/uploads/upload_66b262cb3cf94685297856f8f77c2a73.png)

![](https://codimd.web.cern.ch/uploads/upload_59203312ac707f449f30145780cdc928.png)

"Your assumption about the orbit distortion is absolute correct: the further you move the shims in (closer to the orbit), the more magnetic flux will be “sucked out” from the gap acting like a bypass and hence will attenuate the magnetic field on the orbit. This effect you can already see in the quoted paper for the other shims. However, these shims are much further away from the orbit and so the influence is small and can be ignored." email from Thomas Zickler 11.02.202

## Comparison between MU16 and MU62 vaccum pipes
From a first look, MU16's vaccum pipe at exit is roughly 8 cm further away than MU62. Not a big difference if the argument is that shims in MU16 do not affect the central orbit. Hard to tell without fieldmap though.

![](https://codimd.web.cern.ch/uploads/upload_aa9b9e32b940430472b15fb358fc38b8.png)
