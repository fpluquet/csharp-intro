# C# - Labo 1

## Buts du labo

## Exercice 1

Ecrire un programme qui vous demande votre nom et écrit ```Bonjour x``` où ```x``` est le nom entré. 

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
		Console.WriteLine("Bonjour " + nom);
	}
}
```
</details>

## Exercice 2

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

Ecrire un programme qui combine les exercices 2 et 3, c'est-à-dire qui vous demande votre nom, puis votre sexe (M,F), votre âge et écrit la bonne phrase en fonction des données :

```
Bonjour Monsieur x

Bonjour Madame x

Bonjour Jeune Homme x

Bonjour Mademoiselle x
```

où ```x``` est le nom entré.


## Exercice 5

Ecrire un programme qui trie 3 nombres par ordre croissant.

## Exercice 6

Ecrire un programme qui demande une année. Il doit vous dire si c'est une année bissextile ou pas.

## Exercice 7

Vous allez faire vos courses et vous vous rendez compte que la caissière a des problèmes pour rendre la monnaie. Vous décidez de faire un programme pour l'aider. Pour cela, vous allez décomposer la somme d'argent qu'elle doit rendre en un nombre de pièces et/ou de billets le plus petit possible.

> Demande de connaître les boucles
 
## Exercice 8

Ecrire un programme qui demande à l'utilisateur de taper 5 entiers et qui affiche le plus grand. Le programme ne devra utiliser que 2 variables.
