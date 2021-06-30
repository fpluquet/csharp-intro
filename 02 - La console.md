# Console

La console est le terminal textuel utilisé pour interagir avec l'utilisateur. On l'utilisera pour les programmes en mode "console" et pour le débogage rapide.

Pour lire un texte depuis la console :
```csharp
string ligne = Console.ReadLine(); // la variable ligne contiendra le texte lu sur la console
```

Pour afficher un texte sur la console :
```csharp
Console.Write("Bonjour !");
```

Pour afficher un texte sur la console et revenir à la ligne :
```csharp
Console.WriteLine("Bonjour !");
```

Pour afficher un texte avec des trous à compléter par des paramètres :
```csharp
Console.WriteLine("Les paramètres sont : {0}, {1}, {2}", 5, 12, 24); // affichera "Les paramètres sont : 5, 12, 24"
Console.WriteLine("Les paramètres sont : {1}, {2}, {0}", 5, 12, 24); // affichera "Les paramètres sont : 12, 24, 5"
Console.WriteLine("Les paramètres sont : {1}, {2}, {0}", "coucou", 12, "hello"); // affichera "Les paramètres sont : 12, hello, coucou"
```


## Exercice 1

Que fait exactement le programme suivant si on entre le texte "Salut" ? 

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
