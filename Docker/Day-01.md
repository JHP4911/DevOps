<div align="center">
  <h1> Introduction to Docker </h1>
</div>

## Issues Before Containerization

### Problems with different hardware boxes:

👉 Have to maintain them.
👉 Need more space.
👉 Need seperate network.
👉 Need seperate opertaing system.
👉 High cost.

### Problems with Hypervisor: 

In this, we use a single high processing hardware box and install the hypervisor on top of that. Then we create multiple virtual machines on top of that hypervisor.we were able to solve the wastage issue.But still there are some drawbacks.

👉 Cost is high(includes operating system costs, license cost, maintenance and updations)
👉 Wastage of time (We need to create other virtual machines and other operating systems if we need other webservers. So it will take some time for the bootup process in Virtual machines).



## What is a Container?

Containers are software that wrap up all the parts of a code, all its dependencies, libraries and other binaries, and configuration files needed to run it, into a single deployable unit that can be used on different systems and servers.


## Virtual Machines(VM) vs Container 

<b>
<table><tr><td valign="top" width="50%">
  
### [Virtual Machines(VM)]
  
  VM is piece of software that allows you to install other software inside of it so you basically control it virtually as opposed to installing the software directly on the computer.
  
  Applications running on VM system can run different OS.
  
  VM size is very large.
  
  VM takes minutes to run, due to large size.
  
  VM uses a lot of system memory.
  
</td><td valign="top" width="50%"> 
  
### [Containers]
  
  container is a software that allows different functionalities of an application independently.
  
  While applications running in a container environment share a single OS.
  
  Size of container is very light; i.e. a few megabytes.
  
  Containers take a few seconds to run.
  
  Containers require very less memory.
  
</td></tr></table> </b>

### Architecture of Virtual Machine and Container
![containers-vs-virtual-machines](../images/containers-vs-virtual-machines.jpg)
  
  
 ## What is a docker?

Docker is an open source platform for building, deploying, and managing containerized applications.

## why Docker?

👉 It is Simple.
👉 It is Fast.
👉 Easy collaboration.
  
  

