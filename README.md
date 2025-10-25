# jenkins-guide
jenkins SDLC in detail
-----------------------------------------------------

JENKINS - CI/CD
 
Code Commit
   |                          ]   - Agile dev
Build
   |                        
integrate
   |                  |   > CI
Test
   |                             
Release
   |                             |  > CD(delivery)
Deploy
   |                                          |   > CD
Operate

SDLC :
-------------------------------------------------------------
Continous Integration:

It is the frequent, automatic integration of code, All new and modified code is automatically tested with master code.

Continous Delivery:

It is the extension of CI. it ensures that the Code is alway ready to be deployed, although manual approval is required to actually deploy the Software to production.

Continous deployment:

Automatically deploy all validated changes to production. 
Frequent feedback enables issues to be found and fixed quickly.

Why we need CI/CD?
-------------------------------------------------------

→ Detect bugs and problems in early stages of SDLC

→ Save Cost and efforts

→ Improves Co-ordination between teams, implement innovative ideas .

→Faster release to production system.

→ Automated testing helps deliver a top-notch quality product.

 → Minimum human intervention, hence less chances of manual error.

 CONTINOUS INTEGRATION
-----------------------------------------------------------------------

Build

→  Jenkins triggers a build with the help of webhooks Using tools maven, gradle, npm.

Test

→ It triggers test Cases Using tools such as selenium, Junit then it generates report test cases to developers and stake holders.
It will be uploaded in a repository for achieving and analytical purpose.

Scan

→ If the test cases passed build will be Scanned for vulnerability and Static Code analysis Using tools Blackduck , SonarQube.

Upload

→Once the previous stages are successful it will upload the build to build repository such as nexus, jfrog artifactory

CONTINOUS DELIVERY/DEPLOYMENT
-----------------------------------------------------------------------

Dev

→Then the build is transferred to lower environments ,Such as Dev for the deployment using tools. Such as Ansible, Helm for K8's related deployments

UAT

→Once it is approved and tested in dev it would then deploy in pre-production UAT environment.

Production 

→ Once it is approved  testing in UAT, then it is ready for deployment in production.

Jenkins Installation Script :-
-----------------------------------------------------------------------

#!/bin/bash

sudo yum update -y

sudo wget -0/etc/yum.repos.d/jenkins.repo \

https://pkg.jenkins.io/redhat-stable/jenkins.repo

sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key

sudo yum upgrade

sudo dnf install java-17-amazon-corretto-y

sudo yum install jenkins -y

sudo systemctl start jenkins

sudo systemctl enable jenkins

Login to Jenkins using the below URL:
-----------------------------------------------------------------------

http://:8080 [You can get the ec2-instance-public-ip-address from your AWS EC2 console page]

Note: If you are not interested in allowing All Traffic to your EC2 instance 1. Delete the inbound traffic rule for your instance 2. Edit the inbound traffic rule to only allow custom TCP port 8080

After you login to Jenkins, - Run the command to copy the Jenkins Admin Password - sudo cat /var/lib/jenkins/secrets/initialAdminPassword - Enter the Administrator password

Difference between GitHub Actions and Jenkins written clearly one below the other :
--------------------------------------------------------------------------------

🟦 GitHub Actions :
-------------------------------------------------
GitHub Actions is a cloud-based CI/CD tool provided by GitHub.

It is managed by GitHub, so you don’t need to install or maintain any server.

It is tightly integrated with GitHub repositories — whenever you push code or create a pull request, the workflows can automatically run.

Pipelines are written in YAML files and stored inside the repo under .github/workflows/.

Setup is very easy — you can start using it directly from your GitHub project.

It uses GitHub-hosted runners (virtual machines provided by GitHub) or self-hosted runners if you want more control.

Scaling is automatic; GitHub handles it for you.

It has a marketplace where you can use or create reusable “actions” for different tasks (like testing, building, deploying).

Security is managed by GitHub, and secrets can be stored safely in GitHub Secrets.

It is free up to a limit of build minutes; after that, you pay for usage.

Best suited for teams who are already using GitHub and want a simple, ready-to-use CI/CD system.

The user interface is modern and clean, integrated directly into GitHub.

🟩 Jenkins :
-------------------------------------------
Jenkins is an open-source, self-hosted CI/CD tool.

You must install and manage Jenkins on your own servers or cloud machines.

It can integrate with any source control system like GitHub, GitLab, Bitbucket, or even local repositories.

Pipelines are written using Groovy scripts inside a Jenkinsfile.

Setup requires manual configuration of plugins, agents, and environments.

It is highly customizable, with more than 1800 plugins available for almost any integration.

You must manage scaling manually by adding Jenkins agents (nodes) for parallel builds.

Security and maintenance are your responsibility — you need to handle server updates and plugin patches.

Jenkins is completely free to use, but you pay for your own infrastructure.

It’s more suited for enterprises or teams that need full control and flexibility in their CI/CD pipelines.

The user interface is older and not as modern, but very functional.

🟠 Summary in Simple Words
------------------------------------

GitHub Actions = Cloud-based, simple, GitHub-integrated, no maintenance needed.

Jenkins = Self-hosted, powerful, flexible, but needs setup and maintenance.

