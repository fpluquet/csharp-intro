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

Comme nous travaillons avec des entiers, tous les éléments du tableau sont initialisés à 0.

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

> Attention ! Il faut que le nombre de colonnes soit identique pour chaque ligne renseignée. Si ce n'est pas le cas, le compilateur n'acceptera pas votre code.


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

string[,] mots = new string[8,12];
Console.WriteLine(mots.GetLength(0)); // Affiche 8
Console.WriteLine(mots.GetLength(1)); // Affiche 12
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

## foreach

Il est encore possible d'utiliser un boucle `foreach` avec un tableau à plusieurs dimensions. Cette boucle va alors parcourir le tableau élément par élément de la première à la dernière ligne et pour chaque ligne, de la première à la dernière colonne :

```csharp
int[,] tab = new int[,] {
      {5,4,0},
      {0,0,7}
    };
foreach(int element in tab) {
  Console.WriteLine(element);
}
```

Ce code va produire la sortie suivante :

```
5
4
0
0
0
7
```

C'est donc utile lorsqu'on doit parcourir tous les éléments sans avoir besoin du numéro de ligne ni le numéro de colonne de chaque élément.

## Le nombre de dimensions

Vous pouvez utiliser la propriété `Rank` d'un tableau pour connaître le nombre de dimensions de ce tableau.


```csharp
int[] array1 = new int[10];
int[,] array2 = new int[10,3];
int[,,] array3 = new int[5,8,7];

Console.WriteLine("{0}: {1} dimension(s)",
                  array1.ToString(), array1.Rank);
Console.WriteLine("{0}: {1} dimension(s)",
                  array2.ToString(), array2.Rank);
Console.WriteLine("{0}: {1} dimension(s)",
                  array3.ToString(), array3.Rank);
```

Ce code va produire la sortie suivante :

```
System.Int32[]: 1 dimension(s)
System.Int32[,]: 2 dimension(s)
System.Int32[,,]: 3 dimension(s)
```

Si on ne connaît pas la dimension d'un tableau avant de le créer, nous pouvons utiliser comme type générique `Array` :

```csharp
Array array1 = new int[10];

Console.WriteLine("{0}: {1} dimension(s)",
                  array1.ToString(), array1.Rank);

array1 = new int[10,3];

Console.WriteLine("{0}: {1} dimension(s)",
                  array1.ToString(), array1.Rank);
                  
array1 = new int[5,8,7];

Console.WriteLine("{0}: {1} dimension(s)",
                  array1.ToString(), array1.Rank);
```

Ce code va produire la même sortie :

```
System.Int32[]: 1 dimension(s)
System.Int32[,]: 2 dimension(s)
System.Int32[,,]: 3 dimension(s)
```

Mais l'avantage ici est que le type de chaque variable ne nous force pas à y accueilir des tableaux de dimensions prédéfinies.

# Exercices

## Exercice 1

Que va afficher le programme suivant ?

```csharp
using System;
          
public class Program
{
  
  public static void Main()
  {
    int[,] tab = new int[,] {
      {5,8,9,4},
      {0,0,1,1},
      {1,5,5,3}
    };
    
    int s = 0;
    for(int ligne = 0; ligne < tab.GetLength(0); ligne++) {
      for(int colonne = 0; colonne < tab.GetLength(1); colonne++) {
        s += tab[ligne, colonne];
      }
    }
    Console.WriteLine(s);
  }
}
```

<details>
  <summary>Solution</summary>

Ce programme affiche la somme de tous les éléments du tableau, c'est-à-dire :

```
42
```

Voici l'explication ligne par ligne : 

