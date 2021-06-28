# C# - Labo 1

## Buts du labo
- Découvrir les bases de C#
- Utiliser les variables entières et les chaînes de caractères (string)
- Utiliser le flot conditionnel : if / if-else / if-else-if / ...

## Variables

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
La valeur contenue dans ```age``` sera recopiée dans la variable nommée ```ageMinimum```.

### Exercice 1

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

## Concatenation de string

**Introduction sur les strings et la concatenation**

## Console

Pour afficher un texte sur la console :
```
Console.Write("Bonjour !");
```

Pour afficher un texte sur la console et revenir à la ligne :
```
Console.WriteLine("Bonjour !");
```

Pour lire un texte depuis la console :
```
string ligne = Console.ReadLine();
```

### Exercice

Que fait exactement le programme suivant ? 

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		string entrée = Console.ReadLine();	
		Console.Write("Avant:");
		Console.WriteLine(entrée);
		Console.Write("Après");
	}
}
```

<details>
	<summary>Solution</summary>

> Si on a entré le texte "Salut" alors cela affichera :
> 
> ```
> Avant:Salut
> Après
> ```

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// Le programme va attendre qu'on entre un texte et qu'on revienne à la ligne. 
		// Le texte lu est alors assigné dans la variable nommée *entrée* qui est de type string (chaîne de caractères)
		string entrée = Console.ReadLine();
	
		// On affiche le texte Avant: sans revenir à la ligne
		Console.Write("Avant:");
	
		// On affiche le texte lu par le ReadLine() et on revient à la ligne.
		Console.WriteLine(entrée);

		// On affiche le texte Après
		Console.Write("Après");
	}
}
```
	
</details>

### Exercice 2

Ecrire un programme qui vous demande votre nom et écrit ```Bonjour x``` où ```x``` est le nom entré.

Exemple de sortie :
```
Quel est votre nom ?
Nico
Bonjour Nico
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// affichage de la question sur la console
		Console.WriteLine("Quel est votre nom ?");
		
		// lecture du nom de l'utilisateur 
		string nom = Console.ReadLine();

		// affichage du message sur la console
		Console.Write("Bonjour ");
		Console.WriteLine(nom);
	}
}
```
</details>

## Conditions

**Introduction sur les conditions**

### Exercice 2

Ecrire un programme qui vous demande votre nom, puis votre sexe (M,F) et écrit :
   
   ```Bonjour Monsieur x```
   ou 
   ```Bonjour Madame x```

 où ```x``` est le nom entré.
 
<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// affichage de la question sur la console
		Console.WriteLine("Quel est votre nom ?");
		
		// lecture du nom de l'utilisateur 
		string nom = Console.ReadLine();

		// affichage de la question sur la console
		Console.WriteLine("Quel est votre sexe (M/F) ?");

		// lecture du sexe de l'utilisateur 
		string sexe = Console.ReadLine();
		if (sexe == "M") {
			Console.WriteLine("Bonjour Monsieur " + nom);
		} else {
			Console.WriteLine("Bonjour Madame " + nom);
		}
	}
}
```
</details>


### Exercice 3

Écrire un programme qui vous demande votre âge et affiche si vous êtes majeur ou mineur

<details>
	<summary>Solution</summary>

```csharp
using System;

public class Program
{
	public static void Main()
	{
		// affichage de la question sur la console
		Console.WriteLine("Quel est votre âge ?");

		// lecture de l'entrée de l'utilisateur dans la variable line
		string line = Console.ReadLine();

		// transformation de la chaîne de caractères en entier
		int age = int.Parse(line);

		// si l'âge est plus grand ou égal à 18... 
		if (age >= 18) {
			// ... on affiche qu'il est majeur
			Console.WriteLine("Vous êtes majeur");
		} else {
			// ... sinon on affiche qu'il est mineur
			Console.WriteLine("Vous êtes mineur");
		}
	}
}
```
</details>


### Exercice 4

Ecrire un programme qui combine les exercices 2 et 3, c'est-à-dire qui vous demande votre nom, puis votre sexe (M,F), puis votre âge et écrit la bonne phrase en fonction des données entrées :

```
Bonjour Monsieur x

