# Opencore EFI for Laptop AMD

**Opencore version: 0.9.3**

**macOS version: Ventura 13.5**

## Disclaimer:

## Important: Follow the below before boot with this EFI


### SSDTs
**Using [SSDTTime](https://github.com/corpnewt/SSDTTime)**  
1. Start with option ```P```. It dumps the current system's DSDT, which will be utilised in order to create these SSDTs and patches.
    - [x] ```FixHPET``` (Choose option ```C``` which only patches conflicting IRQs from legacy devices)
    - [x] ```USBX``` (choose the default option ```B``` key)
    - [x] ```RTCAWAC```
    - [x] ```PluginType```  
    **For AMD Laptop**
    - [x] ```FakeEC``` Laptop
    - [x] ```PLNF```
    - [x] ```XOSI``` (Choose default ```A``` key)
2. Copy all the files that start with SSDT and end in ```*.aml``` inside of Drive ```/EFI/OC/ACPI```
3. Finally, merge ```patches_OC.plist``` by using the PatchMerge script included with SSDTTime. Run it the same way as SSDTTime


### Modify config.plist
**NVRAM**  
&ensp;boot-args: -v keepsyms=1 alcid=11 debug=0x100 agdpmod=pikera npci=0x2000  
**PlatformInfo**  
&ensp; Use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate your own SMBIOS  
### Kext
Use Nootedred.kext instead of Whatevergreen.kext
## Laptop Asus Vivobook Pro 15 OLED M3500QC:
- CPU model: AMD Ryzen 7 5800H with Radeon Graphics
- GPU model:
    + [x] AMD Radeon (TM) Graphics
    + [ ] NVIDIA GeForce RTX 3050 Laptop GPU
- Chipset Model: 
- Keyboard, trackpad:
  - Keyboard: PS2
  - Trackpad: I2C
- Audio
  - Realtek ALC294 @ AMD K19.5 - Audio Processor - High Definition Audio Controller (Standalone AZ)
  - Audio Codec: 11
- Network Controller models: Intel(R) Wi-Fi 6 AX200 160 MHz
- Drive Model: 

## What is working?
- Camera
- Speaker build-in
- Wifi 
- Radeon Graphics (with 512MB memory graphics)
## What is not working?
- Trackpad (no kext installed yet)
- Microphone build-in
- Bluetooth (no kext installed yet)
- NVIDIA GPU (absolute not working)
## Structure folder:

```
├── EFI
│   ├── BOOT
│   │   └── BOOTx64.efi
│   └── OC
│       ├── ACPI
│       │   ├── SSDT-EC.aml
│       │   ├── SSDT-HPET.aml
│       │   ├── SSDT-PLUG-ALT.aml
│       │   ├── SSDT-PNLF.aml
│       │   ├── SSDT-USBX.aml
│       │   └── SSDT-XOSI.aml
│       ├── Bootstrap
│       │   └── 
│       ├── Drivers
│       │   ├── HfsPlus.efi
│       │   ├── OpenCanopy.efi
│       │   └── OpenRuntime.efi
│       ├─ Kexts
│       │   ├── AirportItlwm_Ventura.kext
│       │   ├── AMDRyzenCPUPowerManagement.kext
│       │   ├── AmdTscSync.kext
│       │   ├── AppleALC.kext
│       │   ├── AppleMCEReporterDisabler.kext
│       │   ├── ECEnabler.kext
│       │   ├── Lilu.kext
│       │   ├── NootedRed.kext
│       │   ├── NVMeFix.kext
│       │   ├── RadeonSensor.kext
│       │   ├── SMCAMDProcessor.kext
│       │   ├── SMCBatteryManager.kext
│       │   ├── SMCRadeonGPU.kext
│       │   └── VirtualSMC.kext
│       ├── Resources
│       │   ├── Font
│       │   ├── Image
│       │   └── Label
│       ├── Tools
│       │   └── OpenShell.efi
│       ├── .modify_this_config.plist
│       └── OpenCore.efi
```