```csharp
using System;
          
public class Program
{
  
  public static void Main()
  {
    // on crée un tableau à deux dimensions de 3 x 4
    int[,] tab = new int[,] {
      {5,8,9,4},
      {0,0,1,1},
      {1,5,5,3}
    };
    
    // on crée une variable s, qui est un entier initialisé à 0
    int s = 0;

    // ligne va varier de 0 à 2 (tab.GetLength(0) renvoyant 3)
    for(int ligne = 0; ligne < tab.GetLength(0); ligne++) {
      // colonne va varier de 0 à 3 (tab.GetLength(1) renvoyant 4)
      for(int colonne = 0; colonne < tab.GetLength(1); colonne++) {
        // on prend l'élément du tableau à la position (ligne, colonne) et on l'ajoute à s
        s += tab[ligne, colonne];
      }
    }
    // on affiche le contenu de s
    Console.WriteLine(s);
  }
}

```

</details>

## Exercice 2

Réécrivez le programme précédent avec une seule boucle `foreach`.

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  
  public static void Main()
  {
    int[,] tab = new int[,] {
      {5,8,9,4},
      {0,0,1,1},
      {1,5,5,3}
    };
    
    int s = 0;
    // la boucle foreach va donner chaque élément du tableau
    foreach(int item in tab) {
      s += item;
    }
    Console.WriteLine(s);
  }
}
```

</details>

## Exercice 3

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
    // création d'une tableau tab à 2 dimensions et initialisé avec un tableau 3x3
    int[,] tab = new int[3,3];
    
    // on affiche "Avant :" et un retour à la ligne (\n) 
    Console.WriteLine("Avant :\n");

    // on appelle la fonction AfficheArray2D en lui passant tab comme argument
    AfficheArray2D(tab);

    // on affiche "Après :" et des retours à la ligne (\n) 
    Console.WriteLine("\nAprès:\n");

    // ligne va varier de 0 à 2 (tab.GetLength(0) renvoyant 3)
    for(int ligne = 0; ligne < tab.GetLength(0); ligne++) {
      // colonne va varier de 0 à 2 (tab.GetLength(1) renvoyant 3)
      for(int colonne = 0; colonne < tab.GetLength(1); colonne++) {
        // on met ligne * 3 + colonne à la position (ligne, colonne) 
        tab[ligne, colonne] = ligne * 3 + colonne;
      }
    }
    
    // on appelle la fonction AfficheArray2D en lui passant tab comme argument
    AfficheArray2D(tab);

  }
}
```

</details>

## Exercice 4

Que fait le programme suivant ?

```csharp
using System;
          
public class Program
{
  
  public static void AfficheArray(Array array) {
    int nbDimensions = array.Rank;
    int index = 0;
    foreach(int element in array) {
      Console.WriteLine("[{0}] = {1}", index, element);
      index++;
    }
  }
  public static void Main()
  {
    AfficheArray(new int[,] {
      {5,7,8},
      {1,2,1}
    });
    Console.WriteLine();
    AfficheArray(new int[] {10,3,2});
  }
}
```

<details>
  <summary>Solution</summary>
Ce programme affiche la sortie suivante :

```
[0] = 5
[1] = 7
[2] = 8
[3] = 1
[4] = 2
[5] = 1

[0] = 10
[1] = 3
[2] = 2
```

Voici l'explication :

```csharp
using System;
          
public class Program
{
  // déclaration de la méthode AfficheArray qui prend un tableau array en paramètre
  public static void AfficheArray(Array array) {
    // on récupère le nombre de dimensions du tableau
    int nbDimensions = array.Rank;
    // on crée une variable entière index, initialisée à 0
    int index = 0;

    // pour chaque élément de tableau array qu'on met dans element...
    foreach(int element in array) {
      // ... on affiche l'index courant et la valeur de element
      Console.WriteLine("[{0}] = {1}", index, element);
      // on incrémente index
      index++;
    }
  }
  public static void Main()
  {
    // on appelle la méthode AfficheArray en lui passant un tableau 2x3
    AfficheArray(new int[,] {
      {5,7,8},
      {1,2,1}
    });
    Console.WriteLine();
    // on appelle la méthode AfficheArray en lui passant un tableau 1x3
    AfficheArray(new int[] {10,3,2});
  }
}
```

