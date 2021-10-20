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

Les tours de Hanoï est un petit jeu dans lequel on a 3 piques et des disques posés dessus. Ces disques sont soit petits, soit moyens, soit grands. Au départ, 



## Exercice

Créez une fonction qui prend un entier et renvoie la factorielle de cet entier. C’est-à-dire, l’entier multiplié par tous les entiers inférieurs positifs.

Exemple:

factoriel(2) ➞ 2
// 2 * 1 = 2

factoriel(3) ➞ 6
// 3 * 2 * 1 = 6

factoriel(4) ➞ 24
// 4 * 3 * 2 * 1 = 24

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