##  How to reboot the TN:

in the TN terminal

sudo reboot

in WSL

ssh -4 -J eljohnso@lxplus7.cern.ch eljohnso@cwe-513-vpl305

k5reauth -x -i 3600 -f -- vncserver

Connect as usual with mobaxterm

## Technical network status on Grafana

https://wikis.cern.ch/display/ACCADM/VPC+Centos7+CC7+Virtual+Machine+User+Manual#VPCCentos7CC7VirtualMachineUserManual-Killingthesession/Rebootthemachine

https://cosmos-grafana.cern.ch/d/000000029/be-cem-in-collectd-per-host?orgId=1&var-host=cwe-513-vpl305

![[Pasted image 20221018133300.png|1100]]