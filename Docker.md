
### Docker

* [What is docker.io in relation to docker-ce and docker-ee?](https://stackoverflow.com/questions/45023363/what-is-docker-io-in-relation-to-docker-ce-and-docker-ee)
* [Experimenting with Rootless Docker](https://me*dium.com/@tonistiigi/experimenting-with-rootless-docker-416c9ad8c0d6)
* [Building Minimal Docker Containers for Go Applications](https://www.cloudbees.com/blog/building-minimal-docker-containers-for-go-applications/)
* [Minideb comparison to other popular docker images](https://dzone.com/articles/minideb-a-minimalist-debian-based-docker-image)

#### Docker feature
Docker is built on top of runC runtime container and uses daemon

### Docker installation Debian based.
* [install docker from a package](https://docs.docker.com/engine/install/debian/#install-from-a-package)
* [buster docker repository](https://download.docker.com/linux/debian/dists/buster/pool/stable/amd64/)

```

sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
docker run hello-world

dockerd -log info
```



### Windows Container
* https://blog.mdfranz.com/a-windows-container-guide-for-linux-folks-397785f7675e
* [Simple way to Docker on Windows 10 home with WSL 2] (https://hinty.io/ivictbor/simple-way-to-docker-on-windows-10-home-with-wsl-2/)


### Other containercandidates
* https://medium.com/technopanti/docker-vs-podman-c03359fabf77
* https://iximiuz.com/en/posts/journey-from-containerization-to-orchestration-and-beyond/


### Podman
* Redhat market this as the docker replacement
* ability to run rootless
* podman keeps the same commands as docker
* ```podman run -dt -p 8080:8080/tcp -e```


#### Podman dependencies
* Podman uses crun instead of runc. They rewrite crun in C, as runc is written in go.  They expect there is much lower overhead, and it is a lot faster.
* other podman dependencies include buildah for building images. 
