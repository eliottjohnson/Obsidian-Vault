# PS transfer functions

## XSE
PR.XSE01.A, PR.XSE01.B, PR.XSE07 (**always using integrated field**): 
* magnets in SS01: 
    * magnet type MXNBAFWP, old name 608
    * https://norma-db.web.cern.ch/magdesign/idcard/375/
    * magnetic length allocated in LDB: 0.2 m
    * transfer function I_XSE * 6944.E-5/(BRHO) according to NORMA, EDMS1161510 and old MAD-X    
* magnet in SS07: 
    * magnet type MXNCAAWP, old name 610
    * https://norma-db.web.cern.ch/magdesign/idcard/377/ 
    * magnetic length allocated in LDB: 0.66 m
    * transfer function I_XSE * 1956.E-4/(BRHO) according to old MAD-X files (no other document apparently available)
    * https://edms.cern.ch/document/1055048/1 show an intB of 48.2T at 244A -> 0,1975T/A


—> create one logical K in LSA (the sum of all three? - how is it done for the MTE sextupoles?) and use the ratio of the transfer functions in MAD-X

## BSW57

**All magnets apart from PE.BSW57.61 have half the kick due to only two out of four coils being connected.

The following polarities are defined by the magnet cabling:
* PE.BSW57.53: positive
* PE.BSW57.59: negative
* PE.BSW57.61: positive
* PE.BSW57.67: negative

PE.BSW57.53: 
* magnet type MCHBBWWP, old name 206
* https://norma-db.web.cern.ch/magdesign/idcard/212/
* ~~transfer function I_BSW57 * 0.15/430/2/BRHO according to NORMA~~
* I_BSW57 * 318.E-6/2/(BRHO) according to EDMS1161510 and old MAD-X

PE.BSW57.59:
* magnet type MCHBAWWP, old name 205
* https://norma-db.web.cern.ch/magdesign/idcard/211/
* transfer function
    * ~~I_BSW57 * 320.E-6/2/BRHO according to NORMA and old MAD-X~~
    * ~~I_BSW57 * 330.E-6/2/BRHO according to EDMS1161510~~
    * actual source seems to be EDMS2220045, with integrated gradient drawn on mm paper, TF rather I_BSW57 * 300.E-6/2/BRHO
        * for 445 A (operating current in 2018) one extracts 0.13288/2/BRHO from mm paper 

PE.BSW57.61:
* magnet type BLG, old name 213
* transfer function I_BSW57 * 179E-6 / BRHO according to old MAD-X (no other document available, responsibility of TE-ABT, who couldn’t find any information)

PE.BSW57.67: 
* same as PE.BSW57.53

—> create one logical K in LSA (the sum of all ks - absolute values?) and use the ratio of the transfer functions in MAD-X

## Gamma jump quadrupoles

A general document exist for Quad 406,407,408,409 : 
https://edms.cern.ch/ui/file/708488/1/TechnicalnoteGammaTRscheme140405.pdf![](https://codimd.web.cern.ch/uploads/upload_0f63090703fc0bee0ef4d24fdbcbc465.png)


### Doublets - circuit A

PR.QTRDA19: 
* magnet type MQNBAFAP, old name 406
* https://norma-db.web.cern.ch/magdesign/idcard/291/
* transfer function (**integrated gradient**)
    * I_DOUBA * 1099.7E-6/ BRHO according to old MAD-X ---> **in agreement with measurement report EDMS700785 from 2006** 
    * ~~I_DOUBA * 1075.0E-6/ BRHO according to NORMA~~
    * ~~I_DOUBA * 1130.0E-6/ BRHO according to EDMS1161510~~
* **positive polarity**

PR.QTRDA27:
* same as PR.QTRDA19, but
* **negative polarity**

PR.QTRDA87:
* magnet type MQNBDAAP, old name 408
* https://norma-db.web.cern.ch/magdesign/idcard/294/
* transfer function 
    * I_DOUBA * 1000.E-6/ BRHO according to old MAD-X and EDMS1161510 (**integrated**)
    * ~~I_DOUBA * 394E-5/ BRHO according to NORMA (**non-integrated**)~~
* **negative polarity**

PR.QTRDA95:
* same as PR.QTRDA87, but
* **positive polarity**

### Doublets - circuit B

PR.QTRDB29:
* same as PR.QTRDA19, but
* **negative polarity**

PR.QTRDB37:
* same as PR.QTRDA87, but
* **positive polarity**

PR.QTRDB61:
* same as PR.QTRDA19, but
* **positive polarity**

PR.QTRDB69:
* same as PR.QTRDA87, but
* **negative polarity**

### Triplets - circuit A

PR.QTRTA41:
* magnet type MQNBCAWP, old name 407
* https://norma-db.web.cern.ch/magdesign/idcard/293/
* transfer function
    * ~~I_TRIPA * 3043.E-6/ BRHO according to old MAD-X~~
    * I_TRIPA * 3070.E-6/ BRHO according to EMDS1161510
    * ~~nothing in NORMA~~
* **negative polarity**

PR.QTRTA49:
* magnet type MQNCAAWP, old name 409
    * same as QSE
* https://norma-db.web.cern.ch/magdesign/idcard/306/
* transfer function
    * I_TRIPA * 640.E-5/ BRHO according to old MAD-X, NORMA and EDMS1161510
* **positive polarity**

PR.QTRTA73:
* same as PR.QTRTA41
* **negative polarity**

### Triplets - circuit B

PR.QTRTB07:
* same as PR.QTRTA49
* **positive polarity**

PR.QTRTB99.A:
* same as PR.QTRTA41
* **negative polarity**

PR.QTRTB99.B
* same as PR.QTRTA41
* **negative polarity**

## BSW23
PE.BSW23.19, PE.BSW23.27: 
* magnet type MCHBAWWP, old name 205
* https://norma-db.web.cern.ch/magdesign/idcard/211/
* identical to e.g. PR.DHZOC18, PE.BSW12, PE.BSW20...
* transfer function
* transfer function
    * I_BSW57 * 320.E-6/2/BRHO according to NORMA and old MAD-X
    * I_BSW57 * 330.E-6/2/BRHO according to EDMS1161510
    * actual source seems to be EDMS2220045, with integrated gradient drawn on mm paper

—> create one logical K in LSA and a knob defining the amplitude at the septum?

## QSE
PR.QSE29, PR.QSE87:
* magnet type MQNCAAWP, old name 409
* https://norma-db.web.cern.ch/magdesign/idcard/306/
* transfer function
    * I_QSE * 640.E-5/ BRHO according to old MAD-X, NORMA and EDMS1161510

—> create one logical K in LSA and a tune knob?

## XSK - small skew sextupoles (601, 602)

* Potentially a report quoting measured values (however, no distinction between 601 and 602): https://cds.cern.ch/record/183639/files/CM-P00059117.pdf, p.34
* and some earlier document on EDMS (updated specs in the addendum): https://edms.cern.ch/ui/#!master/navigator/document?D:100637856:100637856:subDocs
    * this could be the design parameters, whereas the previous report from 88 is referring to measurements

## Additional remarks

How is it done for BSW26 and the MTE sextupoles: does the k correspond to the individual or the sum of the ks?

