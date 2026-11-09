# WinFo - what's new

## Version 1.8.0 - 2026-11-09

- New ribbon toolbar in the style of MAC Scout: File menu plus Home, View, Tools and Help tabs with Microsoft Fluent icons that follow the light/dark theme. Home has Back, Summary, Refresh, the Find box, reports and settings; View jumps to any page and toggles the navigation pane, dark theme, text size, notifications, tooltips, serial numbers and units; Tools opens every WinFo tool and 15 Windows tools (Event Viewer, Device Manager, Task Manager, Services, Disks, Computer Management, Network Connections, Programs, Printers, Windows Update, System Info, Control Panel, Registry, Command Prompt, PowerShell); Help has About, Check for updates, What's new and Share. Double-click a tab to collapse the ribbon - WinFo remembers
- New "This PC" box at the top of the left panel: computer name, signed-in user, connection type (Wired Ethernet or Wi-Fi with network name and link speed), local IP address, MAC address and the public (outside) IP address - the one sites like ipchicken.com show. Click a line to copy it; updates by itself when the network changes
- New QUIC (HTTP/3) check (Tools > QUIC check, and part of the speed test): tests whether the fast connection type Edge and Chrome use works on this network - blocked, large packets dropped, or fine - and can turn QUIC off in Edge and Chrome with one click (the cure for ERR_QUIC_PROTOCOL_ERROR), with Undo
- "Diagnose with AI" can open in a different browser: pick one per click from the arrow menu, or set your usual one in Settings > Notifications and AI (lists the browsers installed on the PC)

## Version 1.7.1 - 2026-11-09

- Fixed "Diagnose with AI" failing to open in Edge/Chrome (ERR_QUIC_PROTOCOL_ERROR): the link to the AI site is now much shorter. The complete question, with the full event message, is always on the clipboard - the status bar says so, and if a page doesn't load you can open the site and press Ctrl+V

## Version 1.7.0 - 2026-11-09

- Event-log notifications on the Summary dashboard: recent critical events (and serious errors like blue screens, bad disk blocks and hardware errors) appear in a strip at the top, newest first, with when they happened and how many times. New ones appear by themselves within seconds while WinFo is open. Dismiss one and it stays hidden until it happens again
- "Diagnose with AI" on every notification, in Event Log Problems (right-click) and in the event details window: opens Claude, ChatGPT, Copilot, Perplexity or Gemini with a ready-made question - the PC's model, Windows version, processor and memory, the event and its message - asking what it means and how to fix it. The question is also copied to the clipboard. Computer name, user name and serial number are never included
- New Settings section "Notifications and AI": turn notifications on or off, choose critical only / critical + serious errors / every error, how many days back, and your preferred AI assistant - all apply immediately

## Version 1.6.0 - 2026-11-01

- New section - FTC Safeguards Check: checks this PC against the technical requirements of the FTC Safeguards Rule (which applies to car dealers and other businesses that arrange financing) - BitLocker encryption, administrator accounts, unused accounts, blank passwords, password length and lockout, screen lock, UAC, Remote Desktop, remote-access tools, file sharing, supported Windows version, recent updates, antivirus/EDR, firewall, SMB1, end-of-life software (old Office, Flash, Java...), Secure Boot/TPM, sign-in auditing and log size. Each result explains why it matters and how to fix it, with a score and grade
- Printable, client-ready Safeguards report with your company name and a sign-off line for the dealership's compliance file (set the company name in Settings > Reports and snapshots); new FTC Safeguards card on the Summary
- New section - Changes Since Last Visit: WinFo saves a snapshot every time it runs and shows exactly what changed since the last visit - programs installed or removed, new administrators and accounts, startup items, scheduled tasks, services, drivers, hardware swaps, DNS/proxy changes and security settings, with risky changes flagged. Run WinFo from a USB stick and the stick remembers every PC. Compare with any earlier visit; new Changes card on the Summary
- Command-line mode for RMM tools (ConnectWise RMM, N-able, NinjaOne) and scheduled tasks - runs with no window: /report, /safeguards, /snapshot, /changes, and /fleet, which adds one line per PC to a shared spreadsheet so a whole dealer group lands in one list (model, serial, age, Windows support, Windows 11 readiness, BitLocker, antivirus, last update, drive health, Safeguards score). Run WinFo.exe /help for details

## Version 1.5.0 - 2026-11-01

