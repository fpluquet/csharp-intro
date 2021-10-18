# Les fonctions

Une fonction est un bloc d'instructions qui porte un nom, qui peut prendre des paramètres en entrée et peut renvoyer une valeur en sortie.

Commençons par un exemple simple :

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

Toutes les fonctions décrites avant ne renvoie aucune valeur. Elles affichent des `strings` et se termine sans renvoyer de valeur au code qui l'a appelée. 

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
static string Demande(string question){
  Console.WriteLine(question);
  string réponse = Console.ReadLine();
  return réponse;
}
```

Cette fonction :
- a comme nom `Demande`, 
- a un paramètre en entrée nommé `question` de type `string`
- a trois instructions (`Console.WriteLine...`, `string réponse = ...` et `return réponse`) comme bloc d'instructions
- renvoie une chaîne de caractères (indiqué par le `string` avant le nom de la fonction).

Pour appeler cette fonction, il suffit de donner son nom et mettre la question à afficher entre parenthèses :

```csharp
using System;
          
public class Program
{
  static string Demande(string question){
    Console.WriteLine(question);
    string réponse = Console.ReadLine();
    return réponse;
  }

  public static void Main()
  {
    Console.WriteLine("Avant");
    string nom = Demande("Quel est votre nom ?");
    Console.WriteLine("Votre nom est : {0}", nom);
    Console.WriteLine("Après");
  }
}
```

Quand le `Main` est exécuté et qu'il tombe sur la ligne `string nom = Demande("Quel est votre nom ?")`, le programme va d'abord exécuter la fonction `Demande("Quel est votre nom ?")` pour savoir quelle valeur assigner à la variable `nom`. 

Le `string` `"Quel est votre nom ?"` est copié dans la variable `question` et le code contenu dans cette fonction est exécuté : le `Console.WriteLine...` et `string réponse = Console.ReadLine()`  qui va remplir la variable locale `réponse` par ce que l'utilisateur a entré. 

La dernière ligne de la fonction `return réponse;` indique au programme que la fonction se finit et que la valeur de retour est celle contenue dans la variable `réponse`. 

Une fois la fonction exécutée, le programme va revenir où il était dans le `Main`. On peut considérer que la valeur contenue dans `réponse` prend alors la place de l'appel de la fonction `Demande("Quel est votre nom ?")`. Si on entre `"Fréd"` dans `réponse`, le programme considère alors qu'au retour dans le `Main`, il doit exécuter la ligne suivante :

```csharp
    string nom = "Fréd";
```

Et le programme continue son exécution : la variable `nom` est assignée puis affichée et le string `"Après"` est affiché :

```
Avant
Quel est votre nom ? 
Fréd
Votre nom est : Fréd
Après
```

## Les paramètres modifiables

Les paramètres d'une fonction sont par défaut des copies des valeurs passées et ne sont pas liées aux variables utilisées pour passer ces valeurs :

```csharp
using System;

public class Program {
  static void Incremente(int a) {
    a = a + 1;
    Console.WriteLine($"a : {a}");
  }

  public static void Main() {
    int nb = 0;
    Incremente(nb);
    Console.WriteLine($"nb : {nb}");
  }
}
```

Ici la valeur de la variable `nb` (dans le `Main`) a été recopiée dans la variable locale `a` lors de l'appel de la fonction. Cette variable locale est indépendante de `nb` et son incrémentation (`a = a + 1;`) n'a donc pas modifié `nb`. On appelle cela un passage par valeur (car seule la valeur est copiée). Le résultat de l'exécution de ce code est donc :

```
a : 1
nb : 0
```

On peut changer ce comportement en ajoutant le mot clé `ref` avant le paramètre (dans sa définition et lors de l'appel): 

```csharp
using System;

public class Program {
  static void Incremente(ref int a) {
    a = a + 1;
    Console.WriteLine($"a : {a}");
  }

  public static void Main() {
    int nb = 0;
    Incremente(ref nb);
    Console.WriteLine($"nb : {nb}");
  }
}
```

En mettant le mot clé `ref`, nous disons que nous voulons que la variable `nb` et la variable `a` soit la même variable. On appelle cela un passage par référence (d'où le mot clé `ref`). Le résultat de l'exécution est donc le suivant :

```
a : 1
nb : 1
```

Au lieu d'utiliser le mot clé `ref`, on peut utiliser le mot clé `out`. Le comportement est presque identique à `ref` mais C# s'attend alors à ce que le paramètre n'ait pas encore de valeur en entrée et qu'il soit initialisé dans la fonction. 

On a déjà rencontré ce mot clé `out` dans `int.TryParse("5", out monEntier)`. Il va mettre la valeur entière dans la variable `monEntier`.

Voici un autre exemple :

```csharp
using System;

