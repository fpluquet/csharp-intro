# Les boucles do-while et while

## La boucle do-while

Cette forme permet de construire une structure répétitive dans laquelle la condition de rebouclage est vérifiée à la fin : on est donc certain d’exécuter au moins une fois le bloc d’instruction à répéter. Syntaxe :

```csharp
do{ 
	// instructions à répéter
}while ( /* condition de rebouclage */);
```

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		/* Programme pour tester la structure "do...while" :
		   - boucle 3 fois en affichant une valeur i incrementée à chaque itération
		   - affiche la valeur de i après la dernière boucle.
		*/
		int i = 0;
		do {
			Console.WriteLine("iteration {0}", i);
			i = i + 1;
		} while ( i < 3 );

		Console.WriteLine("Valeur de i après la boucle : {0} ", i);
	}
}
```

## La boucle while

Cette deuxième forme est très similaire à la précédente exceptée qu’elle permet de construire une structure pour laquelle le bloc d’instructions à répéter peut éventuellement n’être jamais exécuté (comme dans le cas de la structure itérative “for”) car la condition est vérifiée avant le bloc.

Syntaxe :

```csharp
while ( /* condition de boucle */){
	// bloc d’instructions à répéter
}
```

Exemple :

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		/* Programme pour tester la structure "while" :
		   - boucle 3 fois en affichant une valeur i incrementée à chaque itération
		   - affiche la valeur de i après la dernière boucle.
		*/
		int i = 0;
		while ( i < 3 ) {
			Console.WriteLine("iteration {0}", i);
			i = i + 1;
		}

		Console.WriteLine("Valeur de i après la boucle : {0} ", i);
	}
}
```

# Exercices

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
<pre>
<b>5</b>
<b>8</b>
<b>10</b>
<b>0</b>
Somme : 23, Moyenne : 7.66666666666667
</pre>
<pre>
<b>0</b>
Somme : 0, Moyenne : 0
</pre>
<pre>
<b>5</b>
<b>0</b>
Somme : 5, Moyenne : 5
</pre>



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

Demander un nombre entre 0 et 10 et redemander tant que l'utilisateur entre un texte qui n'est pas un nombre ou l'utilisateur entre un nombre non compris entre 0 et 10. 

Exemple de sortie :
<pre>
Entrez un nombre entre 0 et 10 : <b>-1</b>
Entrez un nombre entre 0 et 10 : <b>1001</b>
Entrez un nombre entre 0 et 10 : <b>un</b>
Entrez un nombre entre 0 et 10 : <b>10</b>
Le nombre entré est 10
</pre>

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// Déclaration et initialisation de la variable entière qui contiendra le nombre entré
		int nombre;
		
		// Déclaration et initialisation de la variable booléenne qui indiquera si l'entrée est correcte ou non
		bool resultat;
		
		// Faire...
		do {
			// Affichage de la question
			Console.Write("Entrez un nombre entre 0 et 10 : ");
			
			// Lecture du nombre de l'utilisateur via TryParse			
			resultat = int.TryParse(Console.ReadLine(), out nombre);
			
		} while(resultat == false || nombre < 0 || nombre > 10); 
		// ... tant que le resultat est false ou que le nombre n'est pas compris entre 0 et 10 
		
		// Affichage du nombre entré correctement
		Console.WriteLine("Le nombre entré est {0}", nombre); 
	}
}
```
</details>

## Exercice 7

Écrire un programme qui va réaliser une calculatrice de base +, -, \*, /. Ne tenez pas compte des priorités. Le programme demande un nombre, puis une opération, puis un nombre, puis une opération, ... jusqu'à ce que le signe `=` soit entré comme opération. Le résultat est alors affiché et le programme se termine.

Exemples de sortie :

<pre>
<b>3</b>
<b>+</b>
<b>5</b>
<b>*</b>
<b>2</b>
<b>=</b>
16
</pre>

<pre>
<b>3</b>
<b>+</b>
<b>6</b>
<b>*</b>
<b>2</b>
<b>/</b>
<b>4</b>
<b>=</b>
4.5
</pre>

<pre>
<b>5</b>
<b>=</b>
5
</pre>


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



## Exercice 8

Tirez un nombre aléatoire entre 1 et 6. Répétez l'opération jusqu'à ce que la somme des nombres sortis soit strictement supérieure à 50.

Exemple de sortie :
```
Nombre tiré : 3, Somme : 3, Nb de tirages : 1
Nombre tiré : 2, Somme : 5, Nb de tirages : 2
Nombre tiré : 3, Somme : 8, Nb de tirages : 3
Nombre tiré : 5, Somme : 13, Nb de tirages : 4
Nombre tiré : 1, Somme : 14, Nb de tirages : 5
Nombre tiré : 5, Somme : 19, Nb de tirages : 6
Nombre tiré : 6, Somme : 25, Nb de tirages : 7
Nombre tiré : 6, Somme : 31, Nb de tirages : 8
Nombre tiré : 4, Somme : 35, Nb de tirages : 9
Nombre tiré : 5, Somme : 40, Nb de tirages : 10
Nombre tiré : 1, Somme : 41, Nb de tirages : 11
Nombre tiré : 2, Somme : 43, Nb de tirages : 12
Nombre tiré : 3, Somme : 46, Nb de tirages : 13
Nombre tiré : 3, Somme : 49, Nb de tirages : 14
Nombre tiré : 3, Somme : 52, Nb de tirages : 15
```

> Pour tirer des nombres aléatoires, vous pouvez utiliser la classe Random définie par C# : https://docs.microsoft.com/en-us/dotnet/api/system.random?view=net-5.0
> ```csharp
>  Random rand = new Random();
>  rand.Next(50, 101); // renvoit un nombre entier entre 50 compris et 101 non compris
> ```
>  

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// Déclaration et initialisation de la variable entière qui contiendra la somme des nombres tirés
		int somme = 0;
		
		// Déclaration et initialisation de la variable entière qui contiendra le nombre de tirages aléatoires effectués
		int nbTirages = 0;

		// Déclaration de la variable entière qui contiendra le dernier nombre aléatoire
		int nombreAleatoire;
		
		// Déclaration et initialisation de la variable qui permettra de tirer un nombre aléatoire
		Random random = new Random();
								   
		// Tant que la somme est plus petite que 50
		while(somme <= 50) {
			// Incremente le nombre de tirage
			nbTirages++;
			
			// Tirage d'un nouveau nombre aléatoire
			nombreAleatoire = random.Next(1,7);
	
			// On ajoute à somme le dernier nombre aléatoire tiré (est équivalent à somme = somme + nombreAleatoire)
			somme += nombreAleatoire;
			
			// On affiche les informations de ce tirage
			Console.WriteLine("Nombre tiré : {0}, Somme : {1}, Nb de tirages : {2}", nombreAleatoire, somme, nbTirages);
		}
	}
}
```
</details>

