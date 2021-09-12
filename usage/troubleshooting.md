---
parent: Usage
nav_order: 3
---
# Trouleshooting
- If you get "Could not create Sunshine Gamepad: Permission Denied", ensure you are part of the group "input":
	- `groups $USER`
	
- If Sunshine sends audio from the microphone instead of the speaker, try the following steps:
 	1. `$ pacmd list-sources | grep "name:"` or `$ pactl info | grep Source` if running pipewire.
	2. Copy the name to the configuration option "audio_sink"
	3. restart sunshine

- If you get "Error: Failed to create client: Daemon not running", ensure that your avahi-daemon is running:
	- `systemctl status avahi-daemon`