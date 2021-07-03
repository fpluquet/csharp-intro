# Conditions

**Introduction sur les conditions**

## Exercice 1

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


## Exercice 3

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


## Exercice 4

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

## Exercice 5

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

## Exercice 6

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
	
## Exercice 7

Vous allez faire vos courses et vous vous rendez compte que la caissière a des problèmes pour rendre la monnaie. Vous décidez de faire un programme pour l'aider. Pour cela, vous allez décomposer la somme d'argent qu'elle doit rendre en un nombre de pièces et/ou de billets le plus petit possible (on ne prend ici que des valeurs entières, sans centimes).

Exemple de sortie :
```
Quel est le montant à rendre ?
537
2 billet(s) de 200 euros
1 billet(s) de 100 euros
1 billet(s) de 20 euros
1 billet(s) de 10 euros
1 billet(s) de 5 euros
1 pièce(s) de 2 euros
```

<details>
	<summary>Solution</summary>

```csharp
using System;

public class Program {

    
    public static void Main(){
		// Affiche la question
		Console.WriteLine("Quel est le montant à rendre ?");

		// Lit, transforme le string en entier et assigne cette valeur à la variable aRendre 
		int aRendre = int.Parse(Console.ReadLine());
		
		// Si il y a au moins 200 euros à rendre...
		if (aRendre >= 200) {
			// ... on compte le nombre de billets de 200 euros à rendre 
			int nbBillets = aRendre / 200; // comme nbBillets est un entier, on a une division entière : 312 / 200 = 1
			
			// on retire les billets de 200 euros de la somme à rendre
			aRendre = aRendre - nbBillets * 200;
			
			// et on affiche le nombre de billets de 200 euros à rendre
			Console.WriteLine("{0} billet(s) de 200 euros", nbBillets);
		}
		// idem pour les autres billets / pièces...
		if (aRendre >= 100) {
			int nbBillets = aRendre / 100;
			aRendre = aRendre - nbBillets * 100;
			Console.WriteLine("{0} billet(s) de 100 euros", nbBillets);
		}
		if (aRendre >= 50) {
			int nbBillets = aRendre / 50;
			aRendre = aRendre - nbBillets * 50;
			Console.WriteLine("{0} billet(s) de 50 euros", nbBillets);
		}
		if (aRendre >= 20) {
			int nbBillets = aRendre / 20;
			aRendre = aRendre - nbBillets * 20;
			Console.WriteLine("{0} billet(s) de 20 euros", nbBillets);
		}
		if (aRendre >= 10) {
			int nbBillets = aRendre / 10;
			aRendre = aRendre - nbBillets * 10;
			Console.WriteLine("{0} billet(s) de 10 euros", nbBillets);
		}
		if (aRendre >= 5) {
			int nbBillets = aRendre / 5;
			aRendre = aRendre - nbBillets * 5;
			Console.WriteLine("{0} billet(s) de 5 euros", nbBillets);
		}
		if (aRendre >= 2) {
			int nbPieces = aRendre / 2;
			aRendre = aRendre - nbPieces * 2;
			Console.WriteLine("{0} pièce(s) de 2 euros", nbPieces);
		}
		if (aRendre >= 1) {
			Console.WriteLine("{0} pièce(s) de 1 euro", aRendre);
		}
    }
}
```
</details>

 
## Exercice 8

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
