# Les tableaux à plusieurs dimensions

Nous avons déjà vu les tableaux à une dimension :

```csharp
int[] monTab = new int[5];
monTab[0] = 1;
monTab[1] = 3;
monTab[2] = 5;
monTab[3] = 7;
monTab[4] = 9;
for(int i = 0; i < monTab.Length; i++) {
  Console.Write("{0} ", monTab[i]);
}
```

Ce code affiche les nombres `1 3 5 7 9` sur la console. Ce tableau n'a qu'une seule dimension.

Les tableaux à plusieurs dimensions permettent de manipuler des tableaux ayant plus qu'une dimension.

Si nous prenons des tableaux à deux dimensions, nous pouvons les voir comme des matrices (voir le cours de Math). Voici comment nous pouvons les créer :

```csharp
int[,] tab = new int[2,3];
```

Le `new int[2,3]` permet de dire au compilateur que nous voulons créer un tableau à deux dimensions avec 2 lignes sur 3 colonnes. Nous avons donc 6 emplacements :

<table border=1>
<tr><td></td><td><b>0</b></td><td><b>1</b></td><td><b>2</b></td></tr>
<tr><td><b>0</b></td><td>0</td><td>0</td><td>0</td></tr>
<tr><td><b>1</b></td><td>0</td><td>0</td><td>0</td></tr>
</table>

Comme nous travaillons avec des entiers, toutes les éléments du tableau sont initialisés à 0.

Le `int[,] tab` permet de définir une variable nommée `tab` qui pourra accepter un tableau à deux dimensions. Notez que la virgule permet de bien montrer que le tableau contiendra 2 dimensions.

Pour assigner une case du tableau, cela ressemble très fort à ce que nous faisions avec les tableaux à une dimension :

```csharp
tab[0,0] = 5;
tab[1,2] = 7;
tab[0,1] = 4;
```

Ces instructions auront pour effet de modifier le tableau comme suit :

<table border=1>
<tr><td></td><td><b>0</b></td><td><b>1</b></td><td><b>2</b></td></tr>
<tr><td><b>0</b></td><td>5</td><td>4</td><td>0</td></tr>
<tr><td><b>1</b></td><td>0</td><td>0</td><td>7</td></tr>
</table>

Pour lire une case du tableau, cela ressemble également très fort à ce que nous faisions avec les tableaux à une dimension :

```csharp
Console.WriteLine(tab[0,0]); // affiche 5
Console.WriteLine(tab[1,0]); // affiche 0
Console.WriteLine(tab[1,2]); // affiche 7
Console.WriteLine(tab[0,1]); // affiche 4
```

## Initialisation

On peut initialiser rapidement un tableau dès sa création via des accolades :

```csharp
int[,] tab = new int[,] {
              {5,4,0},
              {0,0,7}
            };
```

Cette instruction a pour effet de créer le tableau comme suit :

<table border=1>
<tr><td></td><td><b>0</b></td><td><b>1</b></td><td><b>2</b></td></tr>
<tr><td><b>0</b></td><td>5</td><td>4</td><td>0</td></tr>
<tr><td><b>1</b></td><td>0</td><td>0</td><td>7</td></tr>
</table>

> Attention ! Il faut que le nombre de colonnes soit égal pour chaque ligne renseignée. Si ce n'est pas le cas, le compilateur n'acceptera pas votre code.


## Longueurs d'un tableau

Ici la longueur d'un tableau à plusieurs dimensions perd un peu son sens :

```csharp
int[,] tab = new int[2,3];
Console.WriteLine(tab.Length); // Affiche 6
```

La propriété `Length` retourne donc le nombre total d'éléments. Souvent ce n'est pas très utile.

Par contre, nous pouvons utiliser la méthode `GetLength(i)` pour obtenir la longueur de la dimension `i` (basée en `0`):

```csharp
int[,] tab = new int[2,3];
Console.WriteLine(tab.GetLength(0)); // Affiche 2
Console.WriteLine(tab.GetLength(1)); // Affiche 3

tab = new int[8,12];
Console.WriteLine(tab.GetLength(0)); // Affiche 8
Console.WriteLine(tab.GetLength(1)); // Affiche 12
```

C'est donc beaucoup plus pratique pour pouvoir accéder au tableau de manière séquentielle :

