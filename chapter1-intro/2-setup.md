## Mise en place de Podman  

### Installation de Podman sur Linux:

**Distributions basées sur Debian (comme Ubuntu):**  

1. Mettez à jour la liste des paquets:  

`sudo apt update`  

2. Installez les paquets nécessaires:  

`sudo apt -y install software-properties-common uidmap` 

3. Ajoutez le dépôt de Podman:  

`sudo add-apt-repository -y ppa:projectatomic/ppa` 

4. Installez Podman:  

```bash
sudo apt update
sudo apt -y install podman
``` 

**Distributions basées sur Red Hat (comme CentOS, Fedora):**

    Installez Podman:

    bash

    sudo dnf -y install podman

b. Commandes Basiques de Podman:

    Vérifiez la version de Podman:

    bash

podman --version

Obtenez des informations sur l'installation de Podman:

bash

    podman info

c. Avantages de Podman par rapport à d'autres outils de conteneurisation:

    Fonctionne sans daemon: Contrairement à Docker, Podman n'a pas besoin d'un daemon tournant en arrière-plan. Cela réduit la complexité et les risques potentiels.

    Fonctionnement sans privilèges (rootless): Avec Podman, vous pouvez créer et exécuter des conteneurs sans être l'utilisateur root, renforçant la sécurité.

    Compatibilité avec Docker: Podman est conçu pour être compatible avec les commandes Docker, ce qui facilite la transition pour ceux qui sont déjà familiarisés avec Docker.