# Tableau à une dimension et boucles for

**intro**

## Exercice 1

Qu'affiche le programme suivant ?

```csharp
using System;

public class Program
{
	public static void Main()
	{
		int[] tab = new int[6];
		tab[0] = 10;
		tab[1] = 15;
		tab[2] = tab[0];
		tab[3] = tab[1];
		tab[4] = tab[0] + tab[1];
		tab[5] = 1;
		tab[5] += 2;
		tab[5]++;
		for(int i = 0; i < tab.Length; i++) {
			Console.WriteLine("tab[{0}] = {1}", i, tab[i]);
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
		// création d'un tableau nommé tab, qui contiendra 6 entiers
		int[] tab = new int[6];
		// on met 10 dans la case d'index 0
		tab[0] = 10;
		// on met 15 dans la case d'index 1
		tab[1] = 15;
		// on recopie la valeur de tab[0] (donc 10) dans la case d'index 2
		tab[2] = tab[0];
		// on recopie la valeur de tab[1] (donc 15) dans la case d'index 3
		tab[3] = tab[1];
		// on fait la somme de la valeur de tab[0] (donc 10) et tab[1] (donc 15), ce qui donne la valuer 25, qu'on va assigner à la case d'index 4
		tab[4] = tab[0] + tab[1];
		// on met 1 dans la case d'index 5
		tab[5] = 1;
		// on ajoute 2 dans la case d'index 5 (c'est équivalent à tab[5] = tab[5] + 2)
		tab[5] += 2;
		// on ajoute 1 dans la case d'index 5 (c'est équivalent à tab[5] = tab[5] + 1)
		tab[5]++;
		// on fait varier i de 0 à 5
		for(int i = 0; i < tab.Length; i++) {
			// on affiche la case i
			Console.WriteLine("tab[{0}] = {1}", i, tab[i]);
		}
	}
}
```

Ce programme affiche donc :

```
tab[0] = 10
tab[1] = 15
tab[2] = 10
tab[3] = 15
tab[4] = 25
tab[5] = 4
```

</details>

## Exercice 2

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
		// création d'un tableau nommé tab, qui contiendra 10 entiers
		int[] tab = new int[10];

		// création d'un objet random qui permet d'obtenir des nombres aléatoires
		Random random = new Random();
		
		// i varie de 0 à 9
		for(int i = 0; i < 10; i++) {
			// on assigne à tab[i] une valeur aléatoire entre -100 et 100
			tab[i] = random.Next(-100,100);
		}

		// i varie de 0 à 9
		for(int i = 0; i < 10; i++) {
			// on affiche la case i
			Console.WriteLine("tab[{0}] = {1}", i, tab[i]);
		}
	}
}
```

</details>

## Exercice 3

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
		// création d'un tableau nommé tab, qui contiendra 10 entiers
		int[] tab = new int[10];

		// création d'un objet random qui permet d'obtenir des nombres aléatoires
		Random random = new Random();
		
		// i varie de 0 à 9
		for(int i = 0; i < 10; i++) {
			// on assigne à tab[i] une valeur aléatoire entre -100 et 100
			tab[i] = random.Next(-100,100);
		}

		// i varie de 0 à 9
		for(int i = 0; i < 10; i++) {
			// on affiche la case i
			Console.WriteLine("tab[{0}] = {1}", i, tab[i]);
		}
		// on déclare une variable min
		//    dans laquelle on met le plus grand entier possible
		int min = int.MaxValue;

		// i varie de 0 à 9
		for(int i = 0; i < 10; i++) {
			// si la valeur à l'index i du tableau est plus petite que le minimum courant...
			if (tab[i] < min) {
				// ... on retient cette valeur comme minimum courant
				min = tab[i];
			}
		}

		// on affiche le minimum trouvé
		Console.WriteLine("L'élément le plus petit est : {0}", min);
	}
}
```
</details>