- New Tools section - Network Speed Test: download and upload speed, ping, jitter and packet loss to the router, DNS server and three internet servers, DNS lookup time, speed while the line is busy (bufferbloat), public IP and internet provider, Wi-Fi signal and band - with a plain-English diagnosis of whether a problem is inside the building or at the provider. Every test is saved to SpeedTests.csv
- New section - Updates Available: Windows updates waiting to be installed (security updates flagged), plus Microsoft Store apps and programs with newer versions (via winget), with links to the Store and Windows Update to install them
- Shares & Mapped Drives is now a full security review: who can reach each shared folder and what they can do, anonymous and guest access, firewall, saved passwords on mapped drives - with a fix for every problem found
- Which SMB (file sharing) version is in use, explained in plain English, including a warning if the old, insecure SMB1 is still turned on
- New section - Users & Sign-ins: every account with its last sign-in, creation date and whether it's an administrator; new Users card on the Summary
- Event Log Problems: open Windows Event Viewer from the page, or right-click a problem to open Event Viewer straight at that log. Device Problems: open Device Manager from the page
- Fixed "&" showing as an underscore in some page titles

## Version 1.4.0 - 2026-11-01

- Printers: the IP address and host name of every network printer, on the Summary's Printers card and the Printers page (click the IP to open the printer's own web page); USB, shared and virtual printers are labeled
- New section - Activation & Licenses: whether Windows and Microsoft Office are activated, license type (OEM, retail, volume KMS/MAK, Microsoft 365 subscription), product keys, KMS expiry and activation errors explained; new Activation card on the Summary
- New section - Windows 11 Readiness: every Microsoft requirement checked (supported processor generation, TPM 2.0, Secure Boot, UEFI, memory, storage, graphics, display) with a clear verdict and how to fix what fails; new Windows 11 card on the Summary

## Version 1.3.1 - 2026-11-01

- Printers: every printer now shows its real brand and model (worked out from the device and its driver) - not just the name someone gave it
- Summary dashboard: the default printer shows its brand and model too, e.g. "Front Desk - HP LaserJet Pro M404n"
- Virtual printers (Print to PDF, XPS, OneNote, Fax) are labeled as such

## Version 1.3.0 - 2026-11-01

- Printers: shows the last document printed (name, printer, pages, who printed it and when), the last printer used, a "last used" date for every printer, and the 25 most recent print jobs
- Windows keeps print history turned off by default - WinFo offers a one-click switch to turn it on (Administrator; history starts from then)
- Printers: documents stuck in the print queue are listed with their status
- Summary dashboard: new Printers card with the default printer (flagged if offline), the last document printed and any stuck print jobs

## Version 1.2.2 - 2026-11-01

- Processor links to cpubenchmark.net (PassMark): click the processor name on the Summary dashboard or the Processor page to see its CPU Mark score and ranking; a new "CPU Mark (PassMark)" line on the Processor page does the same

## Version 1.2.1 - 2026-11-01

- Summary dashboard: the Security card now shows BitLocker drive encryption for every drive (On, Suspended, Encrypting with progress, Paused, Off), and warns when the Windows drive isn't protected or has no recovery key
- Security page: one BitLocker line per drive, including whether a recovery password exists
- Storage page: clearer BitLocker states on each drive letter

## Version 1.2.0 - 2026-11-01

- BIOS age check: a BIOS older than 6 months is flagged as possibly outdated, with a link straight to the PC or motherboard maker's download site (Dell links open that exact PC's downloads using its service tag)
- The BIOS warning also appears on the Summary dashboard's Motherboard & BIOS card
- Links to web sites in saved web-page reports are clickable

## Version 1.1.0 - 2026-11-01

First public release of WinFo - System Information for Windows.

- Summary dashboard of drag-to-rearrange cards; anything needing attention is yellow or red; click any line to jump to its details
- Hardware: computer & BIOS, motherboard, processor (P/E cores), every memory stick, graphics & monitors, drives with health / temperature / wear, network & Wi-Fi, USB, printers, battery health, Device Manager problems, drivers
- Software: Windows version, activation & product key, Windows 11 readiness, security software in use (antivirus, EDR/MDR, DNS filtering - about 60 products recognized), user accounts with creation / sign-in / password dates, programs, updates, startup items, services, processes
- Event Log Problems: blue screens, sudden shutdowns, hardware & disk errors, driver crashes, failed updates, program crashes, malware detections and failed sign-ins - explained in plain English with what to do
- Live Sensors with history graphs, Benchmarks (CPU, memory, disk) that compare every PC you test, and Reports (web page, text, print/PDF)
- Light/dark theme, standard or metric units, detailed tooltips, animations, settings that apply instantly
- Automatic updates, verified before installing
- Share button: send WinFo to someone by email, Gmail, Outlook, Facebook Messenger, WhatsApp, text message, Teams, LinkedIn, X or Telegram
