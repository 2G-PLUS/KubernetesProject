# Installation:

## Prérequis:

Pour lancer Kubernetes sur Windows, il faut installer Docker Desktop et activer Kubernetes. De plus, il faut installer MiniKube.
Pour lancer Minikube, il faut lancer la commande suivante:
```cmd
minikube start
```
Si vous voulez utiliser l'interface graphique de Kubernetes, il faut lancer la commande suivante:
```cmd
minikube dashboard
```

## Installation de l'application:

Pour installer l'application, il faut lancer les commandes suivantes:

```cmd
kubectl apply -f mysql-deployment.yaml
kubectl apply -f redmine-deployment.yaml
kubectl apply -f redmine-data-pvc.yaml
```

Vous pouvez vérifier l'état de vos déploiements et services en utilisant les commandes suivantes :
```cmd
kubectl get deployments
kubectl get services
```

La base de donnée MySQL est créer, cependant il faut créer la base de donnée Redmine. Pour cela, accéder au shell du pods, depuis l'interface graphique. Une fois cela réalisé, il faut lancer la commande suivante:
```cmd
mysql -uroot -p
```
Le mot de passe est "password". Une fois connecté, il faut créer la base de donnée Redmine:
```cmd
CREATE DATABASE redmine CHARACTER SET utf8;
```

La base de donnée est créer, pour accéder à l'url de Redmine, il faut lancer la commande suivante:
```cmd
minikube service redmine-service
```

## Exposition de l'application:

Pour exposer l'application, il faut lancer la commande suivante:
```cmd
docker run -p 3000:3000 redmine
```

Pour accéder à l'application, il faut lancer l'url suivante:
```cmd
http://localhost:3000
```
