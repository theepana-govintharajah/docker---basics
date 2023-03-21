FROM node:17-alpine

WORKDIR /app
#Working directory is set to app folder, so from this point onwards path will be considered relative to this

COPY . .
#First dot says from which folder we need to copy the source code, suppose if source code is on the src folder instead of the root folder, then ./src will be there
#Second dot says to which folder we need to copy the images - image folder structure, since working directory is specified to app, all will copy to app folder

RUN npm install
#install all dependencies on package.json on working directory

EXPOSE 4000
# required for docker desktop port mapping

#container - running instance of the image

CMD ["node", "app.js"]




#in hub.docker.com you can check the parent image to pull, example - node:16 -alphine 

#inorder to run docker in terminal, type the below command on terminal
#docker build -t myapp .
#'-t' stands for tag and myapp is name of an image and last dot says relative path for the docker
#docker build -t myapp:v1 .
#v1 means version 1, we can add these kind of tags following image name, so it's easy to create container for specific version of the images

#once the image is made, it become read-only. So if you are changing the source code or adding any dependencies, you have to recreate new image


#docker images -> it's a command inorder to list all the available images

#docker run --name myapp_c2 -p 4000:4000 -d myapp
#-p stands for publish, port number on the right port exposed by the container, left container on our computer

#docker run command run image to create new container while docker start helps to run the already created container

#docker start myapp_c2

#docker ps -> ps stands for processes - shows a list of running containers (containers that are currently running only)

#docker ps -a -> here -a stands for all and list out all the conainers available (no need to run at this current moment)

#docker stop myapp_c1 - To stop myapp_c1 container



#In the above code, we copy the source code and there after we run npm install, so every time when we change the source code, 
#it runs from the step copy, (before steps will be get from cache, so unnecessarily every time npm install is running when we make changes in source code),
#so it's better to run npm install before copying source code, but in order to run npm install, we need to know what are present in package,json file, so code will be change as


#FROM node:17-alpine
#WORKDIR /app
#COPY package.json .
#RUN npm install
#COPY . .


#so first 4 layers can be grabed from cache after initial build



#docker image rm myapp -> rm means remove, so it will remove the image myapp, but if it is using by any containers, we can't delete that image.

#docker image rm myapp -f -> -f means force, so it will delete if it is used by container as well

#docker container rm myapp_c2   -> remove the container
#in order to remove the image, you can use -f tag or you can delete the containers used by that particular image first, thereafter you can delete that image 
#we can delete more than one containers once by giving the name separated by space


#docker system prune -a
#it will remove all the images, containers and volumes



#volumnes 
#allow us to specify folders on host computer that can be mada available for running containers and we can map the folders in host computers to spceific folders inside containers. 
#For example, project folder - API folder (in our case) to the app folder (WORKDIR), so everychange in the API folder moves to app folder automatically, so we can see the changes without recreating new images


#if volumes are changed, servers will not get to know until restarted, so in order to restart servers when changes happenings, we need nodemon which is a node package, 
#we need run nodemon app.js instead of run node app.js, that's what we mentioned in package.json in script tag, so instead of the line 
#CMD ["node", "app.js"]
#I need to use CMD ["npm","run","dev"];
#so it restart the server when it detects the changes, nodemon watching for changes in container, if volume - directory map is not done, then container files will not be changed when source code is changed


#docker run --name myapp_c2 -p 4000:4000 -rm myapp
#rm stands for remove, that means it delete the container when we stop it, no need to store the container afterwards 


#docker run --name myapp_c2 -p 4000:4000 -rm -v /home/theepana/Downloads/Docker YouTube Github/docker-crash-course-lesson-5/api:/app myapp
#-v stands for volume
#Next will be absolute path of API folder - not the relative path - To that we can copy path of one file in API folder and can delete that file name - So it will be absolute path of API folder
#Colon
#after colon folder that needs to be map in the container



#docker run --name myapp_c2 -p 4000:4000 -rm -v /home/theepana/Downloads/Docker YouTube Github/docker-crash-course-lesson-5/api:/app -v /app/node_modules myapp
#if we install node modules locally we need to add another volume to override the mapping, because node_modules should not be mapped, because it could be deleted



#study docker 11 file