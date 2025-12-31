# hp-zbook-bluetooth-fix.md
HP ZBook Bluetooth missing – firmware recovery fix

Problem
On HP ZBook laptops, Bluetooth may suddenly disappear even though it worked previously.

Symptoms:
  No Bluetooth toggle in Windows Settings
  Bluetooth missing from Device Manager (even with Show hidden devices)
  Bluetooth services won’t start
  Driver reinstall does nothing
  Device Manager shows "Unknown USB Device (Device Descriptor Request Failed)" under Universal Serial Bus controllers
  Wi-Fi continues to work normally

Root Cause
On HP ZBooks, Bluetooth is implemented as a USB interface on the Intel Wi-Fi/Bluetooth card.
After sleep/hibernate or power-state glitches, the Bluetooth firmware can become stuck in a low-power state and fails USB enumeration.

This is not a driver issue and does not require hardware replacement in many cases.

Fix: ZBook Deep Power + BIOS Reset
This procedure forces the Bluetooth firmware to fully reinitialize.

  Shut down Windows completely
  Unplug the AC charger
  Disconnect all USB devices
  Hold the power button for 60–90 seconds
  Leave the laptop powered off for 10 minutes
  Power on and immediately enter BIOS
  Load Setup Defaults / Optimized Defaults
  Save and exit BIOS

After booting into Windows, Bluetooth should reappear and function normally.

Prevention / Stability Tips

To reduce recurrence:
  Disable Windows Fast Startup

In Device Manager, disable Allow the computer to turn off this device for:
  Bluetooth adapter
  Intel Wi-Fi adapter
  USB Root Hubs
  Perform a full shutdown occasionally instead of only using sleep

Notes
  Reinstalling drivers or Windows does not fix this issue
  BIOS usually does not show a Bluetooth toggle (normal for ZBooks)

This behavior may appear common across multiple HP ZBook generations
