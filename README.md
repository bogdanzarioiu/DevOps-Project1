# DevOps-Project1
This is a very simple CI/CD project. It uses a Jenkinsfile took from the official Jenkins website in order to create a simple pipeline.<br/>
In my example I used the Python option that will create a docker container running Python 3.5.1 and when Jenkins will build successfully, it will print the python version<br/>
https://www.jenkins.io/doc/pipeline/tour/hello-world/
# Setup
I initially created an EC2 instance on AWS running CentOS.
After this I downloaded Jenkins for CentOS(version 2.235.5) - This will be the master Jenkins node.

`sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo`<br/>
`sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key`

In order for Jenkins to work, it needs java also. My EC2 instance didn't have it installed so I had to install it:<br/>
`sudo yum install java`<br/>
Because my example uses Docker, I had to install that also:<br/>
`sudo yum install docker`
Since Jenkins will use Git as SCM(Source Control Management), I had to install git on our instance also:<br/>
`sudo yum install git`


Finally, install Jenkins:<br/>
`sudo yum install jenkins`
# Done with installation! (almost)
Now you need to start jenkins and docker processes:<br/>
`sudo systemctl start jenkins`<br/>
`sudo systemctl start docker`
<br/>
You can check the status of the processes at any time by running<br/>
`sudo systemctl status docker` or `sudo systemctl status jenkins`
# Building and running the pipeline(to be added very soon)
