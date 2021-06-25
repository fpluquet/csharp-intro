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
