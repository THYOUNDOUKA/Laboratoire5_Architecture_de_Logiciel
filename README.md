GEI311 — Laboratoire 5 : Déploiement et distribution de charge

1\. Informations générales



Cours : Architecture des logiciels (GEI311)

Labo : #5 — Déploiement et distribution de charge

Auteurs :



Membre A : Eliel Kone Tawelé (KONT23080402) et Theresa Maelle YOUNDOUKA LOUKOUNGOU (YOUT21549901)



Membre B : Yannick Hien (HIEN01070300)

Session : Automne 2025



2\. Partie 1 — Réponses aux questions

Question 6



Lorsque l'application Python est arrêtée, nous constatons que la page http://10.227.234.214:3000/  n’est plus accessible. Cela montre que le serveur Flask ne fonctionne que tant que le script app\_Eliel\_Maelle.py est actif (c'est-à-dire tant que le programme tourne dans le terminal).

Il est donc conclu qu'aucune requête n’est traitée lorsque le terminal est fermé.



Question 16



Lorsqu’on navigue vers l’adresse http://10.227.234.214:8181/ et qu’on rafraîchit la page à plusieurs reprises, nous observons que les réponses proviennent alternativement de l’IP du membre A (10.227.234.214) et de l’IP du membre B (10.227.234.219).Cela prouve que Nginx distribue les requêtes de façon équilibrée (round-robin).



Question 17



Lorsqu’on arrête l'application du membre A (10.227.234.214), on constate que :



* http://10.227.234.214:3000/ devient inaccessible. C’est normal, car l’application Flask du membre A est arrêtée : plus aucun service n’écoute sur le port 3000, donc l’accès direct à ce port n’est plus possible.



http://10.227.234.214:8181/ reste accessible.

En effet, Nginx (qui écoute sur le port 8181 de la machine A) continue de fonctionner et redirige les requêtes vers le serveur du membre B (10.227.234.219:3001) tant que ce serveur est en marche. Cela illustre la tolérance aux pannes grâce au distributeur de charge.



3\. Partie 2 — Résumé des apprentissages



Lors de ce laboratoire, nous avons appris à :



* Déployer une application Flask sur un réseau ;



* Utiliser Nginx comme reverse proxy (serveur intermédiaire) recevant les requêtes sur le port 8181 pour les transmettre à Flask, mais aussi comme distributeur de charge (load balancer) gérant la répartition entre les serveurs du membre A et du membre B ;



* Enfin, configurer un réseau local (IP, ports, pare-feu).
