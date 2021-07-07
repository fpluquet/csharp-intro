# while et do-while

**intro**
- Utiliser des while (tant que) et do-while (faire tant que)

## Exercice 1

Que fait le programme suivant :

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		int i = 0;
		do {
			Console.WriteLine("i : {0}", i);
			i++;
		} while (i < 10);
	}
}
```

<details>
	<summary>Solution</summary>

Le programme va afficher les nombres de 0 à 9, un par ligne, chacun précédé de "i : ".

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// Déclaration et définition d'une variable entière i
		int i = 0;

		// faire...
		do {
			// on affiche "i : " suivi de la valeur de i 
			Console.WriteLine("i : {0}", i);
			// on incrémente i (revient à faire i = i + 1;)
			i++;
		} while (i < 10); //... tant que i est strictement plus petit que 10
	}
}
```

| i | Console.WriteLine | i++    | i < 10      |
|---|-------------------|--------|-------------|
| 0 | i : 0             | i = 1  | ```True```  |
| 1 | i : 1             | i = 2  | ```True```  |
| 2 | i : 2             | i = 3  | ```True```  |
| 3 | i : 3             | i = 4  | ```True```  |
| 4 | i : 4             | i = 5  | ```True```  |
| 5 | i : 5             | i = 6  | ```True```  |
| 6 | i : 6             | i = 7  | ```True```  |
| 7 | i : 7             | i = 8  | ```True```  |
| 8 | i : 8             | i = 9  | ```True```  |
| 9 | i : 9             | i = 10 | ```False``` |

</details>

## Exercice 2

Que fait le programme suivant :

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		int i = 0;
		while(i < 10) {
			i++;
			Console.WriteLine("i : {0}", i);
		}
	}
}
```

<details>
	<summary>Solution</summary>
Le programme va afficher les nombres de 1 à 10, un par ligne, chacun précédé de "i : ".

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// Déclaration et définition d'une variable entière i
		int i = 0;
		
		// tant que i est strictement plus petit que 10
		while(i < 10) {
			// on incrémente i (revient à faire i = i + 1;)
			i++;
			// on affiche "i : " suivi de la valeur de i 
			Console.WriteLine("i : {0}", i);
		}
	}
}
```

| i  | i < 10      | i++    | Console.WriteLine |
|----|-------------|--------|-------------------|
| 0  | ```True```  | i = 1  | i : 1             |
| 1  | ```True```  | i = 2  | i : 2             |
| 2  | ```True```  | i = 3  | i : 3             |
| 3  | ```True```  | i = 4  | i : 4             |
| 4  | ```True```  | i = 5  | i : 5             |
| 5  | ```True```  | i = 6  | i : 6             |
| 6  | ```True```  | i = 7  | i : 7             |
| 7  | ```True```  | i = 8  | i : 8             |
| 8  | ```True```  | i = 9  | i : 9             |
| 9  | ```True```  | i = 10 | i : 10            |
| 10 | ```False``` |        |                   |

</details>

## Exercice 3

Que fait le programme suivant :

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		int i = 10;
		while(i < 10) {
			i++;
			Console.WriteLine("i : {0}", i);
		}
	}
}
```

<details>
	<summary>Solution</summary>

Le programme n'affiche rien et se termine.

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// Déclaration et définition d'une variable entière i
		int i = 10;
		
		// i étant déjà égal à 10, on ne va pas rentrer dans le bloc du while et on arrive à la fin du programme
		while(i < 10) {
			i++;
			Console.WriteLine("i : {0}", i);
		}
	}
}
```

| i  | i < 10      | i++    | Console.WriteLine |
|----|-------------|--------|-------------------|
| 10 | ```False``` |        |                   |

</details>

## Exercice 4

Que fait le programme suivant :

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		int i = 0;
		while(i < 10); {
			i++;
			Console.WriteLine("i : {0}", i);
		}
	}
}
```



<details>
	<summary>Solution</summary>

Il y a une boucle infinie et le programme ne s'arrête jamais !

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		int i = 0;
		// attention au ; après le while 
		// A cause du ;, le while n'a pas de bloc
		// et on boucle sur la condition i < 10
		// et comme i ne change pas, on boucle indéfiniment
		while(i < 10); {
			// Ce bloc est simplement considéré comme le code à exécuter 
			// après que le while ait fini  
			i++;
			Console.WriteLine("i : {0}", i);
		}
	}
}
```

| i   | i < 10     |
|-----|------------|
| 0   | ```True``` |
| 0   | ```True``` |
| 0   | ```True``` |
| 0   | ```True``` |
| 0   | ```True``` |
| ... |            |

</details>

## Exercice 5

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

## Exercice 6

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



## Exercice 7

Vous êtes le directeur d'une écurie de Formule 1. Lors des essais, vous allez entrer tour par tour le temps réalisé par votre voiture. Le programme affichera alors à chaque tour quel est le plus petit temps, quel est le plus long et la moyenne. Lorsque vous entrez 0, le programme s'arrêtera.

<details>
	<summary>Solution</summary>

```csharp

```
</details>