public class Program {
  static void DemandeQuestion(string question, out string réponse) {
    Console.WriteLine(question);
    réponse = Console.ReadLine();
  }

  public static void Main() {
    string nom;
    DemandeQuestion("Quel est votre nom ? ", out nom);
    Console.WriteLine($"Bonjour {nom} !");
  }
}
```

La fonction `DemandeQuestion` prend deux paramètres : un `string` `question` qui est passé par valeur et un `string` `réponse` qui est passé par référence en sortie. Comme `réponse` est en `out`, elle n'est pas initialisée, elle ne contient pas de valeur et on ne peut pas la lire. Mais on peut y assigner une valeur qui sera présente également dans la variable `nom`.

L'exécution de ce code donne donc le résultat suivant :

```
Quel est votre nom ?
Fréd
Bonjour Fréd !
```

> Attention ! Comme les mots clés `ref` et `out` désignent un passage par référence, l'entité passée en paramètre doit être assignable (une variable donc ici). Vous ne pouvez donc pas écrire `DemandeQuestion("Quel est votre nom ? ", out "coucou")` car "coucou" n'est pas assignable (`"coucou" = "Fréd";` n'a pas de sens en C#).

# Exercices

## Exercice 1 

En sachant que `Math.Pow(a,b)` renvoie a<sup>b</sup>, que fait le programme suivant ?

```csharp
using System;

public class Program
{
    static double Fn(double a, double b)
    {
        return Math.Pow(a, b);
    }

    public static void Main()
    {
        Console.WriteLine(Fn(10, 3));
    }
}
```

Pour info, la fonction `double Math.Pow(double, double)` est toujours disponible car elle est définie dans la librairie standard. 

> Regardez la classe `Math` (https://docs.microsoft.com/en-us/dotnet/api/system.math.pow?view=net-5.0) pour obtenir plus de fonctions mathématiques pour vos différents projets.

<details>
  <summary>Solution</summary>

La fonction `Fn`:
- attend deux paramètres en entrée nommé `a` et `b` de type `double`
- le type de retour est un `double`
- renvoie le résulat de `Math.Pow(a, b)`.

`Fn(10, 3)` va appler la fonction `Fn` en passant `10` pour `a` et `3` pour `b`.

La fonction va retourner $10^3$, c'est-à-dire 1000. Ce retour de fonction prend la place de l'appel : `Console.WriteLine(Fn(10, 3));` devient `Console.WriteLine(1000);` pour C#. La valeur `1000` est donc affichée.

</details>

## Exercice 2

Que fait le programme suivant ?

```csharp
using System;

public class Program
{
    static void Traitement(int a, ref int b)
    {
        a = a * 3;
        b = a + 8;
    }

