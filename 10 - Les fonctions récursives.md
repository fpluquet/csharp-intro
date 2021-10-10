# Les fonctions récursives

**intro**

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