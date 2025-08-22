# 7: Run detection test

## What's covered in this section
- Run detection test to verify deteciton capability (AV, EDRM, Behavior Monitoring)
- Run a detection test to confirm successful onboarding


## Run detection test

### Antivirus (Real time scanning)
Run below command in terminal to confirm real time protection status
```sh
mdatp health --field real_time_protection_enabled
```
If real-time protection is enabled, the output will be *true*.

```sh
curl -o ~/Downloads/eicar.com.txt https://secure.eicar.org/eicar.com.txt
```
https://learn.microsoft.com/en-us/defender-endpoint/validate-antimalware

- Anttivirus (Behavior moniroing)
https://learn.microsoft.com/en-us/defender-endpoint/demonstration-behavior-monitoring
  
- EDR functionality
https://learn.microsoft.com/en-us/defender-endpoint/edr-detection
