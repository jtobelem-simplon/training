# Où sont les toilettes?

Utilisez l'api de la ratp pour :

1. Observez dans un navigateur le résultat json de la requête suivante :  
[https://data.ratp.fr/api/records/1.0/search/?dataset=sanisettesparis2011](https://data.ratp.fr/api/records/1.0/search/?dataset=sanisettesparis2011)
> Note : vous pouvez copier le résultat dans un nouveau fichier .json et mettre en forme ce fichier par exemple dans atom en installant le package PRETTY json.

2. Effectuez cette requête dans le main d'une classe SanisetteFinder. Affichez les coordonnées d'une sanisette (la première de la liste) ainsi que ses coordonnées gps, le numéro et le nom de la voie et les horaires d'ouverture.  


3. Construire un objet java Sanisette représentant une sanisette sur le modèle retourné par le java (par exemple cet objet aura des attributs de type string pour le nom de la voie, etc ...).

4. Ecrivez les deux méthodes suivantes dans SanisetteFinder :

```java
/**
* Retourne la liste de toutes les sanisette de paris
*/
public static List<Sanistte> findAll() {
  // TODO
}

/**
* Retourne la liste de toutes les sanisette de l'arrondissement
*/
public static List<Sanistte> findParArrondissement(int arrondissement) {
  // TODO
}
```

5. Dans une classe Essai, affichez la liste de toutes les sanisettes du 20e arrondissement de Paris.  



# Qu'est ce que c'est *coruscant*? *pétrichor*?

1. Documentez-vous sur l'api de recherche :  
[https://fr.wikipedia.org/w/api.php](https://fr.wikipedia.org/w/api.php)

2. Utilisez les modules opensearch/search de l'api pour afficher tous les résultats. Effectuez la requête dans un navigateur et mettez en forme le résultat (grâce à PRETTY json)

3. Créez un objet java WikiResultat qui contient un titre, une description et une méthode toString(). Codez la méthode suivante dans une classe WikiFinder :

```java

/**
* Retourne une liste de WikiResultat en cherchant le mot @param word dans wikipedia.
*/
public static List<WikiResultat> findWord(String word){
  // TODO
}
```

4. Dans une classe Essai, affichez les définitions disponibles pour coruscant et pétrichor.  
