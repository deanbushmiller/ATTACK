# ATTACK
Class tools for overview of MITRE ATT&amp;CK®
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
