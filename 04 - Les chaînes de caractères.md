# Les chaînes de caractères (string)

Un ```string``` en informatique est une chaîne de caractères, c'est-à-dire une suite ordonnée de caractères.

Exemples :
```csharp
"" // la chaîne vide
"Bonjour à tous !"
"Hello :D"
```

On peut assigner une chaîne de caractères dans une variable de type ```string``` :

```csharp
string texte = "Bonjour à tous";
string unAutreTexte = "Hello everybody !";
```

## Propriétés et méthodes

Il est possible d'obtenir la taille d'une chaîne de caractères via la propriété ```Length```.

```csharp
int taille1 = "Hello".Length; //  taille1 contient 5
string texte = "Bonjour";
int taille2 = texte.Length // taille2 contient 7
```

Il est possible d'obtenir le caractère à une index précis en suffissant la chaîne de caractères par des crochets et l'index désiré (en partant de 0) :

```csharp
"Hello"[0] // renvoie le caractère 'H'
string texte = "Bonjour";
Console.Write(texte[0]) // affiche 'B'
Console.Write(texte[6]) // affiche 'r'
```

Il existe également pas mal de méthodes utiles sur les chaînes de caractères. Pour les retrouver : https://docs.microsoft.com/en-us/dotnet/api/system.string.substring?view=net-5.0

Voici quelques unes des plus intéressantes :

| Nom de la méthode | Utilité | Exemple |
| - | - | - |
| CompareTo | Compare cette instance avec un objet String spécifié et indique si cette instance précède, suit ou apparaît à la même position dans l'ordre de tri que la chaîne spécifiée. | ```"Hello".CompareTo("Bonjour"); // renvoie -1``` |
| IndexOf | Signale l'index de base zéro de la première occurrence de la chaîne spécifiée dans cette instance. | ```"Hello".IndexOf("lo"); // renvoie 3```|
| Contains | Retourne une valeur qui indique si la sous-chaîne spécifiée apparaît dans cette chaîne. | ```"Hello".Contains("ll"); // renvoie True``` |
| StartsWith | Détermine si le début de cette instance de chaîne correspond à la chaîne spécifiée. | ```"Hello".StartsWith("Hel"); // renvoie True``` |
## Concaténation

On peut créer une nouvelle chaîne de caractères en *concaténant* plusieurs chaînes, c'est-à-dire en les collant les unes ou autres. Pour cela, il suffit de mettre un + entre ces chaînes :

```csharp
string uneChaineComplète = "Hello " + "tout " + "le monde"; // uneChaineComplète contient "Hello tout le monde"
```


## Exercice

Créer un programme qui demande une chaîne de caractères et si cette chaîne ne finit pas par un 's', en ajouter un et l'afficher.

Exemple de sortie:
```
Quel mot faut-il mettre au pluriel ? Chien
Le mot "Chien" au pluriel : Chiens
```
```
Quel mot faut-il mettre au pluriel ? Chiens
Le "Chiens" est déjà au pluriel. 
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// affichage de la question
		Console.Write("Quel mot faut-il mettre au pluriel ?");

		// lecture et assignation du mot de l'utilisateur
		string mot = Console.ReadLine();
		
		// si la dernière lettre est un 's'...
		if (mot[mot.Length - 1] == 's') {
			// ... alors on affiche que c'est déjà au pluriel
			Console.WriteLine("Le \"{0}\" est déjà au pluriel.", mot); 
		} else {
			// ... sinon on affiche le mot au pluriel
			Console.WriteLine("Le mot \"{0}\" au pluriel : {1}", mot, mot + "s");
		}
	}
}
```
</details>


## Exercice

Créer un programme qui demande une chaîne de caractères et si cette chaîne ne finit pas par un 's' ou un 'x', ajouter un 'x' si cela finit par 'ou' ou ajouter un 's' et l'afficher.

Exemple de sortie:
```
Quel mot faut-il mettre au pluriel ? Chien
Le mot "Chien" au pluriel : Chiens
```
```
Quel mot faut-il mettre au pluriel ? Chiens
Le "Chiens" est déjà au pluriel. 
```
```
Quel mot faut-il mettre au pluriel ? Hibou
Le mot "Hibou" au pluriel : Hiboux
```

<details>
	<summary>Solution</summary>

```csharp

```
</details>

## Exercice

Demander 2 chaînes de caractères et les afficher dans l'ordre du dictionnaire (défini par défaut dans la méthode CompareTo).

<details>
	<summary>Solution</summary>

```csharp

```
</details>

## Exercice

Demander une chaine de caractères et afficher le menu suivant :

1. Tester ce texte commence par...
2. Tester ce texte finit par...
3. Afficher sa longueur
4. Quitter

Lire le choix et afficher les informations en conséquence.

<details>
	<summary>Solution</summary>

```csharp

```
</details>
