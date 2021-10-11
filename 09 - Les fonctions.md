# Les fonctions

Une fonction est un bloc d'instructions qui porte un nom, qui peut prendre des paramètres en entrée et peut renvoyer une valeur en sortie.

Prenons un exemple simple d'un affichage :

```csharp
static void AfficheHello(){
  Console.WriteLine("Hello !");
}
```

Cette fonction :
- a comme nom `AfficheHello`, 
- n'a pas de paramètre en entrée (car il n'y a rien dans les parenthèses qui suivent le nom), 
- a une seule instruction (`Console.WriteLine...`) comme bloc d'instructions
- ne renvoie rien (indiqué par le `void` avant le nom de la fonction).

> Le mot clé `static` doit toujours être mis avant une fonction (nous analyserons pourquoi en Q2). 

Pour appeler cette fonction, il suffit de donner son nom et de mettre des parenthèses ensuite :

```csharp
using System;
          
public class Program
{
  static void AfficheHello(){
    Console.WriteLine("Hello !");
  }

  public static void Main()
  {
    Console.WriteLine("Avant");
    AfficheHello();
    Console.WriteLine("Après");
  }
}
```

Quand le `Main` est exécuté et qu'il tombe sur l'appel de `AfficheHello()`, le programme va aller exécuter le code contenu dans cette fonction (`Console.WriteLine...`) et revenir où il était dans le `Main` et continuer. Le résultat de l'exécution de ce programme est donc :

```
Avant
Hello !
Après
```

## Les paramètres

Prenons un exemple un peu moins simple d'un affichage d'un texte fourni en entrée :

```csharp
static void Affiche(string text){
  Console.WriteLine(text);
}
```

Cette fonction :
- a comme nom `Affiche`, 
- a un paramètre en entrée nommé `text` et de type `string`, 
- a une seule instruction (`Console.WriteLine...`) comme bloc d'instructions
- ne renvoie rien (indiqué par le `void` avant le nom de la fonction).

Pour appeler cette fonction, il suffit de donner son nom et mettre le texte à afficher entre des parenthèses  :

```csharp
using System;
          
public class Program
{
  static void Affiche(string text){
    Console.WriteLine(text);
  }

  public static void Main()
  {
    Console.WriteLine("Avant");
    Affiche("Bonjour :)");
    Console.WriteLine("Après");
  }
}
```

Quand le `Main` est exécuté et qu'il tombe sur l'appel de `Affiche("Bonjour :)")`, le programme va aller recopier la valeur `"Bonjour :)"` dans la variable `text` et exécuter le code contenu dans cette fonction (`Console.WriteLine...`). Une fois la fonction exécutée, le programme va revenir où il était dans le `Main` et continuer. Le résultat de l'exécution de ce programme est donc :

```
Avant
Bonjour :)
Après
```

Chaque fonction peut avoir 0, 1 ou plusieurs paramètres. Ceux-ci seront séparaés par des virgules. Par exemple ici, nous pourrions la fonction suivante :

```csharp
static void AfficheNFois(string text, int nb){
  for(int i = 0; i < nb; i++) {
    Console.WriteLine(text);
  }
}
```

Cette fonction :
- a comme nom `AfficheNFois`, 
- a deux paramètres en entrée:
  - le premier nommé `text` et de type `string`,
  - le second nommé `nb` et de type `int` 
- a deux instructions (`for` et `Console.WriteLine...`) comme bloc d'instructions
- ne renvoie rien (indiqué par le `void` avant le nom de la fonction).


Pour appeler cette fonction, il suffit de donner son nom et mettre le texte à afficher et le nombre de fois à l'afficher entre des parenthèses  :

```csharp
using System;
          
public class Program
{
  static void AfficheNFois(string text, int nb){
    for(int i = 0; i < nb; i++) {
      Console.WriteLine(text);
    }
  }

  public static void Main()
  {
    Console.WriteLine("Avant");
    AfficheNFois("Bonjour :)", 3);
    Console.WriteLine("Après");
  }
}
```

