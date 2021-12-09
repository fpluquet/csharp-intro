# MasterMind

On vous demande de développer le jeu du MasterMind en console. Veuillez respecter la sortie demandée. Le code ne contient que 4 couleurs (pour plus vite débogger) et les couleurs sont remplacées par des nombres entre 0 et 7.

Vérifiez que l'entrée de l'utilisateur est correcte (que ce soit bien 4 nombres et qu'ils soient tous compris entre 0 et 7). Si elle ne l'est pas, redemandez une nouvelle valeur.

Découpez votre code en fonctions pour éviter d'avoir des fonctions trop grandes (> 30 lignes).

Voici une sortie attendue :

```
********** MasterMind **********

Entrez un code à 4 nombres (entre 0 et 7) : 0000
Nb bien placés : 1
Nb mal placés : 0
Entrez un code à 4 nombres (entre 0 et 7) : 0111
Nb bien placés : 2
Nb mal placés : 0
Entrez un code à 4 nombres (entre 0 et 7) : 0122
Nb bien placés : 1
Nb mal placés : 1
Entrez un code à 4 nombres (entre 0 et 7) : 0313
Nb bien placés : 1
Nb mal placés : 1
Entrez un code à 4 nombres (entre 0 et 7) : 0441
Nb bien placés : 3
Nb mal placés : 0
Entrez un code à 4 nombres (entre 0 et 7) : 0451
Nb bien placés : 3
Nb mal placés : 0
Entrez un code à 4 nombres (entre 0 et 7) :
Merci d'entrer 4 nombres collés entre 0 et 7
Entrez un code à 4 nombres (entre 0 et 7) : 044
Merci d'entrer 4 nombres collés entre 0 et 7
Entrez un code à 4 nombres (entre 0 et 7) : coucou
Merci d'entrer 4 nombres collés entre 0 et 7
Entrez un code à 4 nombres (entre 0 et 7) : 55566
Merci d'entrer 4 nombres collés entre 0 et 7
Entrez un code à 4 nombres (entre 0 et 7) : 8111
Merci d'entrer 4 nombres collés entre 0 et 7
Entrez un code à 4 nombres (entre 0 et 7) : 0461
Nb bien placés : 4
Nb mal placés : 0
Bravo, vous avez trouvé le code !
```

<details>
  <summary>Solution</summary>

```csharp
using System;

namespace MasterMindConsole
{
    class Program
    {
        static void Main(string[] args)
        {
            AfficherTitre();
            int[] code = new int[4];
            GénérerLeCode(code);
            bool estFini = false;
            while (!estFini)
            {
                int[] codeProposé = new int[4];
                DemanderCode(codeProposé);

                int nbBienPlacés, nbMalPlacés;
                ChercherNbBienEtMalPlacés(code, codeProposé, out nbBienPlacés, out nbMalPlacés);

                Console.WriteLine("Nb bien placés : {0}", nbBienPlacés);
                Console.WriteLine("Nb mal placés : {0}", nbMalPlacés);
                estFini = nbBienPlacés == 4;
            }
            Console.WriteLine("Bravo, vous avez trouvé le code !");
        }

        private static void ChercherNbBienEtMalPlacés(int[] code, int[] codeProposé, out int nbBienPlacés, out int nbMalPlacés)
        {
            int[] copieDuCode = (int[])code.Clone();
            int[] copieDuCodeJoué = (int[])codeProposé.Clone();

            nbBienPlacés = 0;
            nbMalPlacés = 0;
            for (int i = 0; i < 4; i++)
            {
                if (code[i] == codeProposé[i])
                {
                    nbBienPlacés++;
                    copieDuCode[i] = -1;
                    copieDuCodeJoué[i] = -2;
                }
            }

            for (int i = 0; i < 4; i++)
            {
                for (int j = 0; j < 4; j++)
                    if (copieDuCode[j] == copieDuCodeJoué[i])
                    {
                        nbMalPlacés++;
                        copieDuCode[j] = -1;
                        copieDuCodeJoué[i] = -2;
                    }
            }
        }

        private static void DemanderCode(int[] codeProposé)
        {
            bool aUneErreur;
            do
            {
                aUneErreur = false;
                Console.Write("Entrez un code à 4 nombres (entre 0 et 7) : ");
                string colors = Console.ReadLine();
                if (colors.Length != 4)
                {
                    aUneErreur = true;
                }
                for (int i = 0; i < 4 && !aUneErreur; i++)
                {
                    if (!Char.IsDigit(colors[i]))
                    {
                        aUneErreur = true;
                    }
                    else
                    {
                        int colorInt = int.Parse(colors[i].ToString());
                        if (colorInt < 0 || colorInt > 7)
                        {
                            aUneErreur = true;
                        }
                        else
                        {
                            codeProposé[i] = colorInt;
                        }
                    }
                }
                if (aUneErreur)
                {
                    Console.WriteLine("Merci d'entrer {0} nombres collés entre 0 et {1}", 4, 7);
                }
            } while (aUneErreur);
        }

        private static void GénérerLeCode(int[] solution)
        {
            Random r = new Random();
            for (int i = 0; i < solution.Length; i++)
            {
                solution[i] = r.Next(8);
            }
        }

        private static void AfficherTitre()
        {
            Console.WriteLine("********** MasterMind **********\n");
        }
    }
}
```
</details>
