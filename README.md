# asp-dotnet-core-webapi-sample
This is a sample project for web api development with dotnet core.
## Dev environment
* Enable WSL: https://code.visualstudio.com/docs/remote/wsl-tutorial#_enable-wsl
* Install Ubuntu: https://code.visualstudio.com/docs/remote/wsl-tutorial#_install-a-linux-distro
* Install Docker Desktop: https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-containers#install-docker-desktop
* Install Windows Terminal: https://docs.microsoft.com/en-us/windows/terminal/get-started#install
* Install VS Code: https://code.visualstudio.com/
* Install VS Code Remote Development Extension Pack: https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack
# Process
## Opening a WSL 2 folder in a container: 
Reference: https://code.visualstudio.com/docs/remote/wsl#_advanced-opening-a-wsl-2-folder-in-a-container  
Notes:
* Use "C# (.NET) and MS SQL" devcontainer

You will get a containerized dev environment and your VS code showing on your Windows OS is actually connecting to the dev container and using the environment there.
## New a webapi project