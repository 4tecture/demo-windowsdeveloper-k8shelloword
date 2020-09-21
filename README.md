# Docker Hello World
This solution and docker container is intended to be used as an introcutionary sample to docker. You learn how to build a docker container and run it. Environment variables provide the ability to change the text which is displayed on the home page.
This repository is also used for the article "ASP.NET Core Microservices in Kubernetes (AKS) betreiben" in the October 2020 issue of Windows Developer. This article describes how to set up an application to deploy it to Kubernetes.

# Building the container
- Build the image based on dockerfile
  - `docker build -t <reponame>:<tag> .`
  - `docker build -t 4tecture/hello-world:v2.1 -t 4tecture/hello-world:latest -f .\HelloWorld\Dockerfile .`
- Verify image
  - `docker images 4tecture/hello-world`
- Publish the image
  - `docker login`
  - `docker push 4tecture/hello-world:v2.1`
  - `docker push 4tecture/hello-world:latest`

# Running the demo
- Visit [https://hub.docker.com](https://hub.docker.com) and search for 4tecture
- Choose `hello-world`
- `docker images`
- `docker run -d -p 8080:80 --name hello-world 4tecture/hello-world`
- `docker images`
- `docker ps`
- Show app in browser, show hostname under about
- `docker stop hello-world` 
- `docker ps`
- `docker ps -a`
- `docker container rm hello-world`
- `docker run -d -p 8080:80 -e Message='Hello dear audience member!' --name hello-world 4tecture/hello-world`

# Showing the docker file system
- `docker ps`
- `docker exec -i -t hello-world /bin/bash`
- `pwd`
- `ls -l`
- `exit`

# Cleanup for demos
- `docker rm -f $(docker ps -a -q)`
- `docker rmi -f $(docker images -q)`