    public static void Main()
    {
        int nb1 = 10;
        int nb2 = 20;
        Traitement(nb1, ref nb2);
        Console.WriteLine($"nb1 = {nb1}, nb2 = {nb2}");
    }
}
```


<details>
  <summary>Solution</summary>

La fonction `Traitment`:
- attend deux paramètres en entrée nommé `a` et `b` de type `double`
- `a` est par valeur alors que `b` est passé par référence
- le type de retour est `void` et donc aucun résultat ne sera renvoyé

Lors de l'appel de `Traitement(nb1, ref nb2);`, comme le paramètre `a` est passé par valeur, la valeur de `nb1` est copiée dans `a` et les deux variables sont indépendentes. Une modification de `a` n'aura aucune incidence sur la variable `nb1`.

Par contre, comme le paramètre `b` est passé par référence (`ref`), `b` et `nb2` sont en fait la même variable : si la valeur `b` est modifiée, la valeur de `nb2` le sera également.

Puisque, lors de l'appel de `Traitement`, `nb1` vaut 10 et `nb2` vaut 20, on entre dans la fonction avec `a` égal à 10 et `b` égale à 20.

La variable `a` est modifiée en `a = a * 3`, on met donc `10 * 3 = 30` dans la variable `a` (`nb1` n'est pas modifiée). 

Ensuite la valeur de `b` est modifiée en `b = a + 8`, c'est-à-dire `b = 30 + 8 = 38`. La valeur de `b` est modifiée ainsi que celle de `nb2`.

On revient alors dans le `Main` et le `Console.WriteLine` affiche la valeur des variables `nb1` et `nb2`: 

```
nb1 = 10, nb2 = 38
```

</details>

## Exercice 3

Créez une fonction `Incremente` qui prend un entier en paramètre, incrémente ce nombre (+ 1) et renvoie le résultat.

Exemples:

```csharp
Console.WriteLine(Incremente(1)); // affiche 2
Console.WriteLine(Incremente(2)); // affiche 3
Console.WriteLine(Incremente(5)); // affiche 6
Console.WriteLine(Incremente(-1)); // affiche 0
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{  
  // renvoie le paramètre n + 1
  static int Incremente(int n){
    n++;
    return n;
  }

  public static void Main()
  {
    Console.WriteLine(Incremente(1)); // affiche 2
    Console.WriteLine(Incremente(2)); // affiche 3
    Console.WriteLine(Incremente(5)); // affiche 6
    Console.WriteLine(Incremente(-1)); // affiche 0
  }
}
```

</details>

## Exercice 4

Écrivez une fonction `ResteDiv` qui prend en paramètres deux nombres et renvoie le reste de la division entière du premier paramètre par le second. Utilisez l'opérateur `%` capable de fournir le reste d’une division.

Exemples:

```csharp
Console.WriteLine(ResteDiv(10,3)); // affiche 1, car 10 / 3 = 3 et 10 - 3 * 3 = 1
Console.WriteLine(ResteDiv(6,3)); // affiche 0, car 6 / 3 = 2 et 6 - 3 * 2 = 0
Console.WriteLine(ResteDiv(17, 7)); // affiche 3, car 17 / 7 = 2 et 17 - 7 * 2 = 3
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  // renvoie le reste de la division entière de dividende par diviseur
  static int ResteDiv(int dividende, int diviseur){
    int reste = dividende % diviseur;
    return reste;
  }

  public static void Main()
  {
    Console.WriteLine(ResteDiv(10,3)); // affiche 1, car 10 / 3 = 3 et 10 - 3 * 3 = 1
    Console.WriteLine(ResteDiv(6,3)); // affiche 0, car 6 / 3 = 2 et 6 - 3 * 2 = 0
    Console.WriteLine(ResteDiv(17, 7)); // affiche 3, car 17 / 7 = 2 et 17 - 7 * 2 = 3
  }
}
```

</details>

## Exercice 5

Créez une fonction `EstDivisiblePar5` qui renvoie `True` si un entier est divisible par 5, sinon retournez `False`.

Exemples:

```csharp
Console.WriteLine(EstDivisiblePar5(5)); // affiche True
Console.WriteLine(EstDivisiblePar5(10)); // affiche True
Console.WriteLine(EstDivisiblePar5(6)); // affiche False
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  // renvoie vrai si le paramètre est divible par 5, faux sinon.
  static bool EstDivisiblePar5(int nb){
    return nb % 5 == 0;
  }

  public static void Main()
  {
    Console.WriteLine(EstDivisiblePar5(5)); // affiche true
    Console.WriteLine(EstDivisiblePar5(10)); // affiche true
    Console.WriteLine(EstDivisiblePar5(6)); // affiche false
  }
}
```

</details>

## Exercice 6

Créez une fonction `IsEmpty` qui renvoie `True` si la chaîne de caractères passée en paramètre est vide et sinon renvoie `False`.

Exemples:

```csharp
Console.WriteLine(IsEmpty("1")); // affiche False
Console.WriteLine(IsEmpty("")); // affiche True
Console.WriteLine(IsEmpty("Trop cool")); // affiche False
Console.WriteLine(IsEmpty("   ")); // affiche False
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  // renvoie vrai si le paramètre est vide, faux sinon. 
  static bool IsEmpty(string texte){
    return texte.Length == 0;
  }

  public static void Main()
  {
    Console.WriteLine(IsEmpty("1")); // affiche False
    Console.WriteLine(IsEmpty("")); // affiche True
    Console.WriteLine(IsEmpty("Trop cool")); // affiche False
    Console.WriteLine(IsEmpty("   ")); // affiche False
  }
}
```

</details>


## Exercice 7

Créez une fonction `Parité` qui prend un paramètre entier `n` et qui renvoie le `string` `"pair"` si `n` est un nombre pair ou le `string` `"impair"` sinon.

Exemples:

```csharp
Console.WriteLine(Parité(2)); // affiche "pair"
Console.WriteLine(Parité(0)); // affiche "pair"
Console.WriteLine(Parité(5)); // affiche "impair"
Console.WriteLine(Parité(-5)); // affiche "impair"
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  // renvoie "pair" si le paramètre est pair, "impair" sinon.
  static string Parité(int n){
    if (n % 2 == 0) {
      return "pair";
    }
    // le else n'est pas nécessaire car lorsqu'on rentre dans le if et que le return est exécuté, la méthode est arrêtée. 
    // Si on a passé le if, c'est donc qu'on est forcément dans le else 
    return "impair";
  }

  public static void Main()
  {
    Console.WriteLine(Parité(2)); // affiche "pair"
    Console.WriteLine(Parité(0)); // affiche "pair"
    Console.WriteLine(Parité(5)); // affiche "impair"
    Console.WriteLine(Parité(-5)); // affiche "impair"
  }
}
```

</details>

## Exercice 8

Créez une fonction `EstMemeLongueur` qui prend deux chaînes `str1` et `str2` comme paramètres et renvoie `true` si le nombre total de caractères dans `str1` est égal au nombre total de caractères dans `str2`. Sinon cette fonction renvoie `false`.

Exemples:

```csharp
EstMemeLongueur("AA", "BB"); // retourne true
EstMemeLongueur("123", "1"); // retourne false
EstMemeLongueur("Ali", "Bob"); // retourne true
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  // retourne vrai si les deux strings passés en paramètre ont la même taille et faux sinon.
  static bool EstMemeLongueur(string str1, string str2){
    return str1.Length == str2.Length;
  }

  public static void Main()
  {
    Console.WriteLine(EstMemeLongueur("AA", "BB")); // retourne true
    Console.WriteLine(EstMemeLongueur("123", "1")); // retourne false
    Console.WriteLine(EstMemeLongueur("Ali", "Bob")); // retourne true
  }
}
```

> ### Remarque :
> Une autre solution est de définir la fonction `EstMemeLongueur` comme ceci : 
> ```csharp
> static bool EstMemeLongueur(string str1, string str2){
>  if (str1.Length == str2.Length) {
>   return true;
>  } else {
>   return false;
>  }
> }
> ```
> Ce code est plus long mais est identique. On peut voir que si la condition est vraie alors on renvoie `true` et si elle est fausse, on renvoie `false`... On peut donc renvoyer directement le résultat de la comparaison sans passer par un `if`.

</details>

## Exercice 9

Un fermier vous demande de lui dire combien de pattes peuvent être comptées parmi tous ses animaux. Il y a trois espèces:

- poulets = 2 pattes
- vaches = 4 pattes
- chevaux = 4 pattes

Le fermier a compté ses animaux et il vous donne un sous-total pour chaque espèce. Vous devez implémenter une fonction `ComptePattes` qui renvoie le nombre total de pattes de tous les animaux.

L’ordre des animaux transmis à la fonction est `ComptePattes(poulets, vaches, chevaux)`.

Exemple:

```csharp
ComptePattes(1, 4, 2); // renvoie 26
ComptePattes(2, 2, 2); // renvoie 20
ComptePattes(2, 0, 3); // renvoie 16
```

N’oubliez pas que le fermier veut connaître le nombre total de pattes et non pas le nombre total d’animaux.

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  // renvoie le nombre de pattes des animaux
  static int ComptePattes(int poulets, int vaches, int chevaux){	  
    return poulets * 2 + vaches * 4 + chevaux * 4;
  }

  public static void Main()
  {
  Console.WriteLine(ComptePattes(1, 4, 2)); // renvoie 26
  Console.WriteLine(ComptePattes(2, 2, 2)); // renvoie 20
  Console.WriteLine(ComptePattes(2, 0, 3)); // renvoie 16
  }
}
```

