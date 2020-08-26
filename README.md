# DevOps-Project1
This is a very simple CI/CD project. It uses a Jenkinsfile took from the official Jenkins website in order to create a simple pipeline.<br/>
In my example I used the Python option that will create a docker container running Python 3.5.1 and when Jenkins will build successfully, it will print the python version<br/>
>https://www.jenkins.io/doc/pipeline/tour/hello-world/
# Setup
I initially created an EC2 instance on AWS running CentOS.
After this I downloaded Jenkins for CentOS(version 2.235.5) - This will be the master Jenkins node.

>`sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo`<br/> 
>`sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key`

In order for Jenkins to work, it needs java also. My EC2 instance didn't have it installed so I had to install it:<br/>
>`sudo yum install java`<br/>
Because my example uses Docker, I had to install that also:<br/>
>`sudo yum install docker`
Since Jenkins will use Git as SCM(Source Control Management), I had to install git on our instance also:<br/>
>`sudo yum install git`


Finally, install Jenkins:<br/>
>`sudo yum install jenkins`
# Done with installation! (almost)
Now you need to start jenkins and docker processes:<br/>
>`sudo systemctl start jenkins`<br/>
>`sudo systemctl start docker`
<br/>
You can check the status of the processes at any time by running<br/>
>`sudo systemctl status docker` or<br/>
>`sudo systemctl status jenkins`
# Building and running the pipeline
In order for Jenkins to build successfully the created task, there are 2 plugins required:<br/>
>`Docker`<br/>
>`Docker Pipeline`<br/>
Both can be very easy installed from Jenkins -> Manage Jenkins -> Manage Plugins (there is an option to install both without needing to restart Jenkins).<br/>
During all this process I encountered a few errors and my builds were failing. Fortunately, the Console Log Output is very useful as it tells you where the error is.<br/>
The last error preventing me to build the project was<br/>
`Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock...`<br/>
After a bit of troubleshooting, I understood that the jenkins service running under the jenkins user couldn't access the docker engine due to permission issues.<br/>
I tried to add the jenkins user to the docker group but still didn't work. 
Finally, I changed the permissions for `docker.sock` file<br/>
sudo chmod 777 docker.sock
Now, I'm aware that this solution is not recommended, but for my testing environment should be ok.
Finally, I'd like to say that it was a small little project but very fun to build actually since allowed me to dig deeper in a few topics like Linux, Jenkins, AWS and understand how they all work together. <br/>
My plan is now to continue learning and build CI/CD pipelines for more difficult projects.
I can see now how I can setup deployment webservers on AWS with auto scaling templates and even load balancing. Also, configuration management tools like Ansible can be very useful.<br/>
I'd like to try running Jenkins on AWS ECS(Docker containers) and dig deeper into Kubernetes. 
