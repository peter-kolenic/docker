## XL Deploy Docker image

### Installation 
```
docker build -t xldeploy .  
```

### Usage
```
docker run -p 4516:4516 --name xldeploy -v <docker_host_license_file>:/opt/xl-deploy-4.5.1-server/conf/deployit-license.lic xldeploy
```
