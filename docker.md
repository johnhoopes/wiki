<!-- TITLE: Docker -->
<!-- SUBTITLE: A quick summary of Docker -->

# Docker
docker ps - what's running now

# Get an Instance
docker pull {dockerpath}

# Start an instance
docker run -ti {dockerpath}

# Start at Bash instead of what's in the docker
docker run -ti --entrypoint bash {dockerpath}

# Create some Persistent Storage
docker create -v /opt/{internalpathname} --name data {dockerpath}

# Run with the persistent Storage
```docker run -ti --volumes-from data {dockerpath}
```
# Run with some internal port forwarding
```docker run -ti --volumes-from data -p 10.0.0.207:80:80 {dockerpath}
```