</details>

## Exercice 10

Créez une fonction `GetMax` qui prend un tableau d'entiers en paramètre et renvoie le plus grand nombre du tableau.

Exemple:
```csharp
GetMax(new int[]{9, 7, 1, 5}); // renvoie 9
GetMax(new int[]{100, -100, 1, 50}); // renvoie 100
GetMax(new int[]{9, 9, 9, 9}); // renvoie 9
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  // renvoie le nombre maximum du tab, int.MinValue sinon
  static int GetMax(int[] tab){
    // on pose que le maximum est la valeur la plus petite possible (int.MinValue donne cette valeur)
    int max = int.MinValue;

    // pour chaque élément du tableau...
    foreach(int element in tab) {
      // si l'élément courant du tableau est plus grand que le max courant...
      if (element > max) {
        // ... on remplace le max 
        max = element;
      }
    }
    // on renvoie le maximum trouvé
    return max;
  }

  public static void Main()
  {
    Console.WriteLine(GetMax(new[]{9, 7, 1, 5})); // affiche 9
    Console.WriteLine(GetMax(new[]{100, -100, 1, 50})); // affiche 100
    Console.WriteLine(GetMax(new[]{9, 9, 9, 9})); // affiche 9
  }
}
```

</details>

## Exercice 11

Créez une fonction `Renverse` qui prend une chaîne de caractères `phrase` en paramètre par référence et la renverse (le premier caractère devient le dernier, etc).

