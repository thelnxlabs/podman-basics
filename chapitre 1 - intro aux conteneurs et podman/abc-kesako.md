## Qu'est-ce qu'un conteneur ?  

 Un conteneur est comme un appartement miniature pour une application et tout ce dont elle a besoin pour fonctionner.  
<p>

![analogie_conteneur](../images/container_appartement.png "Cest quoi un conteneur ?")

<p>

## Pourquoi avons-nous besoin des conteneurs ?   

* Ils nous permettent de s'assurer que notre application fonctionnera de la même manière, peu importe où elle est déployée.  
* Ils offrent une isolation, garantissant que les applications ne se gênent pas mutuellement.  
* Facilité de déploiement et de mise à l'échelle.  
<p>

## Comment les conteneurs diffèrent-ils des machines virtuelles (VM)?

Imaginez une maison (VM) par rapport à un appartement (conteneur) dans un grand immeuble. Les VMs ont leurs propres ressources système tandis que les conteneurs partagent le même système mais restent isolés les uns des autres.      

## Introduction à Podman: Pourquoi Podman et ses avantages.

* Podman est comme un concierge pour votre immeuble d'appartements (conteneurs). Il s'occupe de la création, de la gestion et de la suppression des conteneurs.  
* Pas besoin de daemon en arrière-plan, fonctionne en tant qu'utilisateur régulier (rootless).  
* Compatible avec les commandes Docker et Docker Compose.  
