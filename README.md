Details of setup:

- There are 3 AWS EC2 instances namely users, rides, orchestrator
- In users instance all the users API are there
- In rides instance all the rides API are there
- There is no database read/write API in the above two instances
- In the orchestrator instance we have 6 containers namely orchestrator, rabbitmq, zookeeper, master, slave, shared_db
- The last 3 containers master, slave, shared_db are spawning dynamically from the orchestrator as per they are needed
- In orchestrator container we have the database read/write APIs, rabbitmq client, zookeeper functionality, crash APIs and scale in and out mechanism
- In master container we are performing db write operations
- In slave container we are performing db read operations
- We are using shared_db container and we have mounted a volume code/sdb for making the database persistent

Running the project:

- cd to the RideShare directory
- Just do sudo docker-compose up --build
- It will start the rabbit_mq, zookeeper and orchestrator containers
- Other containers will be started dynamically whenever they are needed