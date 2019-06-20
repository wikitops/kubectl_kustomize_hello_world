# Kubectl Kustomize : Hello World

The aim of this project is to deploy an Hello World application on Kubernetes instance like Minikube thanks to the Kustomize Kubectl option.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

What things you need to run this Ansible playbook :

*   [Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) must be installed on your computer (version >= 1.14.0)
*   [Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/) must be installed on your computer

### Usage

Be aware that you need to be in the root directory of the project to be able to run the commands.

#### Deployment

To deploy development Hello World application on Minikube instance, just run this command :

```bash
$ kubectl apply -k overlays/dev
```

If everything run as expected, you should be able to list the Kubernetes objects created :

```bash
$ kubectl get all -n dev-myhelloworld
NAME                                      READY   STATUS    RESTARTS   AGE
pod/dev-the-deployment-76dcc8f485-sm2pd   1/1     Running   0          19s


NAME                      TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
service/dev-the-service   LoadBalancer   10.107.181.141   <pending>     8666:32277/TCP   19s


NAME                                 READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/dev-the-deployment   1/1     1            1           19s

NAME                                            DESIRED   CURRENT   READY   AGE
replicaset.apps/dev-the-deployment-76dcc8f485   1         1         1       19s
```

To access the Hello World application with your browser, you need to get the Minikube IP in command line :

```bash
$ minikube IP
192.168.99.100
```

If everything run has expected, you should access the Hello World application on the LoadBalancer port : http://192.168.99.100:32277/

#### Destroy

To destroy the Kubernetes objects created, just run this command :

```bash
$ kubectl delete -k overlays/dev
```
## Author

Member of Wikitops : https://www.wikitops.io/

## Licence

This project is licensed under the Apache License, Version 2.0. For the full text of the license, see the LICENSE file.
