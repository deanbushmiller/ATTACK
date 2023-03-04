# ATTACK
Class tools for overview of MITRE ATT&amp;CK®
## Easy setup = open the github in lab machine
### you need these
	* https://github.com/redcanaryco/invoke-atomicredteam/wiki/Installing-Invoke-AtomicRedTeam
	* https://mitre-attack.github.io/attack-navigator/
	* https://atomicredteam.io/atomics/

## Install Win2K12r2

## Win2K12 setup
	Install Chrome
	Update chrome://net-internals/#hsts add github.com and include subdomains.
	This will permit chrome to access hsts sites	
## Powershell files download 
	* https://github.com/MicrosoftDocs/PowerShell-Docs/blob/main/reference/docs-conceptual/windows-powershell/wmf/setup/install-configure.md
	Powershell install 
	* https://learn.microsoft.com/en-us/powershell/scripting/windows-powershell/wmf/setup/install-configure?view=powershell-7.3#installing-from-the-command-prompt
	Run as administrator - command prompt ( NOT current powershell window)
	Navigate to Downloads folder
	Win8.1AndW2K12R2-KB3191564-x64.msu /quiet /norestart
	Check your version $PSVersionTable.PSVersion

## Lab - general problems in lab 
	You must do a few steps out of order to reduce frustration
	1. Have a 2k12 running
	2. Install powershell 5
	3. [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
	4. Install InvokeAtomic
		IEX (IWR 'https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicredteam.ps1' -UseBasicParsing); Install-AtomicRedTeam -getAtomics
## If you close your powershell window
	you must re-set path
	In order make the Invoke-AtomicTest function available for use in your current PowerShell session you must import the module.
		Import-Module "C:\AtomicRedTeam\invoke-atomicredteam\Invoke-AtomicRedTeam.psd1" -Force
	
## When in lab  Always do these steps or you will be sad
	1. Read ATTACK- link, Read Atomic link, then execute
	2. Getprereqs, Invoke-AtomicTest T####.### -GetPrereqs
	3. Close extra command prompt windows
### up arrow is your friend
