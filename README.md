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
| Activation & Licenses | Whether Windows and Microsoft Office are activated, license type (OEM, retail, KMS/MAK, Microsoft 365), activation errors explained |
| Users & Sign-ins | Every local, domain and Entra ID / Microsoft account with last sign-in, creation date and whether it's an administrator |
| Windows 11 Readiness | Every Microsoft requirement checked (processor, TPM 2.0, Secure Boot, UEFI, memory, storage, graphics) with how to fix what fails |
| **FTC Safeguards Check** | See below |
| Updates Available | Windows updates waiting to install (security updates flagged) and Microsoft Store apps / programs with newer versions (via winget) |
| Shares & Mapped Drives | A **security review** of file sharing: who can reach each shared folder, anonymous and guest access, the SMB version in use explained, firewall, saved passwords on mapped drives — with fixes |
| Installed Programs, Windows Updates, Startup, Services, Processes, Environment | Full lists with dates, versions and plain-English notes (startup items disabled in Task Manager are marked) |

### FTC Safeguards Check
Car dealers and other businesses that arrange financing must follow the **FTC Safeguards Rule** (16 CFR Part 314). WinFo checks the technical parts that can be seen on a PC — BitLocker encryption, administrator and unused accounts, blank passwords, password length and lockout, screen lock, UAC, Remote Desktop, remote-access tools, file sharing, supported Windows version, recent updates, antivirus / EDR, firewall, SMB1, end-of-life software, Secure Boot / TPM, sign-in auditing and Security log size — and lists the paperwork items (written program, Qualified Individual, risk assessment, training, etc.) as a checklist. Every result says why it matters and how to fix it, with a score and grade. **Save a printable report** headed with your company name for the dealership's compliance file. *This is a technical checklist, not legal advice.*

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

Double-click any problem to see the actual events, copy them into a ticket, or open Event Viewer straight at the right log.

### Notifications and "Diagnose with AI"
The Summary dashboard opens with a **notifications strip** of recent critical events from the Windows event logs (and, by default, serious errors such as blue screens, bad disk blocks and hardware errors) — newest first, with how often each happened. New events appear by themselves while WinFo is open; dismissed ones stay hidden until they happen again.

Every notification — and every problem on the Event Log Problems page — has **Diagnose with AI**: WinFo writes a ready-made question (PC model, Windows version, processor, memory, the event and its message) and opens it in **Claude, ChatGPT, Copilot, Perplexity or Gemini**, asking what it means and how to fix it. The question is also copied to the clipboard. The computer name, user name and serial number are never included; nothing is sent until you click.

### Diagnostics — Changes Since Last Visit
WinFo saves a small **snapshot** every time it runs and shows exactly what changed since the last visit: programs installed, updated or removed, **new administrators** and accounts, startup items, scheduled tasks, services, drivers, hardware swaps (memory, drives, motherboard), DNS / proxy / hosts-file changes and security settings — risky changes flagged in red or yellow. Compare with any earlier visit. Run WinFo from a USB stick and the stick remembers every PC it has been plugged into.

### Tools
- **Live Sensors:** CPU (per thread), memory, GPU engines and video memory, disk activity, network throughput, temperatures (ACPI, drives, NVIDIA GPUs), battery — with min / max and history graphs.
- **Benchmarks:** CPU integer, floating point and SHA-256 (one thread and all threads), memory read / write / copy / latency, disk sequential and 4K random. Results are saved and **every PC you test is ranked side by side**; when run from a USB stick, results are stored on the stick.
- **Network Speed Test:** download and upload speed, ping, jitter and packet loss to the router, DNS server and three internet servers, DNS lookup time, latency while the line is busy (bufferbloat), public IP and internet provider, Wi-Fi signal and band — with a plain-English verdict on whether a problem is inside the building or at the provider. Every test is saved.
- **Reports:** save as a web page or text, print or make a PDF, or copy into an email or ticket. Serial numbers and keys can be hidden.

### Command line (RMM tools, scheduled tasks)
WinFo can run with **no window**, so ConnectWise RMM, N-able, NinjaOne, a scheduled task or a login script can collect reports from every PC:

