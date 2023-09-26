Quentin : 

Cette semaine j'ai travaillé sur le reverse engineering sur le cas des caches LRU.

Mon but était de comprendre ce que faisaient les méthodes de haut niveau du projet, sans pour autant trop me soucier des opérations de bas niveau.
Pour cela, j'ai commencé par farfouiller principalement dans les tests. J'ai très vite vu que la méthode "ifAbsentPut" était beaucoup utilisée, je m'y suis donc intéréssé.
De plus, il y avait un test dont je comprenais globalement l'éxécution d'un point de vue extérieur, mais pour moi il ne devait pas être validé : 


mettre test 400 là

Pour cela, je suis donc allé voir la documentation de la méthode ifAbsentPut. 
N'ayant pas toputes les informations que je suis venu chercher, j'ai fouillé dans le projet et j'ai compris différents concepts, comme les statistiques, le hit or miss,
le cache d'indices pour le cache mais il y avait une notion dont je ne saissisais pas l'entièreté : le weight, car la documentation de ce concept n'était pas suffisante à l'endroit où il était présenté.

Finalement, c'est dans la documentation de la classe abstraite des caches que j'ai compris, le poids total des éléments équivaut plus ou moins au nombre d'éléments dans le cache.
En fin de compte, ça ne répondait pas à mes questions, mais dans la description de cette classe, il était aussi expliqué que si le cache était plein, on enlevait les éléments les plus anciens pour faire de la place,
et c'est donc pour ça que le test fonctionne pour le 5401ème élément et pas le 5400ème (il y 600 places dans le cache).

Avec du recul, ce focntionnement était sous mes yeux (Least Recently Used cache), et j'aurais dû plus réfléchir à l'utilité globale du projet et tout ce processus aurait été bien plus court.
