Forked from samartzidis/WinAppleKey


# WinAppleKey

Apple Magic Keyboard Driver (model A1644) for Windows 10.
No other drivers (such as Apple's Bootcamp) are needed or should be instaled.

Supported Feafures: 
- Swaps the Fn-Ctrl keys to align with standard Windows keyboard layouts (fearture not supported by Apple's Bootcamp driver).
- Maps the missing Windows keys such as the Del, Insert, Print Screen, Pause/Break, etc.

Note that WinAppleKey is only tested and supported on Windows 10 (64-bit).

### Technical Details

WinAppleKey is implemented as a HIDCLASS LowerFilter WDM kernel mode driver. 

![keyboard-driver-stack](keyboard-driver-stack.png)

### Installation

**DISCLAIMER:** This driver is signed with a self-signed (test/development) certificate. For that reason, Windows will not directly allow the driver installation unless in **TESTSIGNING** mode. Please be aware that permanently running Windows in **TESTSIGNING** mode leaves your system open to various security risks; so please be aware of what you are doing as any consequence because of this is solely your responsibility. WinAppleKey is ***free software*** that you are willing to build and/or use completely ***at your own risk.***

**NOTE:** If your system is running a UEFI BIOS, you will need to disable **Secure Boot** through your BIOS first.

To switch to **TESTSIGNING** mode issue the following command (in an Administrative command prompt) and then reboot: 

``` bcdedit.exe -set TESTSIGNING ON ```

You can now run the Setup.msi installer.

To uninstall, run the uninstaller from the ```Control Panel``` ```Programs``` and then manually revert TESTSIGNING mode by issuing the following command (in an Administrative command prompt):

``` bcdedit.exe -set TESTSIGNING OFF ```


### Key Mapppings

**WinAppleKey** creates the following key mappings:

  <table>
    <tr>
      <th>Input Key(s)</th>
      <th>Output Key</th>
    </tr>
    <tr>
      <td><kbd>LCtrl</kbd></td><td><kbd>Fn</kbd></td>
    </tr>
    <tr>
      <td><kbd>Fn</kbd></td><td><kbd>Left Ctrl</kbd></td>
    </tr>
    <tr>
      <td><kbd>⏏︎ Eject</kbd></td><td><kbd>Del</kbd></td>
    </tr>
    <tr>
      <td><kbd>⌘ Cmd</kbd></td><td><kbd>Alt</kbd></td>
    </tr>    
    <tr>
      <td><kbd>⌥ Alt</kbd></td><td><kbd>Cmd</kbd></td>
    </tr>       
    <tr>
      <td><kbd>Fn</kbd>+<kbd>[F1]</kbd>...<kbd>[F12]</kbd></td><td><kbd>[F13]</kbd>...<kbd>[F24]</kbd></td>
    </tr>
    <tr>
      <td><kbd>Fn</kbd>+<kbd>LCtrl</kbd></td><td><kbd>Right Ctrl</kbd></td>
    </tr>
    <tr>
      <td><kbd>Fn</kbd>+<kbd>Return</kbd></td><td><kbd>Insert</kbd></td>
    </tr>
    <tr>
      <td><kbd>Fn</kbd>+<kbd>P</kbd></td><td><kbd>Print Screen</kbd></td>
    </tr>
    <tr>
      <td><kbd>Fn</kbd>+<kbd>S</kbd></td><td><kbd>Scroll Lock</kbd></td>
    </tr>
    <tr>
      <td><kbd>Fn</kbd>+<kbd>B</kbd></td><td><kbd>Pause/Break</kbd></td>
    </tr>
    <tr>
      <td><kbd>Fn</kbd>+<kbd>&uarr;</kbd></td><td><kbd>Page Up</kbd></td>
    </tr>
    <tr>
      <td><kbd>Fn</kbd>+<kbd>&darr;</kbd></td><td><kbd>Page Down</kbd></td>
    </tr>
    <tr>
      <td><kbd>Fn</kbd>+<kbd>&larr;</kbd></td><td><kbd>Home</kbd></td>
    </tr>
    <tr>
      <td><kbd>Fn</kbd>+<kbd>&rarr;</kbd></td><td><kbd>End</kbd></td>
    </tr>
  </table>

Multimedia Keys:
The multimedia keys are not directly mapped as they correspond to F19-F24 instead but you can easily use this [AutoHotkey script](MapMultimediaKeys.ahk) for that purpose.

### Driver Settings

You can use regedit.exe to optionally modify certain driver settings.

To enable/disable the **Alt-Cmd key swapping** edit the DWORD key value: **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WinAppleKey\SwapAltCmd**. The default value is 0 (off).

To enable/disable the **Fn-Ctrl key swapping** edit the DWORD key value:
**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WinAppleKey\SwapFnCtrl**. The default value is 1 (on).

After changing any of these values, you will need to disconnect/connect your associated Apple keyboard(s) to trigger a driver reload, or alternatively reboot your machine.

### Build Instructions

To build the driver you will need **Visual Studio 2017** along with an installation of the 
  **Windows 10 Driver Kit (WDK)**. For the installer project, you will additionally need to install the **[WiX toolset](http://wixtoolset.org/)** version v3.11
  or better. 

### Donate (Origin author samartzidis's Account)

[![donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=TBM5P9X6GZRCL)


![donate-bitcoin](https://img.shields.io/badge/Donate-Bitcoin-orange.svg)<br/>
![bc1qpu72u9greulx9wx3kukrqag9fgsmzkkjdah872](qr2.png)<br/>
bc1qpu72u9greulx9wx3kukrqag9fgsmzkkjdah872

