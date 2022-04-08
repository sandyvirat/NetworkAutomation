# NetworkAutomation
In this assignment, you are to implement a simple web service. The service is really simple, and the content is shown below.
So the basic service is an Nginx web server, that only serves one simple PHP page. That page renders the hostname, IP, and port of the server running it. 

 However, we expect our service to be a massive hit with our intended customers, so we cannot just run one web server. 
We need to run multiple web servers. Initially, we want to have three Nginx servers running on three different platforms. 
To make access simple, we want HAproxy to load balance between these three servers. 
The site consists of 5 hosts; HAproxy, A, B, C, Bastion, and an internal site-local network.
HAproxy is the host that runs HAproxy and acts as an entry point for accessing the service. 
A, B, and C are the three web servers. These are only to use private addresses from the site-local network. 
The last host, Bastion, is acting as an SSH entry point to the internal network. 
I.e. if you connect to Bastion, you can ssh to all of the other hosts within the site-local network. 

Your task is as follows; 
Write an ansible-playbook, site.yaml, that deploys the HAproxy, and Nginx on appropriate existing hosts, 
i.e. the playbook does not need to launch any Virtual Machines. Once the hosts have been configured, the 

The playbook is assumed to run -outside- the site, but -via- the Bastion host. 
Hence, you need to have an SSH config file that allows your host to use the Bastion host as a jump host, using an SSH key. 
Furthermore, the Bastion host also needs to have SSH access to all of the site-local hosts, using SSH keys, to avoid typing passwords all the time. 
The playbook should also do a rudimentary function test of the deployed application. 
That test is to send three requests to the public IP associated with HAproxy, and verify that all three hosts A, B, and C answers. 
