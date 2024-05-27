# Tutoriel Complet : Installation de Figlet et Personnalisation d'un Message dans .bashrc

# 1 - Introduction
Figlet est un programme en ligne de commande qui génère des bannières textuelles dans divers styles à partir de texte standard. Ce guide explique comment installer Figlet, créer un message personnalisé et l'ajouter à votre fichier `.bashrc` pour qu'il s'affiche chaque fois que vous ouvrez un terminal.

### Prérequis
- Un système d'exploitation basé sur Unix (Linux, macOS) ou Windows avec un terminal compatible.
- Connexion Internet (pour l'installation via gestionnaire de paquets).

# 2 - Installation de Figlet

#### Sous Linux (Debian/Ubuntu)
1. Ouvrez un terminal.
2. Exécutez la commande suivante pour mettre à jour la liste des paquets :
   ```bash
   sudo apt update
   ```
3. Installez Figlet avec la commande :
   ```bash
   sudo apt install figlet
   ```

#### Sous macOS
1. Ouvrez un terminal.
2. Si Homebrew n'est pas installé, installez-le en suivant les instructions sur [brew.sh](https://brew.sh/).
3. Installez Figlet avec la commande :
   ```bash
   brew install figlet
   ```

#### Sous Windows
1. Téléchargez et installez Cygwin depuis [cygwin.com](https://www.cygwin.com/).
2. Pendant l'installation de Cygwin, assurez-vous de sélectionner `figlet` dans les paquets à installer.
3. Complétez l'installation et ouvrez le terminal Cygwin.

## (OPTIONNEL, Passez à la section suivante, ce message est temporaire et ne persiste que pour la session active) - Génération d'un Message Personnalisé

1. Ouvrez un terminal.
2. Utilisez Figlet pour créer votre message personnalisé. Par exemple :
   ```bash
   figlet "Se former avec Haythem"
   ```

# 3- Ajout du Message Personnalisé à `.bashrc`

1. Ouvrez votre fichier `.bashrc` dans un éditeur de texte. Vous pouvez utiliser `nano` ou tout autre éditeur de votre choix. Par exemple :
   ```bash
   nano ~/.bashrc
   ```

2. Ajoutez la commande Figlet à la fin du fichier `.bashrc`. Par exemple, pour ajouter le message "Se former avec Haythem" :
   ```bash
   echo 'figlet "Se former avec Haythem"' >> ~/.bashrc
   ```

3. Enregistrez les modifications et fermez l'éditeur.

4. Pour que les modifications prennent effet sans redémarrer votre terminal, exécutez la commande suivante :
   ```bash
   source ~/.bashrc
   ```

### Exemple Complet
Voici comment le fichier `.bashrc` pourrait ressembler après avoir ajouté le message :
```bash
# ~/.bashrc

# ... autres configurations ...

# Ajouter un message personnalisé avec Figlet
figlet "Se former avec Haythem"
```

# 4 - Résultat
Chaque fois que vous ouvrez un nouveau terminal, le message personnalisé sera affiché :

```
 ____  _____                          _       _             _           
/ ___|| ____|__  ___ __  _ __   __ _ (_) __ _| |_ ___   ___| |_ ___ _ __ 
\___ \|  _| / _ \/ __/ _ \| '_ \ / _` || |/ _` | __/ _ \ / __| __/ _ \ '__|
 ___) | |__|  __/ (_| (_) | | | | (_| || | (_| | ||  __/| (__| ||  __/ |   
|____/|_____\___|\___\___/|_| |_|\__, |_|\__,_|\__\___| \___|\__\___|_|   
                                |___/                                  
```

# 5 - Conclusion
En suivant ce tutoriel, vous pouvez installer Figlet, créer un message personnalisé et l'ajouter à votre fichier `.bashrc` pour qu'il s'affiche à chaque ouverture de terminal. Profitez de la formation avec Haythem !

---

Profitez de la formation avec Haythem !
