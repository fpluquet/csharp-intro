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

Créez un programme qui compte et affiche le nombre de syllabes d’un mot. Chaque syllabe est séparée par un tiret -.

Exemple de sorties :

```
> prin-temps
2 syllabes
```

```
> ar-rê-te
3 syllabes
```

```
> ther-mo-mè-tre
4 syllabes
```

```
> mer
1 syllabe
```

```
>
0 syllabe
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		string phrase;
		int nbSyllabes = 0;
		Console.Write("> ");
		phrase = Console.ReadLine();
		for(int i = 0; i < phrase.Length; i++) {
			if (phrase[i] == '-') {
				nbSyllabes++;
			} else if (phrase[i] != ' ' && nbSyllabes == 0) {
				nbSyllabes++;
			}
		}
		
		Console.WriteLine("{0} syllabe{1}", nbSyllabes, nbSyllabes > 1 ? "s": "");
	}
}
```
</details>

## Exercice 9

Créez un programme qui affiche ```Il y a au moins un espace``` si une chaîne contient des espaces, sinon il affiche ```Aucun espace détecté```.  Pour y arriver, lisez chaque caractère de la chaîne de caractère via une boucle ```for```. Le programme se termine directement ensuite.


Exemple de sorties:

```
> Fréd
Aucun espace détecté 
```

```
> Hello World!
Il y a au moins un espace
```

Si on n'entre qu'uniquement un espace :

```
>  
Il y a au moins un espace
```

Si on entre une chaîne vide :
```
>
Aucun espace détecté 
``` 

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		string phrase;
		bool espaceExiste = false;
		Console.Write("> ");
		phrase = Console.ReadLine();
		for(int i = 0; i < phrase.Length && espaceExiste == false; i++) {
			if (phrase[i] == ' ') {
				espaceExiste = true;
			}
		}
		
		if (espaceExiste) {
			Console.WriteLine("Il y au moins un espace");
		} else {
			Console.WriteLine("Aucun espace détecté");
		}
	}
}
```
</details>

## Exercice 10

Même exercice que le précédent :
> Créez un programme qui affiche ```Il y a au moins un espace``` si une chaîne contient des espaces, sinon il affiche ```Aucun espace détecté```.  Pour y arriver, lisez chaque caractère de la chaîne de caractère via une boucle ```for```. 

Mais le programme continue de demander un mot jusqu'à ce que l'utilisateur entre le mot ```quitter```.


Exemple de sortie:

```
> Fréd
Aucun espace détecté 
> Hello World!
Il y a au moins un espace
> Cool :)
Il y a au moins un espace
>
Aucun espace détecté
> quitter
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		string phrase;
		bool espaceExiste = false;
		Console.Write("> ");
		phrase = Console.ReadLine();
		while(phrase != "quitter") {
			for(int i = 0; i < phrase.Length && espaceExiste == false; i++) {
				if (phrase[i] == ' ') {
					espaceExiste = true;
				}
			}

			if (espaceExiste) {
				Console.WriteLine("Il y au moins un espace");
			} else {
				Console.WriteLine("Aucun espace détecté");
			}
			Console.Write("> ");
			phrase = Console.ReadLine();
		}
	}
}
```
</details>

