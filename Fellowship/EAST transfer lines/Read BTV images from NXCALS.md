# Read BTV images from NXCALS

https://mattermost.web.cern.ch/abt/pl/o3rfhtxd9tbdbdjng6g3q1jzch

## read BTV images from NXCALS

E. Bravin has an app to do that, and it is quite convenient. See below his explanation on how to use it.

```
Hi,
Should work from any VM or console with ACC NFS
 
run
/user/bravin/bin/basler_imager
                View->NXcals
 
-Wait for the device list to be loaded
-Select a device from the left column (some device have more than one acquisition property, you must select the correct one)
-Select a time range (not sure if the cycle filter still works after switching from pytimber to nxcals)
-Click Load (fills the right column)
-Select an item on the right column
 
On the bottom of the dialog you have the status, wait for completion before clicking anything in that dialog
NXcals is slow, be patient…
 
Cheers,
Enrico
 ```

![[Pasted image 20221003153642.png]]