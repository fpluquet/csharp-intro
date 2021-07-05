# C# - Labo 2

## Buts du labo
- Utiliser des conditions imbriquées : if-else-if / if-if-else-else-if / ...
- Utiliser des switchs

## Exercice 1

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

## Exercice 2

Créer un programme qui demande une chaîne de caractères et si cette chaîne ne finit pas par un 's' ou un 'x', ajouter un 'x' si cela finit par 'ou' ou ajouter un 's' et l'afficher.

Exemple de sortie:
```
Quel mot faut-il mettre au pluriel ? Chien
Le mot "Chien" au pluriel : Chiens
```
```
Quel mot faut-il mettre au pluriel ? Chiens
Le "Chiens" est déjà au pluriel. 
```
```
Quel mot faut-il mettre au pluriel ? Hibou
Le mot "Hibou" au pluriel : Hiboux
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// affichage de la question
		Console.Write("Quel mot faut-il mettre au pluriel ?");

		// lecture et assignation du mot de l'utilisateur
		string mot = Console.ReadLine();
		
		// on stocke le dernier caractère dans un variable de type caractère (char)
		char dernierCaractère = mot[mot.Length - 1];
		
		// si la dernière lettre est un 's' ou un 'x'...
		if (dernierCaractère == 's' || dernierCaractère == 'x') {
			// ... alors on affiche que c'est déjà au pluriel
			Console.WriteLine("Le \"{0}\" est déjà au pluriel.", mot); 
		} else {
			// on sait que le mot ne finit pas par un 's' ou un 'x'
			// est-ce qu'il finit pour 'ou' ? 
			if (mot.EndsWith("ou")) {
				// si oui, on met un x
				Console.WriteLine("Le mot \"{0}\" au pluriel : {1}", mot, mot + "x");
			} else {
				// ... sinon on affiche le mot au pluriel
				Console.WriteLine("Le mot \"{0}\" au pluriel : {1}", mot, mot + "s");
			}
		}
	}
}
```
</details>

## Exercice 3

Créer un programme qui demande une chaîne de caractères et si cette chaîne ne finit pas par un 's' ou un 'x', ajouter un 'x' si c'est une des exceptions (Bijou, Caillou, Chou, Genou, Hibou, Joujou, Pou) ou alors ajouter un 's' et l'afficher. La casse du mot (majuscules, miniscules, ...) de ne pas avoir d'importance.

Exemple de sortie:
```
Quel mot faut-il mettre au pluriel ? Chien
Le mot "Chien" au pluriel : Chiens
```
```
Quel mot faut-il mettre au pluriel ? Chiens
Le "Chiens" est déjà au pluriel. 
```
```
Quel mot faut-il mettre au pluriel ? Hibou
Le mot "Hibou" au pluriel : Hiboux
```
```
Quel mot faut-il mettre au pluriel ? hibou
Le mot "Hibou" au pluriel : hiboux
```
```
Quel mot faut-il mettre au pluriel ? Caribou
Le mot "Caribou" au pluriel : Caribous
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// affichage de la question
		Console.Write("Quel mot faut-il mettre au pluriel ?");

		// lecture et assignation du mot de l'utilisateur
		string mot = Console.ReadLine();
		
		// on stocke le dernier caractère dans un variable de type caractère (char)
		char dernierCaractère = mot[mot.Length - 1];
		
		// si la dernière lettre est un 's' ou un 'x'...
		if (dernierCaractère == 's' || dernierCaractère == 'x') {
			// ... alors on affiche que c'est déjà au pluriel
			Console.WriteLine("Le \"{0}\" est déjà au pluriel.", mot); 
		} else {
			// on sait que le mot ne finit pas par un 's' ou un 'x'
			// est-ce qu'il finit pour 'ou' ? 
			if (mot.EndsWith("ou")) {
				// si c'est une exception...
				if (mot.ToLower() == "bijou" ||
					mot.ToLower() == "caillou" ||
					mot.ToLower() == "chou" ||
					mot.ToLower() == "genou" ||
					mot.ToLower() == "hibou" ||
					mot.ToLower() == "joujou" ||
					mot.ToLower() == "pou") {
					// on ajoute un 'x'
					Console.WriteLine("Le mot \"{0}\" au pluriel : {1}", mot, mot + "x");
				} else {
					// sinon on ajoute un 's'
					Console.WriteLine("Le mot \"{0}\" au pluriel : {1}", mot, mot + "s");
				}
			} else {
				// ... sinon on affiche le mot au pluriel
				Console.WriteLine("Le mot \"{0}\" au pluriel : {1}", mot, mot + "s");
			}
		}
	}
}
```
</details>

## Exercice 4

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

## Exercice 5

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

## Exercice 6

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
		// Déclaration de la variable pour y mettre le mois
		string mois;
		
		// Affichage de la question
		Console.Write("Entrez le mois : ");
		
		// Lecture et assignation du mois
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

## Exercice 7

Un prof décide d'inscrire la mention suivante en fonction des points obtenus :

