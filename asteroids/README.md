## Firmware Infos

- **Device:** Nothing Phone (3a)
- **Region:** IND
- **Version:** `UKQ1.260129.001` / `BOOT.MXF.2.1-01955-LANAI-1.88923.2`

## Patches/Fixes

> [!NOTE]
> Ported from the bale_b, muyu/peridot and salami Patches (same `BOOT.MXF.2.1` Branch) and Tested on Hardware.

### ButtonsDxe:

- **Reason:** To make the Power Button usable in UEFI.
- **Patch:** Map power button Key Code as ENTER instead of SUSPEND.
- **Patch Creator:** [Gustave Monce](https://github.com/gus33000)

### ClockDxe:

- **Reason:** To keep some important clocks on.
- **Patch:** Removed "Clock_CESTADisableDependencies" function call.
- **Patch Creator:** [Robotix](https://github.com/Robotix22)

### PmicDxe:

> [!NOTE]
> Must be paired with the SPMIDxe Patch.

- **Reason:** To make UEFI not Hang during UEFI Boot.
- **Patch Nr. 1:** Make failing SPMI Function call always return EFI_SUCCESS.
- **Patch Nr. 2:** Removed PMIC Post Init.
- **Patch Nr. 3:** Removed the Battery/Charger Detection calls in the Battery Init Function, they Wait forever.
- **Patch Creator:** [Kancy Joe](https://github.com/sunflower2333), [Shandorman](https://github.com/jiganomegsdfdf) & [Robotix](https://github.com/Robotix22/)

### SPMIDxe:

> [!NOTE]
> Must be paired with the PmicDxe Patch.

- **Reason:** To make UEFI not Crash during UEFI Boot.
- **Patch:** Removed SPMI Handle Function.
- **Patch Creator:** [Kancy Joe](https://github.com/sunflower2333)

### TzDxeLA:

- **Reason:** To make UEFI not Crash during UEFI Boot.
- **Patch:** The Global TZ Applet Variable has been Changed to `TRUE` from `FALSE`.
- **Patch Creator:** [N1kroks](https://github.com/N1kroks/)

### UFSDxe:

- **Reason:** To make UEFI be able to use the Internal Storage.
- **Patch:** The UFS Sleep call has been Replaced with the UFS Wakeup Call (Start Stop Unit, Active).
- **Note:** The bale_b Hibern8 Exit Patch is not used, the Link is already Active on this Device.
- **Patch Creator:** [Kancy Joe](https://github.com/sunflower2333) & [N1kroks](https://github.com/N1kroks)

### UsbConfigDxe:

- **Reason:** To make USB work in UEFI and the OS.
- **Patch:** ExitBootServices routine was patched to not deinit USB after exit boot services.
- **Patch Creator:** [Gustave Monce](https://github.com/gus33000)

### UsbMsdDxe:

- **Reason:** To make the Internal Storage be recognised as Hard Drives instead of USB Drives in Mass Storage.
- **Patch:** Changed Removable State to Non-Removable.
- **Patch Creator:** [N1kroks](https://github.com/N1kroks)
