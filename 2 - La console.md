# Console

Pour afficher un texte sur la console :
```
Console.Write("Bonjour !");
```

Pour afficher un texte sur la console et revenir à la ligne :
```
Console.WriteLine("Bonjour !");
```

Pour lire un texte depuis la console :
```
string ligne = Console.ReadLine();
```

## Exercice 1

Que fait exactement le programme suivant ? 

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		string entrée = Console.ReadLine();	
		Console.Write("Avant:");
		Console.WriteLine(entrée);
		Console.Write("Après");
	}
}
```

<details>
	<summary>Solution</summary>

> Si on a entré le texte "Salut" alors cela affichera :
> 
> ```
> Avant:Salut
> Après
> ```

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// Le programme va attendre qu'on entre un texte et qu'on revienne à la ligne. 
		// Le texte lu est alors assigné dans la variable nommée *entrée* qui est de type string (chaîne de caractères)
		string entrée = Console.ReadLine();
	
		// On affiche le texte Avant: sans revenir à la ligne
		Console.Write("Avant:");
	
		// On affiche le texte lu par le ReadLine() et on revient à la ligne.
		Console.WriteLine(entrée);

		// On affiche le texte Après
		Console.Write("Après");
	}
}
```
	
</details>

## Exercice 2

Ecrire un programme qui vous demande votre nom et écrit ```Bonjour x``` où ```x``` est le nom entré.

Exemple de sortie :
```
Quel est votre nom ?
Nico
Bonjour Nico
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// affichage de la question sur la console
		Console.WriteLine("Quel est votre nom ?");
		
		// lecture du nom de l'utilisateur 
		string nom = Console.ReadLine();

		// affichage du message sur la console
		Console.Write("Bonjour ");
		Console.WriteLine(nom);
	}
}
```
</details>
