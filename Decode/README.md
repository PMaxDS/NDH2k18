# Decode

## Introduction

**Catégorie** : Forensic

**Difficulté** : Facile

**Points** : 50

L'épreuve présente deux fichiers. Un .zip et in .pcapng

## Analyse

Pour commencer, j'ai essayé d'ouvrir bêtement l'archive .zip. Afin de procéder à l'extraction des fichiers un mot de passe est demandé.
Je n'ai pas décidé de chercher plus loin sur ce sujet et je me suis concentré sur le fichier .pcapng

Le fichier .pcapng présente un sniff de communication réseau, avec uniquement de la communication via HTTP.
Cela facilite le travail vu que la communication se fait en clair.

En filtrant uniquement les trames réseaux par HTTP, je facilite la lecture du trafic et j'enlève par la même occasion les trames
TCP afin de ne pas surcharger l'affichage dans WireShark

Ne sachant pas quoi faire de cela, mais ayant conscience que l'information que je cherche (ici le mot de passe de l'archive .zip)
se trouve dans le flux réseau que j'ai sous les yeux, je cherche rapidement un petit tuto sur YouTube afin de m'indiquer la démarche
à suivre afin d'isoler des informations pouvant transiter par les cookies.

Je tombe sur cette vidéo https://www.youtube.com/watch?v=7ezGTP99xSw, qui m'indique
que pour trouver ces informations, il est judicieux de chercher un trame HTTP ayant l'action POST dans ses informations.

Une analyse rapidement de la seule trame correspondant à ces critères me montre directement les champs form, dont un qui porte le
nom "pwd" ayant pour valeur "95/@Jywf5R@666"

Pur hasard, ça correspond au mot de passe permettant d'extraire les fichiers de l'archive zip. Un seul fichier dans l'archive
contenant des octets écrits en binaire.

Une simple traduction du binaire via n'importe quel outil en ligne donne le flag à trouver qui est "ndh16_cbfce5e36dd33c6adce32a6b577be161b9815893"
