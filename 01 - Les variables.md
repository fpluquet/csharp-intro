# Variables

Une variable est un emplacement mémoire qui a :
- un type (int, double, string, ...)
- un nom
- une valeur courante

Voici le code pour déclarer une variable nommée ```age``` qui est un entier et pour valeur initiale 5 :
```
int age = 18;
```

Le type et le nom d'une variable ne peut pas être changés ensuite. Par contre, sa valeur peut être modifiée. On peut par exemple changer la valeur de la variable ```age``` en y mettant 20. 
```
age = 20;
```

On peut aussi lire le contenu d'une variable en indiquant son nom dans une expression :
```
int ageMinimum = age;
```

La valeur contenue dans ```age``` sera alors recopiée dans la variable nommée ```ageMinimum```.

Le code ```Console.WriteLine(age)``` permet d'afficher la valeur de la variable sur la sortie standard du programme (qu'on appelle la console). 

## Exercice 1

Que contient chaque variable à la fin de ce programme ?

```csharp
using System;

public class Program
{
	public static void Main()
	{
		int age = 18;
		int ageMinimum = 0;
		int ageMaximum = 99;
		
		ageMinimum = age;
		age = age + 20;
		ageMaximum = age;
		ageMinimum = ageMaximum - 30; 
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
		int age = 18; 		// age contient 18
		int ageMinimum = 0; 	// age contient 18, ageMinimum contient 0
		int ageMaximum = 99; 	// age contient 18, ageMinimum contient 0, ageMaximum contient 99
		
		// on va copier la valeur contenue dans age dans la variable ageMinimum
		// attention : seule la valeur est copiée : ageMinimum n'est pas "liée" à age 
		ageMinimum = age;	// age contient 18, ageMinimum contient 18, ageMaximum contient 99
	
		// la partie à droite de l'égalité va d'abord être évaluée et le résultat sera placé dans age
		// 	-> age + 20 : on lit la valeur courante de age (18) et on y ajoute 20 : le résultat de l'évaluation de cette partie vaut 38
		//	-> age = 38 : on assigne à age la valeur 38
		age = age + 20;		// age contient 38, ageMinimum contient 18, ageMaximum contient 99
	
		// on copie la valeur courante de age (38) dans la variable ageMaximum
		ageMaximum = age;	// age contient 38, ageMinimum contient 18, ageMaximum contient 38
	
		// la partie à droite de l'égalité va d'abord être évaluée et le résultat sera placé dans ageMinimum
		// 	-> ageMaximum - 30 : on lit la valeur courante de ageMaximum (38) et on y retir 30 : le résultat de l'évaluation de cette partie vaut 8
		//	-> ageMinimum = 8 : on assigne à ageMinimum la valeur 8
		ageMinimum = ageMaximum - 30; // age contient 38, ageMinimum contient 8, ageMaximum contient 38
	}
}
```
</details>

## Exercice 2

Créez et initialisez 2 variables ```laBase``` de valeur 5 et ```laHauteur``` de valeur 8. Calculer dans une variable ```laSurface``` la surface du triangle de base ```laBase``` et de hauteur ```laHauteur```.

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// on stocke 5 dans une variable entière nommée laBase
		int laBase = 5;

		// on stocke 8 dans une variable entière nommée laHauteur
		int laHauteur = 8;

		// on stocke le résultat du calcul dans une variable entière nommée laSurface
		int laSurface = laBase * laHauteur / 2;

		// on affiche le contenu de la variable laSurface
		Console.WriteLine(laSurface);
	}
}
```
</details>

## Exercice 3

Écrivez un programme qui affiche le quotient et le reste de la division entière de 57 par 13. Pour y arriver, utilisez les opérateurs / et %.

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		Console.WriteLine("Quotient : ");
		Console.WriteLine(57 / 13); // affiche 4 (car il y a 4 * 13 dans 57)
		Console.WriteLine("Reste : ");
		Console.WriteLine(57 % 13); // affiche 5 (car 57 - 4 * 13 = 5)
	}
}
```
</details>

## Exercice 4

Créez deux variables entières ```a``` et ```b``` avec les valeurs ```6``` et ```7```. Affichez la valeur des deux variables. Écrivez ensuite le code qui permet d'inverser la valeur de ces deux variables en utilisant une troisième variable (on appelle cela un swap de variables). Affichez la valeur des deux variables pour montrer que cela a bien fonctionné.

Sortie attendue :
```
Avant le swap : 
6
7
Après le swap : 
7
6
``` 

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		int a = 6, b = 7;
		
		Console.WriteLine("Avant le swap : ");
		Console.WriteLine(a);
		Console.WriteLine(b);

		int tmp = a;
		a = b;
		b = tmp;
		
		Console.WriteLine("Après le swap : ");
		Console.WriteLine(a);
		Console.WriteLine(b);
	}
}
```
</details>
