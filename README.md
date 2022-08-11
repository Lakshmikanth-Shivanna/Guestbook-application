# Guestbook-application

In this example, we will be deploying guestbook application using helm and add the Redis as a dependency.

Prerequisite

Kubernetes Cluster Setup
Clone the git repo: https://github.com/devops4solutions/guestbook
Setup a helm project

helm create guestbook rm -rf guestbook/templates/tests

Adding a Redis Chart dependency Chart dependencies are used to install other charts’ resources that a Helm chart may depend on.

In this example, we are using Redis as a database so we to need add this as a dependency.

First we can search the charts for redis using the below command:

helm search hub redis

Now we will add the dependency section in the Charts.yaml file as shown below:

dependencies:

- name: redis 
  version: 12.7.x
  repository: https://charts.bitnami.com/bitnami
How to download this dependency?

When downloading a dependency for the first time, you should use the helm dependency update command.

This command will download your dependency to the charts/ directory and will generate the Chart.lock file, which specifies metadata about the chart that was downloaded.

helm dependency update guestbook

![image](https://user-images.githubusercontent.com/75528295/184124112-e4cb07da-12f1-4c3d-83a3-bb0e5a835a3d.png)

Now you should see that it has downloaded the dependency and also updated the Chart.lock file

![image](https://user-images.githubusercontent.com/75528295/184124277-6578a187-70c5-4341-9754-c84d7c8fe7e8.png)

![image](https://user-images.githubusercontent.com/75528295/184124336-84cf4c43-1ce0-4352-a806-f5112f2809b1.png)

