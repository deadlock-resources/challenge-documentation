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
├── workdir
└── thumbnail.png

```

* **workdir** le code du challenge
* **scripts** les scrips que vous souhaitez rendre accessible  
* **docs** contient le briefing, les instructions utilisateurs. Le briefing sera ouvert au démarrage de l'IDE. 
* **thumbnail.png** image du challenge 
* Le **Dockerfile** décrit l'image de l'exercice :

```Dockerfile
FROM registry.takima.io/deadlock-public/deadlock-desktop/desktop:latest
# Ici, vous pouvez installer les dépendances nécessaires à l'exercice

# Ajoutez ici les codes sources de votre challenge
COPY ./workdir /workdir

# Ajoutez le contenu accessible à l'utilisateur dans l'IDE
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
    - name: launch # Nom de commande
      command: python3 ./scripts/run.py # Commande à exécuter
    - name: test
      command: python3 ./scripts/test.py

```

### Ajouter des images au briefing
```
![toast](image:toast.jpg)
![Something Else](image:dir/else.png)
```
Vous devez préfixer le path de votre image avec **image:**

## Tester l'exercice

### Prérequis

* Installer [VSCode](https://code.visualstudio.com/) / [VSCodium](https://vscodium.com/)
* Installer l'extention : [Remote - Container](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

### Lancer avec Deadlock-cli

Exécuter la commande suivante dans le dossier de l'exercice:
```shell
dcli run .
```