
![[Pasted image 20221122143457.png|600]]
![[Pasted image 20221122143533.png|600]]

Remote app
http://128.141.184.20/remote.asp

![[Pasted image 20221122140302.png|600]]

![[Pasted image 20221122140310.png|600]]

Installed in 355/R-017

![[Pasted image 20221122140726.png|425]]

![[Pasted image 20221122143057.png|825]]


397 kHz
Third order resonance = 397/3 = 132 kHz


## To control it

The blow-up needs to be enabled in the TFB. In the working set **CPS:TRANSV-FEEDBACK**, device **PA.TFB-DSPU-H**. The important settings are:

-   “**Enable BLU**” which has to be TRUE to use the excitation.
-   “**Start BLU**” and “**End BLU**” are the start and end C-Times of the excitation.
-   “**Internal Source Enable**” must be FALSE to use the external input.
- 
![[image1.jpg]]

![[image2.jpg]]

The signal generator remote interface is available here:

[http://128.141.184.20/remote.asp](http://128.141.184.20/remote.asp)

If you want to change parameters in a script/etc, you should be able to send SCPI commands using the “python-vxi11” package.

``` bash
[tlevens@cwe-513-vpl301] ~ $ python
>>> import vxi11
>>> instr = vxi11.Instrument("128.141.184.20")
>>> instr.ask("*IDN?")
'Agilent Technologies,33522A,MY50002453,5.02-1.19-2.00-58-00'
```

## Sampler


![[Pasted image 20221122144332.png]]

![[Pasted image 20221122144559.png]]

PA.TFBH-BU-SD is the signal from the signal generator

PA.TFBH-FB_ES-SD is the signal from the blow up
![[Pasted image 20221122143339.png|825]]
