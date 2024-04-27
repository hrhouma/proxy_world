# 1 - Configuration du proxy à l'adresse 10.1.0.5:8080

```bash
#!/bin/bash

# Add proxy configuration to /etc/apt/apt.conf
sudo bash -c 'echo "Acquire::http::proxy \"http://10.1.0.5:8080/\";" >> /etc/apt/apt.conf'
sudo bash -c 'echo "Acquire::https::proxy \"https://10.1.0.5:8080/\";" >> /etc/apt/apt.conf'

# Add proxy configuration to ~/.bashrc
echo 'export http_proxy=http://10.1.0.5:8080' >> ~/.bashrc
echo 'export https_proxy=http://10.1.0.5:8080' >> ~/.bashrc
echo 'export ftp_proxy=http://10.1.0.5:8080' >> ~/.bashrc

# Source the ~/.bashrc file to apply changes immediately
source ~/.bashrc

echo "Proxy settings have been applied successfully."
```

**Explications des modifications :**
- Le script écrit directement les configurations de proxy dans le fichier `proxy_college` situé dans `/home/ubuntu`.
- Les variables d'environnement sont ajoutées à `.bashrc` pour qu'elles soient chargées à chaque nouvelle session de terminal.
- Le script garantit que les modifications sont appliquées immédiatement avec `source ~/.bashrc`.

Assurez-vous d'exécuter ce script en tant que root ou ajustez le chemin selon l'utilisateur sudoer souhaité.



# 2 - Configuration inverse

Pour créer un script qui annule les modifications apportées par le premier script, vous pouvez prévoir les actions suivantes :

1. Supprimer le fichier `proxy_college` du répertoire personnel de l'utilisateur.
2. Retirer les variables d'environnement concernant le proxy du fichier `.bashrc` et recharger la configuration.
3. Informer l'utilisateur que les modifications ont été annulées.

Voici comment vous pourriez structurer ce script :

```bash
#!/bin/bash

# Chemin du fichier de configuration du proxy
FILE="$HOME/proxy_college"

# Suppression du fichier de configuration du proxy
if [ -f "$FILE" ]; then
    rm "$FILE"
    echo "Fichier de configuration du proxy supprimé."
else
    echo "Aucun fichier de configuration du proxy à supprimer."
fi

# Retrait des variables d'environnement liées au proxy dans .bashrc
sed -i '/http_proxy="http:\/\/10.1.0.5:8080"/d' ~/.bashrc
sed -i '/https_proxy="http:\/\/10.1.0.5:8080"/d' ~/.bashrc
sed -i '/ftp_proxy="http:\/\/10.1.0.5:8080"/d' ~/.bashrc

# Rechargement des configurations du .bashrc
source ~/.bashrc

echo "Les configurations de proxy et les variables d'environnement ont été retirées."
```

**Détails du script :**
- **Suppression du fichier :** Le script vérifie si le fichier existe avant de tenter de le supprimer, ce qui évite des erreurs si le fichier n'existe pas.
- **Modification du fichier `.bashrc` :** Le script utilise `sed` pour supprimer les lignes qui contiennent les déclarations de variables d'environnement spécifiques au proxy. Cette commande édite le fichier en place et supprime seulement les lignes correspondantes.
- **Rechargement de `.bashrc` :** Après la modification, le script recharge les configurations du fichier `.bashrc` pour que les changements prennent effet immédiatement dans la session courante de l'utilisateur.

Avec ce script, vous annulez toutes les modifications précédemment effectuées par l'autre script, en supprimant le fichier et les configurations environnementales ajoutées. Assurez-vous de l'exécuter avec les droits appropriés si nécessaire.