| Points obtenus  | Acronyme de la mention | Explication             |
|-----------------|------------------------|-------------------------|
| entre 90 et 100 | PGD                    | Plus grande distinction |
| entre 80 et 89  | GD                     | Grande distinction      |
| entre 70 et 79  | D                      | Distinction             |
| entre 60 et 69  | S                      | Satisfaction            |
| entre 50 et 59  | SM                     | Sans mention            |
| entre 0 et 49   | I                      | Insatisfaction          |



Écrire un programme qui demande une note (un nombre entre 0 et 100 à vérifier) et qui affiche la mention correspondante.

Exemple de sorties :

```
Entrez les points (entre 0 et 100 compris) : 100
La mention obtenue est : PGD
```
```
Entrez les points (entre 0 et 100 compris) : 87
La mention obtenue est : GD
```
```
Entrez les points (entre 0 et 100 compris) : -1
Les points entrés sont invalides.
```
```
Entrez les points (entre 0 et 100 compris) : cent
Les points entrés sont invalides.
```
```
Entrez les points (entre 0 et 100 compris) : 
Les points entrés sont invalides.
```

<details>
	<summary>Solution</summary>

```csharp
using System;

public class Program
{
	public static void Main()
	{
		// Déclaration de la variable pour y mettre les points obtenus
		int points;
		
		// Déclaration de la variable qui contiendra le grade obtenu
		string grade = "";
		
		// Affichage de la question
		Console.Write("Entrez les points (entre 0 et 100 compris) : ");
		
		// Lecture, transformation en entier et assignation des points
		bool estUnEntier = int.TryParse(Console.ReadLine(), out points);
		
		if (estUnEntier == false || points < 0 || points > 100) {
			// si le nombre entré n'est pas un nombre ou s'il n'est pas compris entre les 0 et 100 compris
			grade = "Erreur";
		} else if (points >= 90) {
			// ici, points >= 90 et points <= 100
			grade = "PGD";
		} else if (points >= 80) {
			// ici, points >= 80 et points < 90
			grade = "GD";
		} else if (points >= 70) {
			// ici, points >= 70 et points < 80
			grade = "D";
		} else if (points >= 60) {
			// ici, points >= 60 et points < 70
			grade = "S";
		} else if (points >= 50) {
			// ici, points >= 50 et points < 60
			grade = "SM";
		} else if (points < 50) {
			// ici, points >= 0 et points < 50
			grade = "I";
		}
		
		if (grade == "Erreur") {
			// si il y avait une erreur
			Console.WriteLine("Les points entrés sont invalides.");
		} else {
			// sinon on affiche la mention obtenue
			Console.WriteLine("La mention obtenue est : {0}", grade);
		}
	}
}
```
</details>

## Exercice 8

D'après le tableau ci-dessous, utiliser un switch pour afficher le nombre de jours et le tarif en fonction de la formation.

| Formation | Nombre de jour | Tarif journalier |
|-----------|----------------|------------------|
| Outlook   | 1              | 250€             |
| Photoshop | 3              | 300€             |
| PHP       | 3              | 350€             |

Exemple de sorties : 

```
Entrez le nombre de personnes: 3
Entrez la formation: Photoshop
Le montant est de 2700 euros
```
```
Entrez le nombre de personnes: 3
Entrez la formation: C#
La formation n'existe pas.
```
```
Entrez le nombre de personnes: un texte
Le nombre entré de personnes n'est pas valide.
```
	
<details>
	<summary>Solution</summary>

```csharp
using System;

public class Program
{
	public static void Main()
	{
		// Déclaration des variable nécessaires
		int prixJournalier, nbJours, nbPersonnes;
		string nomFormation;
		
		// Affichage de la question
		Console.Write("Entrez le nombre de personnes: ");
		
		// Lecture, transformation en entier et assignation du nombre de personnes
		bool estUnEntier = int.TryParse(Console.ReadLine(), out nbPersonnes);
		
		if (estUnEntier == false || nbPersonnes <= 0) {
			// si le nombre entré n'est pas un nombre ou s'il est nul ou négatif
			Console.WriteLine("Le nombre entré de personnes n'est pas valide.");
		} else {
			// Affichage de la question
			Console.Write("Entrez la formation: ");
			
			// Lecture et assignation du nom de la formation
			nomFormation = Console.ReadLine();
			
			// switch en fonction de la valeur de nomFormation
			switch (nomFormation) {
				case "Outlook":
					prixJournalier = 250;
					nbJours = 1;
					break;
				case "Photoshop":
					prixJournalier = 300;
					nbJours = 3;
					break;
				case "PHP":
					prixJournalier = 350;
					nbJours = 3;
					break;
				default:
					// si nomFormation ne contient pas "Outlook", "Photoshop" ou "PHP"
					nbJours = -1;
					prixJournalier = -1;
					break;
			}
			if (nbJours == -1) {
				Console.WriteLine("Formation inexistante");
			} else {
				Console.WriteLine("Le montant est de {0} euros", nbJours * nbPersonnes * prixJournalier);
			}
		}
	}
}
```
</details>