## Exercice 4

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
		// création d'un tableau nommé tab, qui contiendra 10 entiers
		int[] tab = new int[10];

		// création d'un objet random qui permet d'obtenir des nombres aléatoires
		Random random = new Random();
		
		// i varie de 0 à 9
		for(int i = 0; i < 10; i++) {
			// on assigne à tab[i] une valeur aléatoire entre -100 et 100
			tab[i] = random.Next(-100,100);
		}

		// i varie de 0 à 9
		for(int i = 0; i < 10; i++) {
			// on affiche la case i
			Console.WriteLine("tab[{0}] = {1}", i, tab[i]);
		}
		// on déclare une variable max
		//    dans laquelle on met le plus petit entier possible
		int max = int.MinValue;

		// i varie de 0 à 9
		for(int i = 0; i < 10; i++) {
			// si la valeur à l'index i du tableau est plus grande que le maximum courant...
			if (tab[i] > max) {
				// ... on retient cette valeur comme maximum courant
				max = tab[i];
			}
		}

		// on affiche le maximum trouvé
		Console.WriteLine("L'élément le plus grand est : {0}", max);
	}
}
```
</details>

## Exercice 5

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
		// affichage de la question
		Console.Write("Quel est la taille des tableaux ? ");

		// lecture de la taille *n* des tableaux
		int n = int.Parse(Console.ReadLine());

		// création des tableaux tab1 et tab2 de dimension n
		int[] tab1 = new int[n];
		int[] tab2 = new int[n];
		
		// affichage du texte
		Console.WriteLine("Entrez les {0} éléments du tableau 1 : ", n);

		// i varie de 0 à n - 1
		for(int i = 0; i < n; i++) {
			// affichage de la "question"
			Console.Write("tab1[{0}] = ", i);
			// lecture de l'entier et assignation à l'index i de tab1
			tab1[i] = int.Parse(Console.ReadLine());
		}

		// affichage du texte
		Console.WriteLine("Entrez les {0} éléments du tableau 2 : ",n);

		// i varie de 0 à n - 1
		for(int i = 0; i < n; i++) {
			// affichage de la "question"
			Console.Write("tab2[{0}] = ", i);
			// lecture de l'entier et assignation à l'index i de tab1
			tab2[i] = int.Parse(Console.ReadLine());
		}
		
		// on déclare et initialise la variable somme à 0 
		int somme = 0;
		// i varie de 0 à n - 1
		for(int i = 0; i < n; i++) {
			// on cumule dans somme les valeurs à l'indice i de tab1 et tab2
			somme = somme + tab1[i] + tab2[i];
		}
		
		// on affiche la somme
		Console.WriteLine("La somme des éléments des deux tableaux est : {0}", somme);
	}
}
```
</details>

## Exercice 6

Écrire un programme qui crée un tableau de 5 éléments, le remplit aléatoirement de nombres entiers compris entre -100 et 100 et l'affiche.
Ensuite il demande à l'utilisteur la position d'un élément à supprimer et décale tous les nombres après cette position d'une case vers le début et met 0 dans la dernière case vide. Vous ne devez pas gérer pas les entrées invalides.

Sorties possibles :

```
tab[0] = 81
tab[1] = -55
tab[2] = 43
tab[3] = 36
tab[4] = 45

Quelle position voulez-vous supprimer ? 0

tab[0] = -55
tab[1] = 43
tab[2] = 36
tab[3] = 45
tab[4] = 0
```

```
tab[0] = -30
tab[1] = -55
tab[2] = -100
tab[3] = 92
tab[4] = 11

Quelle position voulez-vous supprimer ? 2

tab[0] = -30
tab[1] = -55
tab[2] = 92
tab[3] = 11
tab[4] = 0
```


<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// création d'un tableau nommé tab, qui contiendra 10 entiers
		int[] tab = new int[5];

		// création d'un objet random qui permet d'obtenir des nombres aléatoires
		Random random = new Random();
		
		// i varie de 0 à 4
		for(int i = 0; i < tab.Length; i++) {
			// on assigne à tab[i] une valeur aléatoire entre -100 et 100
			tab[i] = random.Next(-100,100);
		}

		// i varie de 0 à 4
		for(int i = 0; i < tab.Length; i++) {
			// on affiche la case i
			Console.WriteLine("tab[{0}] = {1}", i, tab[i]);
		}
		// Affiche un ligne blanche
		Console.WriteLine();
		
		// Affiche la question
		Console.Write("Quelle position voulez-vous supprimer ? ");
		
		// index va contenir l'index du tableau à supprimer
		int index;
		int.TryParse(Console.ReadLine(), out index);

		// on décale tout d'un position vers le début :
		//    si i = 0, tab[0] = tab[1]
		//    si i = 1, tab[1] = tab[2]
		for(int i = index; i < tab.Length - 1; i++) {
			tab[i] = tab[i+1];
		}

		// on met zéro à la dernière position
		tab[tab.Length - 1] = 0;

		// Affiche un ligne blanche
		Console.WriteLine();
		// i varie de 0 à 4
		for(int i = 0; i < tab.Length; i++) {
			// on affiche la case i
			Console.WriteLine("tab[{0}] = {1}", i, tab[i]);
		}
	}
}
```
</details>

## Exercice 7

Trier un tableau via l'algorithme du tri à bulles[^refTriBulle].



[^refTriBulle]: https://fr.wikipedia.org/wiki/Tri_%C3%A0_bulles



## Exercice 8

Ecrivez un programme qui vous permet de gérer 10 articles, chacun ayant un nom et un prix. Utilisez 2 tableaux à une dimensions pour y stocker les noms et les prix. Utilisez un menu pour faciliter la gestion de ces articles par l'utilisateur, comme suit :

```
1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: 1

