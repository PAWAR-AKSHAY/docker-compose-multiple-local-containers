# Simple Node app with Docker

* Build docker image
    * `docker build .`
* Build docker image with tag name
    * `docker build -t <your-docker-id>/<project-name> .` 
* Run 
    * `docker run <your-docker-id>/<project-name>`
* Port mapping
    * `docker run -p 8080 : 8080 <image_id / image_name>`
* Run shell inside container
    * `docker run -it <your-docker-id>/<project-name> sh`
* To get container id
    * `docker ps`
* Run shell using exec
    * `docker exec -it <container-id> sh`