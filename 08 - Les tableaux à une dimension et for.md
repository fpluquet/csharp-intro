# Tableaux à une dimension et boucles for

Un tableau est une structure de données qui permet de stocker des informations de même type et d'y accéder via un index.

En C#, un tableau est déclaré en indiquant un type et en le suffixant par des crochets (`[]`) :

```csharp
int[] tab;
string[] mots;
char[] caractères;
double[] monTableau;
```

Ces 4 variables ne sont pas encore initialisées. Pour les utiliser sans avoir créé de tableaux, on peut leur assigner la valeur `null`.

```csharp
int[] tab = null;
if (tab == null) {
	Console.WriteLine("Non initialisé");
} else {
	Console.WriteLine("Initialisé");
}
```

Ce code affiche donc `"Non initialisé"`.

On peut créer un tableau via un `new`, le type et le nombre d'éléments :

```csharp
int[] tab = new int[10];
string[] mots = new string[5];
int nb = 8;
char[] caractères = new char[nb];
double[] monTableau = new double[5 + nb];
```

Comme on le voit sur cet exemple, le nombre d'éléments ne doit pas forcément être constant : il peut être calculé (comme `nb` ou `5 + nb`).

Les différentes cases du tableau sont initialisées à leur valeur par défaut en fonction du type (0 pour les `int` et les `double`, `null` pour les `string`, ...).

## Assignation

