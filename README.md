# ATTACK
Class tools for overview of MITRE ATT&amp;CK®

## Use my image OR Build your own

## BANDWIDTH WARNING
### Downloading during class - do a quick calculation before starting - ON a 1Gb connection = 30min.
This may interupt your class interaction
### You have been warned... no whining
## Use my image
### This file is a full Windows 2k12 image 6.4GB - it has no license. It will shut down after one hour of boot time
* vmware configured
	https://20230305-attack-labs.s3.amazonaws.com/ATTACK/Attacklab230911v3.ova
* virtual box and AWS configured
	https://ceh-v11-20220609.s3.amazonaws.com/ATTACKLAB/ATTACK-LAB-2k12-insecure.ova
### Fast setup - the image has all the preconfigurations
## Easy setup = open the github in lab machine
### You need these websites open on your 2k12 for your lab steps
	* https://github.com/redcanaryco/invoke-atomicredteam/wiki/Installing-Invoke-AtomicRedTeam
	* https://mitre-attack.github.io/attack-navigator/
	* https://atomicredteam.io/atomics/
	* https://github.com/deanbushmiller/ATTACK
## Build your own
### Install Win2K12r2

### Configure setup
*	Install Chrome
*	Update chrome://net-internals/#hsts add github.com and include subdomains.
*	This will permit chrome to access hsts sites
*	Install Office 2013 Word & Excel
*	Install version 10 of PDF viewer 
#### Powershell 5 files download 
*	https://github.com/MicrosoftDocs/PowerShell-Docs/blob/main/reference/docs-conceptual/windows-powershell/wmf/setup/install-configure.md
	Powershell install 
*	https://learn.microsoft.com/en-us/powershell/scripting/windows-powershell/wmf/setup/install-configure?view=powershell-7.3#installing-from-the-command-prompt
	1. Run as administrator - command prompt ( NOT current powershell window)
	2. Navigate to Downloads folder
	3. Win8.1AndW2K12R2-KB3191564-x64.msu /quiet /norestart
	$. Check your version $PSVersionTable.PSVersion
#### Install Atomic Red Team wiki
*	https://github.com/redcanaryco/invoke-atomicredteam/wiki/Installing-Invoke-AtomicRedTeam
## Lab - general problems in lab 
*	You must do a few steps out of order to reduce frustration RUN POWERSHELL AS ADMIN
	* [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
	* Install InvokeAtomic ( watch the next line wrap, Force will reinstall)
	* IEX (IWR 'https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicredteam.ps1' -UseBasicParsing); Install-AtomicRedTeam -getAtomics -Force
## If you close your powershell window
*	You must re-set path
*	Import-Module "C:\AtomicRedTeam\invoke-atomicredteam\Invoke-AtomicRedTeam.psd1" -Force
	
## When in lab  Always do these steps or you will be sad
	1. Read ATTACK- link, Read Atomic link, then execute
	2. Getprereqs, Invoke-AtomicTest T####.### -GetPrereqs
	3. Close extra command prompt windows
## Up arrow is your friend in powershell command line
## For Lab T1555.003-6 Prereq install Firefox first
