Ghost Blog Dockerfile
=====================

Dockerfile to build a Docker image of the Ghost blogging platform

## Deploy from index

Get the image by running:
`sudo docker pull thejf/ghost`

This image has a custom config which requires a number of environment variables to tailor it to your needs. [This is the config it uses](https://gist.github.com/TheJF/6979674). The required environment variables are:
`GHOST_HTTP_URL`, `MAIL_FROMADDRESS`, `MAIL_SERVICE`, `MAIL_USERNAME`, `MAIL_PASSWORD`

These must be configured as part of the run command. If you wanted to run a Ghost container as a daemon, you would type:
`sudo docker run -e GHOST_HTTP_URL=http://your_own_url.com -e MAIL_FROMADDRESS=ghost@your_own_url.com -e MAIL_SERVICE=your_mail_service -e MAIL_USERNAME=your_username -e MAIL_PASSWORD=your_password -d thejf/ghost npm start`

To see which port Docker has assigned to your Ghost container, run:
`sudo docker ps`

## Roll your own image

To build your own image, run `sudo docker build -t <image_name> .` in the directory with the Dockerfile after cloning this.

## License

Public domain. It's a Dockerfile, do whatever you want with it.


