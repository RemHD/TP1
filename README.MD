# Ask Yourself :

Afin d'utiliser les bonnes images, on utilise la commande :

```docker pull
docker pull openjdk
docker pull postgres
docker pull adminer```

Qui téléchargera les images depuis le hub, on peut préciser la version aussi.

Concrètement on se connecte à une DB postgres, avec les paramètres inscrits dans le Dockerfile.

On load cette DB et on vérifie qu'on y a bien accès. Il est possible de faire un docker exec + une connexion plutôt que de passer via adminer si cela pose prob>

Il faut monter l'image puis lancer le container :

```docker build -t ritchieelloumi/postgres .

docker run --name postgres1 -v /postgres/data:/var/lib/postgresql/data -p 8000:8000 -e POSTGRES_USER=usr POSTGRES_PASSWORD=pwd ritchieelloumi/postgres

docker run --link .... -p 8080:8080 adminer
```

## La partie JDK

```
FROM openjdk:7

COPY . /usr/src/myapp
WORKDIR /usr/src/myapp
RUN javac Main.java
CMD ["java", "Main"]
```

Suivi d'un :

```
docker build -f ./DockerFile -t ritchieelloumi/postgres1:latest . docker run -it --rm --name container-backend ritchieelloumi/backend:latest
```

## Maven API demo

```
docker build -f ./DockerFile -t ritchieelloumi/test . docker run -it --name javademo ritchieelloumi/test
```

Il ne faut pas oublier les commandes permettant de mettre les container sur le même network :
On spécifie au lancement du container sur lequel il peut se connecter, on laissera en bridge par défaut :