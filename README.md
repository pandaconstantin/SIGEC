# SIGEC_CEP

Cette application est basee sur l'architecture microservices. Elle comprend trois modules : 

* Le registre (**registry**)
* Le gateway (**SigecGateway**) : qui est la partie UI 
* L'application microservice (**SigecMicro**) : qui est la partie fournisseure de service



# Quelques modifications pour adapter aux contexte du systeme de stockage (schema et utilisateur base de donnees)

Creer un schema **cepgateway** dans la base de donnees **Sigecdb** et ajouter la ligne suivante (dans le fichier *application-dev.yml* et le fichier *application-prod.yml* du projet SigecGateway)
```yml
 hibernate.default_schema: cepgateway
 ```

 dans 
 ```yml
 jpa:
     properties:
```

et 

```yml
default-schema: cepgateway
```
dans 
```yml
liquibase:
```

Creer un schema cep dans la base de donnees **Sigecdb** et ajouter la ligne suivante (dans le fichier *application-dev.yml* et le fichier *application-prod.yml* du projet SigecMicro)
```yml
 hibernate.default_schema: cep
 ```

 dans 
 ```yml
 jpa:
     properties:
```

et 

```yml
default-schema: cep
```
dans 
```yml
liquibase:
```


# Comment lancer l'application ? 

1. Lancer avant tout le registre (sous GNU/Linux) :
```shell 
cd registry
./mvnw 
```
2.   *Lancer le microservice :* 
```shell
cd SigecMicro
./mvnw
```
3. Lancer le gateway : 
```shell
cd SigecGateway
./mvnw
npm start
```

