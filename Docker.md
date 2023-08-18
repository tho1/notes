
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

### Docker troubleshoot
* https://stackoverflow.com/questions/44942790/docker-error-failed-to-register-layer-symlink
* https://stackoverflow.com/questions/35325103/docker-error-when-pulling-java-8-image-failed-to-register-layer/35325477#35325477

### Windows Container
* https://blog.mdfranz.com/a-windows-container-guide-for-linux-folks-397785f7675e
* [Simple way to Docker on Windows 10 home with WSL 2] (https://hinty.io/ivictbor/simple-way-to-docker-on-windows-10-home-with-wsl-2/)


### Other containercandidates
* https://medium.com/technopanti/docker-vs-podman-c03359fabf77
* https://iximiuz.com/en/posts/journey-from-containerization-to-orchestration-and-beyond/

### building 
```
package main
import (
    "fmt"
    "io/ioutil"
    "net/http"
    "os"
)
func main() {
    resp, err := http.Get("https://google.com")
    check(err)
    body, err := ioutil.ReadAll(resp.Body)
    check(err)
    fmt.Println(len(body))
}
func check(err error) {
    if err != nil {
        fmt.Println(err)
        os.Exit(1)
    }
}


FROM golang:onbuild
FROM golang:latest
RUN mkdir /app
ADD . /app/
WORKDIR /app
RUN go build -o main .
CMD ["/app/main"]

go build -o main .
docker build -t example-scratch -f Dockerfile.scratch .


Dockerfile.scratch
FROM scratch
ADD main /
CMD ["/main"]

CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o main .


update 

FROM scratch
ADD ca-certificates.crt /etc/ssl/certs/
ADD main /
CMD ["/main"]
```

* https://www.cloudbees.com/blog/building-minimal-docker-containers-for-go-applications make small Go app!


### Podman
* Redhat market this as the docker replacement
* ability to run rootless
* podman keeps the same commands as docker
* ```podman run -dt -p 8080:8080/tcp -e```
* https://github.com/boot2podman/boot2podman/blob/master/custom_kernel.md  using tc linux as a base.  see other md files for information.


#### Podman dependencies
* Podman uses crun instead of runc. They rewrite crun in C, as runc is written in go.  They expect there is much lower overhead, and it is a lot faster.
* other podman dependencies include buildah for building images. 
