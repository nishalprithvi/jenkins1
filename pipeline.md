# Jenkins Pipeline

Making a jenkins pipeline job to build a docker image and then deploy it over another remote server

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

### Building the pipeline and executing it 

you can refer the pipeline from the <b>jenkinsfile</b> added in this repo and then make changes accordingly

### Results
![image](https://github.com/nishalprithvi/jenkins1/assets/80667999/0748914b-1a6b-4412-81a5-c52527dfa9b0)

## Build your Jenkins Pipeline 😊👍

