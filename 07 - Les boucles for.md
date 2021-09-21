# Boucles for

**intro**

- Utiliser des boucles (for, while, do/while, ...)

> Ajouter l'intro
> Ajouter les solutions manquantes
> Ajouter des commentaires dans les codes solutions


## Exercice 1

Que fait le programme suivant ?

```csharp
using System;

public class Program {
  public static void Main(string[] args) {
    int i;
    for (i = 1; i <= 20; i++) {
      if ((i % 3 == 0 && i % 5 == 0) || i % 7 == 0) {
        Console.WriteLine(i);
      }
    }
  }
}
```

<details>
	<summary>Solution</summary>
	
Ce programme va afficher tous les nombres entre 1 et 20 compris, divisibles par 3 et 5 ou divisibles par 7. Il va donc afficher ```7 14 15```.

| i  | i <= 20 | i % 3 | i % 5 | (i % 3 == 0 && i % 5 == 0) | i % 7 == 0 | (i % 3 == 0 && i % 5 == 0) \|\| i % 7 == 0 | Affichage |
| -- | ------- | ----- | ----- | -------------------------- | ---------- | ------------------------------------------ | --------- |
| 1  | Vrai    | Faux  | Faux  | Faux                       | Faux       | Faux                                       |           |
| 2  | Vrai    | Faux  | Faux  | Faux                       | Faux       | Faux                                       |           |
| 3  | Vrai    | Vrai  | Faux  | Faux                       | Faux       | Faux                                       |           |
| 4  | Vrai    | Faux  | Faux  | Faux                       | Faux       | Faux                                       |           |
| 5  | Vrai    | Faux  | Vrai  | Faux                       | Faux       | Faux                                       |           |
| 6  | Vrai    | Faux  | Faux  | Faux                       | Faux       | Faux                                       |           |
| 7  | Vrai    | Faux  | Faux  | Faux                       | Vrai       | Vrai                                       | 7         |
| 8  | Vrai    | Faux  | Faux  | Faux                       | Faux       | Faux                                       |           |
| 9  | Vrai    | Vrai  | Faux  | Faux                       | Faux       | Faux                                       |           |
| 10 | Vrai    | Faux  | Vrai  | Faux                       | Faux       | Faux                                       |           |
| 11 | Vrai    | Faux  | Faux  | Faux                       | Faux       | Faux                                       |           |
| 12 | Vrai    | Vrai  | Faux  | Faux                       | Faux       | Faux                                       |           |
| 13 | Vrai    | Faux  | Faux  | Faux                       | Faux       | Faux                                       |           |
| 14 | Vrai    | Faux  | Faux  | Faux                       | Vrai       | Vrai                                       | 14        |
| 15 | Vrai    | Vrai  | Vrai  | Vrai                       | Faux       | Vrai                                       | 15        |
| 16 | Vrai    | Faux  | Faux  | Faux                       | Faux       | Faux                                       |           |
| 17 | Vrai    | Faux  | Faux  | Faux                       | Faux       | Faux                                       |           |
| 18 | Vrai    | Vrai  | Faux  | Faux                       | Faux       | Faux                                       |           |
| 19 | Vrai    | Faux  | Faux  | Faux                       | Faux       | Faux                                       |           |
| 20 | Vrai    | Faux  | Vrai  | Faux                       | Faux       | Faux                                       |           |
| 21 | Faux    |       |       |                            |            |                                            |           |


</details>

## Exercice 2

Que fait le programme suivant ?

```csharp
using System;

public class Program {
  public static void Main(string[] args) {
    int j;
    for (j = 10; j > 0; j = j - 3) {
      Console.WriteLine(j);
    }
  }
}
```
<details>
	<summary>Solution</summary>

Ce programme va afficher les nombres entre 10 et 0 en retirant 3 à chaque tour. Il va donc afficher ```10 7 4 1```.

| j  | j > 0 | Affichage |
| -- | ----- | --------- |
| 10 | Vrai  | 10        |
| 7  | Vrai  | 7         |
| 4  | Vrai  | 4         |
| 1  | Vrai  | 1         |
| -2 | Faux  |           |

</details>

## Exercice 3

Que fait le programme suivant ?

```csharp
using System;

public class Program {
  public static void Main(string[] args) {
    int i, j;
    for (i = 1; i <= 10; i++) {
      for (j = 1; j <= 10; j++) {
        Console.WriteLine("{0} x {1} = {2}", i, j, i * j);
      }
    }
  }
}
```

<details>
	<summary>Solution</summary>
Ce programme va afficher les tables de multiplications de 1 à 10 :

