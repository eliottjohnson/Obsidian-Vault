 - Get [technical network trusted virtual machine](https://wikis.cern.ch/display/ACCADM/VPC+Virtual+Machines+BE-CO)  sending an email to: acc-adm-support@cern.ch

 - ssh into your virtual machine 
 - Start VNC server using
```shell
k5reauth -x -i 3600 -f -- vncserver
```
 - Then you can connect to the virtual machine with graphical interface using any VNC application (Remina, [RealVNC](https://www.realvnc.com/en/connect/download/viewer/macos/), [TigerVNC](https://tigervnc.org/), [others](https://www.geckoandfly.com/23203/vnc-client-viewer-windows-mac-linux/)...)
 - In case your VM shows some strange user interface, check your '~/.vnc/xstartup', there you should have only something like this:
     - ![](https://codimd.web.cern.ch/uploads/upload_ae68d12a848a180c6bbd20fe7a28f2e5.png)
     - if not, change it!
 - In case you feel the urge to work on your VM from home (or anyway outside the CERN network), this is how to do it:
     - Run in your terminal this command:
```shell 
ssh -L 5901:<your_virtual_machine>.cern.ch:5901 <user_name>@lxplus7.cern.ch
```
- Then you can connect to it with your vncserver SW using:
    - Hostname: localhost
    - Port: 5901
- Activate python distribution (this only works on the TN and it needs nfs):
```shell
source /acc/local/share/python/acc-py-pyqt/setup.sh
```
 - You can add the above line to your ~/.bashrc or make an alias:

```shell 
alias activate_pyCO='source /acc/local/share/python/acc-py-pyqt/setup.sh'
```
 - Check that python is the right one: ![](https://codimd.web.cern.ch/uploads/upload_44606d47b4bf8e9a056223ba21045332.png)
 - Create a virtual environment:
```shell
# Create virtual environment (venv)
acc-py venv <local_venv_directory>
 
# Activate the virtual environment
cd <local_venv_directory>
source bin/activate
```
 - You can add then some shortcuts to your ".bashrc" file:
 - ![](https://codimd.web.cern.ch/uploads/upload_237295fdf2a025076dee1498b773df87.png)
 - Then you can install __comrad__, which is a CO "hacked" version of QT designer:
```shell
# Install into your virtual environment.
pip install comrad
```
 - Here there are already some prepared widget that one could put in an application. 
---

## Application development
 - To start a new project with the correct structure already do:
```shell
acc-py init <project_name>
```
 - The you can copy the file from the [simple_scan](https://gitlab.cern.ch/abt-optics-and-code-repository/commissioning-tools/simple_scan) application to have already some initial files
 - Once the application is developed, you can use the "setup.py" file in the simple_scan application to make it pip-installable (of course the name and particularity of the application should be changed inside the setup script)
 - The command to install it, once all done, is:
```shell
pip install -e .
```
 - Being in the application main folder
 - Some example applications are available => links in the [presentation](https://slides.com/francesco-1/tools-for-commissioning/fullscreen#/)
 - One of the most important thing is to initialise pyJAPC in this way when testing (__no set is allowed!__):
```python
# Start Japc
japc = pyjapc.PyJapc(noSet=True)
```

### GUI
 - Then we can start using "[comrad](https://wikis.cern.ch/display/ACCPY/Rapid+Application+Development)" (or QT designer, which is pre-installed on all VM) to design the GUI layout (it's a drag-and-drop application builder)
     - You can either start from the example of the "simple_scan" app or start from scratch $\Rightarrow$ creativity is encouraged!
 - Once done, the ```mainwindow.ui``` file can be saved
 - Then use this in your code to use that file:
```python
Form, _ = uic.loadUiType(os.path.dirname(__file__) + '/window/mainwindow_simple.ui')

        self.ui = Form()
        self.ui.setupUi(self)
        # self.ui = uic.loadUi(os.path.dirname(__file__) + '/window/mainwindow_simple.ui', self)

        self.ui.plotArea = MplWidget()
        self.ui.plotArea.setObjectName("plotWidget")
        self.ui.PlotAreaLayout.addWidget(self.ui.plotArea)

        self.context = None
        self.main_widget = QWidget(self)

```
 - Simple scan application example: 
     - ![](https://codimd.web.cern.ch/uploads/upload_78d038853f368843ea01a8aed96a47a9.png)
 - This is on [GitLab](https://gitlab.cern.ch/abt-optics-and-code-repository/commissioning-tools/simple_scan). You can use this one as starting point/template for the others
 - Setting to test the app:
     - MKP.BA1.F3.CONTROLLER/Acquisition#kickCountToPlayMx
     - TT41.BCTF.412340/Acquisition#totalIntensityAutoCh1
     - XTS.SFLATTOP-XTIM/Acquisition#acqC



### CERN controls and useful tools
 - Database to search and investigate devices: [CCDE](https://ccde.cern.ch/dashboard)
 - to get the CCM on your virtual machine, you find the executable here: `/acc/local/share/abt/bin/ccm`
 - Then you can select SPSOP, for example, and finally be able to search for JAPC toolbox
 - One of the most important applications is the "JAPC toolbox"
     - ![](https://codimd.web.cern.ch/uploads/upload_3e624e653d618749f5671f47c1e81a29.png)
 - Here you can browse and test all available devices at CERN 
     - This gives access to both JAPC and RDA devices
     - ![](https://codimd.web.cern.ch/uploads/upload_ffb6cc004a4cb5640323076ae6485488.png)
 - Clicking on "Open Parameter chooser", we can look for the device of interest
 - As you can see here, the parameter of a device can be accessed with the following syntax:
     - ![](https://codimd.web.cern.ch/uploads/upload_5a206ed84db24a9daf117b759a8e0a4c.png)
     - DEVICE/Property#field
     - filed can be omitted and then the full property is returned:
     - ![](https://codimd.web.cern.ch/uploads/upload_67957adea0f3ea8e1431d149173edf36.png)
     - If I am interested only in the "currentAverage", then I will get a single value:
     - ![](https://codimd.web.cern.ch/uploads/upload_e890f3e36759efea41b12a82bcb53b11.png)
 - __This is fundamental for an application development as you need to know in which format the data will be returned and how they can be set!__
 - You can see that for this specific case I had to "force no selector". This is the case only for non-PPM devices. For the rest, you need to select a valid timing user:
 - ![](https://codimd.web.cern.ch/uploads/upload_9565ddfc94d938b17c867680b3d0d544.png)


### Ressources 

- The [scripting tools wiki website](https://wikis.cern.ch/display/ST/Scripting+Tools+Home) with many informations relating to scripting. In particular the [tipcs and tricks page](https://wikis.cern.ch/pages/viewpage.action?pageId=94553828) where I found hot to access EOS from the VM
- PyJapc [documentation](http://bewww.cern.ch/~bdisoft/pyjapc/) and [wiki](https://wikis.cern.ch/display/ST/PyJapc)
- The [controls configuration database](https://apex-sso.cern.ch/pls/htmldb_dbabco/f?p=CONFIG_HOME:HOME:6310002893888:::::) with informations on devices, FESA classes and such
 - [Kevin's tutorials on pyQT](http://like-webchannel.web.cern.ch/like-webchannel/pyqt_tutorial.html)





