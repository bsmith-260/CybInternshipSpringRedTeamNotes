
## How to Prevent, and Protect Against the USB Rubber Ducky
While not many, there are active steps you can take to protect your device against a Rubber Ducky targeted attack.

1. Physical Awareness/Security
2. Endpoint detection and logging
3. Least privilege on endpoint devices
4. Whitelisting approved devices only
5. Disabling unused USB ports
6. Application control
7. Having an incident response plan

### Physical Awareness/Security
* USB Rubber Ducky attacks usually require someone to physically plug the device into a computer, so keeping systems supervised, locking offices, and not leaving devices unattended helps stop the attack before it starts.
* By being aware of the physical capabilities of attack equipment, this can severely limit the amount of damage an attacker may cause to a device, or system.
### Endpoint Detection and Logging
* Security monitoring and system logs help identify suspicious behavior after a device is inserted, such as rapid command execution, PowerShell activity, unexpected processes, or unusual child process chains.
### Least Privilege
* Users should only have the minimum permissions needed for their job. If an injected payload runs on a low-privilege account, it has less ability to install malware, change settings, or gain persistence.
### Whitelisting 
* Device whitelisting allows only authorized USB devices to connect and function. This helps block unknown or rogue devices, including ones pretending to be a keyboard.
### Disable Unused USB Ports
* Turning off unused USB ports through BIOS, operating system policy, or physical blockers reduces the number of places an attacker can plug in a malicious device.
### Application Control
* Application control restricts which programs and scripts are allowed to run. Even if the Rubber Ducky injects commands successfully, the payload may fail if tools like PowerShell, cmd, or unauthorized executables are blocked.
### Incident Response Plan
* An incident response plan ensures there is a clear process for what to do if an attack is suspected, such as isolating the device, collecting logs, resetting credentials, and investigating what executed.