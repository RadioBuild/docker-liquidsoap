## docker-liquidsoap
Dockerfile for running [Liquidsoap](https://www.liquidsoap.info/) in a container. \
Just mount your Liquidsoap script, music directory and you are good to go!

Works well with containerized [icecast2](https://icecast.org/): [pltnk/docker-icecast2](https://github.com/pltnk/docker-icecast2)

### Installation:
You can either pull the image from Dockerhub \
`docker pull pltnk/liquidsoap` \
or build it yourself \
`docker build -t pltnk/liquidsoap github.com/pltnk/docker-liquidsoap`

### Configuration:
- Mount your Liquidsoap script file to `/etc/liquidsoap/script.liq`
- Mount your music directory to `/music`
- In your Liquidsoap script change path to your music directory to `/music`

#### docker run
```
docker run --name liquidsoap -d --restart=always \
--volume /path/to/your/script.liq:/etc/liquidsoap/script.liq \
--volume /path/to/your/music:/music \
pltnk/liquidsoap
```
#### docker-compose.yml
```
liquidsoap:
  image: pltnk/liquidsoap
  container_name: liquidsoap
  restart: always
  volumes:
    - /path/to/your/script.liq:/etc/liquidsoap/script.liq
    - /path/to/your/music:/music
```
