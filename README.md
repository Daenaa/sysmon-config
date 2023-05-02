



##  Summary

Sysmon has two configuration type:

1- Targetting: These configuration's will collect logs of special events and useful for Threat Hunting

2- Tracking: These configuration's will collect more logs (also some noisy logs) to fill dashboards abd useful for SOC and correlation engines.



I create this mixed configuration. I fork sysmon modular and then mix it with other fork's and my knowledge about detection and threat hunting.

 * Significant: 
This configuration contains the protection channel  which is called  "FileBlockExecutable" and is generated when Sysmon detects and blocks the creation of executable files , Event ID= 27.

*Note: This configuration will raise your events (5x of sysmon modular default configuration), so be careful and re-calculate your license, resource's data lifecycle policie's.*

## Fork Information

- Florian Roth @Neo23x0
- Tobias Michalski @humpalum
- Christian Burkard @phantinuss
- Nasreddine Bencherchali @nas_bench
- Olaf Hartong @olafhartong
- @SwiftOnSecurity

## Additional coverage includes

- Cobalt Strike named pipes
- PrinterNightmare
- HiveNightmare
- Mimikatz
- Macros

##Update
on May2,2023: 
Update EventCode=12 and Sub.Technique 1547.014 about Boot or Logon Autostart Execution: Active Setup 
Tactics: Persistence, Privilege Escalation
Adversaries may abuse Active Setup by creating a key under HKLM\SOFTWARE\Microsoft\Active Setup\Installed Components\ and setting a malicious value for StubPath. This value will serve as the program that will be executed when a user logs into the computer.

##  Installation (and make it secure)

We want to install sysmon a little different to protect it more. so we will change process name from "sysmon" to "Daena", change drive name to "daenadrv" and change service name to "daenaservice". follow the example:


**1) Get Ready:**

Download last version of Sysmon from [Microsoft](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) or [Sysinternals](https://download.sysinternals.com/files/Sysmon.zip).

Download symon cofig file in here [(Download)](https://github.com/Daenaa/sysmon-config/blob/master/Daenaa-SysmonConfig.xml) and copy in you downloaded sysmon folder.

Rename "sysmon64.exe" or "sysmon.exe" to another name, to hide it (with different name) in process list. for example we rename "sysmon64.exe" to "Daena.exe"


**2) Installation**

Run powershell or cmd with Admin Rights (Run as Admin) and change path to your sysmon folder

Install command: `Daena.exe -accepteula -i "Daenaa-SysmonConfig.xml" -d daenadrv`


**3) Change Service**

After install, open "regedit.exe" and go to `Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\daena`

Now change DisplayName: Daena Service

And change Description: Enables daena process live



*also you can use these steps for your SIEM agent installation*


## Other Sysmon Configs

- Olaf Hartong's [Sysmon Modular](https://github.com/olafhartong/sysmon-modular) - modular Sysmon config for easier maintenance and generation of specific configs

## Testing

This configuration is focused on detection coverage. We have only one rather small testing environment to avoid problematic expressions that trigger too often. It is recommended to test the downloaded configuration on a small set of systems in your environment in any case.

## Feedback

Since we don't have more than one environment to test the config ourselves, we rely on feedback from the community.

Please report:

1. Expressions that cause a high volume of events
2. Broken configuration elements (typos, wrong conditions)
3. Missing coverage (preferrably as a pull request)

## Usage

### Install

Run with administrator rights

```batch
sysmon.exe -accepteula -i "Daenaa-SysmonConfig.xml"
```

### Update existing configuration

Run with administrator rights

```batch
sysmon.exe -c "Daenaa-SysmonConfig.xml"
```

### Uninstall

Run with administrator rights

```batch
sysmon.exe -u
```

### Change Driver's name

Run with administrator rights
```batch
daena.exe -c "Daenaa-SysmonConfig.xml" -d daenaDrv
```

### You can change name of "sysmon.exe" 
This is good for providing security, but it is not enough, because despite changing the name of the sysmon.exe, the hacker is still able to identify it in other ways.



