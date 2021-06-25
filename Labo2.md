# C# - Labo 2

## Buts du labo
- Utiliser des conditions imbriquées : if-else-if / if-if-else-else-if / ...
- Utiliser des switchs

## Exercice 1

Écrire un programme qui réalise une machine à calculer de base (+ - * /). Le programme demande 2 nombres et la fonction souhaitée. Il affiche alors le résultat. Utilisez un switch quand c'est possible.

Attention à la division par zéro.

<details>
	<summary>Solution</summary>

```csharp
using System;

public class Program
{
	public static void Main()
	{
		// Déclarations des 2 variables pour y mettre les nombres lus
		double nombre1, nombre2;
		// Déclarations de la variable pour y mettre l'opération lue
		string operation;
		
		// Affichage de la question
		Console.Write("Entrez le premier nombre : ");
		
		// Lecture, transformation en entier et assignation du premier nombre
		nombre1 = int.Parse(Console.ReadLine());

		// Affichage de la question
		Console.Write("Entrez l'opération (+,-,/,*) : ");
		// Lecture et assignation de l'opération
		operation = Console.ReadLine();
			
		// Affichage de la question
		Console.Write("Entrez le deuxième nombre : ");
		// Lecture, transformation en entier et assignation du second nombre
		nombre2 = int.Parse(Console.ReadLine());
		
		// Déclaration du résultat et assignation de la valeur NaN (Not a number)
		double resultat = double.NaN;
		
		// sélection du cas en fonction de la valeur d'operation
		switch(operation) {
			// si c'est +...
			case "+": 
				// ... on fait une addition
				resultat = nombre1 + nombre2;
				// ... et on sort du switch
				break;
			// si c'est -...
			case "-": 
				// ... on fait une soustraction
				resultat = nombre1 - nombre2;
				// ... et on sort du switch
				break;
			// si c'est /...
			case "/": 
				// ... on fait une division
				resultat = nombre1 / nombre2;
				// ... et on sort du switch
				break;
			// si c'est *...
			case "*": 
				// ... on fait une multiplication
				resultat = nombre1 * nombre2;
				// ... et on sort du switch
				break;
		}
		// si le résultat est toujours NaN, alors l'opération n'était pas +, -, /, ou *
		if (resultat.CompareTo(double.NaN) == 0) {
			// ... on affiche l'erreur
			Console.WriteLine("Opération {0} non permise", operation);
		} else {	
			// ... sinon on affiche le calcul et le résultat
			Console.WriteLine("{0} {1} {2} = {3}", nombre1, operation, nombre2, resultat);
		}
	}
}
```
</details>

## Exercice 2

Écrire un programme qui lit une date dans deux variables (jj et mm). Il doit alors l'afficher en clair: 12 janvier par exemple.

<details>
	<summary>Solution</summary>

```csharp
using System;

public class Program
{
	public static void Main()
	{
		// Déclarations des 2 variables pour y mettre la date lue
		int jj, mm;
		
		// Affichage de la question
		Console.Write("Entrez le jour : ");
		
		// Lecture, transformation en entier et assignation du jour
		jj = int.Parse(Console.ReadLine());

		// Affichage de la question
		Console.Write("Entrez le mois : ");
		
		// Lecture, transformation en entier et assignation du jour
		mm = int.Parse(Console.ReadLine());
		
		Console.Write("{0} ", jj);
			
		// sélection du cas en fonction de la valeur de mm
		switch(mm) {
			case 1:
				Console.WriteLine("janvier");
				break;
			case 2: 
				Console.WriteLine("février");
				break;
			case 3: 
				Console.WriteLine("mars");
				break;
			case 4: 
				Console.WriteLine("avril");
				break;
			case 5: 
				Console.WriteLine("mai");
				break;
			case 6: 
				Console.WriteLine("juin");
				break;
			case 7: 
				Console.WriteLine("juillet");
				break;
			case 8: 
				Console.WriteLine("août");
				break;
			case 9: 
				Console.WriteLine("septembre");
				break;
			case 10: 
				Console.WriteLine("octobre");
				break;
			case 11: 
				Console.WriteLine("novembre");
				break;
			case 12: 
				Console.WriteLine("décembre");
				break;
			default:
				// si on est dans aucun cas, on affiche "mois inconnu"
				Console.WriteLine("mois inconnu");
				break;
		}
	}
}
```
</details>

## Exercice 

Écrire un programme qui lit un mois en toute lettre ("janvier", "février", ...) et affiche le nombre de jour dans ce mois via un switch.

Conseil: il est possible de regrouper le code pour les mois qui ont le même nombre de jours sans faire de ```break```.

<details>
	<summary>Solution</summary>

```csharp
using System;

public class Program
{
	public static void Main()
	{
		// Déclarations de la variable pour y mettre le mois
		string mois;
		
		// Affichage de la question
		Console.Write("Entrez le mois : ");
		
		// Lecture, transformation en entier et assignation du jour
		mois = Console.ReadLine();
					
		// sélection du cas en fonction de la valeur de mois
		switch(mois) {
			case "janvier":
			case "mars":
			case "mai":
			case "juillet":
			case "août":
			case "octobre":
			case "décembre":
				Console.WriteLine("31 jours");
				break;
			case "février":
				Console.WriteLine("28 ou 29 jours");
				break;
			case "avril":
			case "juin":
			case "septembre":
			case "novembre":
				Console.WriteLine("30 jours");
				break;
			default:
				// si on est dans aucun cas, on affiche "mois inconnu"
				Console.WriteLine("mois inconnu");
				break;
		}
	}
}
```
</details>

## Exercice 

Un prof décide d'inscrire la note suivante en fonction du résultat obtenu :
- entre 90 et 100 PGD
- entre 80 et 89 GD
- entre 60 et 79 D
- entre 50 et 59 S
- entre 0 et 49 I

Écrire un programme qui demande une note (un nombre entre 0 et 100 à vérifier) et qui affiche l'appréciation.

## Exercice 

D'après le tableau ci-dessous, utiliser un switch pour afficher le nombre de jours et le tarif en fonction de la formation.

| Formation | Nombre de jour | Tarif journalier |
|-----------|----------------|------------------|
| Outlook   | 1              | 250€             |
| Photoshop | 3              | 300€             |
| PHP       | 3              | 350€             |

Exemple de sortie : 

```
Entrez le nombre de personnes: 3
Entrez la formation: Photoshop
Le montant est de 2700
```