1. Non défini
2. Non défini
3. Non défini
4. Non défini
5. Non défini
6. Non défini
7. Non défini
8. Non défini
9. Non défini
10. Non défini

1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: 2

Quel numéro d'article voulez-vous modifier ? 1
Quel est le nouveau nom de l'article 1 ? Sac à dos
Nom modifié avec succès

1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: 1

1. Sac à dos : 0 euros
2. Non défini
3. Non défini
4. Non défini
5. Non défini
6. Non défini
7. Non défini
8. Non défini
9. Non défini
10. Non défini

1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: 3

Quel numéro d'article voulez-vous modifier ? 1
Quel est le nouveau prix de l'article 1 ? 30
Prix modifié avec succès

1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: 1

1. Sac à dos : 30 euros
2. Non défini
3. Non défini
4. Non défini
5. Non défini
6. Non défini
7. Non défini
8. Non défini
9. Non défini
10. Non défini

1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: 2

Quel numéro d'article voulez-vous modifier ? 2
Quel est le nouveau nom de l'article 2 ? Manteau
Nom modifié avec succès

1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: 3

Quel numéro d'article voulez-vous modifier ? 2
Quel est le nouveau prix de l'article 2 ? 79
Prix modifié avec succès

1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: 1

1. Sac à dos : 30 euros
2. Manteau : 79 euros
3. Non défini
4. Non défini
5. Non défini
6. Non défini
7. Non défini
8. Non défini
9. Non défini
10. Non défini

1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: 4

Quel numéro d'article voulez-vous modifier ? 1
Article retiré avec succès

1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: 1

1. Non défini
2. Manteau : 79 euros
3. Non défini
4. Non défini
5. Non défini
6. Non défini
7. Non défini
8. Non défini
9. Non défini
10. Non défini

1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: 5
```

Attention à biem gérer les choix invalides :

```
1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: 0

Ce choix est invalide

1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: -1

Ce choix est invalide

1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: 15

Ce choix est invalide

1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: dfgdfgdfg

Ce choix est invalide

1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: 4

Quel numéro d'article voulez-vous modifier ? un
Quel numéro d'article voulez-vous modifier ? -1
Quel numéro d'article voulez-vous modifier ? 11
Quel numéro d'article voulez-vous modifier ? 1
Article retiré avec succès
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		string[] noms = new string[10];
		int[] prix = new int[10];
		int choix = 0;
		do {
			Console.Write(@"
1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: ");
			int.TryParse(Console.ReadLine(), out choix);
			
			Console.WriteLine();
			if (choix == 1) {
				for(int i = 0; i < 10; i++) {
					if (noms[i] != null || prix[i] != 0) {
						Console.WriteLine("{0}. {1} : {2} euros", i + 1, noms[i], prix[i]);
					} else {
						Console.WriteLine("{0}. Non défini", i + 1);
					}
				}
			} else if (choix >= 2 && choix <= 4) {
				int indexArticle = -1;
				do {
					Console.Write("Quel numéro d'article voulez-vous modifier ? ");
					int.TryParse(Console.ReadLine(), out indexArticle);
					if (indexArticle < 1 || indexArticle > 10) {
						indexArticle = -1;
					}
				}while(indexArticle == -1);
				if (choix == 2) {
					Console.Write("Quel est le nouveau nom de l'article {0} ? ", indexArticle);
					string nom = Console.ReadLine();
					noms[indexArticle - 1] = nom;
					Console.WriteLine("Nom modifié avec succès");
				} else if (choix == 3) {
					Console.Write("Quel est le nouveau prix de l'article {0} ? ", indexArticle);
					int nouveauPrix = int.Parse(Console.ReadLine());
					prix[indexArticle - 1] = nouveauPrix;				
					Console.WriteLine("Prix modifié avec succès");
				} else if (choix == 4) {
					noms[indexArticle - 1] = null;
					prix[indexArticle - 1] = 0;
					Console.WriteLine("Article retiré avec succès");
				}
			} else if (choix != 5) {
				Console.WriteLine("Ce choix est invalide");
			}
		} while(choix != 5);
	}
}
```
</details>