Quand le `Main` est exécuté et qu'il tombe sur l'appel de `AfficheNFois("Bonjour :)", 3)`, le programme va aller recopier la valeur `"Bonjour :)"` dans la variable `text` et `3` dans `nb`. Le programme exécute ensuite le code contenu dans cette fonction (le `for` avec `Console.WriteLine...`). Une fois la fonction exécutée, le programme va revenir où il était dans le `Main` et continuer. Le résultat de l'exécution de ce programme est donc :

```
Avant
Bonjour :)
Bonjour :)
Bonjour :)
Après
```

## La valeur de retour

Toutes les fonctions décrites avant ne renvoie aucune valeur. Elles affichent des `strings` et se termine sans renvoyer de valeur au code qui l'a appelé. 

Prenons l'exemple de la fonction suivante :

```csharp
static string getNomDuProf(){
  return "Frédéric Pluquet";
}
```

Cette fonction :
- a comme nom `getNomDuProf`, 
- n'a aucun paramètre en entrée 
- a une seule instruction (`return ...`) comme bloc d'instructions
- renvoie une chaîne de caractères (indiqué par le `string` avant le nom de la fonction).

Pour appeler cette fonction, il suffit de donner son nom et mettre des parenthèses  :

```csharp
using System;
          
public class Program
{
  static string getNomDuProf(){
    return "Frédéric Pluquet";
  }

  public static void Main()
  {
    Console.WriteLine("Avant");
    string unJoliNom = getNomDuProf();
    Console.WriteLine("Votre nom est : {0}", unJoliNom);
    Console.WriteLine("Après");
  }
}
```

Quand le `Main` est exécuté et qu'il tombe sur la ligne `string unJoliNom = getNomDuProf()`, le programme va d'abord exécuté la fonction `getNomDuProf()` pour savoir quelle valeur assigner à la variable `unJoliNom`. 

Le programme exécute donc le code contenu dans cette fonction : la ligne `return "Frédéric Pluquet";` indique au programme que la fonction se finit et que la valeur de retour est le `string` `"Frédéric Pluquet"`. 

Une fois la fonction exécutée, le programme va revenir où il était dans le `Main`. On peut considérer que la valeur `"Frédéric Pluquet"` prend alors la place de l'appel de la fonction `getNomDuProf()` :

```csharp
string unJoliNom = "Frédéric Pluquet";
```

Et le programme continue son exécution : la variable `unJoliNom`est assignée puis affichée et le string `"Après"` est affiché :

```
Avant
Votre nom est : Frédéric Pluquet
Après
```

Prenons l'exemple un peu plus complexe de la fonction suivante :

```csharp
static string demande(string question){
  Console.WriteLine(question);
  string réponse = Console.ReadLine();
  return réponse;
}
```

Cette fonction :
- a comme nom `demande`, 
- a un paramètre en entrée nommé `question` de type `string`
- a trois instructions (`Console.WriteLine...`, `string réponse = ...` et `return réponse`) comme bloc d'instructions
- renvoie une chaîne de caractères (indiqué par le `string` avant le nom de la fonction).

Pour appeler cette fonction, il suffit de donner son nom et mettre la question à afficher entre parenthèses :

```csharp
using System;
          
public class Program
{
  static string demande(string question){
    Console.WriteLine(question);
    string réponse = Console.ReadLine();
    return réponse;
  }

  public static void Main()
  {
    Console.WriteLine("Avant");
    string nom = demande("Quel est votre nom ?");
    Console.WriteLine("Votre nom est : {0}", nom);
    Console.WriteLine("Après");
  }
}
```

Quand le `Main` est exécuté et qu'il tombe sur la ligne `string nom = demande("Quel est votre nom ?")`, le programme va d'abord exécuté la fonction `demande("Quel est votre nom ?")` pour savoir quelle valeur assigner à la variable `nom`. 

Le `string` `"Quel est votre nom ?"` est copié dans la variable `question` et le code contenu dans cette fonction est exécuté : le `Console.WriteLine...` et `string réponse = Console.ReadLine()`  qui va remplir la variable locale `nom` par ce que l'utilisateur a entré. 

