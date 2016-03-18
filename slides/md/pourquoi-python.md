# Python ?


# Simplicité du langage

Note:
...


```
# un boolean
bernard_est_grand = True

# si conditionnel
if bernard_est_grand:
    print("pas si grand que ça")
else:
    print("pas si petit que ça")

# un tableau
couleurs_de_cheveux_de_bernard = ["noir", "blanc"]

# une boucle sur un tableau
for couleur in couleurs_de_cheveux_de_bernard:
    print(couleur)

# une fonction
def une_fonction(param):
    # l'interpolation de chaîne de caractère
    print("une {} fonction !".format(param))
    
une_fonction("grande")

```


# Gestionnaire de dépendance

`pip` et `pypi` sont vos amis :)

```
$ pip install django  
```

Note:
...


# Environnement virtuelle 

Pour nous permettre de rouler plusieurs application ayant:

* une version différente de Python
* des dépendances différentes 

Note:
...