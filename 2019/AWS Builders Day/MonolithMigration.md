# Breaking the Monolith: Road to containerisation and Serverless

## Where to start
Analysis of what you have. Applications, servers, baseline performance, dependencies

Find entry points that can be broken down and isolated out. Break down and replace endpoints at a time

### [12 factor application](https://12factor.net/)
 - Codebase
 - Dependencies
 - Config
 - Backing Services 
 - Build, release, run
 - Processes
 - Port Binding
 - Concurrency
 - Disposability
 - Dev/prod parity
 - Logs
 - Admin Processes

Containers can help manage these. AWS Fargate fully manages this.

You no longer have to worry about infrastructure. Fargate and the containers can take care of all of this.

#### Dependencies
Docker can bring along all dependencies with it

#### Config
Store the config in the environment. This allows environment to prescribe how its run

#### Backing services
Break out shared, underlying data stores. Each microservice should use the data store that is most suitable

It moves storage out the container and into it's own service. Treat data stores as the same any other 3rd party service

#### Processes
Don't maintain state in container processes. This allows scaling to be easy and horizontal

#### Concurrency
Scale out via the process model. This massively changes the cost profile, and also allows cost management on a micro level.

Ensure cost tracking happens so you can change technologies and make sure cost is a first class citizen of design

#### Disposability
Ensure containers are small and can start fast. This allows scaling to be quick, and scale down becomes faster as they will be doing less

#### Dev/prod parity
dev, staging and prod should all be as similar as possible. This allows automation to be repeatable and simple in all environments

#### Logs
Treat logs as event streams. Ensure logs can log to `stdout`, and then logging to Cloudwatch becomes easy and managable.

#### Admin tasks
Run admin tasks as one off processes.

### Tools for containers

[tools for services](services.jpg)

Several tools for managing containers, and lots of supporting services, such as databases and queuing technologies