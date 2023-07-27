# Opencore EFI for Laptop AMD
## Disclaimer

**Opencore version: 0.9.3**

**macOS version: Ventura 13.5**

## Important:
### SSDTs
Using SSDTTime <br>
Start with option P. It dumps the current system's DSDT, which will be utilised in order to create these SSDTs and patches.

### Modify config.plist
- 
- boot-args: -v keepsyms=1 alcid=11 debug=0x100 npci=0x2000

### Kext

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