# Les morceaux de Lego qu'il vous faut pour faire du web en python


## Plan de match

1. Création d'un environnement virtuel
* *Flask*: un framework web minimaliste
* *Jinja2*: un système de templating pour notre HTML
* *Peewee*: un ORM pour l'accès aux données
* Comment sauvegarder les dépendances de notre projet et reconstruire notre projet sur le poste de travail d'un collègue !
* Réalisation d'un micro-projet


## Ce que j'ai déjà fait pour la mise en place de votre machine virtuelle

    # outils de compilation
    $ sudo apt-get install build-essential
    # en-tête C de python pour compiler des modules 
    $ sudo apt-get install python-dev
    # générateur d'environnement virtuel
    $ sudo apt-get install python-virtualenv
    # notre gestionnaire de paquet pythonique
    $ sudo apt-get install python-pip


## 1. Création d'un environnement virtuel

    $ cd /home/waq/mon-projet-web-pythonique
    $ virtualenv venv
    $ source venv/bin/activate
    (venv) $ # c'est TRÈS bon signe si vous arrivez à ce point ;)


## 2. Flask: un framework web minimaliste

    (venv) $ pip install flask


### 2A. Ouvrez Sublime Text

1. Créez un fichier nommé *mon_projet.py* dans le répertoire courant;
2. Tapez le code se trouvant dans la slide suivante:


### 2B. `mon_projet.py`

Pas de copier-coller; prenez le temps de tapez chacun des caractères

```python
# coding: utf-8
from flask import Flask
app = Flask(__name__)

@app.route("/", methods=['GET', 'POST'])
def hello():
    if request.method == 'POST':
        un_param = request.form.get('un_param', None)
        
        if un_param:
            return "Voici un param {}".format(un_param)
    else:
        name = request.args.get('name', None)
        if name:
            return "Hello {}!".format(name)
        return "Hello World!"

if __name__ == "__main__":
    app.run()
```


### 2C. Retournez dans votre terminal et roulez l'application

    (venv) $ python mon_projet.py


### 2D. Ouvrez un navigateur dans la machine virtuelle à l'adresse suivante: http://localhost:5000


## 3. Jinja2: un système de gabarit

    (venv) $ pip install jinja2

Note: Est-ce que le module s'est installé comme il faut ? Quel est le message de pip ?


## 3A. Utilisation de jinja dans un `controller`

```python
# coding: utf-8
from flask import render_template

@app.route('/hello/')
@app.route('/hello/<name>')
def hello2(name=None):
    return render_template('hello.html', name=name)
```


## 3B. Où se trouve le fichier `hello.html` ?

```
(venv) $ cd /home/waq/mon-projet-web-pythoniques
(venv) $ mkdir templates
(venv) $ cd templates
(venv) $ touch hello.html
(venv) $ pwd # /home/waq/mon-projet-web-pythoniques/templates
```


## 3C. Le contenu de `hello.html`

```html
<!doctype html>
<title>Hello from Flask</title>
{% if name %}
  <h1>Hello {{ name }}!</h1>
{% else %}
  <h1>Hello World!</h1>
{% endif %}
```


## 4. Peewee: un ORM

    (venv) $ pip install peewee


## 4A. Exemple d'un `model`

    # coding: utf-8
    from peewee import SqliteDatabase, Model, 
                       Charfield, TextField, DateField, 
                       BooleanField
    
    db = SqliteDatabase('waq.db')
    
    class Human(Model):
        name = CharField(max_length=250)
        age = IntegerField()
        
        class Meta:
            database = db


## 4B. Exemples d'interaction avec la base de données

    # coding: utf-8
    
    # Connexion à la base de données
    db.connect()
    # Création des tables
    db.create_tables([Human]) 
    # Création d'un humain
    me = Human.create(name="Bernard Chhun", age=34)
    # Modifications et sauvegarde
    me.name = "Jackie Chan"
    me.age = 61
    me.save()
    db.close()


## 4C. Exemples de requêtes à la base de données

```python
# coding: utf-8
# la version longue d'un SELECT [...] WHERE [...]
jackie = Human.select().where(Human.name == "Jackie Chan").get()
# le raccourci :)
jackie2 = Human.get(Human.name == "Jackie Chan")

# afficher tous les Human dans la base de données
for h in Human.select():
    print(h.name, h.age)
```


## 5. Comment sauvegarder les dépendances de notre projet ?

    (venv) $ pip freeze > requirements.freeze


## 5A. Comment reproduire notre environnement avec ces dépendances ?

    # 1. Sortir de "virtualenv"
    (venv) $ deactivate
    # 2. Supprimer le dossier "venv"
    $ rm -fr venv
    # 3. Reconstruire l'environnement
    $ virtualenv venv
    $ source venv/bin/activate
    (venv) $ pip install -r requirements.freeze