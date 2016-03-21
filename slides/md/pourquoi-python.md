# Python ?


## Simplicité du langage

<pre><code class="line-numbers">
# des variables
est_grand = True
poids = 175 # livres
hauteur = 180 # pommes 
bernard = {
    "age": 34,
    "papa": True,
    "cheveux": "noir"
}

# si conditionnel
if est_grand:
    print("pas si grand que ça")
else:
    print("pas si petit que ça")

# un tableau
couleurs_de_cheveux = ["noir", "blanc", "brun", "blond", "rouge"]

# une boucle sur un tableau
for couleur in couleurs_de_cheveux:
    if bernard.get("cheveux") == couleur:
        print("weee")

# une fonction
def une_fonction(param):
    # l'interpolation de chaîne de caractère
    print("une {} fonction !".format(param))
    
# affiche "une grande fonction !"
une_fonction("grande")

# importer un module
import requests # pour faire des requêtes HTTP

# utiliser un module
r = requests.get("http://www.google.ca")

</code></pre>


## Gestionnaire de dépendance

`pip` et `pypi` sont vos amis :)

```
$ pip install django  
```

Note:
...


## Environnement virtuelle 

Pour nous permettre de rouler plusieurs applications python ayant:

* des versions différentes de Python
* les mêmes dépendances, mais à des numéros de versions différentes 

```
$ cd /mon/repertoire/de/travail
$ virtualenv venv
$ source venv/bin/activate
(venv) $ pip install django
```

Note:
...