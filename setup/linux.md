# Setup:
sunshine needs access to uinput to create mouse and gamepad events:

- Add user to group 'input':
	`usermod -a -G input $USER`
- Create udev rules:
	- Run the following command: 
	`nano /etc/udev/rules.d/85-sunshine-input.rules`
	- Input the following contents:
	`KERNEL=="uinput", GROUP="input", MODE="0660"`
	- Save the file and exit
		1. `CTRL+X` to start exit
		2. `Y` to save modifications
- `assets/sunshine.conf` is an example configuration file. Modify it as you see fit, then use it by running: 
	`sunshine path/to/sunshine.conf`
- Configure autostart service
	`path/to/build/dir/sunshine.service` is used to start sunshine in the background. To use it, do the following:
	1. Copy it to the users systemd, `cp sunshine.service ~/.config/systemd/user/`
	2. Starting
		- Onetime: 
			`systemctl --user start sunshine`
		- Always on boot:
			`systemctl --user enable sunshine`

- `assets/apps.json` is an [example](README.md#application-list) of a list of applications that are started just before running a stream

## Additional Setup for KMS:
Please note that `cap_sys_admin` may as well be root, except you don't need to be root to run it.
It's necessary to allow Sunshine to use KMS
- `sudo setcap cap_sys_admin+p sunshine`