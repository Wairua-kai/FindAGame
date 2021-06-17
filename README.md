# Find A Game

Base Repo containing Vus, dot net core, mysql.

# Setup
You'll need to make sure the following is installed to get this running.  The first section being entirely prep for the environment.

## Environment Prep
You can skip this entirely if you like, it's assuming PowerShell, etc.

### Open up Powershell
1) Open up as Admin
2) Update to the latest version of Powershell.  Type ```$PSVersionTable.PSVersion```, if you come back with anything less than version 7.1.3, upgrade your Powershell with the following command:
```iex "& { $(irm https://aka.ms/install-powershell.ps1) } -UseMSI"```
<br />Once you've done this, you'll need to shut down your older version, and re-open powershell.  Make sure you use the newer version of Powershell and make it your default so you don't enter back in with an older version.

3) Run ```Get-ExecutionPolicy```. If it returns ```Restricted```, then run ```Set-ExecutionPolicy AllSigned```.<br/>If it says you don't have rights, exit powershell and re-enter - MAKE SURE YOU SELECT THE 'Run as Administrator.'
4) Enter the following into your command line: ```Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))```
5) It will copy a huge command string into your clipboard.  Just hit Ctrl-V and then hit return.  The Chocolatey install should start running.
6) Type ```choco``` - You should get a response back like ```Chocolatey vX.XX.XX```
7) Enter the following, using one line for each of these commands:
```
Install-Module posh-git
Install-Module oh-my-posh
Get-PoshThemes
```
8) That last command will give you a whole slew of different command prompts.  Two things to do here.  If the prompts are filled with weird box like symbols, then you need to run the command below, ignore this if you see clean looking prompts in different colors.  Note that - even if you've installed the PowerLine fonts, you may need to change to one of those fonts by clicking on the small powershell icon in the top left and going to the Properties tab and then Fonts.  All of the PowerLine fonts will have a 'PL' or 'for PowerLine' in their name.  If you've got a large monitor, you may also want to take the time to increase the font size to a readable level.
```
Install-Module -Name PSReadLine -AllowPreRelease -Force -SkipPublisherCheck
```

9) Finally select the theme looks best for your style.  Two I recommend are Paradox and Agnoster.  To do that enter ```Set-PoshPrompt Paradox``` (for example)
10) OK, to make this permanent, we need to make sure you have VS Code installed.  Type ```Code .``` on the command prompt.  If you see an error, you need to install VS Code using the following URL.  There will be a window which has a block of code.  Copy this entire block of code and then paste it onto your powershell command prompt.  It should start downloading and installing VS Code.
```
https://www.powershellgallery.com/packages/Install-VSCode/1.0/Content/Install-VSCode.ps1
```

11) Finally, type ```code $PROFILE```
12) Make sure your profile looks like this:
```
Import-Module posh-git
Import-Module oh-my-posh
Set-PoshPrompt Paradox
# Chocolatey profile
$ChocolateyProfile = "$env:ChocolateyInstall\helpers\chocolateyProfile.psm1"
if (Test-Path($ChocolateyProfile)) {
  Import-Module "$ChocolateyProfile"
}
```
13) Hit Ctrl-S to save your $PROFILE.  Now go to File->Preferences->Settings or Ctrl-, and then search for ```Terminal Integrated Font Family```.  At the top, you'll see a font listing which will either be blank or have some font.  Make sure this font is a Powerline or PL font and then save this.  
14) 
