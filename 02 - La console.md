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

## Convertion

Il arrive souvent que l'on doive passer d'une chaîne de caractères à des entiers et inversément. Pour transformer un ```int``` en ```string```, il suffit d'appeler la méthode ```ToString()``` sur l'entier :

```csharp
int unNombre = 20;
string unNombreEnTexte = unNombre.ToString();
```

Pour passer d'un ```string``` à un ```int```, c'est un peu plus compliqué car la chaîne de caractères ne contient pas forcément un entier. Il faut donc gérer ce cas.

```csharp
int unNombre = int.Parse("150"); // unNombre a la valeur entière 150
int unAutreNombre = int.Parse("dfdsf"); // le programme s'arrête
```

On peut gérer le cas d'une erreur via la méthode ```TryParse``` qui va prendre en paramètres la chaîne de caractères et la variable dans laquelle il faut écrire la valeur. Elle renvoie ```True``` si tout s'est bien passé et ```False``` si le texte n'a pas pu être transformé en entier. 

Remarquez que le mot clé ```out``` est indispensable pour que la méthode ```TryParse``` puisse écrire dans la variable entière.

```csharp
int unNombre;
bool resultat = int.TryParse("150", out unNombre); // unNombre a la valeur entière 150 et resultat vaut True
resultat = int.TryParse("dfdsf", out unNombre); // unNombre a été mis à 0 et resultat vaut False
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
		Console.WriteLine("Bonjour {0}", nom);
	}
}
```
</details>

## Exercice 3

Ecrire un programme qui demande deux nombres et en affiche la somme et le produit.

Exemple de sortie :
<pre>
Premier nombre ? <b>12</b>
Deuxième nombre ? <b>13</b>
12 + 13 = 25
12 * 13 = 156
</pre>

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// affichage de la question sur la console
		Console.Write("Premier nombre ?");
		
		// lecture du premier nombre de l'utilisateur 
		int nb1 = int.Parse(Console.ReadLine());

		// affichage de la question sur la console
		Console.Write("Deuxième nombre ?");
		
		// lecture du deuxième nombre de l'utilisateur 
		int nb2 = int.Parse(Console.ReadLine());

		// affichage du message sur la console
		Console.WriteLine("{0} + {1} = {2}", nb1, nb2, nb1 + nb2);

		// affichage du message sur la console
		Console.WriteLine("{0} * {1} = {2}", nb1, nb2, nb1 * nb2);
	}
}
```
</details>

## Exercice 4

Quel est le problème avec le code suivant ?

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// affichage de la question sur la console
		Console.Write("Votre nombre ?");
		
		// lecture du premier nombre de l'utilisateur 
		string nb1 = int.Parse(Console.ReadLine());

		// affichage du message sur la console
		Console.WriteLine("{0} * 3 = {1}", nb1, nb1 * 3);
	}
}
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		Console.Write("Votre nombre ?");
		
		// /------- on essaie de mettre un entier dans un string
		// |        et le compilateur n'aime pas ça. 
		// |       Il faut changer le string en int :      
		// v       int nb1 = int.Parse(Console.ReadLine());      
		string nb1 = int.Parse(Console.ReadLine());

		Console.WriteLine("{0} * 3 = {1}", nb1, nb1 * 3);
	}
}
```
</details>
