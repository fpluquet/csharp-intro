# Les fonctions récursives

Une fonction récursive est une fonction qui s'appelle elle-même. C'est une approche utile pour résoudre des problèmes qui peuvent être décomposés en sous-problèmes plus petits et similaires à l'original.

## Exemples simples

Prenons un exemple de calcul de la factorielle d'un nombre entier. La **factorielle** d'un nombre entier positif `n`, notée `n!`, est le produit des entiers de `n` à 1. Par exemple, `5! = 5 * 4 * 3 * 2 * 1 = 120`.

Voici une fonction récursive pour calculer une factorielle en C# :

```csharp
int Factorielle(int n) {
    if (n == 1) {  // Cas de base
        return 1;
    } else {        // Appel récursif
        return n * Factorielle(n - 1);
    }
}
```

### Explication :
- **Cas de base** : Si `n` vaut 1, la fonction retourne 1. C'est ce qui met fin à la récursion.
- **Appel récursif** : Sinon, la fonction s'appelle elle-même avec `n - 1` jusqu'à ce que le cas de base soit atteint.



#### Exemple d'appel :
```csharp
int résultat = Factorielle(5);
Console.WriteLine(résultat);  // Affichera 120
```

### Execution de la fonction `Factorielle(5)`

1. `Factorielle(5)` appelle `Factorielle(4) * 5`
2. `Factorielle(4)` appelle `Factorielle(3) * 4`
3. `Factorielle(3)` appelle `Factorielle(2) * 3`
4. `Factorielle(2)` appelle `Factorielle(1) * 2`
5. `Factorielle(1)` retourne 1
6. `Factorielle(2)` retourne `1 * 2 = 2`
7. `Factorielle(3)` retourne `2 * 3 = 6`
8. `Factorielle(4)` retourne `6 * 4 = 24`
9. `Factorielle(5)` retourne `24 * 5 = 120`


## La récursion infinie

Il est essentiel de toujours prévoir un **cas de base** dans une fonction récursive pour éviter une récursion infinie, qui entraînerait un plantage du programme.

Si nous oublions d'inclure un cas de base, le programme continue de s'appeler lui-même indéfiniment :

```csharp
int MauvaiseRecursion(int n) {
    return n * MauvaiseRecursion(n - 1);  // Pas de cas de base
}
```

Cela entraînera une erreur du type **StackOverflowException** à cause du dépassement de la pile mémoire.

## Autres exemples de récursion

### Exponentiation (Calcul de `a^b`)

Voici un exemple d'une fonction récursive pour calculer une puissance `a^b` :

```csharp
int Puissance(int a, int b) {
    if (b == 0) {  // Cas de base
        return 1;
    } else {
        return a * Puissance(a, b - 1);  // Appel récursif
    }
}
```


## Avantages et inconvénients

### Avantages :
- La récursion simplifie le code pour certains problèmes qui ont une structure récursive naturelle, comme les arbres ou les algorithmes de recherche.

### Inconvénients :
- Peut entraîner une utilisation importante de la mémoire si la profondeur de récursion est trop grande.
- Moins efficace que les boucles dans certains cas, car chaque appel de fonction ajoute une nouvelle couche à la pile.


## Exercices

### Exercice 1

Le **nombre de Fibonacci** est défini par la suite suivante :
- `F(0) = 0`
- `F(1) = 1`
- `F(n) = F(n-1) + F(n-2)` pour `n >= 2`

Implémentez une fonction récursive pour calculer le `n`-ième nombre de Fibonacci.

```csharp
Console.WriteLine(Fibonacci(4));  // Affichera 3, car le 4ème nombre de Fibonacci est 3 (0,1,1,2,3)
Console.WriteLine(Fibonacci(6));  // Affichera 8, car le 6ème nombre de Fibonacci est 8 (0,1,1,2,3,5,8)
Console.WriteLine(Fibonacci(10)); // Affichera 55, car le 10ème nombre de Fibonacci est 55 (0,1,1,2,3,5,8,13,21,34,55)
```


<details>
  <summary>Solution</summary>

```csharp
int Fibonacci(int n) {
    if (n == 0) {
        return 0;
    } else if (n == 1) {
        return 1;
    } else {
        return Fibonacci(n - 1) + Fibonacci(n - 2);  // Appels récursifs
    }
}
```
</details>


