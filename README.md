# WinFo – System Information for Windows

**WinFo** is a portable, single-file Windows tool that shows everything about a PC — hardware, software, security, live sensors and problems — in plain English, with explanations for every item.

It's built for IT technicians working on client PCs, and friendly enough for anyone who wants to know what's inside their computer.

**[⬇ Download the latest WinFo.exe](https://github.com/Dialsoft/winfo/raw/main/WinFo.exe)** · [What's new (changelog)](CHANGELOG.md)

No installer: download `WinFo.exe` and run it. It works from a USB stick, a network share, or pushed through a remote-support tool.

---

## Features

### Summary dashboard
- One card per area: This PC, Live usage, Processor, Memory, Storage, Graphics & displays, Network, Security, Motherboard & BIOS, Battery and Health checks.
- **Drag cards to rearrange them**, hide the ones you don't need, and bring them back with *Choose cards…*. Your layout is remembered.
- Anything that needs attention is shown in **yellow or red**. Click any card or line to jump straight to the full details, with the item highlighted.

### Hardware
| Page | What it shows |
|---|---|
| Computer / BIOS | Make, model, serial number / service tag, UUID, BIOS version and date, UEFI or Legacy, Secure Boot, domain / Entra ID join |
| Motherboard | Board maker and model, chipset, memory slots, expansion slots, port connectors |
| Processor | Model, cores and threads (including Performance / Efficient core split), clocks, cache, virtualization, instruction sets, microcode |
| Memory | Installed and in use, every module with size, type (DDR4 / DDR5), speed, maker, part number, slot, XMP / EXPO check, channel layout |
| Graphics & Monitors | GPUs with video memory and driver age; every monitor's model, serial, size (inches or cm), manufacture date and connection type |
| Storage | Every drive with health, temperature, wear, power-on hours and error counts; free space and BitLocker status per drive letter |
| Network | Adapters with MAC, IP, gateway, DNS, DHCP lease, link speed; Wi-Fi network, access-point MAC (BSSID), signal, band and channel |
| Audio & Input, USB, Printers | Every device, USB vendor / product IDs, printer drivers, ports and status |
| Battery | Charge, health (capacity vs. new), wear, charge cycles |
| Device Problems | Every Device Manager warning, with the error code explained |
| Drivers | Every driver with version, date, publisher and signature status |

### Software
| Page | What it shows |
|---|---|
| Operating System | Edition, version and exact build, install date, uptime, pending restart, activation, product key (registry and BIOS OEM key), **Windows 11 readiness check** |
| Security | **Which security software is protecting the PC** — antivirus, EDR / MDR agents (SentinelOne, Huntress, CrowdStrike, Sophos, Bitdefender, ThreatLocker, Umbrella and about 60 others), Defender status and mode, firewall, UAC, TPM, BitLocker, memory integrity, SMBv1, local accounts with **creation date, first and last sign-in, password age and failed attempts**, domain / Entra ID accounts that have signed in, and Administrators group members |
| Installed Programs, Updates, Startup, Services, Processes, Shares, Environment | Full lists with dates, versions and plain-English notes (startup items disabled in Task Manager are marked) |

### Diagnostics — Event Log Problems
Scans the Windows event logs (7 days to 1 year) and explains what it finds, with advice on what to do:
- **Crashes:** blue screens (stop code translated), sudden power-offs, crash dump files
- **Hardware:** errors reported by the processor or memory (WHEA), heat or power throttling, memory test results
- **Disks:** bad blocks, read/write errors and resets, file system corruption, deleted restore points
- **Drivers and updates:** graphics driver crashes, failed updates, crashing services
- **Programs:** crashing and hanging programs, grouped by program
- **Network:** IP address conflicts, domain controller and Group Policy failures, clock sync problems, Wi-Fi and network drops
- **Security:** malware detections, Defender turned off, failed sign-ins grouped by user and source, account lockouts, users added to Administrators, the Security log being cleared, suspicious new services
- **History:** who restarted the PC and why, and how long each startup took

Double-click any problem to see the actual events, copy them into a ticket, or open Event Viewer.

### Tools
- **Live Sensors:** CPU (per thread), memory, GPU engines and video memory, disk activity, network throughput, temperatures (ACPI, drives, NVIDIA GPUs), battery — with min / max and history graphs.
- **Benchmarks:** CPU integer, floating point and SHA-256 (one thread and all threads), memory read / write / copy / latency, disk sequential and 4K random. Results are saved and **every PC you test is ranked side by side**; when run from a USB stick, results are stored on the stick.
- **Reports:** save as a web page or text, print or make a PDF, or copy into an email or ticket. Serial numbers and keys can be hidden.

### Everyday comforts
- Detailed **explanation tooltips** on almost everything
- Light and dark themes, adjustable text size
- **Standard (°F, inches) or Metric (°C, cm)** units
- Animations can be turned off for remote sessions
- Every setting **takes effect instantly** — nothing ever needs a restart
- **Automatic updates:** once a day WinFo checks `latest.json` in this repository; when a new version is published, a bar offers *Update now*. The download is verified (size, SHA-256 checksum, publisher and version) before it replaces the old copy, and WinFo restarts itself.

---

## Requirements
- Windows 10 or Windows 11 (64-bit or 32-bit); Windows Server 2016 and later should also work (not yet tested)
- .NET Framework 4.8 — **already included in Windows 10 and 11**, nothing to install
- **Administrator rights recommended.** WinFo asks when it starts. Without them it still runs, but drive temperature and wear, TPM, BitLocker, battery health and the Security event log are hidden.

### First run: Windows SmartScreen
WinFo isn't code-signed yet, so Windows may show *"Windows protected your PC."* Click **More info → Run anyway**.

---

## Technical details

### Language and platform
- **Language:** C# 7
- **Framework:** .NET Framework 4.8 with Windows Forms (WinForms) for the user interface
- **Packaging:** a single, self-contained `WinFo.exe` (about 500 KB) with an embedded icon, version information and application manifest (DPI-aware; asks for the highest available rights)
- **Third-party libraries:** none. WinFo uses only components built into Windows and the .NET Framework.

### Windows resources used
| Area | Resource |
|---|---|
| Hardware and system inventory | **WMI** (Windows Management Instrumentation) — `root\cimv2`: Win32_ComputerSystem, Win32_BIOS, Win32_BaseBoard, Win32_Processor, Win32_PhysicalMemory, Win32_VideoController, Win32_DiskDrive, Win32_LogicalDisk, Win32_NetworkAdapter(Configuration), Win32_PnPEntity, Win32_PnPSignedDriver, Win32_Battery, Win32_Printer, Win32_Service, Win32_UserAccount and others |
| Drives | WMI `root\Microsoft\Windows\Storage` — MSFT_PhysicalDisk and MSFT_StorageReliabilityCounter (health, temperature, wear, power-on hours) |
| Monitors, battery health | WMI `root\wmi` — WmiMonitorID, WmiMonitorBasicDisplayParams, WmiMonitorConnectionParams, BatteryStaticData, BatteryFullChargedCapacity, BatteryCycleCount |
| Security | WMI `root\SecurityCenter2` (antivirus / firewall), `root\Microsoft\Windows\Defender` (MSFT_MpComputerStatus), `root\cimv2\Security\MicrosoftTpm` (Win32_Tpm), `root\cimv2\Security\MicrosoftVolumeEncryption` (BitLocker), `root\Microsoft\Windows\DeviceGuard`; installed services of known security products |
| Licensing | WMI SoftwareLicensingProduct / SoftwareLicensingService; registry DigitalProductId |
| Windows API (Win32) | kernel32: GetLogicalProcessorInformationEx (cores, P/E cores, caches), GlobalMemoryStatusEx, GetPhysicallyInstalledSystemMemory, IsProcessorFeaturePresent, GetFirmwareType, GetTickCount64, CreateFile / ReadFile / WriteFile with unbuffered I/O (disk benchmark); netapi32: NetUserEnum (account sign-in and password dates); dwmapi and uxtheme (dark title bars and scrollbars); user32 (window activation) |
| Live sensors | Windows **performance counters** — Processor Information, Memory, GPU Engine, GPU Adapter Memory, PhysicalDisk, Network Interface, Thermal Zone Information |
| Event log scanning | Windows **Event Log API** (System.Diagnostics.Eventing.Reader) — System, Application, Security, Microsoft-Windows-Windows Defender/Operational and Diagnostics-Performance logs |
| Registry | Windows version and build, installed programs, startup approval state, Secure Boot, firewall profiles, user profile sign-in times, graphics memory, pending-restart flags |
| Command-line tools | `netsh wlan show interfaces` (Wi-Fi details); `nvidia-smi` (NVIDIA GPU temperature, fan, power and clocks, when an NVIDIA driver is installed) |
| Optional | **LibreHardwareMonitor** / OpenHardwareMonitor: if either is running, WinFo shows their CPU core temperatures, fan speeds and voltages automatically |
| Updates | `latest.json` and `WinFo.exe` in this repository, downloaded over HTTPS (TLS 1.2) from raw.githubusercontent.com |

### Files WinFo writes
- **Settings:** `%APPDATA%\Dialsoft\WinFo\settings.ini`. To keep settings with the program instead (handy on a USB stick), put an empty `WinFo.ini` next to `WinFo.exe`.
- **Logs:** `startup.log` and `error.log` in the same folder.
- **Benchmark results:** `WinFo-benchmarks.csv` next to `WinFo.exe` when that folder is writable, otherwise in the AppData folder.
- **Disk benchmark:** a temporary test file inside a `WinFo-benchmark` folder on the drive being tested. It is deleted automatically, even if WinFo is closed mid-test.

### Privacy
WinFo collects information **locally only**. The only network request it makes on its own is the once-a-day update check to GitHub, which you can turn off in Settings. Nothing about your PC is ever sent anywhere. Reports are only created when you ask for one.

---

## About
**WinFo** © 2026 Dialsoft LLC — Marc Frega, Wharton NJ. All rights reserved.

This repository hosts the official builds: `WinFo.exe` is always the latest version, `latest.json` tells installed copies about it, and `CHANGELOG.md` lists what changed. Bug reports and suggestions are welcome under [Issues](https://github.com/Dialsoft/winfo/issues).
