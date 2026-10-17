# OSDCloud-Provision

Zero-touch Windows 11 deployment script for [OSDCloud](https://www.osdcloud.com/).
Boot a device into OSDCloud WinPE, run one command, and it installs Windows 11 without any prompts, then reboots.

## What it does

1. Starts OSDCloud in **Zero Touch Installation (ZTI)** mode
2. Installs **Windows 11 Pro 25H2**, language `en-us`, retail license
3. Reboots automatically after a 20-second countdown

> ⚠️ **ZTI wipes the target disk without asking.** Only run this on devices you intend to reinstall.

## Requirements

- An OSDCloud boot medium (USB or ISO) built with the [OSD PowerShell module](https://www.powershellgallery.com/packages/OSD)
- Internet access from WinPE

## Usage

In the OSDCloud WinPE PowerShell prompt:

```powershell
Invoke-Expression (Invoke-RestMethod 'https://raw.githubusercontent.com/MarcoGerland/OSDCloud-Provision/main/osdcloudconfig.ps1')
```

Or bake it into your boot medium so it runs automatically:

```powershell
Edit-OSDCloudWinPE -StartURL 'https://raw.githubusercontent.com/MarcoGerland/OSDCloud-Provision/main/osdcloudconfig.ps1'
```

## Customizing

Change the parameters of `Start-OSDCloud` in `osdcloudconfig.ps1`:

| Parameter | Current value | Examples |
|---|---|---|
| `-OSBuild` | `25H2` | `24H2` |
| `-OSEdition` | `Pro` | `Enterprise`, `Education` |
| `-OSLanguage` | `en-us` | `de-de` |
| `-OSLicense` | `Retail` | `Volume` |

For your own setup, fork this repo and point the URL above to your fork.

## License

MIT