### Exercice 2

Ecrivez une fonction récursive `SommeTableau` qui prend 2 paramètres (un tableau et un entier) et calcule la somme des éléments du tableau. Le second paramètre est la taille du tableau et peut être utilisé pour déterminer le cas de base.

```csharp
int[] nombres = { 1, 2, 3, 4, 5 };
int somme = SommeTableau(nombres, nombres.Length);
Console.WriteLine(somme);  // Affichera 15
```

<details>
  <summary>Solution</summary>

```csharp
int SommeTableau(int[] tableau, int n) {
    if (n <= 0) {  // Cas de base
        return 0;
    } else {
        return tableau[n - 1] + SommeTableau(tableau, n - 1);
    }
}
```
</details>

### Exercice 3

Ecrivez une fonction récursive `InverserChaine` qui prend une chaîne de caractères en paramètre et renvoie la chaîne inversée.

```csharp
string chaine = "Hello";
string chaineInverse = InverserChaine(chaine);
Console.WriteLine(chaineInverse);  // Affichera "olleH"
```

<details>
  <summary>Solution</summary>

```csharp
string InverserChaine(string chaine) {
    if (chaine == "") {  // Cas de base
        return "";
    } else {
        return chaine[chaine.Length - 1] + InverserChaine(chaine.Substring(0, chaine.Length - 1));
    }
}
```
</details>

### Exercice 4

Ecrivez une fonction récursive `EstPalindrome` qui prend une chaîne de caractères en paramètre et renvoie `true` si la chaîne est un palindrome (se lit de la même manière dans les deux sens), `false` sinon.

```csharp
Console.WriteLine(EstPalindrome("radar"));  // Affichera true
Console.WriteLine(EstPalindrome("hello"));  // Affichera false
```

<details>
  <summary>Solution</summary>

```csharp
bool EstPalindrome(string chaine) {
    if (chaine.Length <= 1) {  // Cas de base
        return true;
    } else {
        return chaine[0] == chaine[chaine.Length - 1] && EstPalindrome(chaine.Substring(1, chaine.Length - 2));
    }
}
```

</details>

### Exercice 5

Ecrivez une fonction récursive `SommeChiffres` qui prend un entier en paramètre et renvoie la somme de ses chiffres.

```csharp
Console.WriteLine(SommeChiffres(123));  // Affichera 6 (1 + 2 + 3)
Console.WriteLine(SommeChiffres(456));  // Affichera 15 (4 + 5 + 6)
```

<details>
  <summary>Solution</summary>

```csharp
int SommeChiffres(int n) {
    if (n == 0) {  // Cas de base
        return 0;
    } else {
        return n % 10 + SommeChiffres(n / 10);
    }
}
```

</details>

### Exercice 6

Ecrivez une fonction récursive `EstPremier` qui prend un entier en paramètre et renvoie `true` si c'est un nombre premier, `false` sinon.

Pour rappel, un nombre premier est un entier supérieur à 1 qui n'a aucun diviseur autre que 1 et lui-même.

```csharp
Console.WriteLine(EstPremier(7));   // Affichera true
Console.WriteLine(EstPremier(10));  // Affichera false
```

<details>
  <summary>Solution</summary>

```csharp
bool EstPremier(int n, int diviseur = 2) {
    if (n <= 2) {  // Cas de base
        return n == 2;
    } else if (n % diviseur == 0) {
        return false;
    } else if (diviseur * diviseur > n) {
        return true;
    } else {
        return EstPremier(n, diviseur + 1);
    }
}
```

</details>

### Exercice 7

Ecrivez une fonction récursive `NombreChiffres` qui prend un entier en paramètre et renvoie le nombre de chiffres qu'il contient.

```csharp
Console.WriteLine(NombreChiffres(123));  // Affichera 3
Console.WriteLine(NombreChiffres(4567)); // Affichera 4
```

<details>
  <summary>Solution</summary>

```csharp
int NombreChiffres(int n) {
    if (n == 0) {  // Cas de base
        return 0;
    } else {
        return 1 + NombreChiffres(n / 10);
    }
}
```

</details>