On peut assigner des valeurs dans les cases d'un tableau en utilisant le nom du tableau suivi de l'indice (la position, l'index, ...) placé entre crochets (`[]`), un `=` et la valeur à assigner.

```csharp
int[] tab = new int[10]; // tab a 10 cases valant toutes 0
tab[0] = 5; // tab a 10 cases valant toutes 0, sauf la première qui est à 5
tab[5] = 8; // tab a 10 cases valant toutes 0, sauf la première qui est à 5 et la 6e qui est à 8
```

## Lecture

On peut lire les valeurs des cases d'un tableau en utilisant le nom du tableau suivi de l'indice (la position, l'index, ...) placé entre crochets (`[]`).

```csharp
int[] tab = new int[10];
tab[0] = 5;
tab[5] = 8;
int n;
n = tab[0]; // n contient 5
n = tab[1]; // n contient 0
n = tab[5]; // n contient 8
```

## Longueur d'un tableau

On peut obtenir la taille d'un tableau en utilisant sa propriété `Length` :

```csharp
int[] tab = new int[10];
string[] mots = new string[5];
int nb = 8;
char[] caractères = new char[nb];
double[] monTableau = new double[5 + nb];

Console.WriteLine(tab.Length); // affiche 10
Console.WriteLine(mots.Length); // affiche 5
Console.WriteLine(caractères.Length); // affiche 8
Console.WriteLine(monTableau.Length); // affiche 13
```

Cette propriété `Length` est très pratique pour itérer sur tous les éléments d'un tableau :

```csharp
int[] tab = new int[10];
tab[0] = 5;
tab[5] = 8;

for(int i = 0; i < tab.Length; i++) {
	Console.WriteLine("tab[{0}] = {1}", i, tab[i]);
}
```

Ce code va afficher toutes les cases du tableau `tab` :

```
tab[0] = 5
tab[1] = 0
tab[2] = 0
tab[3] = 0
tab[4] = 0
tab[5] = 8
tab[6] = 0
tab[7] = 0
tab[8] = 0
tab[9] = 0
```

## Le mot clé `foreach`

Lorsque l'on veut itérer sur chaque élément d'un tableau, on peut utiliser le mot clé `foreach` (traduit littéralement en `pour chaque`) en lui donnant une variable du type des éléments du tableau, le mot clé `in` et le nom du tableau :

```csharp
int[] tab = new int[10];
tab[0] = 5;
tab[5] = 8;

foreach(int n in tab) {
	Console.WriteLine("{0}", n);
}
```

Ce code affichera :

```
5
0
0
0
0
8
0
0
0
0
```

# Exercices

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

Créer un tableau de 10 entiers, remplissez-le de valeurs aléatoires entre -100 et 100 et triez ce tableau en utilisant l'algorithme du tri à bulles[^refTriBulle]. 

[^refTriBulle]: https://fr.wikipedia.org/wiki/Tri_%C3%A0_bulles


Exemple de sortie:

```
Avant le tri : 

tab[0] = -86
tab[1] = 57
tab[2] = 50
tab[3] = 99
tab[4] = 74
tab[5] = 62
tab[6] = -53
tab[7] = -67
tab[8] = 12
tab[9] = -69

Après le tri :

tab[0] = -86
tab[1] = -69
tab[2] = -67
tab[3] = -53
tab[4] = 12
tab[5] = 50
tab[6] = 57
tab[7] = 62
tab[8] = 74
tab[9] = 99
```

<details>
	<summary>Solution</summary>

Il faut évidemment déjà bien comprendre l'algorithme du tri à bulle qui permet de trier un tableau facilement.

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// déclaration et initialisation d'un tableau de 10 entiers nommé tab
		int[] tab = new int[10];

		// déclaration et initialisation de random qui permettra d'obtenir des nombres aléatoires 
		Random random = new Random(); 
		
		// assignation de 10 nombres aléatoires dans tab
		for(int i = 0; i < tab.Length; i++) {
			tab[i] = random.Next(-100,100);
		}

		// affichage du titre (le \n permet d'ajouter un retour à la ligne)
		Console.WriteLine("Avant le tri : \n");

		// i varie de 0 à tab.Length - 1
		for(int i = 0; i < tab.Length; i++) {
			// on affiche la case i
			Console.WriteLine("tab[{0}] = {1}", i, tab[i]);
		}
		
		// pseudo code provenant de Wikipedia :

		// pour i allant de (taille de T)-1 à 1
    //		pour j allant de 0 à i-1
    //   		si T[j+1] < T[j]
    //       		(T[j+1], T[j]) = (T[j], T[j+1])
		
		// i varie de tab.Length - 1 à 1
		for(int i = tab.Length - 1; i > 0; i--) {
			// j varie de 0 à i - 1
			for(int j = 0; j < i; j++) {
				// si la case suivante ([j+1]) contient un valeur plus petite que la courante ([j])
				if (tab[j + 1] < tab[j]) {
					// on échange les deux cases du tableau (swap)
					int tmp = tab[j + 1];
					tab[j + 1] = tab[j];
					tab[j] = tmp;
				}
			}
		}
		
		// affichage du titre (les \n permettent d'ajouter un retour à la ligne)
		Console.WriteLine("\nAprès le tri :\n");

		// i varie de 0 à tab.Length - 1
		for(int i = 0; i < tab.Length; i++) {
			// on affiche la case i
			Console.WriteLine("tab[{0}] = {1}", i, tab[i]);
		}
	}
}
```

</details>



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
		// déclaration et initialisation du tableau noms de 10 strings 
		string[] noms = new string[10];

		// déclaration et initialisation du tableau prix de 10 entiers 
		int[] prix = new int[10];
		
		// déclaration et initialisation de la variable contenant le choix de l'utilisateur
		int choix = 0;
		
		// on commence la boucle faire...tant que... (do/while) 
		do {
			// on affiche le menu (le préfixe @ permet d'écrire un string sur plusieurs lignes)
			Console.Write(@"
1. Afficher tous les articles et leur prix
2. Modifier le nom d'un article
3. Modifier le prix d'un article
4. Effacer un article
5. Quitter

Votre choix: ");

			// on lit le choix de l'utilisateur
			// 	=> choix sera à 0 si l'entrée n'est pas un nombre 
			int.TryParse(Console.ReadLine(), out choix);
			
			// affichage d'une ligne vide 
			Console.WriteLine();

			// si le choix est 1...
			if (choix == 1) {

				// i varie de 0 à 9
				for(int i = 0; i < 10; i++) {

					// si, pour l'élément à l'indice i, le nom est assigné ou le prix est assigné...
					if (noms[i] != null || prix[i] != 0) {
						// on affiche le nom et le prix
						Console.WriteLine("{0}. {1} : {2} euros", i + 1, noms[i], prix[i]);
					} else { // sinon...
						// on affiche "Non défini"
						Console.WriteLine("{0}. Non défini", i + 1);
					}
				}
			} else if (choix >= 2 && choix <= 4) { // sinon, si le choix est compris entre 2 et 4...
				// on va demander à l'utilisateur l'index de l'article à modifier 

				//  indexArticle va contenir le numéro d'article à modifier
				int indexArticle = -1;

				do {
					// affichage de la question
					Console.Write("Quel numéro d'article voulez-vous modifier ? ");

					// on lit indexArticle sur la console
					int.TryParse(Console.ReadLine(), out indexArticle);
					
					// si l'index est inférieur à 1 ou supérieur à 10
					if (indexArticle < 1 || indexArticle > 10) {
						// on met indexArticle à -1
						indexArticle = -1;
					}
				}while(indexArticle == -1); // on boucle sur la demande de l'indice tant que le nombre n'est pas correct 

				// si le choix est 2 (modification du nom)
				if (choix == 2) {
					// on affiche la question du nom
					Console.Write("Quel est le nouveau nom de l'article {0} ? ", indexArticle);

					// on lit le nouveau nom
					string nom = Console.ReadLine();

					// on l'assigne au bon indice dans la tableau noms
					noms[indexArticle - 1] = nom;

					// on affiche le retour utilisateur
					Console.WriteLine("Nom modifié avec succès");

				} else if (choix == 3) { // ou si le choix est 3 (modification du prix)

					// on affiche la question du prix
					Console.Write("Quel est le nouveau prix de l'article {0} ? ", indexArticle);

					// on lit le nouveau prix
					int nouveauPrix = int.Parse(Console.ReadLine());

					// on l'assigne au bon indice dans la tableau prix
					prix[indexArticle - 1] = nouveauPrix;				

					// on affiche le retour utilisateur
					Console.WriteLine("Prix modifié avec succès");

				} else if (choix == 4) {  // ou si le choix est 4 (suppression de l'article)
					
					// on efface le nom
					noms[indexArticle - 1] = null;
					
					// on efface le prix
					prix[indexArticle - 1] = 0;

					// on affiche le retour utilisateur
					Console.WriteLine("Article retiré avec succès");

				}
			} else if (choix != 5) { // si ce n'est pas 1, ni 2, ni 3, ni 4, ni 5...
				// on affiche le message d'erreur
				Console.WriteLine("Ce choix est invalide");
			}
		} while(choix != 5); // on arrête cette boucle quand le choix est 5
	}
}
```
</details>