La dernière ligne de la fonction `return réponse;` indique au programme que la fonction se finit et que la valeur de retour est celle contenue dans la variable `réponse`. 

Une fois la fonction exécutée, le programme va revenir où il était dans le `Main`. On peut considérer que la valeur contenue dans `réponse` prend alors la place de l'appel de la fonction `demande("Quel est votre nom ?")`. Si on entre `"Fréd"` dans `réponse`, le programme considère alors qu'au retour dans le `Main`, il doit exécuter la ligne suivante :

```csharp
    string nom = "Fréd";
```

Et le programme continue son exécution : la variable `nom`est assignée puis affichée et le string `"Après"` est affiché :

```
Avant
Quel est votre nom ? 
Fréd
Votre nom est : Fréd
Après
```


# Exercices


## Exercice 1

Créez une fonction `incremente` qui prend un entier en paramètre, incrémente ce nombre (+ 1) et renvoie le résultat.

Exemples:

```csharp
Console.WriteLine(incremente(1)); // affiche 2
Console.WriteLine(incremente(2)); // affiche 3
Console.WriteLine(incremente(5)); // affiche 6
Console.WriteLine(incremente(-1)); // affiche 0
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{  
  static int incremente(int n){
    n++;
    return n;
  }

  public static void Main()
  {
  Console.WriteLine(incremente(1)); // affiche 2
  Console.WriteLine(incremente(2)); // affiche 3
  Console.WriteLine(incremente(5)); // affiche 6
  Console.WriteLine(incremente(-1)); // affiche 0
  }
}
```

</details>

## Exercice 2

Écrivez une fonction `resteDiv` qui prend en paramètres deux nombres et renvoie le reste de la division entière du premier paramètre par le second. Utilisez l'opérateur `%` capable de fournir le reste d’une division.

Exemples:

```csharp
Console.WriteLine(resteDiv(10,3)); // affiche 1, car 10 / 3 = 3 et 10 - 3 * 3 = 1
Console.WriteLine(resteDiv(6,3)); // affiche 0, car 6 / 3 = 2 et 6 - 3 * 2 = 0
Console.WriteLine(resteDiv(17, 7)); // affiche 3, car 17 / 7 = 2 et 17 - 7 * 2 = 3
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  static int resteDiv(int dividende, int diviseur){
    int reste = dividende % diviseur;
    return reste;
  }

  public static void Main()
  {
    Console.WriteLine(resteDiv(10,3)); // affiche 1, car 10 / 3 = 3 et 10 - 3 * 3 = 1
    Console.WriteLine(resteDiv(6,3)); // affiche 0, car 6 / 3 = 2 et 6 - 3 * 2 = 0
    Console.WriteLine(resteDiv(17, 7)); // affiche 3, car 17 / 7 = 2 et 17 - 7 * 2 = 3
  }
}
```

</details>

## Exercice 3

Créez une fonction `estDivisiblePar5` qui renvoie `True` si un entier est divisible par 5, sinon retournez `False`.

Exemples:

```csharp
Console.WriteLine(estDivisiblePar5(5)); // affiche True
Console.WriteLine(estDivisiblePar5(10)); // affiche True
Console.WriteLine(estDivisiblePar5(6)); // affiche False
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  static bool estDivisiblePar5(int nb){
	  return nb % 5 == 0;
  }

  public static void Main()
  {
    Console.WriteLine(estDivisiblePar5(5)); // affiche true
    Console.WriteLine(estDivisiblePar5(10)); // affiche true
    Console.WriteLine(estDivisiblePar5(6)); // affiche false
  }
}
```

</details>

## Exercice 4

Créez une fonction `isEmpty` qui renvoie `True` si la chaîne de caractères passée en paramètre est vide et sinon renvoie `False`.

Exemples:

