---
title: Getting up and running with Docker
layout: tech
---
We decided to look into leveraging [Docker](https://docker.com) for deploying some of our applications rather than our current [virtualisation]({% link _notes/tech/virtualisation.md %}) approach.

Seeing that Docker was already available in [Homebrew](https://brew.sh) I ran the install commands ... and got nothing immediately usable :(

I had a quick dig around and saw that there was a few packages in Homebrew, so I installed a couple, but I couldn't get it to work in the 15 minutes I threw at it. The Brew approach would work and be preferred, but I was under time pressue.

So off to Docker to try their app... download, install, done.

Now to do something useful with it.

I tested the setup with the classic:

    docker run -d -p 8081:80 --name webserver nginx

and after docker did its local then remote discovery and downloaded the image it fired up. So running

    docker ps

gave me the output expected

    CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                           NAMES
    731eb2027376        nginx               "nginx -g 'daemon ..."   6 seconds ago       Up 4 seconds        443/tcp, 0.0.0.0:8081->80/tcp   webserver

So now on to Dockerfy one of our [Ruby on Rails](https://rubyonrails.org) apps.

One approach is to create the initial image and then 'get into' it like a virtual machine, install what is required and then save that resulting image. We wanted to go all in and have Docker build the whole thing from scratch, unattended as such.

So we created a Dockerfile (similar to a Makefile) which outlined our build process

running

    docker build -t eastern/ugboot .

kicks off the build. Once done we can lauch the image with

    docker run -i --rm -p 3100:3000 -v /Users/redmeades/Documents/projects/ugboot/code/ugboot/public:/ugboot/public/ ugboot

we then need to get into the app and set one thing up

    docker exec -it 664555f12801 bash
    rake assets:precompile

here we are running the bash shell inside the app server identified by the 6645... hash


sudo vi /usr/local/etc/nginx/servers/ugboot.rohan 
docker inspect 2de21269c942


### next steps

we might leverage the images at <https://github.com/docker-library/ruby>

this woule help to specify the ruby version to be the same as our rbenv one


work through <https://blog.codeship.com/running-rails-development-environment-docker/>
and <https://www.datawire.io/not-engineer-running-3-5gb-docker-images/>
and <https://blog.jessfraz.com/post/docker-containers-on-the-desktop/>
and compose <https://docs.docker.com/compose/install/>

### notes

* getting started <https://docs.docker.com/get-started/part2/>
bi-directional copying between host and container <http://stackoverflow.com/questions/22049212/docker-copy-file-from-container-to-host?rq=1> and <http://stackoverflow.com/questions/22907231/copying-files-from-host-to-docker-container?rq=1> and <http://stackoverflow.com/questions/23405689/accessing-a-docker-containers-file-system-through-terminal>
* reference documentation <https://docs.docker.com/engine/reference/builder/>
* best practices <https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/>
* understanding images and containers <http://stackoverflow.com/questions/30047813/docker-rmi-unable-to-remove-images>
* and another explanation of images and containers <http://stackoverflow.com/questions/23735149/docker-image-vs-container>
* ruby base images <https://hub.docker.com/_/ruby/>
* deprecated rails base image (see above) <https://hub.docker.com/_/rails/>
* discussion of a cut-down image to base off <https://news.ycombinator.com/item?id=10782897>
