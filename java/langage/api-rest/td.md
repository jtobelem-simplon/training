# Format json et api rest

#### Définition json sur wikipedia :

JavaScript Object Notation (JSON) est un format de données textuelles dérivé de la notation des objets du langage JavaScript. Il permet de représenter de l’information structurée comme le permet XML par exemple.


#### Définition rest sur wikipedia :


REST (representational state transfer) est un style d'architecture logicielle définissant un ensemble de contraintes à utiliser pour créer des services web. Les services web conformes au style d'architecture REST, aussi appelés services web RESTful, établissent une interopérabilité entre les ordinateurs sur Internet. Les services web REST permettent aux systèmes effectuant des requêtes de manipuler des ressources web via leurs représentations textuelles à travers un ensemble d'opérations uniformes et prédéfinies sans état.


# Librairies java

Il existe plusieurs libraires non natives pour récupérer le texte json à partir d'une requête puis pour parser (découper) ce texte. On peut regarder sur le site [https://json.org/](https://json.org/) (par exemple la librairie gson, ou jackson) pour une liste exhaustive.

#### java-json
[http://www.java2s.com/Code/Jar/j/Downloadjavajsonjar.htm](http://www.java2s.com/Code/Jar/j/Downloadjavajsonjar.htm
)

#### apache commons-io
[https://commons.apache.org/proper/commons-io/download_io.cgi](https://commons.apache.org/proper/commons-io/download_io.cgi
)

L'exemple suivant utilise les deux libraires précédentes pour aller interroger l'api web de github afin d'obtenir la liste de tous les utilisateurs github qui ont plus de 100 followers (donc des gens influents :).

```java
public static void main(String[] args)
    throws MalformedURLException, IOException, JSONException {

    String url = "https://api.github.com/search/users?q=followers%3E100"; // plus de 100 followers

		String jsonText = IOUtils.toString(new URL(url), Charset.forName("UTF-8"));

		JSONObject json = new JSONObject(jsonText);

		int totalCount = (int) json.get("total_count");

		System.out.println("total count : "+totalCount);
	}
```
#### exemples d'utilisation en java
[https://github.com/jtobelem-simplon/simple-json](https://github.com/jtobelem-simplon/simple-json)

# Un exemple : pull ou marcel ?

1. Créez un compte sur [https://home.openweathermap.org](https://home.openweathermap.org) afin d'obtenir une clé de recherche gratuite.
2. Lancez une requête sur la météo à Paris (à l'aide de votre appid) :
[http://api.openweathermap.org/data/2.5/weather?q=Paris,fr&units=metric&appid=XXXX](http://api.openweathermap.org/data/2.5/weather?q=Paris,fr&units=metric&appid=XXXX)
3. Observez le json obtenu dans un editeur de texte (par exemple atom avec PRETTY json)
4. Récupérez les champs température, humidité et nuage. Affichez des messages adaptés :

    "Time to put your pull" : si la température<10°   
    "Time to get your umbrella" : si l'humidité est supérieure à 90   
    "Time to leave your sunglasses" : si les nuages sont supérieurs à 50   

5. Créer une classe Temperature pour organiser votre code.

# Quelques api publiques

[https://data.ratp.fr/explore](https://data.ratp.fr/explore)

[https://fr.wikipedia.org/w/api.php](https://fr.wikipedia.org/w/api.php)

[https://developer.github.com/v3/](https://developer.github.com/v3/)

[https://opendata.paris.fr/api/](https://opendata.paris.fr/api/) : par exemple les arbres

[https://world.openfoodfacts.org/data](https://world.openfoodfacts.org/data) : open food facts (utilisée par exemple par l'application yuka)

[https://www.ibm.com/watson/developer/](https://www.ibm.com/watson/developer/) : l'intelligence artificielle d'IBM!!

# [Des exercices](./tp.md)