```csharp
int[,] tab = new int[,] {
          {5,4,0},
          {0,0,7}
        };

for(int ligne = 0; ligne < tab.GetLength(0); ligne++) {
  for(int colonne = 0; colonne < tab.GetLength(1); colonne++) {
    Console.Write("{0} ", tab[ligne, colonne]);
  }
  Console.WriteLine();
}
```

Nous utilisons la méthode `GetLength` pour afficher l'entièreté du tableau via 2 boucles `for` (une pour les lignes et pour chaque ligne, une autre pour les colonnes). Cela affiche donc :

```
5 4 0 
0 0 7
```

## Multidimensions

Nous ne sommes pas limités à seulement 2 dimensions. En effet, nous pouvons créer des tableaux de plus de 2 dimensions :

```csharp
int[,,] tab3 = new int[2,3,4]; // tableau à 3 dimensions de 2 sur 3 sur 4 élements
tab3[0,0,0] = 5;
tab3[1,2,2] = 2;

string[,,,] tab4 = new string[2,2,2,2]; // tableau à 4 dimensions de 2x2x2x2
tab4[0,1,0,0] = "Coucou";
```

# Exercices

## Exercice

Que fait le programme suivant ?

```csharp
using System;
					
public class Program
{
	
	public static void AfficheArray2D(int[,] array) {
		for(int ligne = 0; ligne < array.GetLength(0); ligne++) {
			for(int colonne = 0; colonne < array.GetLength(1); colonne++) {
				Console.Write("{0} ", array[ligne, colonne]);
			}
			Console.WriteLine();
		}
	}
	public static void Main()
	{
		int[,] tab = new int[3,3];
		
		Console.WriteLine("Avant :\n");
		AfficheArray2D(tab);

		Console.WriteLine("\nAprès:\n");
		for(int ligne = 0; ligne < tab.GetLength(0); ligne++) {
			for(int colonne = 0; colonne < tab.GetLength(1); colonne++) {
				tab[ligne, colonne] = ligne * 3 + colonne;
			}
		}
		
		AfficheArray2D(tab);

	}
}
```

<details>
  <summary>Solution</summary>
Ce programme affiche la sortie suivante :

```
Avant :

0 0 0 
0 0 0 
0 0 0 

Après:

0 1 2 
3 4 5 
6 7 8
```

Voici l'explication :

```csharp
using System;
					
public class Program
{
  // on définit une fonction qui :
  // - a comme nom : AfficheArray2D
  // - prend 1 paramètre nommé array de type int[,] (un tableau d'entiers à deux dimensions)
  // - ne renvoie aucune valeur (void)
	public static void AfficheArray2D(int[,] array) {
    // ligne va varier de 0 au nombre d'éléments (-1) de la première dimension
		for(int ligne = 0; ligne < array.GetLength(0); ligne++) {
      // colonne va varier de 0 au nombre d'éléments (-1) de la deuxième dimension
			for(int colonne = 0; colonne < array.GetLength(1); colonne++) {
        // on affiche l'élément à la position (ligne,colonne)
				Console.Write("{0} ", array[ligne, colonne]);
			}
      // on affiche l'élément à la position (ligne,colonne)
			Console.WriteLine();
		}
	}
	public static void Main()
	{
		int[,] tab = new int[3,3];
		
		Console.WriteLine("Avant :\n");
		AfficheArray2D(tab);

		Console.WriteLine("\nAprès:\n");
		for(int ligne = 0; ligne < tab.GetLength(0); ligne++) {
			for(int colonne = 0; colonne < tab.GetLength(1); colonne++) {
				tab[ligne, colonne] = ligne * 3 + colonne;
			}
		}
		
		AfficheArray2D(tab);

	}
}
```

</details>

## Exercice



## Exercice

Écrivez une fonction `ScalaireFoisMatrice(int scalaire, int[,] matrice)` qui renvoie un nouveau tableau aux mêmes dimensions que `matrice` et dont les éléments sont les éléments de `matrice` multipliés par `scalaire` (voir le cours de Math).

Exemple 1 :
```csharp
int[,] tab = new int[,]{
        {0,1,2},
        {2,3,3},
      };
Console.WriteLine("matrice = ");
AfficheArray2D(tab);
int[,] resultat = ScalaireFoisMatrice(3, tab);
Console.WriteLine("\n3 * matrice = ");
AfficheArray2D(resultat);
```
doit afficher :
```
matrice = 
0 1 2 
2 3 3 

3 * matrice = 
0 3 6 
6 9 9
```

