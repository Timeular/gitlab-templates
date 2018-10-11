# gitlab-templates

This project intends to simplify the build process within gitlab and make its components reusable.

## How to use it

All of our microservices are having a repository structure with two main branches:

* master
* develop

The `develop` branch reflects the main branch where everything is merged to. The master branch instead
represents the revision which is currently deployed on one of our production systems.

Our microservices are following always the same pattern (regarding build process):

* build/test them
* create + upload a container
* deploy to our testing system ()
* deploy to production

### Gradle microservice

To use the base gradle pipeline you have to copy the following snippet:

```yml
include:
- 'https://raw.githubusercontent.com/Timeular/gitlab-templates/master/templates/templates-docker.yml'
- 'https://raw.githubusercontent.com/Timeular/gitlab-templates/master/templates/templates-deploy-to-k8s.yml'
- 'https://raw.githubusercontent.com/Timeular/gitlab-templates/master/default_jdk8_gradle_pipeline.yml'

variables:
  K8S_NAMESPACE: <namespace>
  K8S_DEPLOYMENT: <deployment-name>
```