## What Exactly Is This?
### CobbleVerse
[CobbleVerse](https://www.lumyverse.com/en/cobbleverse/) is a modpack (collection of mods) for Java Minecraft that bring an experience like the main series of Pokemon games to the world of Minecraft

### Docker
Docker is a way of containerizing applications and their dependencies, and does so in a way very akin to virtual machines

### How to Play
You will want to clone this github repo and edit the .env to your liking. If your server is running mods, then your Minecraft client (the game itself) also needs to have the same mods.

My recommendation is that you use [Prism Launcher](https://prismlauncher.org/). Once it's installed, you can create a new
instance and go down to the modrinth section, then search for **CobbleVerse**, and it will prompt you to install it. Once
you've done that, you'll be able to launch the proper version of Minecraft (equipped with mods) directly from Prism Launcher.
This is the recommended approach. Afterwards, simply run `docker compose up` in the directory, and enter the address of your server. If you're on the same machine, you can use
`localhost:25565` or `127.0.0.1:25565`. You could also use a service like [playit](https://playit.gg) to have a proxy service infront of your network so you don't have to worry about port forwarding or sharing your IP with others. 

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
