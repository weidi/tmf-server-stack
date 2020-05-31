# Trackmania Forever server docker stack
## Prerequisites
Have docker and docker-compose installed.
## Usage

Build the xaseco alpine image:
```
docker build -t toprock/tmserver:xaseco_alpine -f .\xaseco\Dockerfile.alpine .\xaseco\
```


Configure your server settings by editing the `docker-compose.yml` and the game settings in: `GameData/Tracks/MatchSettings/custom_game_settings.txt`
Run the stack:
```
$ docker-compose up
```

Build the xaseco legacy image:
```
$ cd xaseco
$ ./build-image.sh
$ cd ..
```