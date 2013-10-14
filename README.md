Ghost Blog Dockerfile
=====================

Dockerfile to build a Docker image of the Ghost blogging platform

## Deploy from index

Get the image by running:
`sudo docker pull thejf/ghost`

This image has a custom config which requires a number of environment variables to tailor it to your needs. [This is the config it uses](https://gist.github.com/TheJF/6979674). The required environment variables are:
`GHOST_HTTP_URL`, `MAIL_FROMADDRESS`, `MAIL_SERVICE`, `MAIL_USERNAME`, `MAIL_PASSWORD`

It also requires a place to store the database outside the container, as storage inside Docker containers is not persistent. We can do this by creating a `ghost-data` directory somewhere on the server.

`mkdir ghost-data`

These must be configured as part of the run command. If you wanted to run a Ghost container as a daemon, you would type this in the directory below `ghost-data`:
`sudo docker run -e GHOST_HTTP_URL=http://your_own_url.com -e MAIL_FROMADDRESS=ghost@your_own_url.com -e MAIL_SERVICE=your_mail_service -e MAIL_USERNAME=your_username -e MAIL_PASSWORD=your_password -p 2368:2368 -v `pwd`/ghost-data:/content/data -d thejf/ghost npm start`

If you wanted to run this in production mode as opposed to development mode, you need to add `-e NODE_ENV=production` to the run command.

Now point your browser to your `http://your_own_url.com:2368` and magic.

## Roll your own image

To build your own image, run `sudo docker build -t <image_name> .` in the directory with the Dockerfile after cloning this.

## License

Public domain. It's a Dockerfile, do whatever you want with it.


