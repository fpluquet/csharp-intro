# Puissance 4

On vous demande de développer le jeu de Puissance 4 en console. Veuillez respecter la sortie demandée. Les R représentent les rouges et les J les jaunes. Les rouges commencent.

Vérifiez que l'entrée de l'utilisateur est correcte (que ce soit bien un nombre et qu'il soit compris entre 1 et 7). Si elle ne l'est pas, redemandez une nouvelle valeur.

Découpez votre code en fonctions pour éviter d'avoir des fonctions trop grandes (> 30 lignes)

Voici une sortie attendue :

```
*****************************
******** PUISSANCE 4 ********
*****************************
| 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
Quelle colonne voulez-vous jouer ? 4
| 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   | R |   |   |   |
Quelle colonne voulez-vous jouer ? 3
| 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   | J | R |   |   |   |
Quelle colonne voulez-vous jouer ? 5
| 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   | J | R | R |   |   |
Quelle colonne voulez-vous jouer ? 6
| 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   | J | R | R | J |   |
Quelle colonne voulez-vous jouer ? 4
| 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   | R |   |   |   |
|   |   | J | R | R | J |   |
Quelle colonne voulez-vous jouer ? 4
| 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   | J |   |   |   |
|   |   |   | R |   |   |   |
|   |   | J | R | R | J |   |
Quelle colonne voulez-vous jouer ? 5
| 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   | J |   |   |   |
|   |   |   | R | R |   |   |
|   |   | J | R | R | J |   |
Quelle colonne voulez-vous jouer ? 3
| 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   | J |   |   |   |
|   |   | J | R | R |   |   |
|   |   | J | R | R | J |   |
Quelle colonne voulez-vous jouer ? 5
| 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   | J | R |   |   |
|   |   | J | R | R |   |   |
|   |   | J | R | R | J |   |
Quelle colonne voulez-vous jouer ? 5
| 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   | J |   |   |
|   |   |   | J | R |   |   |
|   |   | J | R | R |   |   |
|   |   | J | R | R | J |   |
Quelle colonne voulez-vous jouer ? 6
| 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   | J |   |   |
|   |   |   | J | R |   |   |
|   |   | J | R | R | R |   |
|   |   | J | R | R | J |   |
Quelle colonne voulez-vous jouer ? 2
| 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   | J |   |   |
|   |   |   | J | R |   |   |
|   |   | J | R | R | R |   |
|   | J | J | R | R | J |   |
Les jaunes ont gagné !

```

<details>
  <summary>Solution</summary>

```csharp
using System;

namespace Puissance4
{
    class Program
    {
        static void Main(string[] args)
        {
            int[,] plateau = new int[6, 7];
            int joueurCourant = 1;

            Console.WriteLine("*****************************");
            Console.WriteLine("******** PUISSANCE 4 ********");
            Console.WriteLine("*****************************");

            while (!estFini(plateau))
            {
                affichePlateau(plateau);
                int colonne = demandeColonne();
                ajouteDansColonne(plateau, joueurCourant, colonne);
                if (joueurCourant == 1)
                {
                    joueurCourant = 2;
                }
                else
                {
                    joueurCourant = 1;
                }
            }
            affichePlateau(plateau);
            if (getGagnant(plateau) == 1)
            {
                Console.WriteLine("Les rouges ont gagné !");
            }
            else
            {
                Console.WriteLine("Les jaunes ont gagné !");
            }
        }

        static bool estFini(int[,] plateau)
        {
            return getGagnant(plateau) != 0;
        }

        static int getGagnant(int[,] plateau)
        {
            int gagnant = chercheGagnantDansLignes(plateau);
            if (gagnant == 0)
            {
                gagnant = chercheGagnantDansColonnes(plateau);
            }
            if (gagnant == 0)
            {
                gagnant = chercheGagnantDansDiagonale(plateau);
            }
            if (gagnant == 0)
            {
                gagnant = chercheGagnantDansDiagonaleOpposée(plateau);
            }
            return gagnant;
        }

        private static int chercheGagnantDansLignes(int[,] plateau)
        {
            int gagnant = 0;
            for (int ligne = 0; ligne < plateau.GetLength(0); ligne++)
            {
                for (int colonne = 0; colonne < 4; colonne++)
                {
                    int joueur = plateau[ligne, colonne];
                    if (joueur != 0)
                    {
                        bool a4Alignes = true;
                        for (int delta = 1; delta < 4; delta++)
                        {
                            if (joueur != plateau[ligne, colonne + delta])
                            {
                                a4Alignes = false;
                            }
                        }
                        if (a4Alignes)
                        {
                            gagnant = joueur;
                        }
                    }
                }
            }

            return gagnant;
        }

        private static int chercheGagnantDansColonnes(int[,] plateau)
        {
            int gagnant = 0;
            for (int colonne = 0; colonne < plateau.GetLength(1); colonne++)
            {
                for (int ligne = 0; ligne < 3; ligne++)
                {
                    int joueur = plateau[ligne, colonne];
                    if (joueur != 0)
                    {
                        bool a4Alignes = true;
                        for (int delta = 1; delta < 4; delta++)
                        {
                            if (joueur != plateau[ligne + delta, colonne])
                            {
                                a4Alignes = false;
                            }
                        }
                        if (a4Alignes)
                        {
                            gagnant = joueur;
                        }
                    }
                }
            }

            return gagnant;
        }

        private static int chercheGagnantDansDiagonale(int[,] plateau)
        {
            int gagnant = 0;
            for (int colonne = 0; colonne < 4; colonne++)
            {
                for (int ligne = 0; ligne < 3; ligne++)
                {
                    int joueur = plateau[ligne, colonne];
                    if (joueur != 0)
                    {
                        bool a4Alignes = true;
                        for (int delta = 1; delta < 4; delta++)
                        {
                            if (joueur != plateau[ligne + delta, colonne + delta])
                            {
                                a4Alignes = false;
                            }
                        }
                        if (a4Alignes)
                        {
                            gagnant = joueur;
                        }
                    }
                }
            }

            return gagnant;
        }

        private static int chercheGagnantDansDiagonaleOpposée(int[,] plateau)
        {
            int gagnant = 0;
            for (int colonne = 3; colonne < 7; colonne++)
            {
                for (int ligne = 0; ligne < 3; ligne++)
                {
                    int joueur = plateau[ligne, colonne];
                    if (joueur != 0)
                    {
                        bool a4Alignes = true;
                        for (int delta = 1; delta < 4; delta++)
                        {
                            if (joueur != plateau[ligne + delta, colonne - delta])
                            {
                                a4Alignes = false;
                            }
                        }
                        if (a4Alignes)
                        {
                            gagnant = joueur;
                        }
                    }
                }
            }

            return gagnant;
        }

        static void ajouteDansColonne(int[,] plateau, int joueurCourant, int colonne)
        {
            for (int ligne = 5; ligne >= 0; ligne--)
            {
                if (plateau[ligne, colonne] == 0)
                {
                    plateau[ligne, colonne] = joueurCourant;
                    return;
                }
            }
        }

        static int demandeColonne()
        {
            int colonne;
            bool estOk = false;
            do
            {
                Console.Write("Quelle colonne voulez-vous jouer ? ");
                estOk = int.TryParse(Console.ReadLine(), out colonne);
                if (estOk)
                {
                    estOk = colonne >= 1 && colonne <= 7;
                }
            } while (!estOk);
            return colonne - 1;
        }

        static void affichePlateau(int[,] plateau)
        {
            Console.Write("|");
            for (int j = 0; j < plateau.GetLength(1); j++)
            {
                Console.Write($" {j + 1} |");
            }
            Console.WriteLine();
            Console.Write("|");
            for (int j = 0; j < plateau.GetLength(1); j++)
            {
                Console.Write("---|");
            }
            Console.WriteLine();
            for (int i = 0; i < plateau.GetLength(0); i++)
            {
                Console.Write("|");
                for (int j = 0; j < plateau.GetLength(1); j++)
                {
                    if (plateau[i, j] == 0)
                    {
                        Console.Write("   ");
                    }
                    else if (plateau[i, j] == 1)
                    {
                        Console.Write(" R ");
                    }
                    else
                    {
                        Console.Write(" J ");
                    }
                    Console.Write("|");
                }
                Console.WriteLine();
            }

        }
    }
}
```

</details>