Exemple :

```csharp
string bonjour = "Bonjour tout le monde !";
Renverse(ref bonjour);
// la variable bonjour contient "! ednom el tuot ruojnoB"
```

```csharp
using System;

public class Program
{
    static void Renverse(ref string phrase)
    {
        // déclaration et initialisation d'un string dans lequel on va construire la chaîne inversée
        string phraseRenversée = "";

        // pour chaque indice de la chaîne (de 0 à phrase.Length - 1)...
        for(int i = 0; i < phrase.Length; i++)
        {
            // ... on met le caractère en position i au début de la chaîne renversée
            phraseRenversée = phrase[i] + phraseRenversée;
        }
        // on assigne à phrase la nouvelle phrase
        phrase = phraseRenversée;
    }

    public static void Main()
    {
        string bonjour = "Bonjour tout le monde !";
        Renverse(ref bonjour); // on va modifier la variable bonjour dans la fonction Renverse
        Console.WriteLine(bonjour); // affiche "! ednom el tuot ruojnoB"
    }
}
```

## Exercice 12

Créez une fonction `NbrOfSyllabes` qui compte le nombre de syllabes d’un mot passé en paramètre. Chaque syllabe est séparée par un tiret -.

Exemples:

```csharp
NbrOfSyllabes(""); // renvoie 0
NbrOfSyllabes("mon"); // renvoie 1
NbrOfSyllabes("prin-temps"); // renvoie 2
NbrOfSyllabes("ar-rê-te"); // renvoie 3
NbrOfSyllabes("ther-mo-mè-tre"); // renvoie 4
NbrOfSyllabes("-"); // renvoie 1
NbrOfSyllabes("-mon"); // renvoie 1
NbrOfSyllabes("-mon-"); // renvoie 2
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  // retourne le nombre de syllabes séparés par des '-'
  static int NbrOfSyllabes(string str){
    // initialisation du compteur
    int nb = 0;

    // pour chaque caractère dans str...
    foreach(char caractere in str) {
      // si on est sur le premier caractère...
      if (nb == 0) {
        // ... il y a au moins une syllabe
        nb = 1;
      }
      else if (caractere == '-') { // sinon, si c'est le caractère '-'...
        // ... il y a une syllabe de plus
        nb++;
      }
    }

    return nb;
  }

  public static void Main()
  {
    Console.WriteLine(NbrOfSyllabes("")); // affiche 0
    Console.WriteLine(NbrOfSyllabes("mon")); // affiche 1
    Console.WriteLine(NbrOfSyllabes("prin-temps")); // affiche 2
    Console.WriteLine(NbrOfSyllabes("ar-rê-te")); // affiche 3
    Console.WriteLine(NbrOfSyllabes("ther-mo-mè-tre")); // affiche 4
    Console.WriteLine(NbrOfSyllabes("-")); // affiche 1
    Console.WriteLine(NbrOfSyllabes("-mon")); // affiche 1
    Console.WriteLine(NbrOfSyllabes("-mon-")); // affiche 2
  }
}
```

</details>

## Exercice 13

Créez une fonction `GetIndex` qui prend un tableau `mots` de `string` et un `string` `mot` comme paramètres et renvoie l’index de `mot` dans `mots`. La fonction retourne -1 si `mot` n'existe pas dans `mots`.

Exemples:

