# Conditions

Les instructions conditionnelles permettent d'exécuter des blocs de code que si certaines conditions sont remplies.

Les conditions sont des valeurs booléennes (```true``` ou ```false```) qui peut être évaluée dynamiquement :

```csharp
bool estUnHomme = true;

if (estUnHomme == true)
{
	Console.WriteLine("C'est un homme");
}
else
{
	Console.WriteLine("Ce n'est pas un homme");
}

Console.WriteLine("Et on continue");
```

Si la condition du ```if``` est vraie, alors le bloc qui suit le ```if``` sera exécuté. Sinon le bloc suivant le ```else``` le sera.

Ici, comme estUnHomme est égal à ```true```, seul le bloc du ```if```sera exécuté et on passera ensuite à la ligne ``` Console.WriteLine("Et on continue");```. Le résultat de ce code est donc :

```
C'est un homme
Et on continue
```

Si on assigne ```false``` à la variable booléenne :

```csharp
bool estUnHomme = false;

if (estUnHomme == true)
{
	Console.WriteLine("C'est un homme");
}
else
{
	Console.WriteLine("Ce n'est pas un homme");
}

Console.WriteLine("Et on continue");
```

alors seul le bloc du ```else``` sera exécuté, donnant le résultat suivant :

```
Ce n'est pas un homme
Et on continue
```


Notez que le ```else``` est facultatif :

```csharp
bool estUnHomme = true;

if (estUnHomme == true)
{
	Console.WriteLine("C'est un homme");
}

Console.WriteLine("Et on continue");
```

## Exercice 1

Que fait le programme suivant :

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		string nom = Console.ReadLine();
		if (nom.Length < 3)
		{ 
			Console.WriteLine("Oups...");
		}
		else
		{ 
			Console.WriteLine("Ok");
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
		// Lecture d'une chaîne de caractères sur la console
		// et assignation de cette chaîne dans la variable nom 
		string nom = Console.ReadLine();

		// si la longueur de la chaîne de caractères est strictement plus petite que 3...
		if (nom.Length < 3)
		{
			// ... on affiche "Oups..." 
			Console.WriteLine("Oups...");
		}
		else
		{ 
			// ... sinon, on affiche "Ok" 
			Console.WriteLine("Ok");
		}
	}
}
```
</details>

## Exercice 2

Que fait le programme suivant :


```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		string nom = Console.ReadLine();
		string motDePasse = Console.ReadLine();
		if (nom == "Fréd" && motDePasse == "le c# c'est la vie")
		{ 
			Console.WriteLine("Connecté !");
		}
		else
		{ 
			Console.WriteLine("Erreur");
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
		// Lecture d'une chaîne de caractères sur la console
		// et assignation de cette chaîne dans la variable nom 
		string nom = Console.ReadLine();

		// Lecture d'une chaîne de caractères sur la console
		// et assignation de cette chaîne dans la variable motDePasse 
		string motDePasse = Console.ReadLine();

		// si le nom est "Fréd" et que le mot de passe est "le c# c'est la vie"
		if (nom == "Fréd" && motDePasse == "le c# c'est la vie")
		{ 
			// ... alors on affiche "Connecté !"
			Console.WriteLine("Connecté !");
		}
		else
		{ 
			// ... sinon on affiche Erreur
			Console.WriteLine("Erreur");
		}
	}
}
```
</details>

## Exercice 3


Expliquer chaque ligne du programme suivant : 

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		int entier = int.Parse(Console.ReadLine());

		if (entier > 100)
		{ 
			Console.WriteLine("Assez grand");
		}
		if (entier == 1000)
		{ 
			Console.WriteLine("1000 pile !");
		}
		if (entier % 5 == 0)
		{ 
			Console.WriteLine("Multiple de 5");
		}
	}
}
```

Que se passe-t-il si on entre les entiers suivants :

- 0
- 1
- 20
- 100
- 150
- 1000
- 1001

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// lecture d'un nombre sur la console 
		int entier = int.Parse(Console.ReadLine());

		// si l'entier est strictement plus grand que 100
		if (entier > 100)
		{ 
			// ... on affiche "Assez grand"
			Console.WriteLine("Assez grand");
		}

		// si l'entier est égal à 1000
		if (entier == 1000)
		{ 
			// ... on affiche "1000 pile !"
			Console.WriteLine("1000 pile !");
		}

		// si le reste de la division entière de l'entier par 5 est égal à 0 
		if (entier % 5 == 0)
		{ 
			// ... on affiche "Multiple de 5"
			Console.WriteLine("Multiple de 5");
		}
	}
}
```

Si on entre les entiers suivants :

- 0

```
Multiple de 5
``` 

- 1

Rien ne s'affiche

- 20

```
Multiple de 5
``` 


- 100

```
Multiple de 5
``` 

- 150

```
Assez grand
Multiple de 5
``` 

- 1000

```
Assez grand
1000 pile !
Multiple de 5
``` 
- 1001

```
Assez grand
``` 

</details>

## Exercice 4

Ecrire un programme qui vous demande votre nom, puis votre sexe (M,F) et écrit :
   
   ```Bonjour Monsieur x```
   ou 
   ```Bonjour Madame x```

 où ```x``` est le nom entré.

Exemples de sorties :

<pre>
Quel est votre nom ?
<b>Fréd</b>
Quel est votre sexe (M/F) ?
<b>M</b>
Bonjour Monsieur Fréd
</pre>

<pre>
Quel est votre nom ?
<b>Sabine</b>
Quel est votre sexe (M/F) ?
<b>F</b>
Bonjour Madame Sabine
</pre>

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
		if (sexe == "M")
		{
			Console.WriteLine("Bonjour Monsieur " + nom);
		}
		else
		{
			Console.WriteLine("Bonjour Madame " + nom);
		}
	}
}
```
</details>


## Exercice 5

Écrire un programme qui vous demande votre âge et affiche si vous êtes majeur ou mineur. L'âge pivot est 18 ans.

Exemple de sorties :

```
Quel est votre âge ?
18
Vous êtes majeur
```

```
Quel est votre âge ?
80
Vous êtes majeur
```

```
Quel est votre âge ?
17
Vous êtes mineur
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
		Console.WriteLine("Quel est votre âge ?");

		// lecture de l'entrée de l'utilisateur dans la variable line
		string line = Console.ReadLine();

		// transformation de la chaîne de caractères en entier
		int age = int.Parse(line);

		// si l'âge est plus grand ou égal à 18... 
		if (age >= 18)
		{
			// ... on affiche qu'il est majeur
			Console.WriteLine("Vous êtes majeur");
		}
		else
		{
			// ... sinon on affiche qu'il est mineur
			Console.WriteLine("Vous êtes mineur");
		}
	}
}
```
</details>

## Exercice 6

Écrire un programme qui demande une année. Il doit vous dire si c'est une année bissextile ou pas. Pour rappel, une année est bissextile :
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
L'année 2022 n'est pas bissextile
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
		if ((annee % 4 == 0 && annee % 100 != 0) || (annee % 400 == 0))
		{
			// On affiche que cette année est bissextile
			Console.WriteLine("L'année {0} est bissextile", annee);
		}
		else
		{
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
		if (aRendre >= 200)
		{
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
