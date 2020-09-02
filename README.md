# DevOps-Project1 - Creating a simple pipeline job 
This is a very simple CI/CD project. It uses a Jenkinsfile took from the official Jenkins website in order to create a simple pipeline.<br/>
In my example I used the Python option that will create a docker container running Python 3.5.1 and when Jenkins will build successfully, it will print the python version.<br/>
>https://www.jenkins.io/doc/pipeline/tour/hello-world/
# Setup
I initially created an EC2 instance on AWS running CentOS.
After this I downloaded Jenkins for CentOS(version 2.235.5) - This will be the master Jenkins node.

>`sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo`<br/> 
>`sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key`

In order for Jenkins to work, it needs java also. My EC2 instance didn't have it installed so I had to install it:<br/>
>`sudo yum install java`<br/>
Because my example uses Docker, I had to install that also:<br/>
>`sudo yum install docker`<br/>
Since Jenkins will use Git as SCM(Source Control Management), I had to install git on our instance:<br/>
>`sudo yum install git`


Finally, install Jenkins:<br/>
>`sudo yum install jenkins`
# Done with installation! (almost)
Now you need to start jenkins and docker processes:<br/>
> `sudo systemctl start jenkins`<br/>
> `sudo systemctl start docker`

You can check the status of the processes at any time by running<br/>
>`sudo systemctl status docker` or<br/> 
>`sudo systemctl status jenkins`

# Building the pipeline
In order for Jenkins to build successfully the created task, there are 2 plugins required:<br/>
>`Docker`<br/>
>`Docker Pipeline`<br/>
Both can be very easy installed from Jenkins -> Manage Jenkins -> Manage Plugins (there is an option to install both without needing to restart Jenkins).<br/>


During all this process I encountered a few errors and my builds were failing. Fortunately, the Console Log Output is very useful as it tells you where the error is.
<br/><br/>
It was a small little project but very fun to build actually since allowed me to dig deeper in a few topics like Linux, Jenkins, AWS and understand how they all work together. <br/>
My plan is now to continue learning and build CI/CD pipelines for more difficult projects.
I can see now how I can setup deployment webservers on AWS with auto scaling templates and even load balancing. Also, configuration management tools like Ansible can be very useful.<br/>
Jenkins master and slave nodes can run on Docker containers and tools like Kubernetes can be used to manage them.<br/>

# And finally we can see the successful build!

![image](https://user-images.githubusercontent.com/24807183/91357211-2dd09380-e7f1-11ea-9b68-7343ad06ff7a.png)