```csharp
GetIndex(new string[] {"A", "B", "C", "D"}, "B"); // renvoie 1
GetIndex(new string[] {"Alex", "Bob", "Emily", "Tom"}, "Emily"); // renvoie 2
GetIndex(new string[] {"C#", "PHP", "C++", "Java"}, "C#"); // renvoie 0
GetIndex(new string[] {"A", "B", "C", "D"}, "E"); // renvoie -1
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  // retourne l'indice de mot dans le tableau mots si il existe. Sinon -1.
  static int GetIndex(string[] mots, string mot){
    // on va parcourir chaque mot via l'indice i
    for(int i = 0; i < mots.Length; i++) {
      if(mots[i] == mot) {
        // si mots[i] est le mot recherché, on retoure i
        return i;
      }
    }
    // si on n'a rien trouvé, on retourne -1
    return -1;
  }

  public static void Main()
  {
    Console.WriteLine(GetIndex(new string[] {"A", "B", "C", "D"}, "B")); // affiche 1
    Console.WriteLine(GetIndex(new string[] {"Alex", "Bob", "Emily", "Tom"}, "Emily")); // affiche 2
    Console.WriteLine(GetIndex(new string[] {"C#", "PHP", "C++", "Java"}, "C#")); // affiche 0
    Console.WriteLine(GetIndex(new string[] {"A", "B", "C", "D"}, "E")); // affiche -1
  }
}
```

</details>

## Exercice 14

La distance de Hamming est le nombre de caractères qui diffèrent entre deux chaînes. Prenons un exemple :

```csharp
string str1 = "abcdef";
string str2 = "abcdff";
```

