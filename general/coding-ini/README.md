# Coding Ini

> Par nature un fichier `.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Fonctionnement d’un fichier .ini

Par nature un fichier `.ini` est descriptif, il est composé d'une liste de [sections]. Chaque section possède éventuellement des paramètres décrit avec un nom et une valeur.  `ezs` considère chaque section comme une instruction, les listes des sections comme l'ordonnancement d'une suite de traitements.

Les paramètres des section sont les paramètres des instructions. Dans un fichier .ini standard, les paramètres sont des valeurs statiques mais `ezs` propose également un paramétrage dynamique et contextuel des traitements. Cela permet d’adapter les traitements aux données reçues ou de paramétrer les traitements avec des variables d’environnement Toutes les valeurs des paramètres d’une section peuvent être dynamiques ou statiques.

## Nom de l'instruction

Le nom de chaque section du fichier .ini correspond au nom d'une fonction de traitement ([une instruction](statement)).

Les fonctions disponibles varient en fonction des [plugins](plugin) qui sont installés et déclarés en début de fichier. Par défaut, seules fonctions [core](plugin-core) sont disponibles.

Pour charger d'autres fonctions on utilisera l'instruction `[use]`. Exemple:  

```ini
[use]
plugin = basics
plugin = analytics
```
Dans cette exemple, on chargera les plugins [basics](plugin-basics) et [analytics](plugin-analytics) ce qui permettra d'utiliser dans le fichier .ini toutes les fonctions de ces deux plugins.


## Valeurs statiques

Pour donner une valeur statique à un paramètre, il suffit de la renseigner de
manière "naturelle". `ezs` se charge ensuite de définir automatiquement son
type.

### Chaîne de caractères

```ini
[STATEMENT]
param1 = valeur une
```

### Chiffres et Nombres

```ini
[STATEMENT]
param1 = 1234
param2 = 1.234
```

### Booléens

```ini
[STATEMENT]
param1 = true
param2 = false
```

### Caractères spéciaux et autres cas

```ini
[STATEMENT]
param1 = fix('\n')
param2 = fix('1.234')
param3 = fix(1234)
param4 = fix('Voici ', 'valeur', ' ', 'concaténé

*[truncated — see source for full prompt]*