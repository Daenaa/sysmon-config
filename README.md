# sysmon-config | A Sysmon configuration file

This is Daena and it is a forked and modified version of @SwiftOnSecurity  [sysmon config](https://github.com/SwiftOnSecurity/sysmon-config) And @Neo23x0 .


It started as a is simply copy of the original repository. We merged most of the 30+ open pull requests. Thus we have fixed many of the issues that are still present in the original version and extended the coverage with important new extensions.

## Maintainers of this Fork

- Florian Roth @Neo23x0
- Tobias Michalski @humpalum
- Christian Burkard @phantinuss
- Nasreddine Bencherchali @nas_bench

## Additional coverage includes

- Cobalt Strike named pipes
- PrinterNightmare
- HiveNightmare
- Mimikatz

- Macros

## Configs in this Repository

This repo includes the original and one additional configurations

- `sysmonconfig-export.xml` the original config provided by @SwiftOnSecurity

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
sysmon.exe -c "Daenaa-SysmonConfig.xml" -d XDrv
```

### You can change name of "sysmon.exe" 
This is good for providing security, but it is not enough, because despite changing the name of the sysmon.exe, the hacker is still able to identify it in other ways.