</details>

## Exercice 5

Écrivez un programme qui crée un tableau de 5x10 entiers et y place aléatoirement 10 cases à la valeur 7. Faites attention de ne pas choisir 2 fois la même case pour qu'il y ait bien 10 élements du tableau à 7. Affichez ce tableau.

Exemples de sortie :

```
7 0 0 0 7 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 7 0 7 0 0 0 0 0 
0 7 0 0 7 0 0 7 0 7 
0 0 0 0 0 0 0 0 7 7
```

```
7 0 0 0 0 0 0 0 0 0 
0 0 0 0 7 0 7 0 0 7 
0 0 0 0 7 0 0 0 7 0 
0 7 0 0 0 7 0 7 0 0 
0 0 0 0 0 7 0 0 0 0
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  // même fonction que les exercices précédents
  public static void AfficheArray2D(int[,] array) {
    for(int ligne = 0; ligne < array.GetLength(0); ligne++) {
      for(int colonne = 0; colonne < array.GetLength(1); colonne++) {
        Console.Write("{0} ", array[ligne, colonne]);
      }
      Console.WriteLine();
    }
  }

  public void Main() {

    // création d'un tableau nommé tab de 5x10 entiers
    int[,] tab = new int[5,10];

    // on crée un objet random qui nous permettra d'obtenir des nombres aléatoires 
    Random random = new Random();

    // on va placer 10 éléments => i va de 0 à 9
    for(int i = 0; i < 10; i++) {
      // on déclare x et y comme des entiers, ils contiendront la position
      int x, y;
      do {
        // on choisit un x et un y aléatoirement en fonction de la taille du tableau tab 
        x = random.Next(tab.GetLength(0));
        y = random.Next(tab.GetLength(1));
      }while(tab[x,y] != 0); // on recommence la boucle jusqu`à ce qu'on ait la position d'une case vide (== 0)
      
      // on assigne 7 à cette position
      tab[x,y] = 7;
    }

    // on affiche le tableau tab via la méthode AfficheArray 
    AfficheArray2D(tab);
  }
}
```

</details>



## Exercice 6

Écrivez un programme qui :
1. demande à l'utilisateur deux entiers `n` et `m`
2. créé un tableau de `double` à 2 dimensions `n` x `m`
3. demande à l'utilisateur une position `i,j`
4. demande à l'utilisateur une valeur `v`
5. assigne la valeur `v` à la position `(i,j)` dans le tableau
6. affiche le tableau
7. recommence à l'étape 3 jusqu'à ce que `i` soit inférieur à 0

Attention à bien vérfier que les dimensions soient possibles (> 0) et que les positions soient correctes par rapport aux dimensions. Si ce n'est pas le cas, redemandez d'entrez quelque chose.

Exemple de sortie :

<pre>
Entrez le nombre de lignes : <b>5</b>
Entrez le nombre de colonnes : <b>six</b>
Entrez le nombre de colonnes : <b>6</b>
Entrez une position i,j : <b>3,2</b>
Entrez une valeur : <b>5</b>
0 0 0 0 0 0 
0 0 0 0 0 0 
0 0 0 0 0 0 
0 0 5 0 0 0 
0 0 0 0 0 0 
Entrez une position i,j : <b>5,0</b>
Entrez une position i,j : <b>8,9</b>
Entrez une position i,j : <b>0,0</b>
Entrez une valeur : <b>8</b>
8 0 0 0 0 0 
0 0 0 0 0 0 
0 0 0 0 0 0 
0 0 5 0 0 0 
0 0 0 0 0 0 
Entrez une position i,j : <b>3,3</b>
Entrez une valeur : <b>2</b>
8 0 0 0 0 0 
0 0 0 0 0 0 
0 0 0 0 0 0 
0 0 5 2 0 0 
0 0 0 0 0 0 
Entrez une position i,j : <b>3,3</b>
Entrez une valeur : <b>9</b>
8 0 0 0 0 0 
0 0 0 0 0 0 
0 0 0 0 0 0 
0 0 5 9 0 0 
0 0 0 0 0 0 
Entrez une position i,j : <b>-1,0</b>
</pre>

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  // même fonction que les exercices précédents
  public static void AfficheArray2D(int[,] array) {
    for(int ligne = 0; ligne < array.GetLength(0); ligne++) {
      for(int colonne = 0; colonne < array.GetLength(1); colonne++) {
        Console.Write("{0} ", array[ligne, colonne]);
      }
      Console.WriteLine();
    }
  }

  public void Main() {
    // les deux dimensions n et m
    int n, m;
  
    // correct contiendra le retour de TryParse (true si le string contient bien un nombre)
    bool correct;
  
    // Demande du nombre de lignes
    do {
      Console.Write("Entrez le nombre de lignes : ");
      correct = int.TryParse(Console.ReadLine(), out n);
    }while(correct == false || n <= 0);
                                      
    // Demande du nombre de colonnes
    do {
      Console.Write("Entrez le nombre de colonnes : ");
      correct = int.TryParse(Console.ReadLine(), out m);
    }while(correct == false || m <= 0);
  
    // Déclarations de i, j et v
    int i = 0, j = 0, v;
  
    // déclaration de tab et initialisation avec un tableau n x m
    int[,] tab = new int[n,m];
  
    // boucle principale
    do {
      // boucle de demande de la position
      do {
        Console.Write("Entrez une position i,j : ");
        string position = Console.ReadLine();

        // on sépare l'entrée en deux avec la virgule : i,j
        string[] p = position.Split(',');
  
        // le tableau p contient 2 strings
        correct = int.TryParse(p[0], out i);
  
        // correct contient correct *et* le parse de j
        // --> si correct est faux avant d'arriver ici, il restera faux
        correct = correct && int.TryParse(p[1], out j);
      // on continue tant que les valeurs ne sont pas correctes
      }while(correct == false || j < 0 || i >= n || j >= m);
  
      // si i est négatif...
      if (i < 0) {
        break; // ...arrête la boucle en cours (le do/while)
      }
                
      // on demande une valeur
      do {
        Console.Write("Entrez une valeur :");
        correct = int.TryParse(Console.ReadLine(), out v);
      }while(correct == false);
      
      // on assigne la valeur à la bonne position
      tab[i,j] = v;

      // on affiche le tableau tab
      AfficheArray2D(tab);
    
    // tant que i est supérieur à 0, on boucle
    }while(i >= 0);
  }
}
```