| Option | What it does |
|---|---|
| `/report <file>` | Full report of every page (`.html`, or `.txt` for plain text) |
| `/safeguards <file>` | Printable FTC Safeguards report (`.html`) |
| `/snapshot [folder]` | Save a snapshot for *Changes Since Last Visit* |
| `/changes <file>` | What changed since the last snapshot |
| `/fleet <file.csv>` | Add one line about this PC to a shared spreadsheet — point every PC at the same file on a server share and a whole dealer group lands in one list (model, serial, age, Windows support date, Windows 11 readiness, BitLocker, antivirus, last update, drive health, Safeguards score…) |
| `/site "<name>"` | Store / location name written to the fleet line |
| `/help` | List the options |

In file names `{computer}` and `{date}` are replaced. Command-line snapshots are kept in `%ProgramData%\Dialsoft\WinFo\Snapshots` (or the folder given to `/snapshot`), because RMM tools often run programs from a temporary folder. If the fleet spreadsheet is open in Excel, the PC's line waits in a `<name> pending` folder and is added on the next run. Exit codes: `0` done, `1` something failed, `2` done but Safeguards checks failed. Progress is written to the console and to `cli.log`.

Because WinFo is a Windows (not console) program, ask the script to wait for it:
```powershell
$p = Start-Process "C:\Tools\WinFo.exe" -Wait -PassThru -ArgumentList '/safeguards "\\server\it\{computer}.html" /fleet "\\server\it\fleet.csv" /site "Main St"'
exit $p.ExitCode
```
or from a batch file: `start "" /wait WinFo.exe /report "C:\Reports\{computer} {date}.html"`. Run it as Administrator or SYSTEM for complete results.

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
- **Packaging:** a single, self-contained `WinFo.exe` (under 1 MB) with an embedded icon, version information and application manifest (DPI-aware; asks for the highest available rights)
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
| Security policy | netapi32 NetUserModalsGet (password and lockout policy); advapi32 AuditQuerySystemPolicy (sign-in auditing) |
| Updates available | Windows Update Agent (`Microsoft.Update.Session` COM); `winget upgrade` (Windows Package Manager — Microsoft Store and winget catalog) |
| Network speed test | ICMP ping (System.Net.NetworkInformation); Cloudflare's public speed-test endpoints at `speed.cloudflare.com` (download, upload, provider lookup) — only when you press *Start* |
| Scheduled tasks | `schtasks /query` (for snapshots) |
| Updates | `latest.json` and `WinFo.exe` in this repository, downloaded over HTTPS (TLS 1.2) from raw.githubusercontent.com |

### Files WinFo writes
- **Settings:** `%APPDATA%\Dialsoft\WinFo\settings.ini`. To keep settings with the program instead (handy on a USB stick), put an empty `WinFo.ini` next to `WinFo.exe`.
- **Logs:** `startup.log` and `error.log` in the same folder.
- **Benchmark results:** `WinFo-benchmarks.csv` next to `WinFo.exe` when that folder is writable, otherwise in the AppData folder.
- **Snapshots** (*Changes Since Last Visit*): small text files in a `WinFo Snapshots` folder next to `WinFo.exe` when that folder is writable (e.g. a USB stick), otherwise in `%APPDATA%\Dialsoft\WinFo\Snapshots`. The newest 60 per PC are kept. Can be turned off in Settings.
- **Speed test history:** `SpeedTests.csv` in the same folder as the benchmark results.
- **Command line:** `cli.log` in the settings folder.
- **Disk benchmark:** a temporary test file inside a `WinFo-benchmark` folder on the drive being tested. It is deleted automatically, even if WinFo is closed mid-test.

### Privacy
WinFo collects information **locally only**. The only network request it makes on its own is the once-a-day update check to GitHub, which you can turn off in Settings. The network speed test contacts Cloudflare's speed-test servers only when you press *Start speed test*; the Updates Available page asks Windows Update and winget. *Diagnose with AI* opens the AI site you pick in your browser, with the question in the link — only when you click it. Nothing about your PC is ever sent anywhere. Reports are only created when you ask for one.

---

## About
**WinFo** © 2026 Dialsoft LLC — Marc Frega, Wharton NJ. All rights reserved.

This repository hosts the official builds: `WinFo.exe` is always the latest version, `latest.json` tells installed copies about it, and `CHANGELOG.md` lists what changed. Bug reports and suggestions are welcome under [Issues](https://github.com/Dialsoft/winfo/issues).
