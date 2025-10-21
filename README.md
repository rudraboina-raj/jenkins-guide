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