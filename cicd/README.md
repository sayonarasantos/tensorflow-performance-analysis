# Jenkins configuration (Infra config - 2st step)

Files for configuring Jenkins server and pipelines.

## Configure Jenkins server

1. Clone this repository:

```sh
git clone https://github.com/sayonarasantos/tensorflow-performance-analysis.git
```

2. Build Jenkins Docker image and run the container:

```sh
cd cicd/jenkins-server
docker-compose up -d --build
```

3. Get the admin password:

```sh
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

4. And access the UI in http://<jenkins_ip>:8080.


## Create pipeline items

1. Create a new Jenkins item of type pipeline;

2. Copy the script from a Jenkinsfile in the 'cicd/pipeline' folder and paste it into the item.

Now you can run the pipeline.


## References

- https://www.jenkins.io/doc/book/installing/docker/#downloading-and-running-jenkins-in-docker

- https://devopscube.com/run-docker-in-docker/

- https://github.com/sayonarasantos/jenkins-lab