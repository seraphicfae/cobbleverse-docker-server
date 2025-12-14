## What Exactly Is This?
### CobbleVerse
[CobbleVerse](https://www.lumyverse.com/en/cobbleverse/) is a modpack (collection of mods) for Java Minecraft that bring an experience like the main series of Pokemon games to the world of Minecraft

### Docker
[Docker](https://www.docker.com/) is a way of containerizing applications and their dependencies.

## Quick Start
1. Download this repository and unzip it and enter the folder. You’ll see an **.env** file. Open the **.env** file in your text editor
and edit the values to what you want.

2. Next, run the command `docker compose up` in your terminal **you need to be in the folder you downloaded from this repository**. This process can take 5–10 minutes,
because it is downloading the modpack and fabric server. Once the console shows a message like `Done (4.245s)! For help, type "help"` your server is running.

3. If you're on the same machine, you can connect using **localhost:25565** or **127.0.0.1:25565** in the server address. You can also use a service like [playit](https://playit.gg)
to set up a proxy in front of your network so you don’t have to worry about port forwarding or sharing your IP. I left a commented out image called `"playit:latest"`. Simply uncomment
every line and paste in the secret key you obtained when creating your tunnel.

4. If you want to play on the server, I recommend using [Prism Launcher](https://prismlauncher.org/) to install the modpack, since your Minecraft client and
the server need to have the same mods. Once Prism Launcher is installed, create a new instance and locate the Modrinth tab. Search for **CobbleVerse**, and it will prompt
you to install it. After that, you’ll be able to launch the correct modded version of Minecraft directly from Prism Launcher.

```bash
git clone https://github.com/seraphicfae/cobbleverse-docker-server
cd cobbleverse-docker-server
nano .env
docker compose up
```

> [!NOTE]
> If you're having errors with the docker daemon service or needing root access, see this [guide](https://docs.docker.com/engine/install/linux-postinstall/).

## Useful Commands And Tips

### How To Give Myself OP?
```bash
docker exec -it cobbleverse-docker-server-mc-1 bash
rcon-cli op USERNAME
exit
```

## How To Change CobbleVerse Versions?
You will need to go to the [Modrinth](https://modrinth.com/modpack/cobbleverse/) page and find the version you want, and edit `COBBLEVERSE_VERSION=`
to the version you want. E.g: `version/1.7.0c` to `version/1.6` for version 1.6

## How To Trigger A Backup?
```bash
docker compose exec mc-backup /usr/bin/backup now
```

## How To Import A Backup?
> [!WARNING]
> Shutdown the server to prevent corruption: `docker compose down`. Ensure data transfer stops entirely.

Now, simply go to your backups folder and extract the archived file, then place it inside the **data** directory, deleting or overwriting your previous world. After that, start the server as usual.

You can also run this command while you're in your server directory:
`tar -xzf ./backups/<your-backup-filename>.tgz -C ./data` Make sure to adjust the command for your world name and timestamp.

## What Are These Commented Out Mods?
**Alternative Authenticator** and **No Chat Report** only exist to make it so users logging in via [Ely.by](https://ely.by/) can join your server. In most cases, you don't need this. Feel free to remove the commented out section.
