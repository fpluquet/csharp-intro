# Boucles for

Les boucles ```do/while``` et ```while``` permettent de répéter un bout de code autant de fois que nécessaire. Il existe un autre type de boucles qui permet une écriture plus concise : les boucles ```for``` (pour en anglais).

Une boucle ```for``` prend 3 paramètres `for([1]; [2]; [3]) { [4] }` :
1. l'initialisation  
2. la condition de répétition
3. le post-traitement
4. le bloc de code à répéter.

Prenons un exemple simple :

```csharp
for(int i = 0; i < 10; i = i + 1) {
	Console.WriteLine(i);
}
```
On peut décortiquer ce code comme cela :

1. L'initialisation est `int i = 0`
	- on déclare une variable `i`
	- on initilise cette variable à 0
2. La condition de répétition est `i < 0`. 
	- On ne va exécuter le bloc de code que si la condition est vraie.
3. Une fois qu'on a exécuté le bloc, le post-traitement `i = i + 1` est toujours exécuté.
4. Le bloc à répéter est conposé uniquement de `Console.WriteLine(i);`.

L'exécution se passe toujours comme cela :
1. l'initialisation [1] est exécutée
2. le condition [2] est évaluée :
	- si elle est fausse, on passe au code après le bloc [4].
	- si elle est vraie :
		- le code du bloc [4] est exécuté.
		- le post-traitement [3] est exécuté.
		- on revient au point 2.  

Le code suivant va donc afficher les nombre de 0 à 9 :
```csharp
for(int i = 0; i < 10; i = i + 1) {
	Console.WriteLine(i);
}
```

On peut s'en rendre compte en suivant la valeur de `i` et des différentes étapes :
| i = 0 | i  | i < 10 | Console.WriteLine(i) | i = i + 1 |
| ----- | -- | ------ | -------------------- | --------- |
| 0     | 0  | Vrai   | "0"                  | 1         |
|       | 1  | Vrai   | "1"                  | 2         |
|       | 2  | Vrai   | "2"                  | 3         |
|       | 3  | Vrai   | "3"                  | 4         |
|       | 4  | Vrai   | "4"                  | 5         |
|       | 5  | Vrai   | "5"                  | 6         |
|       | 6  | Vrai   | "6"                  | 7         |
|       | 7  | Vrai   | "7"                  | 8         |
|       | 8  | Vrai   | "8"                  | 9         |
|       | 9  | Vrai   | "9"                  | 10        |
|       | 10 | Faux   |                      |           |

La boucle `for` est donc plus concise dans son écriture mais permet de faire ce que l'on pouvait déjà faire avec un `while`. C'est juste une autre manière d'écrire les choses. Voici le même code que le précédent mais avec un `while` :

```csharp
int i = 0;
while(i < 10) {
	Console.WriteLine(i);
	i = i + 1;
}
```

Notez que l'initialisation et le post-traitement d'un `for` peuvent être vides mais les 3 parties doivent toujours être présentes (via les `;`) :

```csharp
int i = 0;
for( ; i < 10 ; ) {
	Console.WriteLine(i);
	i++;
}
```

...mais on perd un peu l'intérêt du `for` ! 

> Attention : les variables déclarées dans l'initialisation d'un `for` ne sont connues que dans le `for` (et son bloc de code). Si vous avez besoin de connaître la valeur d'une variable après l'exécution du `for`, vous devez définir la variable avant le `for` :
```csharp
int i = 0;
for( ; i < 10 ; i++) {
	Console.WriteLine(i);
}
Console.WriteLine(i); // affiche 10
```

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

Transformez le code suivant pour n'utiliser que des boucles `for`:

```csharp
using System;

public class Program
{
	public static void Main()
	{
		
		int i = 0;
		while( i < 20) {
			if(i % 3 != 0) {
				Console.WriteLine(i);
			}
			i += 2;
		}
	}
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
		// [1] déclaration et initialisation de i à 0
		//			i ne sera connu que dans le for et son bloc
		// [2] condition : i < 20
		// [3] post traitement : i = i + 2
		for(int i = 0; i < 20; i += 2) {
			if(i % 3 != 0) {
				Console.WriteLine(i);
			}
		}
	}
}
```
</details>

## Exercice 8

Transformez le code suivant pour n'utiliser que des boucles `for`:

```csharp
using System;

public class Program
{
	public static void Main()
	{
		int i = 0;
		while( i < 20) {
			if(i % 3 != 0) {
				Console.WriteLine(i);
			}
			i += 2;
		}
		while(i % 8 != 0) {
			Console.WriteLine(i);
			i += 1;
		}
	}
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
		// on est obligé de sortir la déclaration de i du for 
		// car il doit être encore connu dans le deuxième for
		int i = 0;
		for(;i < 20;i += 2) {
			if(i % 3 != 0) {
				Console.WriteLine(i);
			}
		}
		for(;i % 8 != 0;i += 1) {
			Console.WriteLine(i);
		}
	}
}
```
</details>

