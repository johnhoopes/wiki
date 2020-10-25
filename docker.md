<!-- TITLE: Docker -->
<!-- SUBTITLE: A quick summary of Docker -->

# Docker
```
docker ps - what's running now
```

# Docker Service
```
systemctl start docker.service
```

# Get an Instance
```
docker pull {dockerpath}
```

# Start an instance
```
docker run -ti {dockerpath}
```

# Start at Bash instead of what's in the docker
```
docker run -ti --entrypoint bash {dockerpath}
```

# Create some Persistent Storage
```
docker create -v /opt/{internalpathname} --name data {dockerpath}
```
# Run with the persistent Storage
```
docker run -ti --volumes-from data {dockerpath}
```

# Run with some internal port forwarding
```text
docker run -ti --volumes-from data -p 10.0.0.207:80:80 {dockerpath}
```

# Read some logs
```
docker logs -f {nameofdocker}
```

# Get a Shell in the docker
```
docker exec -ti {nameofdocker} bash
```

# Interesting Dockers
## Cobalt Strike
From https://obscuritylabs.com/blog/2017/12/24/docker-your-command-control-c2/ 
```
git clone https://github.com/killswitch-GUI/CobaltStrike-ToolKit.git
```

rebuild the image replace cskey with the license key of choice; 
```
docker build --build-arg cskey="xxxx-xxxx-xxxx-xxxx" -t cobaltstrike\cs
```
Run it.  -d makes it run headless -name gives it a name.
```
docker run -d -p 192.168.2.238:50050:50050 --name "war_games" cobaltstrike\cs 192.168.2.238 password
```

## Empire
empireproject/empire