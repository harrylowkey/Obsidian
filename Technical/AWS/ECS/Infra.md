![[ECS diagram.png]]

# ECS vs EC2

ECS is a manager while EC2 instances are just like employees. All the employees (EC2) under this manager(ECS) can perform "Docker" tasks and the manager also understands "docker" pretty well. So, whenever you need "docker" resources, you show up to the Manager. Manager already has status from every employee(EC2) decides which one should perform the task.


- **`EC2`** - is simply a remote (virtual) machine.
- **`ECS`** stands for **`Elastic Container Service`** - as per basic definition of [computer cluster](https://en.wikipedia.org/wiki/Computer_cluster), **`ECS` is basically a logical grouping of `EC2` machines/instances**. Technically speaking `ECS` is a mere configuration for an efficient use and management of your `EC2` instance(s) resources i.e. storage, memory, CPU, etc.


The next confusing thing here is the **container** term - which is not fully virtualized machine instances, and **Docker** is one technology we can use to create container instances. `Docker` is a utility you can install on our machine, which makes it a `Docker` host, and on this host you can create containers (same as virtual machines - but much more light-weight). To sum up, **`ECS` is just about clustering of EC2 instances, and uses `Docker` to instantiate containers/instances/virtual machines on these (`EC2`) hosts**.

All you need to do is launch an `ECS`, and register/add as much `EC2` instances to it as you need. You can add/register EC2 instances, all you need is Amazon ECS Container Agent running on your EC2 instance/machine, which can be done manually or directly using the special AMI (Amazon Machine Image) i.e. Amazon ECS-optimized AMI, which already has the Amazon ECS Container Agent. During the launch of a new EC2 instance the Agent automatically registers it to the default ECS cluster.

The **container agent** running on each of the instances (`EC2` instances) within an `Amazon ECS` cluster sends information about the instance's current running tasks and resource utilization to Amazon ECS, and starts and stops tasks whenever it receives a request from Amazon ECS. For more information, see [Amazon ECS Container Agent](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_agent.html). Once set, each of the created container instances (of whatever `EC2` machine/node) will be an instance in `Amazon ECS`'s swarm.


# Task vs Service in ECS

## Task Definition

This is the blueprint describing which Docker containers to run and represents your application. It includes several tasks.

![[Task Definition.png]]

## Service

An instance of Task Definition. It also defines the minimum and maximum Tasks from one Task Definition run at any given time, autoscaling, and load balancing.

## ECS Container Instances

- They are EC2 instances that has Docker and ECS Container Agent running on it

## Relationship

![[ECS Cluster.png]]