## Exercice 9

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
		// déclaration de la variable qui contiendra le nombre de lignes à afficher
		int nbLignes;
		
		// affichage de la question
		Console.Write("Combien de lignes voulez-vous afficher ? ");
		
		// lecture et transformation en entier du nombre de lignes
		nbLignes = int.Parse(Console.ReadLine());
		
		// Pour chaque ligne i (de 1 à nbLignes compris)...
		for(int i = 1; i <= nbLignes; i++) {
			// ... on va afficher i étoiles en faisant varier j de 1 à i compris
			for(int j = 1; j <= i; j++) {
				Console.Write("*");
			}
			// et on affiche un retour à la ligne une fois les étoiles affichées
			Console.WriteLine();
		}
	}
}
```
</details>

## Exercice 10

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

Indice : il faut afficher le bon nombre d'espaces avant d'afficher les étoiles.

<details>
	<summary>Solution</summary>

La complexité de cet exercice est d'afficher les étoiles bien alignées, et donc d'afficher le bon nombre d'espaces avant de commencer à afficher les étoiles.

Combien d'espaces et d'étoiles faut-il afficher à chaque ligne ? Il suffit de compter et trouver une formule mathématique qui fonctionne avec le nombre de lignes entrés :

| Numéro de ligne | Nb étoiles | Nb espaces |
| --------------- | ---------- | ---------- |
| 1               | 1          | 7          |
| 2               | 3          | 6          |
| 3               | 5          | 5          |
| 4               | 7          | 4          |
| 5               | 9          | 3          |
| 6               | 11         | 2          |
| 7               | 13         | 1          |
| 8               | 15         | 0          |

Pour le nombre d'espaces, on peut trouver la formule simple : ```nbLignes - numéroLigne```. À la 7e ligne, il y a 8 - 7 = 1 étoile.

Pour le nombre d'étoiles, on peut trouver la formule suivante : ```numéroLigne * 2 - 1```. À la 7e ligne, il y a 7 * 2 - 1 = 13 étoiles.


```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// déclaration de la variable qui contiendra le nombre de lignes à afficher
		int nbLignes;
		
		// affichage de la question
		Console.Write("Combien de lignes voulez-vous afficher ? ");
		
		// lecture et transformation en entier du nombre de lignes
		nbLignes = int.Parse(Console.ReadLine());
		
		// Pour chaque ligne i (de 1 à nbLignes compris)...
		for(int i = 1; i <= nbLignes; i++) {
			// ... on affiche les nbLignes - numéroLigne (i) espaces 
			for(int j = 0; j < nbLignes - i; j++) {
				Console.Write(" ");
			}

			// ... on affiche les numéroLigne * 2 - 1 étoiles 
			for(int k = 1; k < i * 2; k++) {
				Console.Write("*");
			}

			// et on affiche un retour à la ligne une fois les étoiles affichées
			Console.WriteLine();
		}
	}
}
```
</details>

## Exercice 11

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
		// déclaration de la variable contenant le mot duquel on doit compter les syllabes   
		string mot;
		
		// déclaration et initialisation à 0 du nombre de syllabes trouvées
		int nbSyllabes = 0;

		// on affiche le > initial
		Console.Write("> ");

		// on lit le mot sur la console
		mot = Console.ReadLine();

		// on va parcourir chaque caractère du mot (i va de 0 à mot.Length - 1)
		for(int i = 0; i < mot.Length; i++) {
			// si le ième caractère du mot est '-'...
			if (mot[i] == '-') {
				// ... on incrémente le nombre de syllabes (équivalent à nbSyllabes = nbSyllabes + 1;)
				nbSyllabes++;
			} else if (mot[i] != ' ' && nbSyllabes == 0) { // ... sinon si le ième caractère n'est pas un espace et que le nombre de syllabes est à 0
				// ... le mot contient donc au moins un caractère et donc au moins un syllabes 
				nbSyllabes++;
			}
		}
		// on affiche le nombre de syllabes et un 's' si nécessaire
		Console.WriteLine("{0} syllabe{1}", nbSyllabes, nbSyllabes > 1 ? "s": "");
	}
}
```
</details>

## Exercice 12

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
		// déclaration de la variable contenant la phrase à analyser   		
		string phrase;
		
		// déclaration et initialisation à false de la variable indiquant s'il y a au moins un espace dans la phrase   		
		bool espaceExiste = false;

		// on affiche le > initial
		Console.Write("> ");

		// on lit la phrase sur la console
		phrase = Console.ReadLine();

		// on va parcourir tous les caractères de la phrase (i va de 0 à phrase.Length - 1) et si on n'a pas encore trouvé un espace
		for(int i = 0; i < phrase.Length && espaceExiste == false; i++) {
			// si le ième caractère est un espace...
			if (phrase[i] == ' ') {
				// ... on passe la variable espaceExiste à true (cela va donc arrêter la boucle for)
				espaceExiste = true;
			}
		}
		
		// si on a détecté un espace...
		if (espaceExiste) {
			// ... on l'affiche
			Console.WriteLine("Il y au moins un espace");
		} else {
			// sinon on affiche l'inverse
			Console.WriteLine("Aucun espace détecté");
		}
	}
}
```
</details>




## Exercice 13

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

		// on ajoute cette boucle tant que la phrase n'est pas égale à "quitter"
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

			// on ajoute ces deux lignes pour recommencer la lecture de l'entrée de l'utilisateur
			Console.Write("> ");
			phrase = Console.ReadLine();
		}
	}
}
```
</details>

