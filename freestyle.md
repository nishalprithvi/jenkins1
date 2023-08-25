# Jenkins Freestyle

Making a jenkins freestyle job to build a dockerfile and then deploy it over another remote server

#### Repo used here 
- https://github.com/nishalprithvi/django-todo-cicd.git

### Installing plugins

before get started with the freestyle job make sure to install following two required plugins - 
Git and Publish over SSH
Post installing both the plugins, setup over remote server by going in   <b> Manage Jenkins > Settings > Publish Over SSH </b>

#### Adding remote server

adding access details for remote server
![image](https://github.com/nishalprithvi/jenkins1/assets/80667999/350493b0-86d5-4400-90bb-12363ee2731b)

adding remote server
![image](https://github.com/nishalprithvi/jenkins1/assets/80667999/1e426de3-ffe0-43ca-a408-e6dbc8b62f8f)

### Configuring the freestyle pipeline

#### * Make either to add the jenkins user in docker group to use docker commands or if you are using cloud servers then use sudo to execute the docker commands

#### Build stage commands 

```bash
$ docker build -t django-todo .
$ echo Logging in to Docker Hub...
$ echo "******************" | docker login -u "*******" --password-stdin
$ echo creating tags for image
$ timestamp=$(date +'%Y%m%d_%H%M%S')
$ export REPOSITORY_URI=nishalprithvi/demo_django_img  # Replace with your Docker Hub image repository
$ export IMAGE_TAG=$timestamp  # Use the timestamp as the image tag
$ echo pushing image to docker registry
$ docker tag django-todo "$REPOSITORY_URI:$IMAGE_TAG"
$ docker tag django-todo "$REPOSITORY_URI:latest"  # Tagging as "latest"
$ docker push "$REPOSITORY_URI:$IMAGE_TAG"
$ docker push "$REPOSITORY_URI:latest"  # Pushing the "latest" tagged image
```

![image](https://github.com/nishalprithvi/jenkins1/assets/80667999/46373c55-1751-46aa-a8f3-329ef7d37b3c)

#### Commands for executing in remote server (Publish over SSH)

```bash
$ echo Hi from home ubuntu
$ echo Logging in to Docker Hub...
$ echo "*********************" | docker login -u "*********" --password-stdin
$ echo pulling image from dockerhub registry
$ export REPOSITORY_URI=nishalprithvi/demo_django_img
$ sudo docker pull "$REPOSITORY_URI:latest"
$ echo running image
$ sudo docker run -d -p 8000:8000 "$REPOSITORY_URI:latest"
```

![image](https://github.com/nishalprithvi/jenkins1/assets/80667999/99f7b83a-64c9-4173-883c-5287a3eeca0a)

## Proceed to build your jenkins job now !!! 😊👍
