# LOVE VSCode Game Template
A fully configured VSCode template for LOVE.\
This repo is a fork of [LOVE VSCode Game Template](https://github.com/Keyslam/LOVE-VSCode-Game-Template) by @Keyslam. I removed parts that I'm not using extensively, changed VSCode scripting accordingly, and slightly rewrote this README file. It's a bit less beginner friendly than original one.

## Features
- 📄 Rich Lua language features with [Lua Language Server](https://github.com/LuaLS/lua-language-server)
- 🔧 Debugging with [Local Lua Debugger](https://github.com/tomblind/local-lua-debugger-vscode). Launch configs included.
- 🏢 Automatic builds with [Makelove](https://github.com/pfirsich/makelove). A "Build All" task already configured for the game.
- 🗂️ Organized with [Workspaces](https://code.visualstudio.com/docs/editor/workspaces)

## Prerequisites
- [Visual Studio Code](https://code.visualstudio.com/download)
- [LÖVE 11.4](https://love2d.org/)
- [Makelove](https://github.com/pfirsich/makelove)

_**LÖVE and Makelove should be in your PATH environment variable.**_

## Setup
1 - [Use this template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template) to create a new repository for your game, then clone that repository locally.

2 - Open the `Workspace.code-workspace` file with Visual Studio Code.
You will be prompted that there are recommended extensions and if you want to install these. Click 'Install'.\
If this does not happen, install [Sumneko's Lua extension](https://marketplace.visualstudio.com/items?itemName=sumneko.lua) and [Local Lua Debugger](https://marketplace.visualstudio.com/items?itemName=tomblind.local-lua-debugger-vscode) manually.

3 - Configure the `game/conf.lua` and `game/build_all.toml` with the settings specific for your game.\
**NOTE**: Make sure to keep `t.console` set to `false` in `conf.lua`. Local Lua Debugger will not work otherwise.

4 - Change the `LICENSE` file to your liking and add your name where prompted.

In case you need help, feel free reach out at [LÖVE Discord server](https://discord.com/invite/rhUets9).

## Running
Press `F5` to launch the game in 'Debug mode'. In debug mode you can use breakpoints and inspect variables.\
You can switch to 'Release mode' in the 'Run and Debug' tab (`Ctrl+Shift+D`).\
Alternatively, you can run `lovec game` in the terminal, but you will not have debugging capabilities.

## Structure
```
├── LICENSE             You may want to edit or remove this file
│
├── /game
│   ├── conf.lua        Project config file
│   ├── build_all.toml  Build config file
│   ├── /assets         Contains the game's assets
│   ├── /lib            Contains external libraries
│   └── /src            Contains the game's source code
│
└── /builds              Contains the builds of your game made with makelove
```

### Appendix: Setting up a minimal project yourself.
Sometimes you don't want a full blown template and just get the minimum required settings to get your editor working. The following steps will explain how to setup a project with the Sumneko Language Server and a launch task:

1. Create a folder for your game with your `main.lua` and `conf.lua`.

2. Open the folder with VSCode. 

3. Install the [Sumneko Lua Language Server](https://marketplace.visualstudio.com/items?itemName=sumneko.lua) and [Local Lua Debugger](https://marketplace.visualstudio.com/items?itemName=tomblind.local-lua-debugger-vscode) extensions.

4. In the same folder as your `main.lua`, create a folder named `.vscode`

5. In the `.vscode` folder, create a file named `settings.json` and copy the following contents into it:
```
{
	"Lua.workspace.library": [
		"${3rd}/love2d/library",
		"lib"
	],
	"Lua.runtime.version": "LuaJIT",
	"Lua.workspace.checkThirdParty": false,
}
```

6. In the `.vscode` folder, create a file named `launch.json` and copy the following contents into it:
```
{
	"version": "0.2.0",
	"configurations": [
		{
			"type": "lua-local",
			"request": "launch",
			"name": "Release",
			"program": {
				"command": "love"
			},
			"args": [
				".",
			],
		},
	]
}
```

You can use this template as a basis for how to add additional features such as debugging, code styles, folder structures, automatic builds, et cetera.
