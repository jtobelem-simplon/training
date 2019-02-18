# Hibernate


## 1. Généralités (JPA, ORM, hibernate)

[Un cours en français](http://orm.bdpedia.fr/introjpa.html)

#### Rôle d'un ORM

Le but d'un ORM (Object Relation Map) est de relier des objects (java) avec des relations.

Par exemple si on a les deux relations suivantes :

* Table films

id |titre        |année|idRéalisateur
---|---          |---  |---          
17 |Pulp Fiction |1994 |37
54 |Le Parrain   |1972 |64
57 |Jackie Brown |1997 |37

* Table artistes

id  |nom      |prénom   |année_naissance
--- |---      |---      |---
1   |Coppola	|Sofia	  |1971
37	|Tarantino|Quentin	|1963
64	|Coppola  |Francis	|1939


On va leur faire correspondre les deux objets suivantes :

```java
public class Film {

	Artiste realisateur;
}
```

```java
public class Artiste {

	Set<Film> filmsDiriges;

}
```
> On remarque une première différence importante : les relations en base de données sont bi-directionnelles, alors qu'en java on spécifie le sens. Ici, on indique explicitement un lien de Film vers Artiste, et un lien de Artiste vers Film.

#### JPA

Le mapping objet/relation est un aspect important de la programmation, une spécification indique comment il doit s'opérer avec java : c'est [JPA](https://fr.wikipedia.org/wiki/Java_Persistence_API).

#### Hibernate

JPA est essentiellement une spécification. Il existe plusieurs implémentations de JPA, la plus connue est Hibernate.

[Hibernate](https://fr.wikipedia.org/wiki/Hibernate)

## 2. Configuration d'hibernate avec springboot

Pour configurer hibernate, il suffit d'ajouter la dépendance spring-boot-starter-data-jpa (à votre pom.xml ou bien build.gradle). Vous aurez aussi besoin d'ajouter un connecteur spécifique pour votre bdd (mysql, postgres, ...).

[Maven repository](https://mvnrepository.com/)


## 3. Quelques exemples

#### One to One

Ce type de relation n'étant pas la plus courante (car elle revient souvent à avoir deux tables qui auraient pu se ramener en une seule), nous allons d'abord étudier les suivantes.

#### One to Many

[Cahier des charges ici](oneToMany/README.md)

#### Many to Many

[Cahier des charges ici](manyToMany/README.md)

## 4. Requêtes HQL

Pour des requêtes un peu plus complexes, et comme l'ensemble des requêtes passent par hibernate, on peut utiliser le langage [HQL](https://docs.jboss.org/hibernate/orm/3.5/reference/fr-FR/html/queryhql.html).

Pour les utiliser, nous aurons besoin de récupérer l'entityManager que l'on va placer en attribut de la classe :

```java
@PersistenceContext
private EntityManager em;
```

```java
public void hqlQuery(String etudiantNom) {

		String hql = "FROM Etudiant E WHERE E.nom like :nom"; // the java class, not entity
		TypedQuery<Etudiant> query = em.createQuery(hql, Etudiant.class);
		query.setParameter("nom", "%eg%");
		List<Etudiant> results = query.getResultList();

		for (Etudiant etudiant : results) {
			log.info(etudiant.getNom());
		}
	}
```

## 5. Entities from relation, Eclipse

- new jpa project
- init connexion with the good driver (test the connexion)
- new entites from tables

## Kahoot time

(Ne suivez pas le lien, présentation seulement) https://play.kahoot.it/#/?quizId=b0328654-804b-4cde-a6d0-e5c05028cf48

#### [retour](../README.md)
