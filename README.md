# Opencore EFI for Laptop AMD

**Opencore version: [0.9.3](https://github.com/acidanthera/OpenCorePkg/releases/)**  
**macOS version: Ventura 13.5**

## Disclaimer:

## Important: Follow the below before boot with this EFI

### SSDTs

**Using [SSDTTime](https://github.com/corpnewt/SSDTTime)**

1. Start with option `P`. It dumps the current system's DSDT, which will be utilised in order to create these SSDTs and patches. + `FixHPET` (Choose option `C` which only patches conflicting IRQs from legacy devices) + `USBX` (choose the default option `B` key) + `RTCAWAC` + `PluginType`  
   **For AMD Laptop** + `FakeEC Laptop` + `PLNF` + `XOSI` (Choose default `A` key)
2. Copy all the files that start with SSDT and end in `*.aml` inside of Drive `/EFI/OC/ACPI`
3. Finally, merge `patches_OC.plist` by using the PatchMerge script included with SSDTTime. Run it the same way as SSDTTime

Or you can start the guide [here](https://nootinc.github.io/guide/gathering-files/acpi)

### Kext

In this case I used [Nootedred.kext](https://github.com/NootInc/NootedRed) instead of [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases) but I still include [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases) in [zip file](EFI/OC/Kexts/WhateverGreen.kext.zip)

Included [itlwm.kext](https://github.com/OpenIntelWireless/itlwm/releases) and [Heliport.dmg](https://github.com/OpenIntelWireless/HeliPort/releases) in case you don't want use [AirportItlwm.kext](https://github.com/OpenIntelWireless/itlwm/releases) (this case I use AirportItlwm.kext for Ventura)

### config.plist [Setup](https://dortania.github.io/OpenCore-Install-Guide/AMD/zen.html#starting-point)

**Rename `.modify_this_config.plist` to `config.plist`**  
**Any changes in EFI folder you must be take OC clean snapshot config.plist with [ProperTree](https://github.com/corpnewt/ProperTree)**

**NVRAM**  
&ensp;boot-args: `-v keepsyms=1 alcid=11 debug=0x100 agdpmod=pikera npci=0x2000`


**PlatformInfo**  
&ensp; Use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate your own SMBIOS

**Misc > Debug**
- If you want enable all logging
  - AppleDebug = YES
  - ApplePanic = YES
  - Target = 67

## Laptop Asus Vivobook Pro 15 OLED M3500QC:

- CPU model: AMD Ryzen 7 5800H with Radeon Graphics
- GPU model:
  - [x] AMD Radeon (TM) Graphics
  - [ ] NVIDIA GeForce RTX 3050 Laptop GPU
- Chipset Model:
- Keyboard, trackpad:
  - Keyboard: PS2
  - Trackpad: I2C
- Audio
  - Realtek ALC294 @ AMD K19.5 - Audio Processor - High Definition Audio Controller (Standalone AZ)
  - Audio Codec: 11
- Network Controller models: Intel(R) Wi-Fi 6 AX200 160 MHz
- Drive Model:

## Post-install

### What is working?

- Camera
- Speaker build-in
- Wifi
- Radeon Graphics (with 512MB memory)
- Battery percentage
-

### What is not working?

- NVIDIA GPU
- Trackpad (not patched/fixed)
- Microphone build-in
- Bluetooth
- Sleep

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

## Images:

![](Images/pic1.png)

## Preferences:

**[Dortania](https://dortania.github.io/)**  
**[Noot](https://nootinc.github.io/)**
