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

## How to Correlate Suspicious Activity to the Ducky
If you discover a suspicious new Event ID 6416 ("A new external device was recognized by the system.")

## Detection Demonstration
