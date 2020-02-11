## Trouble Shooting

* Docker connect permission denied
  * Error msg: `Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post http://%2Fvar%2Frun%2Fdocker.sock/v1.30/images/load?quiet=0: dial unix /var/run/docker.sock: connect: permission denied`
  * Steps:
    * Run `sudo usermod -aG docker <cur_user_name>` to set your user to be part of `docker` group
      * Example cmdL `sudo usermod -aG docker dshu`
    * Logout the desktop (not the terminal), and log back in
    * To test if the user now has access to docker, run this without `sudo`: `$ docker run hello-world`
      * `sudo docker run hello-world` will always run no matter the user has access to docker or not
