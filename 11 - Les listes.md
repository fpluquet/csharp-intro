# Les Listes

Les listes en C# offrent une alternative dynamique aux tableaux, permettant d'ajouter ou de supprimer des éléments de manière flexible. Voici comment déclarer, initialiser et utiliser des listes en C#.

## Déclaration et Initialisation

Vous pouvez déclarer et initialiser une liste comme suit :

```csharp
// Déclaration et initialisation d'une liste d'entiers
List<int> maListe = new List<int>();
```

## Ajouter et supprimer des Éléments

Vous pouvez ajouter des éléments à une liste à l'aide de la méthode `Add` et les supprimer avec `Remove` :

```csharp
List<string> listeChaines = new List<string>();

// Ajouter des éléments
listeChaines.Add("Bonjour");
listeChaines.Add("à");
listeChaines.Add("tous");

// Supprimer un élément
listeChaines.Remove("à");
```

La liste `listeChaines` contient maintenant les éléments "Bonjour" et "tous". 
Les éléments sont stockés dans l'ordre dans lequel ils ont été ajoutés et lors d'une suppression, les éléments suivants sont décalés automatiquement vers la gauche.

## Accéder aux Éléments

L'accès aux éléments d'une liste se fait via l'index, tout comme dans un tableau :

```csharp
Console.WriteLine(listeChaines[0]);  // Affiche "Bonjour"
Console.WriteLine(listeChaines[1]);  // Affiche "tous"
```

## Taille d'une Liste

La propriété `Count` indique le nombre d'éléments dans une liste :

```csharp
Console.WriteLine(listeChaines.Count);  // Affiche 2 après la suppression
```

## ```foreach``` avec les Listes

Vous pouvez utiliser une boucle `foreach` pour parcourir les éléments d'une liste :

```csharp
foreach (string element in listeChaines)
{
    Console.WriteLine(element);
}
```

La boucle `foreach` parcourt tous les éléments de la liste et les stocke dans la variable `element` à chaque itération.
Vous pouvez nommer la variable `element` comme vous le souhaitez, mais elle doit être du même type que les éléments de la liste.

## Types de données

Les listes peuvent contenir des éléments de n'importe quel type de données :

```csharp
List<int> listeEntiers = new List<int>();
List<string> listeChaines = new List<string>();
List<double> listeDoubles = new List<double>();
List<bool> listeBooleens = new List<bool>();
```

Nous pouvons même jouer avec des listes de listes :

```csharp
List<List<int>> listeListesEntiers = new List<List<int>>();
listListesEntiers.Add(new List<int>() { 1, 2, 3 });
listListesEntiers.Add(new List<int>() { 4, 5, 6, 7 });

Console.WriteLine(listeListesEntiers[0].Count);  // Affiche 3
Console.WriteLine(listeListesEntiers[1].Count);  // Affiche 4

Console.WriteLine(listeListesEntiers[0][0]);  // Affiche 1
Console.WriteLine(listeListesEntiers[1][3]);  // Affiche 7
```

Ou des listes de tableaux :

```csharp
List<int[]> listeTableauxEntiers = new List<int[]>();
listeTableauxEntiers.Add(new int[] { 1, 2, 3 });
listeTableauxEntiers.Add(new int[] { 4, 5, 6, 7 });

Console.WriteLine(listeTableauxEntiers[0].Length);  // Affiche 3
Console.WriteLine(listeTableauxEntiers[1].Length);  // Affiche 4

Console.WriteLine(listeTableauxEntiers[0][0]);  // Affiche 1
Console.WriteLine(listeTableauxEntiers[1][3]);  // Affiche 7
```


## Exercices

### Exercice 1

Créez une liste d'entiers appelée `nombres` et ajoutez les chiffres de 1 à 5. Ensuite, utilisez une boucle `foreach` pour afficher chaque nombre.

<details>
  <summary>Solution</summary>

```csharp
List<int> nombres = new List<int>();
for (int i = 1; i <= 5; i++)
{
    nombres.Add(i);
}

foreach (var nombre in nombres)
{
    Console.Write($"{nombre} ");
}
// Affiche "1 2 3 4 5"
```

</details>

### Exercice 2

Supprimez le nombre 3 de la liste créée dans l'exercice précédent, puis affichez la nouvelle liste.