```csharp
Console.WriteLine(isEmpty("1")); // affiche False
Console.WriteLine(isEmpty("")); // affiche True
Console.WriteLine(isEmpty("Trop cool")); // affiche False
Console.WriteLine(isEmpty("   ")); // affiche False
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  static bool isEmpty(string texte){
	  return texte.Length == 0;
  }

  public static void Main()
  {
    Console.WriteLine(isEmpty("1")); // affiche False
    Console.WriteLine(isEmpty("")); // affiche True
    Console.WriteLine(isEmpty("Trop cool")); // affiche False
    Console.WriteLine(isEmpty("   ")); // affiche False
  }
}
```

</details>


## Exercice

Créez une fonction qui prend un nombre comme argument et renvoie « pair » pour les nombres pairs et « impair » pour les nombres impairs.

Exemple:

check(2) ➞ "pair"

check(7) ➞ "impair"

check(22) ➞ "pair"

## Exercice

Créez une fonction qui prend deux chaînes str1 et str2 comme arguments et renvoie TRUE si le nombre total de caractères dans la première chaîne est égal au nombre total de caractères dans la deuxième chaîne sinon renvoie FALSE.

Exemple:

compareSize("AA", "BB") ➞ True

compareSize("123", "1") ➞ False

compareSize("Ali", "Bob") ➞ True

## Exercice

Dans ce défi, un fermier vous demande de lui dire combien de pattes peuvent être comptées parmi tous ses animaux. Il y a trois espèces:

poulets = 2 pattes
vaches = 4 pattes
chevaux = 4 pattes
Le fermier a compté ses animaux et il vous donne un sous-total pour chaque espèce. Vous devez implémenter une fonction qui renvoie le nombre total de pattes de tous les animaux.

L’ordre des animaux transmis à la fonction est `nbrsPattes(poulets, vaches, chevaux)`.

Exemple:
nbrsPattes(1, 4, 2) ➞ 26

nbrsPattes(2, 2, 2) ➞ 20

nbrsPattes(2, 0, 3) ➞ 16

N’oubliez pas que le fermier veut connaître le nombre total de pattes et non pas le nombre total d’animaux.

## Exercice

Créez une fonction qui prend un tableau de nombres et renvoie le plus grand nombre du tableau.

Exemple:

getBigNbr([9, 7, 1, 5]) ➞ 9

getBigNbr([100, -100, 1, 50]) ➞ 100

getBigNbr([9, 9, 9, 9]) ➞ 9


## Exercice

Créez une fonction qui compte le nombre de syllabes d’un mot. Chaque syllabe est séparée par un tiret -.

Exemple:

nbrOfSlab("prin-temps") ➞ 2

nbrOfSlab("ar-rê-te") ➞ 3

nbrOfSlab("ther-mo-mè-tre") ➞ 4

## Exercice

Créez une fonction qui prend un tableau et une chaîne comme arguments et renvoie l’index de la chaîne.

Exemple:

getIndex(new string[] {"A", "B", "C", "D"}, "B") ➞ 1

getIndex(new string[] {"Alex", "Bob", "Emily", "Tom"}, "Emily") ➞ 2

getIndex(new string[] {"C#", "PHP", "C++", "Java"}, "C#") ➞ 0

## Exercice

La distance de Hamming est le nombre de caractères qui diffèrent entre deux chaînes. Prenons un exemple :

Str1: « abcdde »
Str2: « abcdbe »

Distance de Hamming = 1 car « d » et « b » est la seule différence.

Créez une fonction qui calcule la distance de hamming entre deux chaînes.

Exemple:

distanceHamming("abcdde", "abcdbe") ➞ 1

distanceHamming("abcdef", "defabc") ➞ 6

distanceHamming("agresser", "adresser") ➞ 1

distanceHamming("attention", "intention") ➞ 2

## Exercice

Écrivez une fonction qui prend la base et la hauteur d’un triangle et retourne sa surface. Notez que la surface d’un triangle est: (base * hauteur) / 2

Exemple:
getSurface(8, 2) ➞ 8

getSurface(7, 3) ➞ 10

## Exercice

Créez une fonction qui prend un tableau et renvoie le dernier élément du tableau.

Exemple:
getLastElem([1, 2, 3, 4]) ➞ 4

getLastElem([8, 7, 6]) ➞ 6

getLastElem([1]) ➞ 1


