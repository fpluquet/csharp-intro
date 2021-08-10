# Boucles for

**intro**

- Utiliser des boucles (for, while, do/while, ...)

> Ajouter des exos de lecture
> Transformer les exos pour retirer les fonctions


## Exercice 1

Que fait le programme suivant ?

```csharp
using System;

public class Program {
  public static void Main(string[] args) {
    int i;
    for (i = 1; i <= 100; i++) {
      if ((i % 3 == 0 && i % 5 == 0) || i % 7 == 0) {
        Console.WriteLine(i);
      }
    }
  }
}
```

## Exercice 2

Que fait le programme suivant ?

```csharp
using System;

public class Program {
  public static void Main(string[] args) {
    int j;
    for (j = 30; j > 0; j = j - 3) {
      Console.WriteLine(i);
    }
  }
}
```

## Exercice 3

Que fait le programme suivant ?

```csharp
using System;

public class Program {
  public static void Main(string[] args) {
    int i, j;
    for (i = 0; i <= 10; i++) {
      for (j = 0; j <= 10; j++) {
        Console.WriteLine("{0} x {1} = {2}", i, j, i * j);
      }
    }
  }
}
```

## Exercice 4

Que fait le programme suivant ?

```csharp
using System;

public class Program {
  public static void Main(string[] args) {
    int i, j;
    for (i = 0; i <= 10; i++) {
      for (j = 0; j <= i; j++) {
        Console.WriteLine("{0} x {1} = {2}", i, j, i * j);
      }
    }
  }
}
```

## Exercice 5

Quelle est la sortie du programme suivant ?

```csharp
using System;

public class Program {
  public static void Main(string[] args) {
    int somme = 0;
    while(somme < 50) {
      int i, j;
      for (i = 0; i <= 10; i++) {
        if (i % 2 == 0) {
          somme += i;
        }
      }
    }
    Console.WriteLine(somme);
  }
}
```

## Exercice 6

Quelle est la sortie du programme suivant ?

```csharp
using System;

public class Program {
  public static void Main(string[] args) {
    int somme = 0;
    while(somme < 50) {
      int i, j;
      for (i = 0; i <= 10 && somme < 50; i++) {
        if (i % 2 == 0) {
          somme += i;
        }
      }
    }
    Console.WriteLine(somme);
  }
}
```

## Exercice 7

Utilisez des boucles afin de construire un triangle rectangle formé par le caractère étoile (\*). 
Affichez-en ```nbLignes``` lignes, où ```nbLignes``` est entré au clavier par l'utilisateur. 

Exemple de sortie :
```
Combien de lignes voulez-vous afficher ? 8
*
**
***
****
*****
******
*******
********
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		int nbLignes;
		
		Console.Write("Combien de lignes voulez-vous afficher ? ");
		nbLignes = int.Parse(Console.ReadLine());
		
		for(int i = 1; i <= nbLignes; i++) {
			for(int j = 1; j <= i; j++) {
				Console.Write("*");
			}
			Console.WriteLine();
		}
	}
}
```
</details>

## Exercice 8

Créez une fonction qui renvoie ```true``` si une chaîne contient des espaces. Sinon renvoie ```false```. Pour y arriver, lisez chaque caractère de la chaîne de caractère via une boucle ```for```.  


Exemple:

containSpaces("Thomas") ➞ False

containSpaces("Hello World!") ➞ True

containSpaces(" ") ➞ True

containSpaces("") ➞ False

<details>
	<summary>Solution</summary>

```csharp

```
</details>

## Exercice 9

Créez une fonction qui compte le nombre de syllabes d’un mot. Chaque syllabe est séparée par un tiret -.

Exemple:

nbrOfSlab("prin-temps") ➞ 2

nbrOfSlab("ar-rê-te") ➞ 3

nbrOfSlab("ther-mo-mè-tre") ➞ 4

<details>
	<summary>Solution</summary>

```csharp

```
</details>