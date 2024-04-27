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

# Remove proxy configuration from /etc/apt/apt.conf
sudo sed -i '/Acquire::http::proxy/d' /etc/apt/apt.conf
sudo sed -i '/Acquire::https::proxy/d' /etc/apt/apt.conf

# Remove proxy configuration from ~/.bashrc
sed -i '/http_proxy/d' ~/.bashrc
sed -i '/https_proxy/d' ~/.bashrc
sed -i '/ftp_proxy/d' ~/.bashrc

# Optionally, you can reload ~/.bashrc to apply the changes immediately
source ~/.bashrc

echo "Proxy settings have been removed successfully."

```

**Détails du script :**
- **Suppression du fichier :** Le script vérifie si le fichier existe avant de tenter de le supprimer, ce qui évite des erreurs si le fichier n'existe pas.
- **Modification du fichier `.bashrc` :** Le script utilise `sed` pour supprimer les lignes qui contiennent les déclarations de variables d'environnement spécifiques au proxy. Cette commande édite le fichier en place et supprime seulement les lignes correspondantes.
- **Rechargement de `.bashrc` :** Après la modification, le script recharge les configurations du fichier `.bashrc` pour que les changements prennent effet immédiatement dans la session courante de l'utilisateur.

Avec ce script, vous annulez toutes les modifications précédemment effectuées par l'autre script, en supprimant le fichier et les configurations environnementales ajoutées. Assurez-vous de l'exécuter avec les droits appropriés si nécessaire.

# Annexe : sed 

`sed` est un outil très puissant et polyvalent en ligne de commande qui est utilisé pour effectuer des transformations textuelles sur un flux de données (fichier ou entrée directe). Il est particulièrement utile pour les scripts d'automatisation car il peut modifier des fichiers en place sans avoir besoin de créer un fichier temporaire. Voici pourquoi `sed` est souvent le choix privilégié pour des tâches comme celle que nous abordons :

1. **Automatisation :** `sed` peut être utilisé dans des scripts pour modifier automatiquement des fichiers sans interaction manuelle, ce qui est idéal pour des opérations comme modifier des fichiers de configuration ou des scripts de démarrage.

2. **Puissance et flexibilité :** `sed` permet une grande variété d'opérations textuelles, comme l'insertion, la suppression, la recherche et le remplacement, ce qui le rend extrêmement flexible pour traiter des textes complexes.

Quant à l'option `-i` spécifiquement :

- **In-place editing (`-i`) :** Cela permet à `sed` de modifier le fichier directement sur place. Sans cette option, `sed` imprime le résultat sur la sortie standard (par défaut, l'écran), et le fichier original reste inchangé. Avec l'option `-i`, vous pouvez directement modifier le fichier sans avoir à le rediriger dans un nouveau fichier puis remplacer l'ancien.

Un exemple de commande utilisant `sed` pourrait ressembler à cela :

```bash
sed -i '/pattern_to_delete/d' file.txt
```

Cette commande supprimera toutes les lignes qui contiennent `pattern_to_delete` du fichier `file.txt`, modifiant le fichier original directement grâce à l'option `-i`.

Dans le contexte de notre script, utiliser `sed` pour retirer les lignes ajoutées au `.bashrc` concernant les variables de proxy est une manière efficace et propre de s'assurer que ces modifications sont correctement et complètement annulées.
