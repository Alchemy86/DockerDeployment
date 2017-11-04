# DockerDeployment
Working example docker scripts for both creating a private, local repository for docker images. Also includes teamcity/ agent setup and examples for application building and deploying in docker images.

#### <i class="icon-upload"></i> Create a local repository
Using the docker-compose.yml file in the main working directory of the project, you can create and deploy the repo.

```
docker-compose up -d
```

You should then be able to hit http://localhost:5000/v2/_catalog 

> **Note:** You MUST add this unsecure repo to the docker daemon (localhost:5000) - which will then restart docker.

To push to the repo, choose an image and tag it:
E.g: 
image : aspnetcore/generator
Repo: 172.27.75.90:5000
Tag: multi

```
docker tag aspnetcore/generator:multi 172.27.75.90:5000/aspnetcore/generator:multi
```
```
docker images -ls
```

You will see this ref the same image as its previous one.
Final step is the push:

```
docker push 172.27.75.90:5000/aspnetcore/generator:multi
```

This will then push to the repo of all is well and will be shown as an available resource.
  
