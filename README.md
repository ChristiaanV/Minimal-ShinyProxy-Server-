# Minimal-ShinyProxy-Server
Create a docker network that ShinyProxy will use to communicate with the Shiny containers
```
sudo docker network create sp-example-net
```
## Shiny app image
Move to the App directory and build the dockerfile 
```
sudo docker build -t testapp .
```
This creates an image of the Shiny app which will run in a container

## ShinyProxy image
Move to the Server directory and build the dockerfile
```
sudo docker build -t shinyproxy .
```
This creates an image of the ShinyProxy server that is configured to run the testapp.

## Start the ShinyProxy server
Start up a server with the shinyproxy image on the docker network that you created with
```
sudo docker run -d -v /var/run/docker.sock:/var/run/docker.sock --net sp-example-net -p 8080:8080 shinyproxysudo docker build -t shinyproxy .
```

The ShinyProxy server should now be live! You can find it at 0.0.0.0:8080. The default username and password is user:Jack  password:password
