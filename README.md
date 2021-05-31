# Docker

**Docker Commands:**

- Spin up a container:
    - Read more: [https://stackoverflow.com/questions/33715499/what-is-the-difference-between-docker-compose-up-and-docker-compose-start](https://stackoverflow.com/questions/33715499/what-is-the-difference-between-docker-compose-up-and-docker-compose-start)
    - Running `docker-compose up -d` starts the containers in the background and leaves them running.

```jsx
docker-compose up
```

- To bash into a container:

```jsx
docker exec -it <container-name> bash
```

- To force a container to keep spinning, add this to your docker yaml file:

```jsx
command: tail -f/dev/null
```

- Keep a container going, bash into the container and run make to see the logs of spinning it up. make is the command for docker to run:
```jsx
make
```

- Run an instance of the nginx application on the Docker host

```jsx
docker run nginx
```

- List all running containers:

```jsx
docker ps
```

- List **all** containers (inc previously stopped):

```jsx
docker ps -a
```

- Stop a container:

```jsx
docker stop <insert-name>
```

- Remove a container:

```jsx
docker rm <insert-name>
```

- List images:

```jsx
docker images
```

- Remove an image (note: must have all containers deleted first):

```jsx
docker rmi nginx
```

- Download an image (pulls the image and doesn't run the container):

```jsx
docker pull nginx
```

- Execute a command on a running container (name and path are examples):

```jsx
docker exec distracted_mcclintock cat /etc/hosts
```

- Run - attach and detach (both apps are examples):
    - Foreground:

    ```jsx
    docker run kodekloud/simple-webapp
    ```

    - Background:

    ```jsx
    docker run -d kodekloud/simple-webapp
    ```

    - If you'd like to attach back to the running container (example id):

    ```jsx
    docker attach a043d
    ```

- Kill all running containers with:

```jsx
docker kill $(docker ps -q)
```

- Delete all stopped containers with:

```jsx
docker rm $(docker ps -a -q)
```

- Delete all images with:

```jsx
docker rmi $(docker images -q)
```

- Run a container using a specific version of a service using a tag:

```jsx
docker run redis:4.0
```

- Port mapping - set a port for your container that can be accessed from the outside world (ports and app are examples):

```jsx
docker run -p 80:5000 kodekloud/simple-webapp
```

![Docker%207b30269e678e48f89cf145c8ebbdf9a7/Screen_Shot_2021-03-25_at_2.16.45_PM.png](Docker%207b30269e678e48f89cf145c8ebbdf9a7/Screen_Shot_2021-03-25_at_2.16.45_PM.png)

- This way, you can run multiple instances of your application and map them to different ports on the docker host or run instances of different applications on different ports:

    ![Docker%207b30269e678e48f89cf145c8ebbdf9a7/Screen_Shot_2021-03-25_at_2.19.26_PM.png](Docker%207b30269e678e48f89cf145c8ebbdf9a7/Screen_Shot_2021-03-25_at_2.19.26_PM.png)

- Persist data outside of a container:

    ![Docker%207b30269e678e48f89cf145c8ebbdf9a7/Screen_Shot_2021-03-25_at_2.22.35_PM.png](Docker%207b30269e678e48f89cf145c8ebbdf9a7/Screen_Shot_2021-03-25_at_2.22.35_PM.png)

```jsx
docker run -b /opt/datadir:/var/lib/mysql mysql
```

- Inspect a container:

```jsx
docker install <insert-name>
```

- View container logs:

```jsx
docker logs <insert-name>
```

- View container details:

```jsx
docker inspect <insert-name>
```

- Set an environment variable within the container (env variable and app name are examples):

```jsx
docker run -e APP_COLOR=blue simple-webapp-color
```

- To start a program within a container:

```jsx
CMD ["<insert-name>"]
```

- If you run into errors, you can try pruning all your docker volumes and dangling containers:

```jsx
docker system prune 
```

and:

```jsx
docker volume prune
```

Extremely useful docker commands: [https://www.codenotary.com/blog/extremely-useful-docker-commands/](https://www.codenotary.com/blog/extremely-useful-docker-commands/)

For more, see the docs: [https://docs.docker.com/](https://docs.docker.com/)
