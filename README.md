# <div align="center">Anti - Royal</div>
## <div align="center">Catch the malware your EDR is missing!</div>

![](https://github.com/shadowdevnotreal/anti_Royal/blob/main/Images/antiroyal.jpg)

![][Powered by Chat GPT-3](https://github.com/shadowdevnotreal/anti_Royal/blob/main/Images/chat%20GPT3.png)

## LOGIC
[Wiki for deatiled analysis](https://github.com/shadowdevnotreal/anti_Royal/wiki)
EDR is great, but it should not be your magic bullet!
Ransomware groups like Conti and Royal utilize partially encrypted files in order to deploy their malware.
Many EDR will ignore this, and some will ignore file sizes.
This can allow bad actors to deploy their malware on to your network and systems.

## Features
PowerShell script that:
* Creating a Windows service.
** This is a basic service script that defines the OnStart and OnStop methods, which are called when the service is started and stopped, respectively. You can add any additional code you want the service to perform in these methods.
* Searches for partially encrypted files.
** 
* Moves those files to a folder on the desktop.
* Logging the activity to a text file.
* Creates a Windows Sandbox configuration file.
** 
* Launches Sandbox, then automatically scans the files in question.
#
#
> SentinelLabs has posted a report examining a trend started by LockFile in mid-2021 and now adopted by the likes of Black Basta, ALPHV (BlackCat), PLAY, Agenda, and Qyick.

> **Ransomware gangs switching to new intermittent encryption tactic**
A growing number of ransomware groups are adopting a new tactic that helps them encrypt their victims' systems faster while reducing the chances of being detected and stopped.
> This tactic is called intermittent encryption, and it consists of encrypting > only parts of the targeted files' content, which would still render the data > unrecoverable without using a valid decryptor+key.
> For example, by skipping every other 16 bytes of a file, the encryption process takes almost half of the time required for full encryption but still locks the contents for good.
> Additionally, because the encryption is milder, automated detection tools that rely on detecting signs of trouble in the form of intense file IO operations are more likely to fail.

## Installation

```sh
1. Download repository.
2. Move to your desired location.
3. Make sure to check the script and edit the folder names and locations. By default it wants to install on your desktop.
```

### Test Files
```sh
I have included test files for your conveinence.
```

## License

GNU Affero General Public License v3.0
