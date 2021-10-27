# Les fonctions récursives

Une fonction récursive est une fonction qui s'appelle elle-même :

```csharp
int sommeN(int n) {
    if (n <= 0) {
        return 0;
    }
    int resultatPourNMoins1 = sommeN(n-1); // appel récursif
    return resultatPourNMoins1 + n;
}
```

Si on devait décrire en français cette fonction, on dirait que `sommeN(n)` vaut `0` pour tout `n <= 0` et qu'elle vaut `sommeN(n-1) + n` pour tout `n > 0`.  

On obtient donc les résultats suivants :

| n   | sommmeN(n) |
| --- | ---------- |
| -1  | 0          |
| 0   | 0          |
| 1   | 1          |
| 2   | 3          |
| 3   | 6          |
| 4   | 10         |
| 5   | 15         |
| ... | ...        |

Remarquez qu'on aurait pu écrire cette fonction sans appel récursif :

```csharp
int sommeN(int n) {
    int résultat = 0;
    for(int i = 1; i <= n;i++) {
        résultat += i;
    }
    return résultat;
}
```
Cette écriture est clairement plus facile à lire que son écriture récursive. Alors pourquoi s'embêter avec des appels récursifs ? Parce que parfois c'est plus simple...

Prenons un exemple concret : les tours de Hanoï.

Les tours de Hanoï est un petit jeu dans lequel on a 3 piques et des disques posés dessus. Ces disques ont tous une taille différentes. Au départ, les disques sont rangés sur une seule pique de manière croissante (le plus petit en haut et le grand en bas) :

![hanoi](images/Tower_of_Hanoi.jpeg)

Le jeu consiste à déplacer toute la tour d'une pique à une autre en respectant les règles suivantes :
- on ne déplace d'un seul disque à la fois
- on ne peut poser un disque `d1` sur un disque `d2` que si `d1` est plus petit que `d2`. En d'autres termes, les tours de disques doivent toujours être bien ordonnée de manière croissante.

Comment fait-on pour résoudre ce problème ?


Pour faire une bonne fonction récursive, il faut :
- penser aux cas d'arrêts de la récursion
- penser aux valeurs des paramètres lors de l'appel récursif

## Exercice

Créez une fonction récursive `factorielle` qui prend un entier et renvoie la factorielle de cet entier, c’est-à-dire, l’entier multiplié par tous les entiers inférieurs positifs.

Exemples :

```csharp
Console.WriteLine(factorielle(2)); // affiche 2 car 2 * 1 = 2
Console.WriteLine(factorielle(3)); // affiche 6 car 3 * 2 * 1 = 6
Console.WriteLine(factorielle(4)); // affiche 24 car 4 * 3 * 2 * 1 = 24
```

<details>
    <summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	static int factorielle(int n) {
		if (n <= 1) {
			return 1;
		}
		return n * factorielle(n-1);
	}
	public static void Main()
	{
		Console.WriteLine(factorielle(2)); // affiche 2 car 2 * 1 = 2
		Console.WriteLine(factorielle(3)); // affiche 6 car 3 * 2 * 1 = 6
		Console.WriteLine(factorielle(4)); // affiche 24 car 4 * 3 * 2 * 1 = 24
	}
}
```

</details>

## Exercice

Tour de Hanoï

## Division

Est divisible par 

def est_divisible_par(a, b):
    '''
    :param a, b: (int)
    :return: (bool)
      - True si a est divisible par b
      - False sinon.
    :CU: a >= 0 et b > 0
    '''
    if a < b:
        res = a == 0
    else:
        res = est_divisible_par(a - b, b)
    return res

## Exercice 

PGCD
```
(define (pgcd a b)
 (if (= b 0)
 (error ”b doit ˆetre non nul”)
 (let ((m (modulo a b)))
 (if (= m 0)
 b
 (pgcd b m)))))
```

## Exercice 
Trouver la sortie dans un labyrinthe.

## Exercice

Liste des mots d'une certaine longueur avec un alphabet donné.

<details>
	<summary>Solution</summary>

```csharp
public class Program
{
    public static List<string> mots(int longueur, string alphabet)
    {
        if (longueur == 1)
        {
            List<string> lettres = new List<string>();
            lettres.AddRange(alphabet.Select(c => c.ToString()));
            return lettres;
        }
        List<string> intermediaire = mots(longueur - 1, alphabet);
        List<string> res = new List<string>();
        foreach (char c in alphabet)
        {
            foreach (string mot in intermediaire)
            {
                res.Add(c + mot);
            }
        }
        return res;
    }

    public static void Main()
    {
        foreach (string mot in mots(3, "01"))
        {
            Console.WriteLine(mot);
        }
    }
}
```

</details>