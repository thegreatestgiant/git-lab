# Git-Lab
### How To Set Up Your Own Temporary GitLab Instance
1. Make a docker hub account and log into [pwd](https://labs.play-with-docker.com/).
2. Create a new 4 hour session and a new instance
3. I reccomend opening the terminal in your own now using the ssh they give you
4. Run this command
```
  docker run --detach \
  --publish 1443:443 --publish 8080:80 --publish 1001:22 \
  --name gitlab \
  --restart always \
  --volume gitlab_config:/etc/gitlab \
  --volume gitlab_logs:/var/log/gitlab \
  --volume gitlab_data:/var/opt/gitlab \
  --shm-size 2gb \
  gitlab/gitlab-ce:latest
  ```
  5. Once that's done wait around 10 minutes checking the 8080 port up top until you can log in or you can run this script to see the logs
  ```
  docker logs -f gitlab
  ```
  6. The UserName is `root` and you can get the password by running 
  ```
  docker exec -it gitlab grep 'Password:' /etc/gitlab/initial_root_password
  ```
