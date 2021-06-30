# Les chaînes de caractères (string)

**Introduction sur les strings et la concatenation**

## Exercice

Créez une fonction qui prend un mot et détermine s’il est pluriel ou singulier. Un mot pluriel est celui qui se termine par « s ». S’il est pluriel renvoyer TRUE sinon FALSE.

Exemple:
```
check("enfants") ➞ True

check("filles") ➞ True

check("fille") ➞ False

check("enfant") ➞ False
```

## Exercice

Créez une fonction qui renvoie TRUE si une chaîne contient des espaces. Sinon renvoie FALSE.

Exemple:

containSpaces("Thomas") ➞ False

containSpaces("Hello World!") ➞ True

containSpaces(" ") ➞ True

containSpaces("") ➞ False


## Exercice

Créez une fonction qui compte le nombre de syllabes d’un mot. Chaque syllabe est séparée par un tiret -.

Exemple:

nbrOfSlab("prin-temps") ➞ 2

nbrOfSlab("ar-rê-te") ➞ 3

nbrOfSlab("ther-mo-mè-tre") ➞ 4