</details>

## Exercice 7

Écrivez un programme qui fait les étapes suivantes.

1. Il crée un tableau 10x10. 
2. Il place aléatoirement 30 cases à la valeur 1.
3. Il demande alors une position à l'utilisateur.
4. Si la case vaut 0, il y met un 2 et l'utilisateur gagne un point. Le tableau est affiché (uniquement les 2) et recommence au point 3. 
5. Si la case vaut 1, l'utilisateur a perdu, le programme affiche le nombre de points obtenus et se termine.

Conseils :
- Créez une méthode `static void RemplirDe1(int[,] tab)` pour l'étape 2.
- Utilisez et adaptez la méthode `AfficheArray2D` pour l'étape 3.

<pre>
  0 1 2 3 4 5 6 7 8 9 
0                     
1                     
2                     
3                     
4                     
5                     
6                     
7                     
8                     
9                     
Quelle ligne voulez-vous jouer ? : <b>0</b>
Quelle colonne voulez-vous jouer ? : <b>0</b>
Bonne case ! Votre score : 1 point
  0 1 2 3 4 5 6 7 8 9 
0 X                   
1                     
2                     
3                     
4                     
5                     
6                     
7                     
8                     
9                     
Quelle ligne voulez-vous jouer ? : <b>3</b>
Quelle colonne voulez-vous jouer ? : <b>3</b>
Bonne case ! Votre score : 2 points
  0 1 2 3 4 5 6 7 8 9 