<details>
  <summary>Solution</summary>

```csharp
List<int> nombres = new List<int>();
for (int i = 1; i <= 5; i++)
{
    nombres.Add(i);
}

foreach (var nombre in nombres)
{
    Console.Write($"{nombre} ");
}
nombres.Remove(3);

foreach (var nombre in nombres)
{
    Console.Write($"{nombre} ");
}
// Affiche "1 2 4 5"
```

</details>

### Exercice 3

Créez une liste de chaînes appelée `prenoms` et ajoutez trois prénoms. Affichez la taille de la liste.

<details>
  <summary>Solution</summary>

```csharp
List<string> prenoms = new List<string>() { "Alice", "Bob", "Charlie" };

Console.WriteLine(prenoms.Count);  // Affiche 3
```

</details>

### Exercice 4

Ajoutez deux prénoms supplémentaires à la liste `prenoms`, puis utilisez une boucle `foreach` pour afficher tous les prénoms.

<details>
  <summary>Solution</summary>

```csharp
List<string> prenoms = new List<string>() { "Alice", "Bob", "Charlie" };

prenoms.Add("David");
prenoms.Add("Eva");

foreach (var prenom in prenoms)
{
    Console.Write($"{prenom} ");
}
// Affiche "Alice Bob Charlie David Eva"
```

</details>

### Exercice 5

Supprimez le prénom "Bob" de la liste `prenoms` et affichez la nouvelle liste.

<details>
  <summary>Solution</summary>

```csharp
prenoms.Remove("Bob");

foreach (var prenom in prenoms)
{
    Console.Write($"{prenom} ");
}
// Affiche "Alice Charlie David Eva"
```

</details>

### Exercice 6 : Gestion d'un Site Web

Vous travaillez sur une fonctionnalité pour un site web de commerce électronique. Les produits sont stockés dans une liste représentant le panier d'achat d'un utilisateur. Chaque produit a un nom et un prix.

Implémentez une fonction en C# qui prend une liste de produits dans le panier d'achat et calcule le montant total de la commande. Les prix des produits sont fixés, et vous avez une liste correspondante qui associe chaque produit à son prix.

<details>
  <summary>Solution</summary>

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static decimal CalculerMontantTotal(List<string> panier, List<decimal> prixProduits)
    {
        decimal montantTotal = 0;

        for (int i = 0; i < panier.Count; i++)
        {
            // Assurez-vous que l'index est valide
            if (i < prixProduits.Count)
            {
                montantTotal += prixProduits[i];
            }
        }

        return montantTotal;
    }

    static void Main()
    {
        List<string> panierUtilisateur = new List<string> { "Livre", "Téléphone", "Casque" };

        List<decimal> prixProduits = new List<decimal>
        {
            12.99m,   // Prix du Livre
            299.99m,  // Prix du Téléphone
            49.99m    // Prix du Casque
        };

        decimal montantTotal = CalculerMontantTotal(panierUtilisateur, prixProduits);
        Console.WriteLine($"Le montant total de la commande est : {montantTotal:C}");
    }
}
```
</details>


### Exercice 7 : Filtrage des Tâches

Vous développez une application de gestion de tâches. Chaque tâche est représentée par une chaîne de caractères indiquant la description de la tâche et son état (terminée ou non).

Implémentez une fonction en C# qui prend une liste de tâches et renvoie une nouvelle liste ne contenant que les tâches non terminées.

<details>
  <summary>Solution</summary>

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static List<string> FiltrerTachesNonTerminees(List<string> listeTaches)
    {
        List<string> tachesNonTerminees = new List<string>();

        foreach (var tache in listeTaches)
        {
            if (!tache.EndsWith("(Terminée)"))
            {
                tachesNonTerminees.Add(tache);
            }
        }

        return tachesNonTerminees;
    }

    static void Main()
    {
        List<string> tachesUtilisateur = new List<string>
        {
            "Répondre aux e-mails",
            "Préparer le rapport mensuel (Terminée)",
            "Planifier la réunion"
        };

        List<string> tachesNonTerminees = FiltrerTachesNonTerminees(tachesUtilisateur);

        foreach (var tache in tachesNonTerminees)
        {
            Console.WriteLine(tache);
        }
    }
}
```
</details>



