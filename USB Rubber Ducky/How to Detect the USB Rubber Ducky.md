## How to Detect the USB Rubber Ducky
1.  USB-A or USB-C Ports
	* Rubber Ducky is a physical attack device, it can be physically observed when plugged into either the `USB-A`, or `USB-C` ports directly on the target computer.
2.  Device Manager
	* In device manager you can see every device connected to the computer. 
	* When the `HID` attack mode is activated either through clicking the device button, or directly through the payload, an extra device will appear in the keyboard list as shown below. The `HID Keyboard Device` is the Ducky actively in attack mode.
		 ![[Pasted image 20260318201456.png]]
	* When the device is in either `STORAGE` or `HID STORAGE` mode, you can observe the Ducky being listed as a `USB Input Device`. 
		![[Screenshot 2026-03-18 200826.png]]
3.  Event Viewer- Windows Security Event ID 6416
	* `Event Viewer` is a Windows tool that can be used to monitor, troubleshoot, and diagnose the system's health based on detailed logs of application, security, and system events.
	* When the Ducky is plugged into the target computer, a Windows Security log with an Event ID of 6416 is created. If these logs are not set to be tracked by default, you must activate logging through an administrator CMD.
	* Event logs under `DriverFrameworks-UserMode` also will appear as a result of the device being plugged in.
###### How to Activate Log Creation
1. Open an administrator CMD.
2. Run `auditpol /list /subcategory:*` to list all log categories, with their subcategories.
3. The log subcategory we are looking to track is listed as `Plug and Play Events`. This log will track external devices that are plugged into the system.
4. Run `auditpol /set /subcategory:"Plug and Play Events" /success:enable` to activate log creation.
5. Run `auditpol /get /subcategory:"Plug and Play Events"` to make sure that the log creation is activated. It will say `Success` next to the subcategory name if it is.
6. Return to Event Viewer, and you will see logs of devices plugged into the computer after the rule is changed.
7. To activate `DriverFrameworks-UserMode` logs, you have to locate its folder in the `Applications and Services Logs` folder, to `Microsoft`, to `Windows` to the `DriverFrameworks-UserMode` folder.
8. After finding this folder, click the expansion arrow, right click on the `Operational` log channel, and click on properties.
9. Click the `Enable logging` button and ensure that it is highlighted blue.

## How to Correlate Suspicious Activity to the Ducky
1. When correlating logs, it is smart to check the timestamps of the logs to be able to correlate them. With the Rubber Ducky being a fast action device, it is likely that a new USB insertion followed by commands being ran are correlated with each other.
2. Compare the time of the suspected device connection with the logged-in user session and the processes launched right after. If shells, PowerShell, Run dialogs, or scripting tools start without normal user interaction, that is suspicious.
3. Trace the process chain after the suspicious event. Correlate the first opened process with its child processes. For example, if `explorer.exe` is followed by `cmd.exe`, `powershell.exe`, or a downloaded executable immediately after USB insertion, that can indicate an injected payload.
4. Check for any follow-on behavior such as creation of new accounts, registry changes, scheduled tasks, dropped files, outbound connections, or credential access attempts shortly after the suspected keystroke injection. These help confirm whether the device was used in an actual attack.

## Common Attacks
1. Malware Installation
2. Backdoor Creation
3. Data Exfiltration
4. Privilege Abuse
5. Credential Collection
6. Terminal/Command Prompt Commands
7. Prank Payloads

## Detection Demonstration
