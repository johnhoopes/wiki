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

# Connecting it to syslog
```
docker run --log-driver syslog --log-opt syslog-address=udp://10.0.0.112:514 alpine echo hello world
```

# Creating Docker Images
Need an entrypoint script like:  entrypoint.sh
```
#!/bin/ash
ssh-honeypot -r /ssh-honeypot/ssh-honeypot.rsa -p 22 -u nobody
echo "SSH Honeypot is Running..."
exec "$@"
```

Make a dockerfile
```
FROM alpine:latest
#RUN apk add --no-cache git clang libssh-dev screen gcc musl-dev nano openssl build-base bash openssh geoip curl netcat-openbsd
RUN apk add --no-cache git clang libssh-dev json-c-dev screen gcc musl-dev nano openssl build-base bash openssh geoip curl netcat-openbsd

RUN git clone https://github.com/droberson/ssh-honeypot.git
WORKDIR /ssh-honeypot/
RUN make
RUN ssh-keygen -t rsa -f ./ssh-honeypot.rsa
RUN chmod 777 /ssh-honeypot/bin/ssh-honeypot
RUN mv /ssh-honeypot/bin/ssh-honeypot /bin/ssh-honeypot
EXPOSE 22
ADD entrypoint.sh /entrypoint.sh
RUN chmod 777 /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
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