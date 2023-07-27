# Opencore EFI for Laptop AMD
## Disclaimer

**Opencore version: 0.9.3**

**macOS version: Ventura 13.5**

## Important:
Important

### SSDTs
Using [SSDTTime](https://github.com/corpnewt/SSDTTime)  
1. Start with option P. It dumps the current system's DSDT, which will be utilised in order to create these SSDTs and patches.
    - [x] FixHPET  
    - [x] USBX  
    - [x] RTCAWAC  
    - [x] PluginType  
    - [x] FakeEC (for AMD)
2. Copy all the files that start with SSDT and end in .aml inside of Drive/EFI/OC/ACPI  
3. Finally, merge patches_OC.plist by using the PatchMerge script included with SSDTTime. Run it the same way as SSDTTime


### Modify config.plist
**NVRAM**  
&ensp;boot-args: -v keepsyms=1 alcid=11 debug=0x100 npci=0x2000


**PlatformInfo**  
&ensp; Use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate your own SMBIOS  


### Kext
Kext
## Laptop: Vivobook Asus M3500QC:
- CPU model: AMD Ryzen 7 5800H with Radeon Graphics
- GPUmodel:
    + [x] AMD Radeon (TM) Graphics
    + [ ] NVIDIA GeForce RTX 3050 Laptop GPU
- Chipset Model: x
- Keyboard, trackpad:
  - Keyboard: PS2
  - Trackpad: x
- Audio Codec: 11
- Network Controller models: Intel(R) Wi-Fi 6 AX200 160 MHz
- Drive Model: x

## What is working?
- Speaker
- 
- 

## What is not working?
- Trackpad


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
│       ├── config.plist
│       ├── Drivers
│       │   ├── HfsPlus.efi
│       │   ├── OpenCanopy.efi
│       │   └── OpenRuntime.efi
│       ├── Kexts
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
│       ├── OpenCore.efi
│       └── Resources
│           ├── Font
│           ├── Image
│           └── Label

```