Bonjour Madame x

Bonjour Jeune Homme x

Bonjour Mademoiselle x
```

où ```x``` est le nom entré, et l'âge pivot est 18 ans.

<details>
	<summary>Solution</summary>

```csharp
using System;

public class Program
{
	public static void Main()
	{
		// affichage de la question sur la console
		Console.WriteLine("Quel est votre nom ?");
		
		// lecture du nom de l'utilisateur 
		string nom = Console.ReadLine();

		// affichage de la question sur la console
		Console.WriteLine("Quel est votre sexe (M/F) ?");

		// lecture du sexe de l'utilisateur 
		string sexe = Console.ReadLine();
		
		// affichage de la question sur la console
		Console.WriteLine("Quel est votre âge ?");

		// lecture de l'entrée de l'utilisateur dans la variable line
		string line = Console.ReadLine();

		// transformation de la chaîne de caractères en entier
		int age = int.Parse(line);

		// si l'âge est plus grand ou égal à 18... 
		if (age >= 18) {
			// ... et que c'est un homme
			if (sexe == "M") {
				Console.WriteLine("Bonjour Monsieur " + nom);
			} else {
				// ... et que c'est une femme
				Console.WriteLine("Bonjour Madame " + nom);
			}
		} else {
			// ... et que c'est un homme
			if (sexe == "M") {
				Console.WriteLine("Bonjour Jeune Homme " + nom);
			} else {
				// ... et que c'est une femme
				Console.WriteLine("Bonjour Mademoiselle " + nom);
			}
		}
	}
}
```
</details>

### Exercice 5

Ecrire un programme qui demande 3 nombres à l'utilisateur et les affiche ensuite par ordre croissant.

Exemple de sortie :

```
Quel est le premier nombre ?
22
Premier nombre : 22
Quel est le deuxième nombre ?
33
Deuxième nombre : 33
Quel est le troisième nombre ?
11
Troisième nombre : 11
Nombres triés : 11 22 33
```

<details>
	<summary>Solution</summary>

```csharp
using System;

public class Program
{
	public static void Main()
	{
		int a, b, c;

		// affichage de la question sur la console
		Console.WriteLine("Quel est le premier nombre ?");		
		
		// lecture, transformation de la chaîne de caractères en entier et assignation dans a
		int.TryParse(Console.ReadLine(), out a);
		
		// affichage de l'entier lu
		Console.WriteLine("Premier nombre : " + a);		

		// affichage de la question sur la console
		Console.WriteLine("Quel est le deuxième nombre ?");		
		
		// lecture, transformation de la chaîne de caractères en entier et assignation dans b
		int.TryParse(Console.ReadLine(), out b);
		
		// affichage de l'entier lu
		Console.WriteLine("Deuxième nombre : " + b);		
		
		// affichage de la question sur la console
		Console.WriteLine("Quel est le troisième nombre ?");		
		
		// lecture, transformation de la chaîne de caractères en entier et assignation dans c
		int.TryParse(Console.ReadLine(), out c);
		
		// affichage de l'entier lu
		Console.WriteLine("Troisième nombre : " + c);
		
		// affichage du début de la ligne (le Write n'écrit pas de retour à la ligne)
		Console.Write("Nombres triés : ");

		if (a < b) {
			// a < b
			if (b < c) {
				// a < b && b < c, donc a < b < c
				Console.WriteLine("{0} {1} {2}", a, b, c); 
			} else {
				// b >= c
				if (a < c) {
					// a < b && a < c && c <= b, donc a < c <= b
					Console.WriteLine("{0} {1} {2}", a, c, b); 
				} else {
					// a < b && c <= a && c <= b, donc c <= a < b
					Console.WriteLine("{0} {1} {2}", c, a, b); 
				}
			}
		} else {
			// b <= a
			if (c < b) {
				// b <= a && c < b, donc c < b <= a
				Console.WriteLine("{0} {1} {2}", c, b, a); 
			} else {
				// b <= a && b <= c
				if (a < c) {
					// b <= a && b <= c && a < c, donc b <= a < c
					Console.WriteLine("{0} {1} {2}", b, a, c); 
				} else {
					// b <= a && b <= c && a >= c, donc b <= c <= a
					Console.WriteLine("{0} {1} {2}", b, c, a); 
				}
			}
		}		
	}
}
```
</details>

### Exercice 6

Ecrire un programme qui demande une année. Il doit vous dire si c'est une année bissextile ou pas. Pour rappel, une année est bissextile :
- si l'année est divisible par 4 et non divisible par 100
- ou si l'année est divisible par 400.
	
« Divisible » signifie que la division donne un nombre entier, sans reste.

Exemple de sorties :
	
```
Entrez une année : 2021
L'année 2021 n'est pas bissextile
```
```
Entrez une année : 2022
L'année 2022 est bissextile
```
```
Entrez une année : 2000
L'année 2000 est bissextile
```
```
Entrez une année : 2100
L'année 2100 n'est pas bissextile
```

<details>
	<summary>Solution</summary>

```csharp
using System;

