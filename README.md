# devserver

Serve any site by it's repo name using docker

# Setup Instructions:

- RUN `git clone https://github.com/shahriar1/devserver.git`
- CD into `devserver` and run `docker-compose up -d`
- Go back and CD into `apps` directory
- Clone your repo here.
- Edit `/etc/hosts` and use your repo name to point to `127.0.0.1 REPO_NAME`. e.g. if your reo name is `example-app` then add this `127.0.0.1 example-app`
- `http://REPO_NAME` e.g. `http://example-app`


# USAGE
### CD into `devserver` repo first and then 

- To start the services(php, nginx, mysql, redis) - `docker-compose up -d`

- To execute one time script in any container - **docker-compose exec SERVICE_NAME COMMAND**

  eg. `docker-compose exec php php artisan migrate`

- For running command interactively - **docker-compose exec -it SERVICE_NAME COMMAND** 
 
   eg. `docker-compose exec -it php bash`

