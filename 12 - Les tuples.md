### Les Tuples

Les tuples sont une structure de données légère qui permet de stocker plusieurs éléments hétérogènes dans un seul conteneur. Chaque élément peut être de type différent, offrant ainsi une flexibilité dans la manipulation de données. En C#, vous pouvez créer des tuples en utilisant la classe `Tuple` ou à l'aide de la syntaxe de tuple introduite dans C# 7.0.

#### Création de Tuples

##### À l'aide de la Classe `Tuple`

```csharp
Tuple<int, string, double> monTupleParClasse = Tuple.Create(42, "Bonjour", 3.14);
```

##### À l'aide de la Syntaxe de Tuple

```csharp
(int, string, double) monTupleParSyntaxe = (42, "Bonjour", 3.14);
(int x, string str, double pi) monTupleNommé = (42, "Bonjour", 3.14);
```

#### Accès aux Éléments d'un Tuple

##### À l'aide de la Classe `Tuple`

```csharp
int premierElement = monTupleParClasse.Item1;
string deuxiemeElement = monTupleParClasse.Item2;
double troisiemeElement = monTupleParClasse.Item3;
```

##### À l'aide de la Syntaxe de Tuple

```csharp
int premierElement = monTupleParSyntaxe.Item1;
string deuxiemeElement = monTupleParSyntaxe.Item2;
double troisiemeElement = monTupleParSyntaxe.Item3;

// Ou, via le type nommé

int premierElement = monTupleNommé.x;
string deuxiemeElement = monTupleNommé.str;
double troisiemeElement = monTupleNommé.pi;
```

##### À l'aide de la Décomposition de Tuple

Qu'importe la méthode utilisée pour créer un tuple, vous pouvez utiliser la décomposition de tuple pour accéder à ses éléments :

```csharp
(int premierElement, string deuxiemeElement, double troisiemeElement) = monTuple;

Console.WriteLine(premierElement);  // Affiche 42
Console.WriteLine(deuxiemeElement);  // Affiche "Bonjour"
Console.WriteLine(troisiemeElement);  // Affiche 3.14
```


#### Modification d'un Tuple

Les tuples sont immuables, ce qui signifie que vous ne pouvez pas modifier leurs valeurs une fois qu'ils sont créés. Cependant, vous pouvez créer un nouveau tuple avec des valeurs mises à jour.

```csharp
(int, string, int) monTupleModifie = (premierElement, "Bonsoir", troisiemeElement);
```

### Exercices sur les Tuples

#### Exercice 1

Créez un tuple représentant les informations d'un étudiant : nom (string), âge (int) et moyenne (double).

<details>
  <summary>Solution</summary>

```csharp
(string, int, double) etudiant = ("Alice", 20, 16.5);
```

</details>

#### Exercice 2

Écrivez une fonction qui prend un tuple (nom, prénom, année de naissance) en paramètre et renvoie l'âge de la personne.

<details>
  <summary>Solution</summary>

```csharp
int CalculerAge((string Nom, string Prenom, int AnneeNaissance) personne)
{
    return DateTime.Now.Year - personne.AnneeNaissance;
}
```

</details>

#### Exercice 3

Créez une fonction qui prend un tuple représentant la mesure des côtés d'un triangle (a, b, c) et renvoie le type du triangle sous forme de string ("équilatéral", "isocèle" ou "scalène").

<details>
  <summary>Solution</summary>

```csharp
string TypeTriangle((int a, int b, int c) triangle)
{
    if (triangle.a == triangle.b && triangle.b == triangle.c)
    {
        return "Équilatéral";
    }
    else if (triangle.a == triangle.b || triangle.b == triangle.c || triangle.a == triangle.c)
    {
        return "Isocèle";
    }
    else
    {
        return "Scalène";
    }
}
```

</details>

#### Exercice 4

Créez un tuple représentant une date (jour, mois, année). Écrivez une fonction qui prend deux dates en paramètre et renvoie la différence en jours entre ces deux dates.

Pour cela, vous pouvez utiliser la classe `DateTime` et la différence entre deux dates (date1 - date2) qui vous renverra un objet `TimeSpan` sur lequel vous pouvez demander le nombre de jours via la propriété `Days`.

<details>
  <summary>Solution</summary>

```csharp
int DifferenceJours((int Jour, int Mois, int Annee) date1, (int Jour, int Mois, int Annee) date2)
{
    DateTime premiereDate = new DateTime(date1.Annee, date1.Mois, date1.Jour);
    DateTime deuxiemeDate = new DateTime(date2.Annee, date2.Mois, date2.Jour);

    TimeSpan difference = deuxiemeDate - premiereDate;
    return difference.Days;
}

// Exemple d'utilisation de cette fonction 

(int Jour, int Mois, int Annee) dateNaissance = (1, 1, 1990);
(int Jour, int Mois, int Annee) dateAujourdhui = (1, 1, 2024);

int nbJours = DifferenceJours(dateNaissance, dateAujourdhui);

Console.WriteLine(nbJours);  // Affiche 12418
Console.WriteLine(nbJours / 365);  // Affiche 34
```

</details>
