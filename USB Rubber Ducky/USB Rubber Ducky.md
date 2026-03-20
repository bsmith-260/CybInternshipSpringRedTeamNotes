## USB Rubber Ducky 
The `USB Rubber Ducky` is a  USB device used as a [[Keystroke Injection]] tool that uses a scripting language called [[DuckyScript]]. It works as a device that mimics a standard USB keyboard (USB HID). 

When plugged into a device, and the device is started, the operating system will typically trust it as a legitimate input device and the keystrokes configured will begin immediately unless specifically delayed in the `payload`.
###### Keystroke Injection
`Keystroke Injection` is a form of physical hardware-based cyberattack where a malicious device, such as a modified USB drive, that will mimic a standard `human interface device (HID) keyboard` to inject unauthorized commands into a targeted device.

Through running a scripting language on whatever malicious device is used, it is able to bypass traditional security such as firewalls, or antivirus software. 

The device (usually a USB) can be plugged into any device that contains the necessary port, usually being a USB-C, or USB-A.
###### Payload
A `payload` is the specific part of malware, or a cyberattack, that executes a malicious activity on the system that is being targeted. This can be keystrokes, data theft, ransomware encryption, system disruption, etc. 

Once system/device security is bypassed, the payload will deliver the harmful action that was programmed. 
## Use Cases
The USB Rubber Ducky acts as a `standard USB keyboard (USB HID)`, and performs pre-programmed keystroke payloads into a target computer. 

The Rubber Ducky can be used for multiple cases, legitimate, or malicious.
1. Security and Penetration Testing 
2. Task Automation
3. Malware Installation
4. Backdoor Creation
5. Exfiltration
6. Privilege Abuse
7. Credential Collection
8. Terminal/Command Prompt Commands
## Configuration Details
Before using the USB Rubber Ducky, the `Quack-Start` menu should be accessed as it gives the user the necessary details on how to configure and use their device.
## Instructions
The Rubber Ducky's payload can be configured and changed via [[Hak5 Payload Studio Pro]]. 

When plugged into a computer in arming mode, it will appear in the drives section as a normal flash drive, under This PC in file explorer, named `DUCKY`.

In the drive will be multiple files/folders, including a file named `inject.bin`. 

On `Payload Studio Pro`, you are able to write a script of keystroke injections with `DuckyScript` that will be ran on the device you choose to target.

After writing a script, you are able to save, and then download the new `inject.bin` file from the Payload Studio Pro website.

After downloading it, you can drag and drop the new file into the `DUCKY` drive on file explorer. Replace the old `inject.bin` file with the new one, and your device will be ready for use.

Unplug the `Rubber Ducky` and plug the device into a USB-C or USB-A port of your choice. The `Rubber Ducky` is compatible with almost any device that has one of these ports as the device acts as a standard `HID keyboard`. 





