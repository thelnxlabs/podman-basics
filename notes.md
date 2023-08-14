podman version --> gives the go version used as well   
  on ubuntu 22.04, seems a quite old version (3.x.x and go version 1.18.x)  
    --> tocheck the repo that provides the soft: apt policy podman 
  in rhel, what is packaged is relatively new but not the latest though: podman 4.4.3 with go 1.19.6   
    --> to check the repo here: dnf list podman (its in appstreams)


podman images -f 'dangling=true' --> images no longer tagged AND not used by any container (tant quil ya meme un ancien container stopped, il ne va pa clean limage)
                                                                                            qui plus est, si il clean on verra a loutput les couches supprimées avec un rc=0 - si il prune pas il ya kan meme aussi un rc=0
podman image prune  --> to get rid of the dangling images
Au lieu de echo y | podman image prune, faire podman image prune -f 
  ou plus flex mais completement overkill: podman rmi -f $(podman images -f 'dangling=true' -q)

the command podman info is really enjoying.
u can see both dynamic and static info like number of images, number of current containers, cgroup version, location of image store, location of containers store,
backing filesystem, load on the system, the default registries, etc ... 
for e.g.:
--> better monitor storage utilization for /home than /var/lib/containers 
--> compare the OCI specs between docker info and podman info 
cgroup2 est plus neat que cgroup1 -- mount | grep cgroup 

kan tu desinstalle podman, ca ne perd pas les stores.

-- LE FLOW --
--> on cree les networks necessaires, un network pour la comm entre API et DB, un autre network pour la comm entre API et FRONT
--> on cree davance un named volume pour la persistence des data
--> au lieu de forcement utiliser nodejs pour le front car dans les requetes javascript coté client, on ne peut pas adresser l'API avec son nom
    puiske ca se passe dans le browser, on peut utiliser nginx comme reverse proxy sur le container front

* considerons le stack: postgresql db + python api + html frontend 
* les images postgresql ont pour sinitialiser un repertoire start présent dans un dossier désigné par la variable CONTAINER_SCRIPTS_PATH 
  tout script .sh dans ce repertoire se verra automatiquement exécuté au lancement du ctr 
  on créée dc un script .sh qui va soccuper du DDL et eventuellement du DML initial -- abuser de la clause IF EXISTS pour ne pas dupliquer a chauqe lancement de ctr --
  il faut prendre lhabitude kan on pull une image de faire un printenv
  podman run --rm image env --> si limage ets bien documentee on verra toutes les vars dispo 
* mais attention aux droits avec postgresql liès a lauth initial; jai du exporter PGPASSWORD dans le .sh malgré la specification de psql -U dans le db_init.sql 
* dans db_init.sql, toujours utiliser des paths complets
* le networking avec dns enabled nous permet de ne pas exposer le port DB ainsi que le port API, on nexpose que le port FRONT
* lorskon utilise linstruction VOLUME dans le Containerfile, ca créée certes un volume a la creation du conteneur mais il est ephemere
* pour l'API, ne pas oublier dutiliser un venv avec python3 -m venv env && source env/bin/activate 
  afin davoir juste le requirements.txt suffisant: pip freeze > requirements.txt 

--> remarque: lorske je run uncontainer basé sur une image avec nginx en CMD et ke je fais un run -it sh par exemple, je override le CND donc je dois
    pas mattendre a pouvoir me connecter a nginx; curl localhost va echouer !!!
    et si javais fait limage avec ENTRYPOINT["nginx","-g","daemon off;"] je nallais éeée pas pouvoir invoquer sh

>> PODMAN CP  
   ca copie non seulement du host vers le container et vice-versa, mais aussi d'un container a l'autre !!!
   
