# What I did
I have spent the last 3 days setting up the CI/CD Pipeline for the very site you are on. I have pulled out many hairs setting up.
# Homelab
I run a homelab. I like putting things on servers that I own so I don't have to pay for cloud costs. A side effect of this is that I like to put EVERYTHING on my homelab even if it doesn't belong.

# Madness
I decided the only proper course of action was to set up my own git server using [ForgeJo](https://forgejo.org/) and have it mirror the GitHub repo. When I make a commit, Forgejo would get that commit then run "Forgejo actions" on it. This ended up being a massive rabbit hole that I went on for 2 days before reverting back to GitHub actions like a normal person

# Forging My Brains Out
Step one was to yoink a docker compose file from their documentation
```yaml
version: "3"
networks:
  forgejo:
    external: false
services:
  forgejo:
    image: codeberg.org/forgejo/forgejo:7
    container_name: forgejo
    environment:
      - USER_UID=1000
      - USER_GID=1000
    restart: always
    networks:
      - forgejo
    volumes:
      - ./forgejo:/home/shlok/forgejo
      - /etc/timezone:/etc/timezone:ro
      - /etc/localtime:/etc/localtime:ro
    ports:
      - 30000:3000
      - 22200:22
```
It was late so I did end up messing up the volumes section but that's besides the point. It worked and I got to see a familiar dashboard that I promptly mirrored my repo over to. 
 
We are almost done🥳 next is setting up the runner that would execute my actions. I created another docker compose file and set up the ForgeJo runner in no time. 
 
So the plan was simple, commit on GitHub -> commit on ForgeJo -> action to build container -> push to ForgeJo registry -> Deploy -> profit! 

Unfortunately ForgeJo had other plans. I wrote up a simple GitHub actions file and I committed it and got so many errors. The main one that I still haven't been able to fix is `Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?` 

I'm pretty sure that this error is caused by the way that ForgeJo actions actually run. The action first starts and calls the runner. The runner then tells a docker-in-docker API to create a container to the configs specifications. Code is ran in those containers and if all goes well the action will have succeeded. This works for almost everything except for when you need to containerize something as you need the docker socket. The container that docker-in-docker spins up is not part of the docker network and cannot call the docker-in-docker API. This means that I cannot gain access to docker build tools using that strategy. I would have to make another VM and run all the CI stuff in the VM which is just too much work to set up for me.

# Leeroyyyy Jenkins
I also tried out [Jenkins](https://www.jenkins.io/) as a part of the ci/cd troubles but also ran into the same issue where it was much more work then it was worth.

# Microsoft saves me :/
I decided that I would just use GitHub actions for now and ill deal with this later. GitHub/Microsoft really does not get the credit they deserve for creating such a seamless CI/CD pipeline. My site isn't too complicated so It doesn't need any unit tests or anything, but I'm sure that If I did need them in the future, GitHub actions wouldn't let me down. This is a fail on my end, but this is not over! I will eventually figure this out and then I will have the last laugh over Microsoft.