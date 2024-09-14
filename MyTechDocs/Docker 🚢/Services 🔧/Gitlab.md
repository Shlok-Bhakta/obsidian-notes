A git server that I host myself :)
[docs](https://docs.gitlab.com/ee/install/docker.html)

# [[Docker Compose]] 

```yml
# docker-compose.yml
version: '3.7'
services:
  web:
    image: 'gitlab/gitlab-ce:latest'
    restart: always
    hostname: 'localhost'
    container_name: gitlab-ce
    environment:
      GITLAB_OMNIBUS_CONFIG: |
        external_url 'http://localhost'
    ports:
      - '8080:80'
      - '8443:443'
    volumes:
      - '/home/shlok/gitlabConf/config:/etc/gitlab'
      - '/home/shlok/gitlabConf/logs:/var/log/gitlab'
      - '/home/shlok/gitlabConf/data:/var/opt/gitlab'
    networks:
      - gitlab
  gitlab-runner:
    image: gitlab/gitlab-runner:alpine
    container_name: gitlab-runner    
    restart: always
    depends_on:
      - web
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - '/home/shlok/gitlabConf/gitlab-runner:/etc/gitlab-runner'
    networks:
      - gitlab

networks:
  gitlab:
    name: gitlab-network
```

Root Login 

Username: root
password:
```bash
grep 'Password:' /etc/gitlab/initial_root_password
```