public class Program
{
	public static void Main()
	{
		int annee;

		// affichage de la question sur la console
		Console.Write("Entrez une année : ");		
		
		// lecture, transformation de la chaîne de caractères en entier et assignation dans annee
		int.TryParse(Console.ReadLine(), out annee);
		
		// (si annee est divisible par 4 et pas par 100) ou (si annee est divisible par 400)
		if ((annee % 4 == 0 && annee % 100 != 0) || (annee % 400 == 0)) {
			// On affiche que cette année est bissextile
			Console.WriteLine("L'année {0} est bissextile", annee);
		} else {
			// On affiche que cette année n'est pas bissextile
			Console.WriteLine("L'année {0} n'est pas bissextile", annee);
		}
	}
}
```
</details>
	
### Exercice 7

Vous allez faire vos courses et vous vous rendez compte que la caissière a des problèmes pour rendre la monnaie. Vous décidez de faire un programme pour l'aider. Pour cela, vous allez décomposer la somme d'argent qu'elle doit rendre en un nombre de pièces et/ou de billets le plus petit possible.

> Demande de connaître les boucles
 
### Exercice 8

Ecrire un programme qui demande à l'utilisateur de taper 5 entiers et qui affiche le plus grand. Le programme ne devra utiliser que 2 variables.

Exemple de sortie :
```
Entrez un nombre : 5
Entrez un nombre : 2
Entrez un nombre : 3
Entrez un nombre : 20
Entrez un nombre : 1
La valeur maximale est 20
```
	
<details>
	<summary>Solution</summary>
	
```csharp
using System;

public class Program
{
	public static void Main()
	{
		// Déclaration et initialisation de la variable qui contiendra le maximum
		int max = int.MinValue;

		// Déclaration de la variable qui contiendra le dernier nombre entré
		int last;
		
		// Affichage de la question
		Console.Write("Entrez un nombre : ");
		
		// Lecture du nombre
		int.TryParse(Console.ReadLine(), out last);
		
		// Si le nombre lu est plus grand que la valeur contenue dans max, alors on remplace...
		if (last > max) {
			// ... alors on remplace le max par cette valeur
			max = last;
		}
		
		// puis idem 4 fois

		Console.Write("Entrez un nombre : ");
		int.TryParse(Console.ReadLine(), out last);
		
		if (last > max) {
			max = last;
		}
		Console.Write("Entrez un nombre : ");
		int.TryParse(Console.ReadLine(), out last);
		
		if (last > max) {
			max = last;
		}
		
		Console.Write("Entrez un nombre : ");
		int.TryParse(Console.ReadLine(), out last);
		
		if (last > max) {
			max = last;
		}
		
		Console.Write("Entrez un nombre : ");
		int.TryParse(Console.ReadLine(), out last);
		
		if (last > max) {
			max = last;
		}
		
		// Affichage de la valeur maximale
		Console.WriteLine("La valeur maximale est {0}", max);
		
	}
}
```
</details>