0 X                   
1                     
2                     
3       X             
4                     
5                     
6                     
7                     
8                     
9                     
Quelle ligne voulez-vous jouer ? : <b>7</b>
Quelle colonne voulez-vous jouer ? : <b>0</b>
Mauvaise case ! Votre score final : 2 points
</pre>

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  public static void AfficherArray2D(int[,] array) {
    Console.Write("  ");
    for(int colonne = 0; colonne < array.GetLength(1); colonne++) {
      Console.Write("{0} ", colonne);
    }
    Console.WriteLine();
    for(int ligne = 0; ligne < array.GetLength(0); ligne++) {
      Console.Write("{0} ", ligne);
      for(int colonne = 0; colonne < array.GetLength(1); colonne++) {
        if (array[ligne, colonne] == 2) {
          Console.Write("X ");
        } else {
          Console.Write("  ");
        }	
      }
      Console.WriteLine();
    }
  }
  public static void RemplirDe1(int[,] tab) {
    Random random = new Random();
    for(int i = 0; i < 10; i++) {
      int x, y;
      do {
        x = random.Next(tab.GetLength(0));
        y = random.Next(tab.GetLength(1));
      }while(tab[x,y] == 1);
      tab[x,y] = 1;
    }
  }		
  public static void Main()
  {
    int[,] tab = new int[10,10];
    RemplirDe1(tab);
    AfficherArray2D(tab);
    int score = 0;
    int x, y;
    do {
      Console.Write("Quelle ligne voulez-vous jouer ? : ");
      x = int.Parse(Console.ReadLine());
      Console.Write("Quelle colonne voulez-vous jouer ? : ");
      y = int.Parse(Console.ReadLine());
      if (tab[x,y] == 0) {
        score ++;
        tab[x,y] = 2;
        Console.WriteLine("Bonne case ! Votre score : {0} point{1}", score, score > 1 ? "s" : "");
        AfficherArray2D(tab);
      }
    } while (tab[x,y] != 1);
    Console.WriteLine("Mauvaise case ! Votre score final : {0} point{1}", score, score > 1 ? "s" : "");		
  }
}
```
</details>

## Exercice 8

Écrire une fonction `memeTaille` qui retourne `true` si les deux tableaux passés en paramètre ont le même nombre de dimensions et les mêmes dimensions. Sinon elle renvoie `false`.

Exemples d'utilisation :

```csharp
Console.WriteLine(memeTaille(new int[3,3], new int[3,3])); // affiche True
Console.WriteLine(memeTaille(new int[2,3], new int[3,3])); // affiche False
Console.WriteLine(memeTaille(new int[3], new int[3,3])); // affiche False
Console.WriteLine(memeTaille(new int[3], new int[3])); // affiche True
Console.WriteLine(memeTaille(new int[3,5,5], new int[3,5,5])); // affiche True
Console.WriteLine(memeTaille(new int[3,5,8], new int[3,5,5])); // affiche False
Console.WriteLine(memeTaille(new int[3,5,8], new int[3])); // affiche False
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  public static bool memeTaille(Array tab1, Array tab2) {
    if (tab1.Rank != tab2.Rank) {
      return false;
    }
    for(int i = 0; i < tab1.Rank; i++) {
      if (tab1.GetLength(i) != tab2.GetLength(i)) {
        return false;
      }
    }
    return true;
  }

  public void Main() {
    Console.WriteLine(memeTaille(new int[3,3], new int[3,3])); // affiche True
    Console.WriteLine(memeTaille(new int[2,3], new int[3,3])); // affiche False
    Console.WriteLine(memeTaille(new int[3], new int[3,3])); // affiche False
    Console.WriteLine(memeTaille(new int[3], new int[3])); // affiche True
    Console.WriteLine(memeTaille(new int[3,5,5], new int[3,5,5])); // affiche True
    Console.WriteLine(memeTaille(new int[3,5,8], new int[3,5,5])); // affiche False
    Console.WriteLine(memeTaille(new int[3,5,8], new int[3])); // affiche False
  }
}
```

</details>


## Exercice 9

Écrivez une fonction `ScalaireFoisMatrice(int scalaire, int[,] matrice)` qui renvoie un nouveau tableau aux mêmes dimensions que `matrice` et dont les éléments sont les éléments de `matrice` multipliés par `scalaire` (voir le cours de Math).

Exemples :
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

## Exercice 10

Écrivez une fonction `SommeMatrices(int[,] tab1, int[,] tab2)` qui renvoie un nouveau tableau aux mêmes dimensions que `matrice` et dont les éléments sont la somme des éléments deux à deux de `tab1` et `tab2` (voir la somme de matrices dans le cours de Math).

Exemples :

```csharp
int[,] resultat = SommeMatrices(new int[,] {{1,3,4},{2,3,3}}, new int[,] {{0,2,5},{0,1,1}});
AfficheArray2D(resultat);
```
doit afficher :
```
1 5 9 
2 4 4
```

```csharp
int[,] resultat = SommeMatrices(new int[,] {{1},{2}}, new int[,] {{3},{4}});
AfficheArray2D(resultat);
```
doit afficher :
```
4
6
```

```csharp
int[,] resultat = SommeMatrices(new int[,] {{1}}, new int[,] {{3},{4}});
if (resultat != null) {
  AfficheArray2D(resultat);
} else {
  Console.WriteLine("Les deux matrices ne sont pas de la même taille");
}
```
doit afficher :
```
Les deux matrices ne sont pas de la même taille
```

<details>
  <summary>Solution</summary>

```csharp
using System;
          
