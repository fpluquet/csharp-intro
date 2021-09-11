# Tableau à une dimension et boucles for

**intro**

## Exercice

Écrire un programme qui crée un tableau de 10 éléments, le remplit aléatoirement de nombres entiers compris entre -100 et 100 et l'affiche.

Sortie possible :
```
tab[0] = 81
tab[1] = 40
tab[2] = -86
tab[3] = -31
tab[4] = 18
tab[5] = -81
tab[6] = 63
tab[7] = 10
tab[8] = -16
tab[9] = 63
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		int[] tab = new int[10];
		Random random = new Random();
		
		for(int i = 0; i < 10; i++) {
			tab[i] = random.Next(-100,100);
		}

		for(int i = 0; i < 10; i++) {
			Console.WriteLine("tab[{0}] = {1}", i, tab[i]);
		}
	}
}
```

</details>

## Exercice

Écrire un programme qui crée un tableau de 10 éléments, le remplit aléatoirement de nombres entiers compris entre -100 et 100 et l'affiche.
Ensuite il recherche le plus petit élément et l'affiche.

Sortie possible :
```
tab[0] = -38
tab[1] = 90
tab[2] = 21
tab[3] = -80
tab[4] = -84
tab[5] = 52
tab[6] = -39
tab[7] = 32
tab[8] = 84
tab[9] = 4
L'élément le plus petit est : -84
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		int[] tab = new int[10];
		Random random = new Random();
		
		for(int i = 0; i < 10; i++) {
			tab[i] = random.Next(-100,100);
		}

		for(int i = 0; i < 10; i++) {
			Console.WriteLine("tab[{0}] = {1}", i, tab[i]);
		}
		int min = int.MaxValue;
		for(int i = 0; i < 10; i++) {
			if (tab[i] < min) {
				min = tab[i];
			}
		}
		Console.WriteLine("L'élément le plus petit est : {0}", min);
	}
}
```
</details>

## Exercice

Écrire un programme qui crée un tableau de 10 éléments, le remplit aléatoirement de nombres entiers compris entre -100 et 100 et l'affiche.
Ensuite il recherche le plus grand élément et l'affiche.

Sortie possible :
```
tab[0] = -87
tab[1] = 1
tab[2] = -5
tab[3] = -22
tab[4] = -8
tab[5] = 66
tab[6] = -62
tab[7] = -38
tab[8] = 25
tab[9] = -95
L'élément le plus grand est : 66
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		int[] tab = new int[10];
		Random random = new Random();
		
		for(int i = 0; i < 10; i++) {
			tab[i] = random.Next(-100,100);
		}

		for(int i = 0; i < 10; i++) {
			Console.WriteLine("tab[{0}] = {1}", i, tab[i]);
		}
		int max = int.MinValue;
		for(int i = 0; i < 10; i++) {
			if (tab[i] > max) {
				max = tab[i];
			}
		}
		Console.WriteLine("L'élément le plus grand est : {0}", max);
	}
}
```
</details>

## Exercice

Écrivez un programme qui :
- lit un nombre ```n``` strictement positif
- lit ensuite les entrées de deux tableaux de taille ```n```
- effectue ensuite l'addition des éléments de ces deux tableaux et en affiche son résultat.

Exemple de sorties :

```
Quel est la taille des tableaux ? 3
Entrez les 3 éléments du tableau 1 : 
tab1[0] = 1
tab1[1] = 5
tab1[2] = 7
Entrez les 3 éléments du tableau 2 : 
tab2[0] = 2
tab2[1] = 2
tab2[2] = 0
La somme des éléments des deux tableaux est : 17
```

```
Quel est la taille des tableaux ? 2
Entrez les 2 éléments du tableau 1 : 
tab1[0] = 1
tab1[1] = 8
Entrez les 2 éléments du tableau 2 : 
tab2[0] = 3
tab2[1] = 7
La somme des éléments des deux tableaux est : 19
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		Console.Write("Quel est la taille des tableaux ? ");
		int n = int.Parse(Console.ReadLine());
		int[] tab1 = new int[n];
		int[] tab2 = new int[n];
		
		Console.WriteLine("Entrez les {0} éléments du tableau 1 : ", n);
		for(int i = 0; i < n; i++) {
			Console.Write("tab1[{0}] = ", i);
			tab1[i] = int.Parse(Console.ReadLine());
		}

		Console.WriteLine("Entrez les {0} éléments du tableau 2 : ",n);
		for(int i = 0; i < n; i++) {
			Console.Write("tab2[{0}] = ", i);
			tab2[i] = int.Parse(Console.ReadLine());
		}
		
		int somme = 0;
		for(int i = 0; i < n; i++) {
			somme = somme + tab1[i] + tab2[i];
		}
		
		Console.WriteLine("La somme des éléments des deux tableaux est : {0}", somme);
	}
}
```
</details>

## Exercice

Ecrivez un programme qui vous donne le prix sur 10 articles, utilisez 2 vecteurs et un menu dans votre programme.

- Lire les articles + les prix
- Afficher un menu
    1. Modifier prix article
    2. Modifier type article
    3. Afficher prix d’un article (en indiquant le nom de cet article ou le numéro)
    4. Effacer un article
    5. Quitter

<details>
	<summary>Solution</summary>

```csharp

```
</details>

## Exercice

Lire un vecteur et l'afficher. On demande alors la position d'un élément de ce vecteur. Supprimer cet élément et afficher le vecteur.


<details>
	<summary>Solution</summary>

```csharp

```
</details>