#### Connectin multiple docker containers
- Use Docker CLI's Network Features
- Use Docker Compose

#### Docker Compose
- Docker Compose is a separate CLI tool that gets installed along with Docker.
- It is used to start up multiple Docker containers at the same time and automatically conect them together with some form of networking.
- It automates some of the long-winded arguments we were passing to **docker run**.
- Docker Compose really exists to keep you from having to write out a ton of different repetitive commands with Docker CLI.
- The purpose of Docker Compose is to essentially function as Docker CLI but allow you to kind of issue multiple commands much more quickly.
- `docker run myimage` => `docker-compose up`
- `docker build .` and `docker run myimage` => `docker-compose up --build`
- **We created two separate services and compose automatically made connections between the two available. The real key thing to keep in mind here is that in order to communicate between the two, we used a hostname of the name of that other service or that other container that was created, and that name is specified of our docker-compose file.**
-  **So any time you are making use of maybe some database driver inside of your web application layer anywhere, you would normally put in a connection URL or connection URI, you can instead just list the name of that other container and the host name will be automatically resolved for you by Docker**

#### Stopping Docker Compose Containers
- `docker run -d redis` This will start up a new container, but it executed in the background so we could continue running commands in this terminal window if we wanted to.
- Run `docker ps` to get all of our running containers.
- Stop those containers by `docker stop container_id`.
- Let's imagine that when we start using `docker-compose` and we are working with multiple images or multiple containers at the same time, it would really be a pain to have to run `docker stop` with each different ID for each container we started.
- We can automatically start up multiple containers in the background at the same time and then close them all at the same time with one single command.
	- Launch in backgroud
		- `docker-compose up -d`
	- Stop Containers
		- `docker-compose down`

#### Automatic Container Restarts
##### Exit Status Codes

| Exit Status Codes | Description|
|--|--|
|  0| We exited and everything is OK |
|1,2,3, etc| We exited because something went wrong!|

##### Restart Policies

|Restart Policies| Description|
|--|--|
| "no" (By default Policy)| Never attemt to restart this . container if it stops or crashes  |
|always| If this container stops *for any reason* always attempt to restart it|
|on-failure| Only restart if the container stops with an error code|
|unless-stopped|Always restart unless we (the developers) forcibly stop it|

#### Why would we ever want to use always v/s on-failure?
- You might have a container that you **always, always, always** want to make sure it's running. **Ex. Web Server**. Then use **always** restart policy.
- On other hand, if you are running some type of worker process, like some container that is meant to do some amount of processing on some file and then naturally exit, that would probably be a good use case for the **on-failure** restart policy.
- That's how we get Docker-Compose to automatically maintain our containers.

#### Container status with Docker Compose
- `docker-compose ps` this will print out the status of the containers inside of docker-compose file. But we have to run this command from the same directory where our docker-compose.yml is.
- When we ran `docker-compose ps`, it's going to specifically look for a `docker-compose` file inside of your current directory. And if it finds one, it'll read that file and the it will try to find all of the running containers on your local machine that belongs essentially to this `docker-compose` file.
- *If you try runnig the `docker-compose ps` command from any other directory, you're going to get an error message.*