```csharp
int[,] tab = new int[,]{
        {2,1,1,4,1},
        {1,3,0,1,4},
        {2,2,2,3,0},
      };
Console.WriteLine("matrice = ");
AfficheArray2D(tab);
int[,] resultat = ScalaireFoisMatrice(2, tab);
Console.WriteLine("\n2 * matrice = ");
AfficheArray2D(resultat);
```
doit afficher :
```
matrice = 
2 1 1 4 1 
1 3 0 1 4 
2 2 2 3 0 

2 * matrice = 
4 2 2 8 2 
2 6 0 2 8 
4 4 4 6 0
```

<details>
  <summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	
	public static void AfficheArray2D(int[,] array) {
		for(int ligne = 0; ligne < array.GetLength(0); ligne++) {
			for(int colonne = 0; colonne < array.GetLength(1); colonne++) {
				Console.Write("{0} ", array[ligne, colonne]);
			}
			Console.WriteLine();
		}
	}
	public static int[,] ScalaireFoisMatrice(int scalaire, int[,] matrice) {
		int[,] resultat = new int[matrice.GetLength(0), matrice.GetLength(1)];
		for(int ligne = 0; ligne < matrice.GetLength(0); ligne++) {
			for(int colonne = 0; colonne < matrice.GetLength(1); colonne++) {
				resultat[ligne, colonne] = scalaire * matrice[ligne, colonne];
			}
		}
		return resultat;
	}
	public static void Main()
	{
    int[,] tab = new int[,]{
            {2,1,1,4,1},
            {1,3,0,1,4},
            {2,2,2,3,0},
          };
    Console.WriteLine("matrice = ");
    AfficheArray2D(tab);
    int[,] resultat = ScalaireFoisMatrice(2, tab);
    Console.WriteLine("\n2 * matrice = ");
    AfficheArray2D(resultat);
	}
}
```

</details>

## Exercice

Écrivez une fonction `SommeMatrices(int[,] tab1, int[,] tab2)` qui renvoie un nouveau tableau aux mêmes dimensions que `matrice` et dont les éléments sont la somme des éléments deux à deux de `tab1` et `tab2` (voir la somme de matrices dans le cours de Math).

<details>
  <summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	
	public static void AfficheArray2D(int[,] array) {
		for(int ligne = 0; ligne < array.GetLength(0); ligne++) {
			for(int colonne = 0; colonne < array.GetLength(1); colonne++) {
				Console.Write("{0} ", array[ligne, colonne]);
			}
			Console.WriteLine();
		}
	}
	public static int[,] SommeMatrices(int[,] tab1, int[,] tab2) {
		if (tab1.GetLength(0) != tab2.GetLength(0) || tab1.GetLength(1) != tab2.GetLength(1)) {
			// on ne peut pas faire la somme si les dimensions ne sont pas identiques
			return null;
		}
		int[,] resultat = new int[tab1.GetLength(0), tab1.GetLength(1)];
		for(int ligne = 0; ligne < tab1.GetLength(0); ligne++) {
			for(int colonne = 0; colonne < tab1.GetLength(1); colonne++) {
				resultat[ligne, colonne] = tab1[ligne,colonne] + tab2[ligne, colonne];
			}
		}
		return resultat;
	}
	public static void Main()
	{
		int[,] resultat = SommeMatrices(new int[,] {{1,3,4},{2,3,3}}, new int[,] {{0,2,5},{0,1,1}});
		AfficheArray2D(resultat);
	}
}
```

</details>

## Exercice

Écrivez un programme qui :
1. demande à l'utilisateur deux entiers `n` et `m`
2. créé un tableau de `double` à 2 dimensions `n` x `m`
3. demande à l'utilisateur une position `(i,j)`
4. demande à l'utilisateur une valeur `v`
5. assigne la valeur `v` à la position `(i,j)` dans le tableau
6. affiche le tableau
7. recommence à l'étape 3 jusqu'à ce que `i` soit inférieur à 0

Attention à bien vérfier que les positions soient correctes par rapport aux dimensions.