# Coding Statement

> ## Fonction

La fonction est exécutée pour chaque élément du flux d'entrée, plus une dernière
fois pour indiquer qu'il n'y a plus d’élément à traiter.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Fonctionnement d’une instruction

## Fonction

La fonction est exécutée pour chaque élément du flux d'entrée, plus une dernière
fois pour indiquer qu'il n'y a plus d’élément à traiter. À chaque fois, elle
reçoit deux paramètres : `data` & `feed`.

> Si un flux contient 10 éléments, la fonction sera exécutée 11 fois.

Chaque fonction possède un `scope` lui donnant accès à des fonctions dédiées.
Le `scope` est partagé entre chaque appel pour chaque élément.

### data

Contient la valeur de l'élément courant du flux, pour un flux texte ou binaire,
`data` contiendra un `chunk`. Pour un flux d’objets `data` contiendra un objet
JavaScript.

### feed

Est un objet permettant de contrôler le flux en sortie de la fonction. Il permet
de générer zéro, un ou N élément(s) en sortie. L'objet `feed` propose les
fonctions suivantes :

#### feed.write(something)

Permet d'envoyer un élément dans le flux de sortie.
Cette fonction peut être exécutée plusieurs fois.

#### feed.flow(stream, [callback])

Permet d'envoyer le contenu d'un *stream* à l'élément suivant.

Chaque *chunk* est envoyé séparément. Quand le stream s'arrête ("end"),
l'élément courant est fermé, sauf si une fonction de *callback* est passée en
argument. Dans ce cas, il faudra fermer l'élement courant explicitement via un
appel à `feed.end()`.

Cette fonction peut être exécutée plusieurs fois.

#### feed.end()

Permet de fermer le flux pour l’élément courant.

#### feed.send(something)

Permet d’enchaîner `feed.write` et `feed.end` en une seule fonction.

#### feed.close()

Permet de fermer définitivement le flux de sortie, plus aucun élément ne pourra
être envoyé.

#### feed.stop(withAnError)

Permet de fermer le flux de sortie en précisant l'erreur ayant provoqué l’arrêt
impromptu, plus aucun élément ne pourra être envoyé.

## Scope

### Environnement partagé

Le *scope* de chaque fonction est le même entre chaque appel à la fonction pour
chaque élément du flux.
C’est un moyen simple pour partager des données entr

*[truncated — see source for full prompt]*