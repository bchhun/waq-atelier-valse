# Les morceaux de robots qu'il vous faut pour faire du web en python


## Plan de match

* Flask: un framework minimaliste
* Jinja2: un système de templating
* Peewee: un ORM
* Comment sauvegarder les dépendances de notre projet ?
  * et reconstruire notre projet !
* Réalisation d'un micro-projet


## Création d'un environnement virtuel

    $ cd /home/waq/mon-projet-web-pythonique
    $ virtualenv venv
    $ source venv/bin/activate
    (venv) $ # c'est bon signe si vous arrivez à ce point


## Flask: un framework web minimaliste

    (venv) $ pip install flask


### Avec l'éditeur texte de votre choix

1. Créez un fichier nommé *mon-projet.py* dans le répertoire courant;
2. Tapez le code se trouvant dans la slide suivante


### mon-projet.py

```
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello World!"

if __name__ == "__main__":
    app.run()  
```


### Retournez dans votre terminal

    (venv) $ python mon-projet.py


### Ouvrez votre navigateur à l'adresse suivante: http://localhost:5000


## Jinja2: un système de gabarit

TODO


## Peewee: un ORM

TODO


## Comment sauvegarder les dépendances de notre projet ?

TODO


## Réalisation d'un micro-projet

TODO