# C# - Labo 3

## Buts du labo
- Utiliser des while (tant que) et do-while (faire tant que)

## Exercice 1

Ecrire un programme qui vous demande des nombres entiers. Le programme s'arrête lorsque l'on entre 0. Il affiche alors la somme et la moyenne des nombres entrés.

Exemples de sortie :
```
5
8
10
0
Somme : 23, Moyenne : 7.66666666666667
```
```
0
Somme : 0, Moyenne : 0
```
```
5
0
Somme : 5, Moyenne : 5
```



<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// déclaration et définition de la variable qui contiendra la somme des nombres entrés
		int somme = 0;
		// déclaration et définition de la variable qui contiendra le nombre de nombres entrés
		int nb = 0;
		
		// déclaration et définition de la variable qui contiendra le dernier nombre entré
		int entree = int.Parse(Console.ReadLine());
		
		// tant que le nombre entré est différent de 0
		while(entree != 0) {
			
			// on ajoute ce nombre entrée à la somme
			somme = somme + entree;
			
			// on incrémente nb
			nb = nb + 1;
			
			// on relit un nombre sur la console
			entree = int.Parse(Console.ReadLine());
		}
		
		// quand on arrive ici, entree vaut 0. 
		
		// on va gérer le cas au il n'y a aucun nombre entré
		if (nb == 0) {
			// on affiche les 0 sans faire de calcul
			Console.WriteLine("Somme : 0, Moyenne : 0");
		} else {
			// on affiche la somme et on calcule la moyenne
			// le (double) permet de caster (transformer le type de) somme d'entier en double pour avoir une moyenne en double  
			Console.WriteLine("Somme : {0}, Moyenne : {1}", somme, (double) somme / nb);
		}
	}
}
```
</details>

## Exercice 2

Écrire un programme qui va réaliser une calculatrice de base +, -, \*, / sur ```n``` nombres. Ne tenez pas compte des priorités. 

Exemple :

```
3
+
5
*
2
=
16
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// déclaration de la variable qui contiendra le résultat
		double resultat = 0;
		
		// déclaration et affectation de la variable qui contient l'entrée numérique de l'utilisateur
		double entree = int.Parse(Console.ReadLine());
		
		// le premier résultat est la première entrée 
		resultat = entree;
		
		// déclaration de la variable qui contiendra le type d'opération (+, -, *, /, =)
		string operation;
		
		// on va répéter le bloc tant que l'opération est différente de "="
		do {
			// on lit l'opération
			operation = Console.ReadLine();
			
			// si cette opération est différente de "="...
			if (operation != "=") {
				
				// ... on lit le deuxième terme de l'opération
				entree = int.Parse(Console.ReadLine());
				
				// en fonction de l'opération, on va changer le résultat avec le deuxième terme lu
				switch(operation) {
					case "+": 
						resultat = resultat + entree;
						break;
					case "-": 
						resultat = resultat - entree;
						break;
					case "/": 
						resultat = resultat / entree;
						break;
					case "*": 
						resultat = resultat * entree;
						break;
				}
			}
		} while (operation != "=");
		
		// une fois qu'on sort de la boucle, c'est que operation vaut "=", on affiche donc le résultat 
		Console.WriteLine(resultat);
	}
}
```
</details>



## Exercice 3

Vous êtes le directeur d'une écurie de Formule 1. Lors des essais, vous allez entrer tour par tour le temps réalisé par votre voiture. Le programme affichera alors à chaque tour quel est le plus petit temps, quel est le plus long et la moyenne. Lorsque vous entrez 0, le programme s'arrêtera.

<details>
	<summary>Solution</summary>

```csharp

```
</details>

