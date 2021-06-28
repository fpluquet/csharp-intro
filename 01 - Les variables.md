# Variables

Une variable est un emplacement mémoire qui a :
- un type (int, double, string, ...)
- un nom
- un valeur courante

Pour déclarer une variable nommée ```age``` qui est un entier et pour valeur initiale 5 :
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
		int ageMaximum = 99; 	// age contient 18, ageMinimum contient 0, ageMaximum contient 0
		
		// on va copier la valeur contenue dans age dans la variable ageMinimum
		// attention : seule la valeur est copiée : ageMinimum n'est pas "liée" à age 
		ageMinimum = age;	// age contient 18, ageMinimum contient 18, ageMaximum contient 0
	
		// la partie à droite de l'égalité va d'abord être évaluée et le résultat sera placé dans age
		// 	-> age + 20 : on lit la valeur courante de age (18) et on y ajoute 20 : le résultat de l'évaluation de cette partie vaut 38
		//	-> age = 38 : on assigne à age la valeur 38
		age = age + 20;		// age contient 38, ageMinimum contient 18, ageMaximum contient 0
	
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
