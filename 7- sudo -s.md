# p1 - sudo -s vs su ? 
La commande `sudo` et la commande `su` sont deux outils couramment utilisés dans les systèmes d'exploitation basés sur Unix (comme Linux) pour exécuter des commandes avec des privilèges élevés, généralement ceux de l'utilisateur root (l'administrateur du système). Voici une explication des différences entre `sudo -s` et `su`, avec des exemples de la vie réelle.

### `sudo -s`
La commande `sudo -s` lance un shell avec les privilèges de l'utilisateur root, mais elle maintient certaines variables d'environnement de l'utilisateur actuel. Cela signifie que vous restez connecté en tant que votre utilisateur normal, mais vous avez temporairement des privilèges de superutilisateur pour exécuter des commandes.

- **Exemple de la vie réelle:** Imaginez que vous soyez un administrateur de système qui doit effectuer des tâches de maintenance sur un serveur sans changer complètement d'utilisateur. Vous utilisez `sudo -s` pour obtenir un accès root et effectuer ces tâches tout en conservant votre environnement utilisateur habituel (comme les variables d'environnement personnalisées).

### `su`
La commande `su` (sans options) vous permet de changer d'utilisateur, généralement pour devenir root si aucun nom d'utilisateur n'est spécifié. Contrairement à `sudo -s`, `su` vous demande le mot de passe du compte vers lequel vous basculez et change complètement l'environnement pour celui de l'autre utilisateur.

- **Exemple de la vie réelle:** Vous êtes développeur et avez besoin de tester une application dans l'environnement de l'utilisateur root pour vérifier son comportement avec des privilèges élevés. Vous utilisez `su` pour basculer vers l'utilisateur root et lancer l'application comme si vous étiez cet utilisateur, avec tous ses paramètres environnementaux.

### Comparaison
- **Authentification:** `sudo -s` utilise le mot de passe de l'utilisateur actuel pour élever les privilèges, tandis que `su` demande le mot de passe de l'utilisateur vers lequel vous changez.
- **Environnement:** `sudo -s` conserve une partie de l'environnement de l'utilisateur actuel, tandis que `su` change complètement pour celui de l'autre utilisateur.
- **Usage courant:** `sudo -s` est souvent utilisé pour des tâches administratives temporaires, tandis que `su` est utilisé pour des sessions plus prolongées ou pour des tests dans un environnement utilisateur spécifique.

Utilisez `sudo -s` quand vous avez besoin de privilèges élevés sans quitter votre environnement utilisateur, et `su` quand vous devez opérer comme un autre utilisateur.

# p2 - su c'est quoi ? 
Imaginons une analogie pour expliquer la commande `su` dans un contexte de la vie réelle. Considérez que vous êtes à une réception sécurisée où chaque personne a un badge avec des niveaux d'accès différents.

### Analogie
Vous êtes un employé (l'utilisateur normal) à cette réception, et vous avez besoin de vous rendre dans une pièce sécurisée où seul le directeur (l'utilisateur root) a le droit d'entrer. Pour y accéder, vous avez besoin de prendre temporairement l'identité du directeur.

- **Utilisation de `su`:** C'est comme si vous demandiez à la sécurité de vous laisser entrer dans le bureau du directeur. La sécurité vous demande le code personnel du directeur (le mot de passe de l'utilisateur root). Une fois que vous fournissez ce code, vous pouvez entrer dans le bureau, et tout le monde vous traite comme si vous étiez le directeur. Vous avez accès à tous ses dossiers et ressources, et vous agissez sous son identité jusqu'à ce que vous décidiez de quitter le bureau (fermer la session `su`).

Dans cette analogie, le changement d'identité est complet : vous portez le "badge" du directeur et agissez avec tous ses privilèges et dans son environnement. Cela illustre comment `su` vous permet de prendre complètement l'identité d'un autre utilisateur (souvent root) et d'opérer dans son environnement total.


# p3 - Analogie avec `sudo -s`, imaginons une situation similaire dans un contexte de la vie réelle.

### Analogie
Vous êtes toujours cet employé dans la réception sécurisée, mais cette fois, au lieu de prendre l'identité complète du directeur, vous obtenez une permission spéciale.

- **Utilisation de `sudo -s`:** Imaginez que vous avez besoin d'utiliser l'ordinateur du directeur pour effectuer une tâche précise qui nécessite ses droits d'accès. Au lieu de devenir le directeur, la sécurité vous donne une clé temporaire (le privilège root) qui vous permet d'utiliser l'ordinateur du directeur, mais en tant que vous-même, l'employé. Vous entrez dans son bureau, utilisez son ordinateur avec tous les droits d'accès du directeur, mais vos préférences personnelles (votre environnement) sont préservées. Vous pouvez accéder à ses fichiers et applications à niveau élevé, mais vos raccourcis et vos réglages personnels restent les mêmes.

Dans cette analogie, `sudo -s` vous permet d'obtenir les privilèges du directeur sans changer complètement d'identité. Vous opérez avec vos propres préférences et environnement, mais avec les droits d'accès élevés nécessaires pour une tâche spécifique.
