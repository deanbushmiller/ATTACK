# ATTACK

Class tools for a hands-on overview of MITRE ATT&CK.

Students run real ATT&CK techniques on a Windows target, read what each technique
does, run the matching Atomic test, and watch the result. The goal is to connect
the ATT&CK matrix to what actually happens on a machine.

Part 2 rebuilds these labs on Caldera, where a Linux server drives the tests
instead of typing them on the Windows box. See the wiki link near the bottom.

---

## Three ways to do the labs

Pick one.

1. **Watch along.** Open the class mindmap and follow the links. No build needed.
2. **Use my image.** Download the prebuilt Windows target. Fastest to start.
3. **Build your own.** Install and configure the Windows target yourself.

---

## Bandwidth warning

Read this before class.

The prebuilt image is large. On a 1 Gb line at 27.5 Mbps it takes about ten
minutes to download. A download that size during class can interrupt the session.

Download it the night before. You have been warned.

---

## Option 1: Use my image

A full Windows Server 2012 R2 image, preconfigured for the labs.

- Size: about 6.4 GB.
- License: none. The image shuts down one hour after each boot.
- Configured for both VMware and VirtualBox.

Download the OVA:

- https://20230305-attack-labs.s3.amazonaws.com/ATTACK/20230911-ATTACK-LAB-2k12r2-1qaz%40WSX-20230301-fromVMware.ova

The image already has every preconfiguration below, so you can skip Option 2.

---

## Option 2: Build your own

### Install the operating system

Install Windows Server 2012 R2.

### Configure the base

- Install Chrome.
- Open `chrome://net-internals/#hsts` and add `github.com` with subdomains
  included. This lets Chrome reach HSTS sites.
- Install Office 2013 Word and Excel.
- Install version 10 of a PDF viewer.

### Install PowerShell 5

1. Read the Microsoft install guide.
   - https://learn.microsoft.com/en-us/powershell/scripting/windows-powershell/wmf/setup/install-configure
2. Open a Command Prompt as Administrator. Do not use an open PowerShell window.
3. Change to your Downloads folder.
4. Run the update package.

   ```
   Win8.1AndW2K12R2-KB3191564-x64.msu /quiet /norestart
   ```

5. Reboot, then check the version.

   ```powershell
   $PSVersionTable.PSVersion
   ```

### Install Invoke-AtomicRedTeam

Follow the Red Canary install guide:

- https://github.com/redcanaryco/invoke-atomicredteam/wiki/Installing-Invoke-AtomicRedTeam

---

## Keep these sites open during labs

Open these on the Windows target before you start.

- https://github.com/redcanaryco/invoke-atomicredteam/wiki/Installing-Invoke-AtomicRedTeam
- https://mitre-attack.github.io/attack-navigator/
- https://atomicredteam.io/atomics/
- https://github.com/deanbushmiller/ATTACK

---

## First-time setup steps

Run these once, in this order, to avoid common errors. Run PowerShell as
Administrator.

1. Allow modern TLS so downloads work.

   ```powershell
   [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
   ```

2. Install Invoke-AtomicRedTeam and pull the atomics. `-Force` reinstalls.

   ```powershell
   IEX (IWR 'https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicredteam.ps1' -UseBasicParsing); Install-AtomicRedTeam -getAtomics -Force
   ```

---

## The rhythm of each test

Do these every time so the lab makes sense and stays clean.

1. Read the ATT&CK link, then the Atomic link, then run the test.
2. Get the prerequisites first.

   ```powershell
   Invoke-AtomicTest T####.### -GetPrereqs
   ```

3. Close any extra Command Prompt windows the test opened.

Tips.

- The up arrow recalls your last command. Use it.
- Run PowerShell as Administrator for every lab.

---

## If you close your PowerShell window

You lose the module path. Set it again before you continue.

```powershell
Import-Module "C:\AtomicRedTeam\invoke-atomicredteam\Invoke-AtomicRedTeam.psd1" -Force
```

---

## Per-lab notes

- **T1555.003 test 6.** Install Firefox first. It is a prerequisite for this test.

---

## Part 2: the Caldera rebuild

Part 2 moves the same tests onto Caldera. A Linux server sends each test to an
agent on the Windows target, and you drive everything from a web interface.

- Start here: the wiki. https://github.com/deanbushmiller/ATTACK/wiki

---

## What is in this repository

- **LAB-MM** â the class mindmap for the watch-along path.
- **Lab-sysmon** â Sysmon setup used to observe the tests.
- **Layers-for-navigator** â ATT&CK Navigator layer files for class.
- **lab-machine-build.zip** â build files for the lab machine.

---

## Safety and legal

- Run these labs only on an isolated lab network.
- The tests run real attack techniques. Never run them on a production machine.
- The provided image is unlicensed and shuts down one hour after each boot. It is
  for classroom use only.
