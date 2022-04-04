# Challenge Desktop

Vous souhaitez que vos étudiants travaillent dans un environnement familier? 
Laissez les profiter de l'IDE VsCode qu'ils possèdent sur leurs ordinateurs !

Avec ce type de challenge, l'étudiant va être en mesure de réaliser les exercices directement sur sa machine.
Fini les limitations techniques, l'étudiant peut à présent utiliser la commande docker 😁.

## Comment ?

Votre exercice doit suivre l'arborescence suivante :

```shell
.
├── challenge.yaml
├── Dockerfile
├── docs
│   └── briefing.md
├── scripts
│   ├── run.py
│   └── test.py
├── src
└── thumbnail.png

```

* **src** le code du challenge
* **scripts** les scrips que vous souhaitez rendre accessible  
* **docs** contient le briefing, les instructions utilisateurs. Le briefing sera ouvert au démarrage de l'IDE. 
* **thumbnail.png** image du challenge 
* Le **Dockerfile** décrit l'image de l'exercice :

```Dockerfile
FROM registry.takima.io/deadlock-public/deadlock-desktop/desktop:latest
# Here, you can install the necessary dependencies for the exercise


# Insert challenge source code in the mage
COPY ./src /src

# Insert the challenge briefing
COPY docs /home/deadlock/docs
```
* **challenge.yml** est le fichier descripteur

```yaml
version: 0.1
name: code_desktop_exemple
label: "Exercice desktop"
description: "An exemple of desktop exercice"
level: jedi # difficulté du challenge [comment ça marche](https://deadlock-resources.github.io/challenge-documentation/#level)
type: DESKTOP # obligatoire
xp: # points d'expérience, vous pouvez ajouter les labels que vous voulez
  programming: 1 # c'est un poids, pas un nombre
  java: 1
desktop:
  scripts: # L'étudiant pourra accéder aux scripts listés ici depuis l'extension deadlock 
    - name: launch
      command: python3 ./scripts/run.py
    - name: test
      command: python3 ./scripts/test.py

```

### Ajouter des images au briefing
```
![toast](image:toast.jpg)
![Something Else](image:dir/else.png)
```
Vous devez préfixer le path de votre image avec **image:**
