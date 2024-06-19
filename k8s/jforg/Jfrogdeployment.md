### Create a Jfrog repository account to store the praivate Docker images

https://jfrog.com/artifactory/?utm_source=google&utm_medium=cpc&utm_campaign=Search|DSK|Brand|IN|202308&utm_term=jfrog%20free%20trial&gads_network=g&cq_plac=&cq_plt=gp&utm_content=u-bin&gads_campaign_id=20437321111&gads_adgroup_id=157827667091&gads_extension_id=23305458432&gads_target_id=kwd-1598615738072&gads_matchtype=b&gad_source=1&gclid=CjwKCAjwg8qzBhAoEiwAWagLrICHLwKcramNRAQIa5CVel6vzizSjPGaupvwjmwcp4u4uuePgs-ndxoCtrcQAvD_BwE
![alt text](image-19.png)
![alt text](image.png)
* Give the nesseary values
* After the page like this
 ![alt text](image-1.png)
 ![alt text](image-2.png)
 ![alt text](image-3.png)
 ![alt text](image-4.png)
 * Now the page hows like this after click on continue
 ![alt text](image-5.png)
 * Now click on usermenu and Edit profile
 ![alt text](image-6.png)
 ![alt text](image-7.png)
* Now Generate an identity Token 
![alt text](image-8.png)
* Its shows onetime only now Copy the Necessary details 
![alt text](image-9.png)
* Connect the docker machine and seach for docker images
![alt text](image-10.png)
* Pull the docker images from docker hub or create your own docker images 
![alt text](image-11.png)
![alt text](image-12.png)
![alt text](image-13.png)
* Login to the docker machine using the command 
```bash
docker login <account name>
docker login krishna0527.jfrog.io
```
username: krishna315283@gmail.com
password: paste the reference token 
![alt text](image-14.png)
* Tag the docker image using the command 
```bash
docker image tag <imagename> <Reponame>
# in my case 
docker image tag nginx:latest krishna0527.jfrog.io/gopi-docker/nginx:1.0
```
* Push the docker image to Repository
```bash
# docker push < image name >
docker push krishna0527.jfrog.io/gopi-docker/nginx:1.0
```
![alt text](image-15.png)
* Check the Jfrog Repository 
![alt text](image-16.png)
* Click on the scanned 
![alt text](image-17.png)
![alt text](image-18.png)



