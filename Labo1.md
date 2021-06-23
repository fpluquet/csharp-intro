# C# - Labo 1

## Buts du labo

## Exercices

1. Écrire un programme qui vous demande votre âge et affiche si vous êtes majeur ou mineur

<details>
  <summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
    // affichage de la question sur la console
		Console.WriteLine("Quel est votre âge ?");
    
    // lecture de l'entrée de l'utilisateur dans la variable line
		string line = Console.ReadLine();
    
    // transformation de la chaîne de caractères en entier
		int age = int.Parse(line);
    
    // si l'âge est plus grand ou égal à 18... 
		if (age >= 18) {
      // ... on affiche qu'il est majeur
			Console.WriteLine("Vous êtes majeur");
		} else {
      // ... sinon on affiche qu'il est mineur
			Console.WriteLine("Vous êtes mineur");
		}
	}
}
```
</details>

2. Ecrire un programme qui vous demande votre nom, votre sexe (M,F) et écrit :
   
   ```Bonjour monsieur x ou bonjour madame x```

3.       Ecrire un programme qui combile les deux premiers :

          Bonjour monsieur x

          Bonjour madame x

          Bonjour jeune homme x

          Bonjour Mademoiselle x         

4.       Ecrire un programme qui trie 3 nombres par ordre croissant.

5.       Ecrire un programme qui demande une année. Il doit vous dire si c'est une année bissextile ou pas.

6.       Vous allez faire vos courses et vous vous rendez compte que la caissière a des problèmes pour rendre la monnaie. Vous décidez de faire un programme pour l'aider. Pour cela, vous allez décomposer la somme d'argent qu'elle doit rendre en un nombre de pièces et/ou de billets le plus petit possible.

7.       Ecrire un programme qui demande à l'utilisateur de taper 5 entiers et qui affiche le plus grand. Le programme ne devra utiliser que 2 variables.
