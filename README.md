## What Exactly Is This?
### CobbleVerse
[CobbleVerse](https://www.lumyverse.com/en/cobbleverse/) is a modpack (collection of mods) for Java Minecraft that bring an experience like the main series of Pokemon games to the world of Minecraft

### Docker
Docker is a way of containerizing applications and their dependencies, and does so in a way very akin to virtual machines

## Quick Start
Download this repository and unzip it. Make sure you’re in the correct directory. You’ll see an **.env** file; open it in your text editor and edit the values to what you want. 

Next, run the command `docker compose up` in your terminal. This process can take 5–10 minutes, because it is downloading the modpack and fabric server. Once the console shows a message like "Running" or "Done!" the server is up and running.

If you're on the same machine, you can connect using **localhost:25565** or **127.0.0.1:25565**. You can also use a service like [playit](https://playit.gg) to set up a proxy in front of your network so you don’t have to worry about port forwarding or sharing your IP. 

I left a commented out image called `"playit:0.16"`. Simply uncomment every line and paste in the secret key you obtained when creating your tunnel.

If you want to play on the server, I recommend using [Prism Launcher](https://prismlauncher.org/) to install the modpack, since your Minecraft client and the server need to have the same mods. Once Prism Launcher is installed, create a new instance and locate the Modrinth tab. Search for **CobbleVerse**, and it will prompt you to install it. After that, you’ll be able to launch the correct modded version of Minecraft directly from Prism Launcher.

## Useful commands
### How to give myself op?
```bash
docker exec -it cobbleverse-docker-server-mc-1 bash
rcon-cli op YOUR_USERNAME
exit
```
## How to trigger a backup?
```bash
docker compose exec mc-backup /usr/bin/backup now
```

## How to import a backup?
**IMPORTANT: shutdown the server via `docker compose down` to ensure data transfer stops entirely.**
Run the command: `tar -xzf ./backups/<your-backup-filename>.tgz -C ./data` Adjust for your world name, and timestamp, as
well as making sure you're in the working directory of the server. Simply start the server again and ta-da!
