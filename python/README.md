# Introduction au langage python, CyberSecu-LP1

Nous allons travailler avec python3 (dernière version 3.7.4) : [doc de référence](https://docs.python.org/fr/3.7/)

## Cours

[les cours](course/python.md)

## Exercices

[les exercices](exercice/python.md)

## Les fondamentaux de l'algo

Pour pratiquer plus sur les boucles en codant avec un langage de bloc (à la souris, pour apprendre la programmation) :

1. [Créez un compte sur code.org en suivant le lien suivant](https://studio.code.org/join/WTCFSG)
2. Faites la leçon 2 : le labyrinthe
3. Faites la leçon 5 : l'artiste
4. Faites la leçon 15 : l'artiste4 (pour utiliser des fonctions)

Tester ces algos avec python :

1. Installez le module tk pour python3 :
```shell
sudo apt install python3-tk
```
2. Testez le code suivant pour vérifier que python3-tk fonctionne :
```python
from turtle import *
color('red', 'yellow')
begin_fill()
while True:
    forward(200)
    left(170)
    if abs(pos()) < 1:
        break
end_fill()
done()
```
3. Essayez de convertir en python3 les algos de la leçon 5.

solution pour le 6 de la leçon 5 :
```python
for i in range(3) :
    forward(100)
    right(120)
for i in range(4) :
    left(90)
    forward(100)
done()
```
