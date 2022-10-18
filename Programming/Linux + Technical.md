##  How to reboot the TN:

in the TN terminal

sudo reboot

in WSL

ssh -4 -J eljohnso@lxplus7.cern.ch eljohnso@cwe-513-vpl305

k5reauth -x -i 3600 -f -- vncserver

Connect as usual with mobaxterm