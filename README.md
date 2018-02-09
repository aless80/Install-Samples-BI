# InstallSamplesBI
Automatically install SAMPLES in IRIS Data Platform

### Description
In InterSystems' IRIS Data Platform the samples in the SAMPLES namespace are not available out of the box, but they are freelyavailable on github: [intersystems/Samples-BI](https://github.com/intersystems/Samples-BI).  
This routine automates the whole installation process. It will install the namespace, database, webapp, and a temporary "Temp" SSLConfigs. The [intersystems/Samples-BI](https://github.com/intersystems/Samples-BI) repository will be downloaded as zip file to the /mgr/ directory of the installation. This routine will try to automatically extract the zip file (see the instructions below). The installation routine from [intersystems/Samples-BI](https://github.com/intersystems/Samples-BI) will install the samples. Finally, this routine will remove zip file, extracted directory, and the "Temp" SSLConfigs.  

### Requirements
* An installation of InterSystems IRIS Data Platform, though Caché will work too;  
* An appropriate licence to run BI, see [intersystems/Samples-BI](https://github.com/intersystems/Samples-BI)  
* The %SYS namespace must be writable;  
* The user running the routinne should have privileges for the operations.  

### Instructions

Clone this repository or manually download and extract the zip file.  
Import InstallSamplesBI.mac from Atelier, Studio, or from terminal as follows:  
```
Set path="/home/amarin/Install-Samples-BI/"  //Set your path
W $system.OBJ.Load(path_"InstallSamplesBI.mac","cf")
```
Launch the routine from terminal:
```
Do ^InstallSamplesBI(<namespace>,<command to unzip>)
```
The argument for the InstallSamplesBI routine are optional. The default *namespace* is "SAMPLES" and *command to unzip* is the command in your OS to unzip a zip file. The routine will try using "jar.exe xf" or "unzip -o" in Windows/Unix. If that does not work a prompt will instruct the user to unzip the ropository file


### Limitations
This routine is **not officially supported by InterSystems Co.** I suggest using this routine only in test environments.