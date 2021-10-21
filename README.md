# asp-dotnet-core-webapi-sample
This is a sample project for web api development with dotnet core.
## Dev environment
* Enable WSL: https://code.visualstudio.com/docs/remote/wsl-tutorial#_enable-wsl
* Install Ubuntu: https://code.visualstudio.com/docs/remote/wsl-tutorial#_install-a-linux-distro
* Install Docker Desktop: https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-containers#install-docker-desktop
* Install Windows Terminal: https://docs.microsoft.com/en-us/windows/terminal/get-started#install
* Install VS Code: https://code.visualstudio.com/
* Install VS Code Remote Development Extension Pack: https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack
# Process of making this sample from scratch
## Opening a WSL 2 folder in a container: 
Reference: https://code.visualstudio.com/docs/remote/wsl#_advanced-opening-a-wsl-2-folder-in-a-container  
Notes:
* Use "C# (.NET) and MS SQL" devcontainer

You will get a containerized dev environment and your VS code showing on your Windows OS is actually connecting to the dev container and using the environment there.  
Check your docker containers with `docker ps`. You will see 2 containers are created.
```
IMAGE                                            STATUS             PORTS      NAMES
asp-dotnet-core-webapi-sample_devcontainer_app   Up About an hour              asp-dotnet-core-webapi-sample_devcontainer_app_1
mcr.microsoft.com/mssql/server:2019-latest       Up About an hour   1433/tcp   asp-dotnet-core-webapi-sample_devcontainer_db_1
```
In addition, these 2 containers are sharing the same network stack.
The db is using a bridge network.  
Try `docker inspect asp-dotnet-core-webapi-sample_devcontainer_db_1 | grep NetworkMode`.  
You will see.
```
"NetworkMode": "asp-dotnet-core-webapi-sample_devcontainer_default"
```
The db is using the bridge network `asp-dotnet-core-webapi-sample_devcontainer_default`.  
And the app is sharing the network stack of the db.  
Try `docker inspect asp-dotnet-core-webapi-sample_devcontainer_app_1 | grep NetworkMode`
You will see.
```
"NetworkMode": "container:f8f17300cc111a8a095da97a872a800b1fb0a330229a556ce8eeeeaf65155a58"
```
This is done by the docker compose setting `network_mode: service:db` in the file `./.devcontainer/docker-compose.yml`.  
Here are some reference:
* https://github.com/docker/docker.github.io/issues/9725#issuecomment-761832882
## New a webapi project