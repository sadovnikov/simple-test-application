# Simple Test Application

## Building the application

All steps to build this simple application are in GitHub [workflow](.github/workflows/bulid.yaml) file.

* Checkout Source Code
* Setup Java JDK
* Build Java Application
* Build and Push Docker Image
  * uses the `DOCKERHUBTOKEN` secret
  * uses the commit SHA as the docker image version
* Redeploy Application to K8S
  * uses the `KUBECONFIG` secret
  * uses the commit SHA to set the `version` Helm value

The application docker image is pushed to the [Docker Hub](https://hub.docker.com/repository/docker/sadovnikov/sample-app/general).

## Opening the application in browser

* setup correct kube context by `export KUBECONFIG=<path the the kube.config file>`
* start port-forwarding `kubectl -n sample port-forward service/sample-application 8080:80`
* open the [application](http://127.0.0.1:8080/hello?name=Reviewer) in the browser


## Scaling up

Should the load on the application raises, the [Horizontal Pod Autoscaler](helm/templates/deployment.yaml) starts
creating more replicas of the application.

## Reference Documentation
For further reference, please consider the following sections:

* [Official Apache Maven documentation](https://maven.apache.org/guides/index.html)
* [Spring Boot Maven Plugin Reference Guide](https://docs.spring.io/spring-boot/docs/3.0.6/maven-plugin/reference/html/)
* [Create an OCI image](https://docs.spring.io/spring-boot/docs/3.0.6/maven-plugin/reference/html/#build-image)
