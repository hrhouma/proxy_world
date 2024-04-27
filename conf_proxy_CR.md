# Configuration du proxy à l'adresse 10.1.0.5:8080

```bash
#!/bin/bash

# Chemin du fichier de configuration du proxy
FILE="/home/ubuntu/proxy_college"

# Création/écrasement du fichier avec les lignes de configuration du proxy
echo "Acquire::http::Proxy \"http://10.1.0.5:8080/\";" > $FILE
echo "Acquire::https::Proxy \"https://10.1.0.5:8080/\";" >> $FILE

# Ajout des variables d'environnement au fichier .bashrc pour persistance
echo "export http_proxy=\"http://10.1.0.5:8080\"" >> ~/.bashrc
echo "export https_proxy=\"http://10.1.0.5:8080\"" >> ~/.bashrc
echo "export ftp_proxy=\"http://10.1.0.5:8080\"" >> ~/.bashrc

# Application des changements
source ~/.bashrc

echo "Configuration du proxy et variables d'environnement ajoutées."
```

**Explications des modifications :**
- Le script écrit directement les configurations de proxy dans le fichier `proxy_college` situé dans `/home/ubuntu`.
- Les variables d'environnement sont ajoutées à `.bashrc` pour qu'elles soient chargées à chaque nouvelle session de terminal.
- Le script garantit que les modifications sont appliquées immédiatement avec `source ~/.bashrc`.

Assurez-vous d'exécuter ce script en tant que root ou ajustez le chemin selon l'utilisateur sudoer souhaité.
