# Setup WarpScript

## Docker image

Download the Warp 10 docker image, and build it.

```
git clone https://github.com/cityzendata/warp10-docker.git
cd warp10-docker
docker build -t warp10/warp10:1.0.1 .
```

Start the Warp10 platform, this command will bind the external ports 8080 and 8081 in all interfaces with the container. 

```
docker run -p 8080:8080 -p 8081:8081 -d -i warp10/warp10:1.0.1
```
