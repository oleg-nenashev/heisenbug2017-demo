Heisenbug 2017. Pipeline Library Demo
---

## Sources

*  [Jenkins Configuration](https://github.com/oleg-nenashev/demo-jenkins-config-as-code/tree/heisenbug-demo)
* [Pipeline Library](https://github.com/oleg-nenashev/pipeline-library/tree/heisenbug2017-demo)
  * Demo scripts: 'demo/' directory
* [Job Restrictions Plugin](https://github.com/oleg-nenashev/job-restrictions-plugin/tree/cobertura-profile)

## Prerequisites

* Docker
* Good bandwidth :(

## Startup

1. Download Sources
2. Got to the Jenkins Configuration repo
3. Build the image: `docker build -t onenashev/demo-jenkins-config-as-code .`
4. Run redirector if needed: `docker run -d -v /var/run/docker.sock:/var/run/docker.sock -p 2376:2375 bobrik/socat TCP4-LISTEN:2375,fork,reuseaddr UNIX-CONNECT:/var/run/docker.sock`
5. Setup environment
  * MY_PIPELINE_LIBRARY_DIR - path to the Pipeline library
  * CURRENT_HOST - Current host to access docker from the Jenkins master container (see socat above)
6. Run in the development mode: `docker run --rm --name ci-jenkins-io-dev -v maven-repo:/root/.m2 -v ${MY_PIPELINE_LIBRARY_DIR}:/var/jenkins_home/pipeline-library -e DEV_HOST=${CURRENT_HOST} -p 8080:8080 -p 50000:50000  onenashev/demo-jenkins-config-as-code`
7. Login as `admin/admin` or `user/user`
8. Enjoy!

## What can you do?

* Run jobs
* See results in BlueOcean and reports
* Edit Pipeline library and demos without committing 

## Slides

To Be published soon, see http://bit.ly/heisenbug2017-nenashev-slides.
