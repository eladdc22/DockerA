# Docker module
Local Registry

---

## Preparations
```
docker pull registry:2
docker pull ubuntu:22.04
```

## Instructions

 - Run the following containers using dockerhub images:
```
docker run -d -p 5000:5000 --restart=always --name registry registry:2
```

 - Please validate that your ontainers are running successfully:
```
docker ps
```

 - Lets tag and push to our local registry:
 
```
docker tag ubuntu:22.04 localhost:5000/my-ubuntu
docker push localhost:5000/my-ubuntu
```

 - Lets clear the image lacal cach :
```
docker image remove ubuntu:22.04
docker image remove localhost:5000/my-ubuntu
```

 - Pull image from local registry :
```
docker pull localhost:5000/my-ubuntu
```

 - Lets see what we have in our registry :
```
curl -X GET http://localhost:5000/v2/_catalog
curl -X GET http://localhost:5000/v2/my-ubuntu/tags/list
```