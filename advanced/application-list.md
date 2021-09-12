## Application List
**Note:** You can change the Application List in the "Apps" section of the User Interface `https://xxx.xxx.xxx.xxx:47990/`
- You can use Environment variables in place of values
	- $(HOME) will be replaced by the value of $HOME
	- $$ will be replaced by $ --> $$(HOME) will be replaced by $(HOME)
- env: Adds or overwrites Environment variables for the commands/applications run by Sunshine.
	- "Variable name":"Variable value"
- apps: The list of applications
	- Example:
	```json
	{
	"name":"An App",
	"cmd":"command to open app",
	"prep-cmd":[
			{
				"do":"some-command",
				"undo":"undo-that-command"
			}
		],
	"detached":[
		"some-command",
		"another-command"
		]
	}
	```
	- name: Self explanatory
	- output <optional>: The file where the output of the command is stored
		- If it is not specified, the output is ignored
	- detached: A list of commands to be run and forgotten about
	- prep-cmd: A list of commands to be run before/after the application
		- If any of the prep-commands fail, starting the application is aborted
		- do: Run before the application
			- If it fails, all 'undo' commands of the previously succeeded 'do' commands are run
		- undo <optional>: Run after the application has terminated
			- This should not fail considering it is supposed to undo the 'do' commands.
			- If it fails, Sunshine is terminated
	- cmd <optional>: The main application
		- If not specified, a processs is started that sleeps indefinitely

1. When an application is started, if there is an application already running, it will be terminated.
2. When the application has been shutdown, the stream shuts down as well.
3. In addition to the apps listed, one app "Desktop" is hardcoded into Sunshine. It does not start an application, instead it simply starts a stream.

Linux
```json
{
	"env":{ 
		"DISPLAY":":0",
		"DRI_PRIME":"1",
		"XAUTHORITY":"$(HOME)/.Xauthority",
		"PATH":"$(PATH):$(HOME)/.local/bin"
	},
	"apps":[
	{
		"name":"Low Res Desktop",
		"prep-cmd":[
		{ "do":"xrandr --output HDMI-1 --mode 1920x1080", "undo":"xrandr --output HDMI-1 --mode 1920x1200" }
		]
	},
	{
		"name":"Steam BigPicture",

		"output":"steam.txt",
		"cmd":"steam -bigpicture",
		"prep-cmd":[]
	}
	]
}
```
Windows
```json
{
	"env":{
		"PATH":"$(PATH);C:\\Program Files (x86)\\Steam"
	},
	"apps":[
	{
		"name":"Steam BigPicture",

		"output":"steam.txt",
		"prep-cmd":[
			{"do":"steam \"steam://open/bigpicture\""}
		]
	}
	]
}
```