```
1 x 1 = 1
1 x 2 = 2
1 x 3 = 3
1 x 4 = 4
1 x 5 = 5
1 x 6 = 6
1 x 7 = 7
1 x 8 = 8
1 x 9 = 9
1 x 10 = 10
2 x 1 = 2
2 x 2 = 4
2 x 3 = 6
2 x 4 = 8
2 x 5 = 10
2 x 6 = 12
2 x 7 = 14
2 x 8 = 16
2 x 9 = 18
2 x 10 = 20
3 x 1 = 3
3 x 2 = 6
3 x 3 = 9
3 x 4 = 12
3 x 5 = 15
3 x 6 = 18
3 x 7 = 21
3 x 8 = 24
3 x 9 = 27
3 x 10 = 30
4 x 1 = 4
4 x 2 = 8
4 x 3 = 12
4 x 4 = 16
4 x 5 = 20
4 x 6 = 24
4 x 7 = 28
4 x 8 = 32
4 x 9 = 36
4 x 10 = 40
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
5 x 4 = 20
5 x 5 = 25
5 x 6 = 30
5 x 7 = 35
5 x 8 = 40
5 x 9 = 45
5 x 10 = 50
6 x 1 = 6
6 x 2 = 12
6 x 3 = 18
6 x 4 = 24
6 x 5 = 30
6 x 6 = 36
6 x 7 = 42
6 x 8 = 48
6 x 9 = 54
6 x 10 = 60
7 x 1 = 7
7 x 2 = 14
7 x 3 = 21
7 x 4 = 28
7 x 5 = 35
7 x 6 = 42
7 x 7 = 49
7 x 8 = 56
7 x 9 = 63
7 x 10 = 70
8 x 1 = 8
8 x 2 = 16
8 x 3 = 24
8 x 4 = 32
8 x 5 = 40
8 x 6 = 48
8 x 7 = 56
8 x 8 = 64
8 x 9 = 72
8 x 10 = 80
9 x 1 = 9
9 x 2 = 18
9 x 3 = 27
9 x 4 = 36
9 x 5 = 45
9 x 6 = 54
9 x 7 = 63
9 x 8 = 72
9 x 9 = 81
9 x 10 = 90
10 x 1 = 10
10 x 2 = 20
10 x 3 = 30
10 x 4 = 40
10 x 5 = 50
10 x 6 = 60
10 x 7 = 70
10 x 8 = 80
10 x 9 = 90
10 x 10 = 100
```

</details>

## Exercice 4

Que fait le programme suivant ?

```csharp
using System;

public class Program {
  public static void Main(string[] args) {
    int i, j;
    for (i = 1; i <= 10; i++) {
      for (j = 1; j <= i; j++) {
        Console.WriteLine("{0} x {1} = {2}", i, j, i * j);
      }
    }
  }
}
```

<details>
	<summary>Solution</summary>

Ce programme va afficher les tables de multiplication de 1 à 10 mais s'arrête quand les deux facteurs sont égaux, parce que la seconde boucle s'arrête après que ```j``` soit égal à ```i``` :

```
1 x 1 = 1
2 x 1 = 2
2 x 2 = 4
3 x 1 = 3
3 x 2 = 6
3 x 3 = 9
4 x 1 = 4
4 x 2 = 8
4 x 3 = 12
4 x 4 = 16
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
5 x 4 = 20
5 x 5 = 25
6 x 1 = 6
6 x 2 = 12
6 x 3 = 18
6 x 4 = 24
6 x 5 = 30
6 x 6 = 36
7 x 1 = 7
7 x 2 = 14
7 x 3 = 21
7 x 4 = 28
7 x 5 = 35
7 x 6 = 42
7 x 7 = 49
8 x 1 = 8
8 x 2 = 16
8 x 3 = 24
8 x 4 = 32
8 x 5 = 40
8 x 6 = 48
8 x 7 = 56
8 x 8 = 64
9 x 1 = 9
9 x 2 = 18
9 x 3 = 27
9 x 4 = 36
9 x 5 = 45
9 x 6 = 54
9 x 7 = 63
9 x 8 = 72
9 x 9 = 81
10 x 1 = 10
10 x 2 = 20
10 x 3 = 30
10 x 4 = 40
10 x 5 = 50
10 x 6 = 60
10 x 7 = 70
10 x 8 = 80
10 x 9 = 90
10 x 10 = 100
```


</details>

## Exercice 5

Quelle est la sortie du programme suivant ?

