# Description

Automatically switch wlan profiles on Windows using this Powershell script!

Inspired by [xzer/wlanprofilemanager](https://github.com/xzer/wlanprofilemanager) (nodeJS)

# Features

 - Unlimited amount of profiles
 - Set specific IP, Mask and Gateway or reset to auto (DHCP)
 - Set specific DNS or reset to auto
 - Be notified when a profile is applied

# How to use

## Configure

- Download this repository and extract it in a local folder
- Copy the `profiles.sample.psd1` to `profiles.psd1`
- Customize your `profiles.psd1` file: add your own profile using the WiFi network name (SSID)

Logs can be found in .\logs folder.

## Installation

- Register a new task in Task Scheduler (Start -> Search for Tasks Scheduler)
    - Create Task
    - Change User to **SYSTEM** 
    - Define the trigger as following:
        - Begin the task: On an event
        - Select Basic button from the left side.
        - Log: Microsoft-Windows-WLAN-AutoConfig/Operational
        - source: WLAN-AutoConfig
        - event id: 11001
    - Set the actions as following:
        - Start a Program
        - Program: "C:\Program Files\PowerShell\7\pwsh.exe"
        - Argument: "**PATH**\wlanprofilemanager-ps\wlanprofilemanager-ps.ps1"
        - Start in: "**PATH**\wlanprofilemanager-ps\"
    - Disable all the condition in the next tab.
    - Click OK and you're done.

# License

MIT License - see LICENSE file
