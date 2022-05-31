# Docker Compose With Multiple Local Containers

* We created two separate services and compose automatically made connections between the two available. The real key thing to keep in mind here is that in order to communicate between the two, we used a hostname of the name of that other service or that other container that was created, and that name is specified of our docker-compose file.

* Build docker image
    * `docker build .`
* Build docker image with tag name
    * `docker build -t akshaypawar10/visits:latest .`
* Run 
    * `docker run redis`
* Run docker my Node image along side with redis image
    * `docker run akshaypawar10/visits`
* Create docker-compose.yml start up run multiple containers at same time
    * `docker run myimage` => `docker-compose up`
    * `docker build .` and `docker run myimage` => `docker-compose up --build`
* Start up a new container, but it executed in the background
    * `docker run -d redis`
* To get container id
    * `docker ps`
* To get container status with docker compose
    * `docker-compose ps`
* Stop those containers by 
    * `docker stop container_id`
* Start up multiple containers in the background
   * `docker-compose up -d`
* Stop multiple containers
    * `docker-compose down`
* Port mapping
    * `docker run -p 8080 : 8080 <image_id / image_name>`
* Run shell inside container
    * `docker run -it <your-docker-id>/<project-name> sh`
* Run shell using exec
    * `docker exec -it <container-id> sh`