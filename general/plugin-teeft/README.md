# Plugin Teeft

> ## Présentation

Ce plugin propose une série d'instructions pour extraire des mots-clés d'un
texte français ou anglais en utilisant l'algorithme Teeft

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# teeft

## Présentation

Ce plugin propose une série d'instructions pour extraire des mots-clés d'un
texte français ou anglais en utilisant l'algorithme Teeft.

C'est le paquet officiel qui fait suite à l'expérimentation
[ezs-teeftfr](https://github.com/istex/node-ezs-teeftfr).

### Bibliographie

Cuxac P., Kieffer N., Lamirel J.C. : SKEEFT: indexing method taking into account the structure of the document. 20th Collnet meeting, 5-8 Nov 2019, Dalian, China.

## Installation

```bash
npm install @ezs/core
npm install @ezs/teeft
```

## Flux

Le principe est de décomposer le flux en une série d'instructions ayant chacune
ses propres paramètres (voir [usage](#usage)).

Voici la séquence typique d'instructions qui permet de lire les fichiers `.txt`
d'un répertoire et de les envoyer aux tokenizers de phrase, puis de mots;
ensuite on procède à un étiquetage grammatical, puis on extrait les termes, et
on les filtre (par fonction grammaticale), on enlève les nombres, on supprime
les mots vides, on calcule les fréquences des tokens, puis leur spécificité,
enfin, on les filtre suivant leur fréquence.

```txt
[ "/path/to/a/directory/of/documents" ] ->

[TeeftListFiles]
pattern = *.txt

--> [ "/path1", "path2", ... ] -->

[TeeftGetFilesContent]

--> [ { path, content }, ... ] -->

[TeeftSentenceTokenize]

--> [ { path, sentences: [ "sentence", ... ] }, ... ] -->

[TeeftTokenize]

--> [ { path, sentences: [ ["token", ... ], ...] }, ... ] -->

[TeeftNaturalTag]

--> [  { path, sentences: [ [
  {
    token: "token",
    tag: [ "tag", ...]
  }, ...
 ], ... ] }, ... ]


[TeeftExtractTerms]
nounTag = NOM
adjTag = ADJ

--> [  { path, terms:  [
  {
    term: "monoterm",
    tag: [ "tag", ...],
    frequency,
    length
  },
  {
    term: "multiterm",
    frequency,
    length
  }, ...
 ] }, ... ]

[TeeftFilterTags]
tags = NOM
tags = ADJ

--> [  { path, terms:  [
  {
    term: "monoterm",
    tag: [ "tag", ...],
    frequency,
    length
  },
  {
    term: "multiterm",
    frequency,
 

*[truncated — see source for full prompt]*