public class Program
{
  // même fonction que les exercices précédents
  public static void AfficheArray2D(int[,] array) {
    for(int ligne = 0; ligne < array.GetLength(0); ligne++) {
      for(int colonne = 0; colonne < array.GetLength(1); colonne++) {
        Console.Write("{0} ", array[ligne, colonne]);
      }
      Console.WriteLine();
    }
  }

  // prend en paramètre 2 matrices, les additionne et retourne la matrice résultat
  public static int[,] SommeMatrices(int[,] tab1, int[,] tab2) {
    if (tab1.GetLength(0) != tab2.GetLength(0) || tab1.GetLength(1) != tab2.GetLength(1)) {
      // on ne peut pas faire la somme si les dimensions ne sont pas identiques
      return null;
    }
    // on crée un tableau nommé résultat qui aura les même dimension que le tab1 (on aurait pu prendre le tab2)
    int[,] resultat = new int[tab1.GetLength(0), tab1.GetLength(1)];

    // ligne va varier de 0 au nombre de lignes de tab1 (-1)
    for(int ligne = 0; ligne < tab1.GetLength(0); ligne++) {
      // colonne va varier de 0 au nombre de colonnes de tab1 (-1)
      for(int colonne = 0; colonne < tab1.GetLength(1); colonne++) {
        // on additionne les deux coeffiants aux positions (ligne, colonne) et on place la somme dans résultat 
        resultat[ligne, colonne] = tab1[ligne,colonne] + tab2[ligne, colonne];
      }
    }
    // on retourne le tableau résultat
    return resultat;
  }

  public static void Main()
  {
    int[,] resultat = SommeMatrices(new int[,] {{1,3,4},{2,3,3}}, new int[,] {{0,2,5},{0,1,1}});
    AfficheArray2D(resultat);
    resultat = SommeMatrices(new int[,] {{1},{2}}, new int[,] {{3},{4}});
    AfficheArray2D(resultat);
    resultat = SommeMatrices(new int[,] {{1}}, new int[,] {{3},{4}});
    if (resultat != null) {
      AfficheArray2D(resultat);
    } else {
      Console.WriteLine("Les deux matrices ne sont pas de la même taille");
    }
  }
}
```

</details>