```csharp
using System;

public class Program {
  public static void Main(string[] args) {
    int somme = 0;
    while(somme < 50) {
      int i;
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

<details>
	<summary>Solution</summary>
La sortie est 

```
60
```

La ```somme``` commence à 0. 

| somme | somme < 50 | i  | i <= 10 | i % 2 == 0 | somme += i | i++ |
| ----- | ---------- | -- | ------- | ---------- | ---------- | --- |
| 0     | Vrai       | 0  | Vrai    | Vrai       | 0          | 1   |
|       |            | 1  | Vrai    | Faux       |            | 2   |
|       |            | 2  | Vrai    | Vrai       | 2          | 3   |
|       |            | 3  | Vrai    | Faux       |            | 4   |
|       |            | 4  | Vrai    | Vrai       | 6          | 5   |
|       |            | 5  | Vrai    | Faux       |            | 6   |
|       |            | 6  | Vrai    | Vrai       | 12         | 7   |
|       |            | 7  | Vrai    | Faux       |            | 8   |
|       |            | 8  | Vrai    | Vrai       | 20         | 9   |
|       |            | 9  | Vrai    | Faux       |            | 10  |
|       |            | 10 | Vrai    | Vrai       | 30         | 11  |
|       |            | 11 | Faux    |            |            |     |
| 30    | Vrai       | 0  | Vrai    | Vrai       | 30         | 1   |
|       |            | 1  | Vrai    | Faux       |            | 2   |
|       |            | 2  | Vrai    | Vrai       | 32         | 3   |
|       |            | 3  | Vrai    | Faux       |            | 4   |
|       |            | 4  | Vrai    | Vrai       | 36         | 5   |
|       |            | 5  | Vrai    | Faux       |            | 6   |
|       |            | 6  | Vrai    | Vrai       | 42         | 7   |
|       |            | 7  | Vrai    | Faux       |            | 8   |
|       |            | 8  | Vrai    | Vrai       | 50         | 9   |
|       |            | 9  | Vrai    | Faux       |            | 10  |
|       |            | 10 | Vrai    | Vrai       | 60         | 11  |
|       |            | 11 | Faux    |            |            |     |
| 60    | Faux       |    |         |            |            |     |



</details>

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


<details>
	<summary>Solution</summary>
La sortie est 

```
50
```

La ```somme``` commence à 0. 

| somme | somme < 50 | i  | i <= 10 | somme < 50 | i <=10 && somme < 50 | i % 2 == 0 | somme += i | i++ |
| ----- | ---------- | -- | ------- | ---------- | -------------------- | ---------- | ---------- | --- |
| 0     | Vrai       | 0  | Vrai    | Vrai       | Vrai                 | Vrai       | 0          | 1   |
|       |            | 1  | Vrai    | Vrai       | Vrai                 | Faux       |            | 2   |
|       |            | 2  | Vrai    | Vrai       | Vrai                 | Vrai       | 2          | 3   |
|       |            | 3  | Vrai    | Vrai       | Vrai                 | Faux       |            | 4   |
|       |            | 4  | Vrai    | Vrai       | Vrai                 | Vrai       | 6          | 5   |
|       |            | 5  | Vrai    | Vrai       | Vrai                 | Faux       |            | 6   |
|       |            | 6  | Vrai    | Vrai       | Vrai                 | Vrai       | 12         | 7   |
|       |            | 7  | Vrai    | Vrai       | Vrai                 | Faux       |            | 8   |
|       |            | 8  | Vrai    | Vrai       | Vrai                 | Vrai       | 20         | 9   |
|       |            | 9  | Vrai    | Vrai       | Vrai                 | Faux       |            | 10  |
|       |            | 10 | Vrai    | Vrai       | Vrai                 | Vrai       | 30         | 11  |
|       |            | 11 | Faux    | Vrai       | Faux                 |            |            |     |
| 30    | Vrai       | 0  | Vrai    | Vrai       | Vrai                 | Vrai       | 30         | 1   |
|       |            | 1  | Vrai    | Vrai       | Vrai                 | Faux       |            | 2   |
|       |            | 2  | Vrai    | Vrai       | Vrai                 | Vrai       | 32         | 3   |
|       |            | 3  | Vrai    | Vrai       | Vrai                 | Faux       |            | 4   |
|       |            | 4  | Vrai    | Vrai       | Vrai                 | Vrai       | 36         | 5   |
|       |            | 5  | Vrai    | Vrai       | Vrai                 | Faux       |            | 6   |
|       |            | 6  | Vrai    | Vrai       | Vrai                 | Vrai       | 42         | 7   |
|       |            | 7  | Vrai    | Vrai       | Vrai                 | Faux       |            | 8   |
|       |            | 8  | Vrai    | Vrai       | Vrai                 | Vrai       | 50         | 9   |
|       |            | 9  | Vrai    | Faux       | Faux                 |            |            |     |
| 50    | Faux       |    |         |            |                      |            |            |     |



</details>

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

Utilisez des boucles afin de construire un triangle bien équilibré formé par le caractère étoile (\*). 
Affichez-en ```nbLignes``` lignes, où ```nbLignes``` est entré au clavier par l'utilisateur. 

Exemple de sortie :

```
Combien de lignes voulez-vous afficher ? 8
       *
      ***
     *****
    *******
   *********
  ***********
 *************
***************
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
			for(int j = 0; j < nbLignes - i; j++) {
				Console.Write(" ");
			}
			for(int j = 1; j < i * 2; j++) {
				Console.Write("*");
			}
			Console.WriteLine();
		}
	}
}
```
</details>

## Exercice 9

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

## Exercice 10

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

## Exercice 11

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

