# jenkins-guide
jenkins SDLC in detail

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


Continous Integration:

It is the frequent, automatic integration of code, All new and modified code is automatically tested with master code.

Continous Delivery:

It is the extension of CI. it ensures that the Code is alway ready to be deployed, although manual approval is required to actually deploy the Software to production.

Continous deployment:

Automatically deploy all validated changes to production. 
Frequent feedback enables issues to be found and fixed quickly.

Why we need CI/CD?

→ Detect bugs and problems in early stages of SDLC

→ Save Cost and efforts

→ Improves Co-ordination between teams, implement innovative ideas .

→Faster release to production system.

→ Automated testing helps deliver a top-notch quality product.

 → Minimum human intervention, hence less chances of manual errors.

 CONTINOUS INTEGRATION

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

Dev

→Then the build is transferred to lower environments ,Such as Dev for the deployment using tools. Such as Ansible, Helm for K8's related deployments

UAT

→Once it is approved and tested in dev it would then deploy in pre-production UAT environment.

Production 

→ Once it is approved  testing in UAT, then it is ready for deployment in production.

Jenkins installation script 

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