La distance de Hamming entre `str1` et `str2` est de `1` car il n'y a qu'une seule différence entre les deux mots (un `f` au lieu d'un `e`).

Créez une fonction `DistanceHamming` qui calcule la distance de Hamming entre deux chaînes passées en paramètres. Vous pouvez considérer que les deux chaînes sont de la même taille. 

Exemples:

```csharp
DistanceHamming("abcdde", "abcdbe"); // renvoie 1
DistanceHamming("abcdef", "defabc"); // renvoie 6
DistanceHamming("agresser", "adresser"); // renvoie 1
DistanceHamming("attention", "intention"); // renvoie 2
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  // renvoie le nombre de caractères différents entre 2 chaînes
  static int DistanceHamming(string str1, string str2)
  {
    // i sera l'indice de parcours et nbDifférences sera le nombre de différences
    int i = 0, nbDifférences = 0;

    // tant que i est un indice de str1
    while (i < str1.Length)
    {
      // si les caractères à la même position sont différents...
      if (str1[i] != str2[i]) 
      {
        // on incrémente le nombre de différences
        nbDifférences++;
      }

      // on incrémente i
      i++;
    }

    // on renvoie le nombre de différences
    return nbDifférences;
  }
  public static void Main()
  {
    Console.WriteLine(DistanceHamming("abcdde", "abcdbe")); // affiche 1
    Console.WriteLine(DistanceHamming("abcdef", "defabc")); // affiche 6
    Console.WriteLine(DistanceHamming("agresser", "adresser")); // affiche 1
    Console.WriteLine(DistanceHamming("attention", "intention")); // affiche 2
  }
}
```

</details>

## Exercice 14

Voici le code de la solution d'un précédent exercice :

```csharp
using System;
          
public class Program
{
  public static void Main()
  {
    // déclaration et initialisation du tableau noms de 10 strings 
    string[] noms = new string[10];

    // déclaration et initialisation du tableau prix de 10 entiers 
    int[] prix = new int[10];
    
    // déclaration et initialisation de la variable contenant le choix de l'utilisateur
    int choix = 0;
    
    // on commence la boucle faire...tant que... (do/while) 
    do {
      // on affiche le menu (le préfixe @ permet d'écrire un string sur plusieurs lignes)
      Console.Write(@"
1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: ");

      // on lit le choix de l'utilisateur
      // 	=> choix sera à 0 si l'entrée n'est pas un nombre 
      int.TryParse(Console.ReadLine(), out choix);
      
      // affichage d'une ligne vide 
      Console.WriteLine();

      // si le choix est 1...
      if (choix == 1) {

        // i varie de 0 à 9
        for(int i = 0; i < 10; i++) {

          // si, pour l'élément à l'indice i, le nom est assigné ou le prix est assigné...
          if (noms[i] != null || prix[i] != 0) {
            // on affiche le nom et le prix
            Console.WriteLine("{0}. {1} : {2} euros", i + 1, noms[i], prix[i]);
          } else { // sinon...
            // on affiche "Non défini"
            Console.WriteLine("{0}. Non défini", i + 1);
          }
        }
      } else if (choix >= 2 && choix <= 4) { // sinon, si le choix est compris entre 2 et 4...
        // on va demander à l'utilisateur l'index de l'article à modifier 

        //  indexArticle va contenir le numéro d'article à modifier
        int indexArticle = -1;

        do {
          // affichage de la question
          Console.Write("Quel numéro d'article voulez-vous modifier ? ");

          // on lit indexArticle sur la console
          int.TryParse(Console.ReadLine(), out indexArticle);
          
          // si l'index est inférieur à 1 ou supérieur à 10
          if (indexArticle < 1 || indexArticle > 10) {
            // on met indexArticle à -1
            indexArticle = -1;
          }
        }while(indexArticle == -1); // on boucle sur la demande de l'indice tant que le nombre n'est pas correct 

        // si le choix est 2 (modification du nom)
        if (choix == 2) {
          // on affiche la question du nom
          Console.Write("Quel est le nouveau nom de l'article {0} ? ", indexArticle);

          // on lit le nouveau nom
          string nom = Console.ReadLine();

          // on l'assigne au bon indice dans la tableau noms
          noms[indexArticle - 1] = nom;

          // on affiche le retour utilisateur
          Console.WriteLine("Nom modifié avec succès");

        } else if (choix == 3) { // ou si le choix est 3 (modification du prix)

          // on affiche la question du prix
          Console.Write("Quel est le nouveau prix de l'article {0} ? ", indexArticle);

          // on lit le nouveau prix
          int nouveauPrix = int.Parse(Console.ReadLine());

          // on l'assigne au bon indice dans la tableau prix
          prix[indexArticle - 1] = nouveauPrix;				

          // on affiche le retour utilisateur
          Console.WriteLine("Prix modifié avec succès");

        } else if (choix == 4) {  // ou si le choix est 4 (suppression de l'article)
          
          // on efface le nom
          noms[indexArticle - 1] = null;
          
          // on efface le prix
          prix[indexArticle - 1] = 0;

          // on affiche le retour utilisateur
          Console.WriteLine("Article retiré avec succès");

        }
      } else if (choix != 5) { // si ce n'est pas 1, ni 2, ni 3, ni 4, ni 5...
        // on affiche le message d'erreur
        Console.WriteLine("Ce choix est invalide");
      }
    } while(choix != 5); // on arrête cette boucle quand le choix est 5
  }
}
```

La fonction `Main` contient trop de lignes de code. Créez les fonctions manquantes pour que le programme fonctionne comme avant avec cette nouvelle définition de `Main`: 

```csharp
public static void Main()
  {
    // déclaration et initialisation du tableau noms de 10 strings 
    string[] noms = new string[10];

    // déclaration et initialisation du tableau prix de 10 entiers 
    int[] prix = new int[10];

    // déclaration et initialisation de la variable contenant le choix de l'utilisateur
    int choix = 0;

    // on commence la boucle faire...tant que... (do/while) 
    do
    {
      // on affiche le menu (le préfixe @ permet d'écrire un string sur plusieurs lignes)
      choix = DemandeChoix();
      // si le choix est 1...
      if (choix == 1)
            {
                AfficherArticles(noms, prix);
            }
            else if (choix >= 2 && choix <= 4)
            { // sinon, si le choix est compris entre 2 et 4...
              // on va demander à l'utilisateur l'index de l'article à modifier 

                //  indexArticle va contenir le numéro d'article à modifier
                int indexArticle = DemandeIndex(); 

                // si le choix est 2 (modification du nom)
                if (choix == 2)
                {
                    ChangerNom(noms, indexArticle);

                }
                else if (choix == 3)
                { // ou si le choix est 3 (modification du prix)
                    ChangerPrix(prix, indexArticle);

                }
                else if (choix == 4)
                {  // ou si le choix est 4 (suppression de l'article)
                    SupprimerArticle(noms, prix, indexArticle);

                }
            }
            else if (choix != 5)
      { // si ce n'est pas 1, ni 2, ni 3, ni 4, ni 5...
        // on affiche le message d'erreur
        Console.WriteLine("Ce choix est invalide");
      }
    } while (choix != 5); // on arrête cette boucle quand le choix est 5
  }
```

<details>
  <summary>Solution</summary>

```csharp
using System;

public class Program
{
  public static void Main()
  {
    // déclaration et initialisation du tableau noms de 10 strings 
    string[] noms = new string[10];

    // déclaration et initialisation du tableau prix de 10 entiers 
    int[] prix = new int[10];

    // déclaration et initialisation de la variable contenant le choix de l'utilisateur
    int choix = 0;

    // on commence la boucle faire...tant que... (do/while) 
    do
    {
      // on affiche le menu (le préfixe @ permet d'écrire un string sur plusieurs lignes)
      choix = DemandeChoix();
      // si le choix est 1...
      if (choix == 1)
            {
                AfficherArticles(noms, prix);
            }
            else if (choix >= 2 && choix <= 4)
            { // sinon, si le choix est compris entre 2 et 4...
              // on va demander à l'utilisateur l'index de l'article à modifier 

                //  indexArticle va contenir le numéro d'article à modifier
                int indexArticle = DemandeIndex(); 

                // si le choix est 2 (modification du nom)
                if (choix == 2)
                {
                    ChangerNom(noms, indexArticle);

                }
                else if (choix == 3)
                { // ou si le choix est 3 (modification du prix)
                    ChangerPrix(prix, indexArticle);

                }
                else if (choix == 4)
                {  // ou si le choix est 4 (suppression de l'article)
                    SupprimerArticle(noms, prix, indexArticle);

                }
            }
            else if (choix != 5)
      { // si ce n'est pas 1, ni 2, ni 3, ni 4, ni 5...
        // on affiche le message d'erreur
        Console.WriteLine("Ce choix est invalide");
      }
    } while (choix != 5); // on arrête cette boucle quand le choix est 5
  }

  static int DemandeChoix()
  {
    int choix = 0;
    Console.Write(@"
1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: ");

    // on lit le choix de l'utilisateur
    // 	=> choix sera à 0 si l'entrée n'est pas un nombre 
    int.TryParse(Console.ReadLine(), out choix);

    // affichage d'une ligne vide 
    Console.WriteLine();

    return choix;
  }

  static void AfficherArticles(string[] noms, int[] prix)
  {
      // i varie de 0 à 9
      for (int i = 0; i < 10; i++)
      {

          // si, pour l'élément à l'indice i, le nom est assigné ou le prix est assigné...
          if (noms[i] != null || prix[i] != 0)
          {
              // on affiche le nom et le prix
              Console.WriteLine("{0}. {1} : {2} euros", i + 1, noms[i], prix[i]);
          }
          else
          { // sinon...
            // on affiche "Non défini"
              Console.WriteLine("{0}. Non défini", i + 1);
          }
      }
    }

    static int DemandeIndex()
    {
        int indexArticle = -1;

        do
        {
            // affichage de la question
            Console.Write("Quel numéro d'article voulez-vous modifier ? ");

            // on lit indexArticle sur la console
            int.TryParse(Console.ReadLine(), out indexArticle);

            // si l'index est inférieur à 1 ou supérieur à 10
            if (indexArticle < 1 || indexArticle > 10)
            {
                // on met indexArticle à -1
                indexArticle = -1;
            }
        } while (indexArticle == -1);
        // on boucle sur la demande de l'indice tant que le nombre n'est pas correct
        
        return indexArticle;
    }

    static void ChangerNom(string[] noms, int indexArticle)
    {
        // on affiche la question du nom
        Console.Write("Quel est le nouveau nom de l'article {0} ? ", indexArticle);

        // on lit le nouveau nom
        string nom = Console.ReadLine();

        // on l'assigne au bon indice dans la tableau noms
        noms[indexArticle - 1] = nom;

        // on affiche le retour utilisateur
        Console.WriteLine("Nom modifié avec succès");
    }

    static void ChangerPrix(int[] prix, int indexArticle)
    {
        // on affiche la question du prix
        Console.Write("Quel est le nouveau prix de l'article {0} ? ", indexArticle);

        // on lit le nouveau prix
        int nouveauPrix = int.Parse(Console.ReadLine());

        // on l'assigne au bon indice dans la tableau prix
        prix[indexArticle - 1] = nouveauPrix;

        // on affiche le retour utilisateur
        Console.WriteLine("Prix modifié avec succès");
    }

    static void SupprimerArticle(string[] noms, int[] prix, int indexArticle)
    {
        // on efface le nom
        noms[indexArticle - 1] = null;

        // on efface le prix
        prix[indexArticle - 1] = 0;

        // on affiche le retour utilisateur
        Console.WriteLine("Article retiré avec succès");
    }
}
```

</details>