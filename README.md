<p align="center">
Anti - Royal
</p>
<p align="center">
Catch the malware your EDR is missing!
</p>

<p align="center">
  <img width="400" src="https://github.com/shadowdevnotreal/anti_Royal/blob/main/Images/antiroyal.jpg">
</p>

<p align="center">
  <img width="180" src="https://github.com/shadowdevnotreal/anti_Royal/blob/main/Images/chat%20GPT3.png">
</p>

<a href="https://www.buymeacoffee.com/notarealdev" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 40px !important;width: 145px !important;" ></a>

[Please read the WIKI!](https://github.com/shadowdevnotreal/anti_Royal/wiki)

## CODE HAS NOT BEEN FULLY TESTED BUT IS SAFE = LOOKING FOR TESTERS WHILE I PROCEED WITH THE REST OF THE FRAMEWORK ##
* This tool is among several that will make up a framework of EDR assistance that is actually missed by EDR and AV.
* Much like OWASP or Maryam, this will consist of modules. The best part is..... the missing modules over time will self update!
* The goal of this project is to automate reporting and notifying to the admin, NOC, SOC, etc. of site issues. Even IF something gets past EDR/AV/Etc..... It will not matter once it hits the desktop.....our code will stop it, mitigate it, and over time..... will leaarn patterns.
* The problem in cyber security is not the lack of products, frameworks, reporting, tools, services, admins, etc. The problem in SEC in general is the end user. If you removed the end user blunders, I estimate 75+% of your issues would go away.
* Facts = During my time at Microsoft as a EMS SME, over 80% of admins did not enable MFA. Prior to Sentinal being what it is, with all it's data..... this was the sole cause of majority of the cyber breaches at that point in time.
* We have all the tools we need to stop malware DEAD in it's tracks. I'd stake my life on it..... it is time to get back to the roots of forensics, simple code.
** X happens because of Y. This is not hard math. We have cause, and we have effect.

## Basic Description
PowerShell script that combines creating a Windows service, searching for partially encrypted files, moving them to a folder on the desktop, logging the activity to a text file, and creating a Windows Sandbox configuration file which will then auto scan those files.

This script should help remediate this problem for you!

## LOGIC
EDR is great, but it should not be your magic bullet!
Ransomware groups like Conti and Royal utilize partially encrypted files in order to deploy their malware.
Many EDR will ignore this, and some will ignore file sizes.
This can allow bad actors to deploy their malware on to your network and systems.
Some encryption algorithms have a distinctive file header that can be used to identify encrypted files. For example, the AES encryption algorithm adds a 16-byte header to the beginning of the encrypted file, which consists of the following:
The first 4 bytes contain the magic number "Salted__"
The next 8 bytes contain the salt
The last 4 bytes contain the length of the salt in little-endian format
If you are using AES to encrypt your files, you could check for this header to determine if a file is encrypted.

> SentinelLabs has posted a report examining a trend started by LockFile in mid-2021 and now adopted by the likes of Black Basta, ALPHV (BlackCat), PLAY, Agenda, and Qyick.

> **Ransomware gangs switching to new intermittent encryption tactic**
[Wiki for deatiled analysis](https://github.com/shadowdevnotreal/anti_Royal/wiki)
A growing number of ransomware groups are adopting a new tactic that helps them encrypt their victims' systems faster while reducing the chances of being detected and stopped.
> This tactic is called intermittent encryption, and it consists of encrypting > only parts of the targeted files' content, which would still render the data > unrecoverable without using a valid decryptor+key.
> For example, by skipping every other 16 bytes of a file, the encryption process takes almost half of the time required for full encryption but still locks the contents for good.
> Additionally, because the encryption is milder, automated detection tools that rely on detecting signs of trouble in the form of intense file IO operations are more likely to fail.

## Features
PowerShell script that:
* Creating a Windows service. (Set service to auto start)
** This is a basic service script that defines the OnStart and OnStop methods, which are called when the service is started and stopped, respectively. You can add any additional code you want the service to perform in these methods.
* Searches for partially encrypted files using the following parameters:
** Read the first 16 bytes of the file.
** Check if the header is the correct magic number.
** Check if the file has the correct extension.
** Check for a particular string of characters.
** Check files seizes.
** And.... more......
* Moves those files to a folder on the desktop.
* Logging the activity to a text file (date and time)
* Creates a Windows Sandbox configuration file with:
** 4096 MB of memory.
** Disable the virtual GPU.
** Disable network access.
** Set the execution policy to Restricted.
** Protected Host.
** Read Only Folder between host and sandbox.
* Launches Sandbox, then automatically scans the files in question:
** The files in the C:\My Folder folder will be scanned on start using the MpCmdRun.exe tool from Windows Defenderwhich will be run as a protected client process.


## Installation

```sh
1. Download repository.
2. Move to your desired location.
3. Make sure to check the script and edit the folder names and locations. By default it wants to install on your desktop.
```

### Test Files
```sh
Here are the sample partially encrypted files with full file extensions:
To use the sample partially encrypted files that I created for you, you can copy them to the $directory specified in the script (e.g. C:\MyFiles) and then run the script. The script will search for partially encrypted files in the specified directory and move any that it finds to the My Folder directory on the desktop.

If you want to test the different methods for identifying partially encrypted files, you can rename the files to change their extension or modify their contents to match the criteria used by each method. For example, you could rename the file with the magic number header to have a different extension (e.g. .txt) or you could add the string "PARTIALLY ENCRYPTED" to the file with the correct extension.

PartiallyEncrypted-MagicNumber.encrypted: This file has the magic number header ("Salted__") and the correct file extension, so it will not be identified as a partially encrypted file using the first method.

PartiallyEncrypted-CorrectExtension.encrypted: This file has the correct file extension, but it does not have the magic number header, so it will be identified as a partially encrypted file using the first method.

PartiallyEncrypted-IncorrectExtension.txt: This file does not have the correct file extension, so it will be identified as a partially encrypted file using the second method.

PartiallyEncrypted-MarkerString.txt: This file has the string "PARTIALLY ENCRYPTED" in its contents, so it will be identified as a partially encrypted file using the third method.
```

## License
GNU Affero General Public License v3.0

## INSPIRATION
This guy gave me the idea because since cyber wasn't paying s**t...... I had been contemplating a career in cyber crime.

Check out his git, he is considered a contributor to this project
https://github.com/tahkisis

Donations to my broke a$$:
* Bitcoin (BTC) Address: bc1qa27kjjqacshg3szwvr5rr48dfwfdfrtyu8agd4
