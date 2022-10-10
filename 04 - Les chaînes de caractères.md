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

Il est possible d'obtenir le caractère à un index précis en suffixant la chaîne de caractères par des crochets et l'index désiré (en partant de 0) :

```csharp
"Hello"[0] // renvoie le caractère 'H'
string texte = "Bonjour";
Console.Write(texte[0]) // affiche 'B'
Console.Write(texte[6]) // affiche 'r'
```

Il existe également d'autres méthodes utiles sur les chaînes de caractères. Pour les retrouver : https://docs.microsoft.com/en-us/dotnet/api/system.string?view=net-5.0

Voici quelques unes des plus intéressantes :

| Nom de la méthode | Utilité | Exemple |
| - | - | - |
| CompareTo | Compare cette instance avec un objet ```String``` spécifié et indique si cette instance précède (```>0```), suit(```<0```) ou apparaît à la même position (```0```) dans l'ordre de tri que la chaîne spécifiée. | ```"Hello".CompareTo("Bonjour"); // renvoie 1``` <br> ```"Hello".CompareTo("Hello"); // renvoie 0``` <br> ```"Bonjour".CompareTo("Hello"); // renvoie -1``` |
| IndexOf | Signale l'index de base zéro de la première occurrence de la chaîne spécifiée dans cette instance. | ```"Hello".IndexOf("lo"); // renvoie 3```|
| Contains | Retourne une valeur qui indique si la sous-chaîne spécifiée apparaît dans cette chaîne. | ```"Hello".Contains("ll"); // renvoie True``` |
| StartsWith | Détermine si le début de cette instance de chaîne correspond à la chaîne spécifiée. | ```"Hello".StartsWith("Hel"); // renvoie True``` |
| EndsWith | Détermine si la fin de cette instance de chaîne correspond à la chaîne spécifiée. | ```"Hello".EndsWith("llo"); // renvoie True``` |
| ToLower| Retourne une copie de cette chaîne convertie en minuscules. | ```"HelLo".ToLower(); // renvoie "hello"``` |
| ToUpper| Retourne une copie de cette chaîne convertie en majuscules. | ```"HelLo".ToUpper(); // renvoie "HELLO"``` |

## Concaténation

On peut créer une nouvelle chaîne de caractères en *concaténant* plusieurs chaînes, c'est-à-dire en les collant les unes ou autres. Pour cela, il suffit de mettre un + entre ces chaînes :

```csharp
string uneChaineComplète = "Hello " + "tout " + "le monde"; // uneChaineComplète contient "Hello tout le monde"
```


## Exercice 1

Créer un programme qui demande une chaîne de caractères et si cette chaîne ne finit pas par un 's', en ajouter un et l'afficher.

Exemple de sortie:
<pre>
Quel mot faut-il mettre au pluriel ? <b>Chien</b>
Le mot "Chien" au pluriel : Chiens
</pre>
<pre>
Quel mot faut-il mettre au pluriel ? <b>Chiens</b>
Le mot "Chiens" est déjà au pluriel. 
</pre>

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
			Console.WriteLine("Le mot \"{0}\" est déjà au pluriel.", mot); 
		} else {
			// ... sinon on affiche le mot au pluriel
			Console.WriteLine("Le mot \"{0}\" au pluriel : {1}", mot, mot + "s");
		}
	}
}
```

Une autre possibilité est d'utiliser la méthode ```EndsWith``` au lieu de ```mot[mot.Length - 1]``` :

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
		if (mot.EndsWith("s")) {
			// ... alors on affiche que c'est déjà au pluriel
			Console.WriteLine("Le mot \"{0}\" est déjà au pluriel.", mot); 
		} else {
			// ... sinon on affiche le mot au pluriel
			Console.WriteLine("Le mot \"{0}\" au pluriel : {1}", mot, mot + "s");
		}
	}
}
```
</details>



## Exercice 2

Demander 2 chaînes de caractères et les afficher dans l'ordre du dictionnaire (défini par défaut dans la méthode CompareTo).

Exemple de sortie :

<pre>
Quel est le premier mot ? <b>Bonbon</b>
Quel est le deuxième mot ? <b>Arbre</b>
Arbre vient avant Bonbon
</pre>
<pre>
Quel est le premier mot ? <b>Arbre</b>
Quel est le deuxième mot ? <b>Bonbon</b>
Arbre vient avant Bonbon
</pre>

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// affichage de la question
		Console.Write("Quel est le premier mot ?");

		// lecture et assignation du premier mot de l'utilisateur
		string mot1 = Console.ReadLine();

		// affichage de la question
		Console.Write("Quel est le deuxième mot ?");

		// lecture et assignation du deuxième mot de l'utilisateur
		string mot2 = Console.ReadLine();
		
		// on compare les deux mots... 
		if (mot1.CompareTo(mot2) < 0) {
			// ... et si le résultat est < 0, alors mot1 est avant mot2
			Console.WriteLine(mot1 + " vient avant " + mot2);
		} else {
			// ... sinon c'est l'inverse
			Console.WriteLine(mot2 + " vient avant " + mot1);
		}		
	}
}
```
</details>

## Exercice 3

Demander une chaine de caractères et afficher le menu suivant :

```
1. Afficher en majuscules
2. Afficher en miniscules
3. Afficher sa longueur
4. Quitter
```

Lire le choix et afficher les informations en conséquence.

Exemples de sorties :

<pre>
Quel est le mot ? <b>Hello</b>
1. Afficher en majuscules
2. Afficher en miniscules
3. Afficher sa longueur
4. Quitter
Votre choix : <b>1</b>
Hello en majuscules : HELLO
</pre>

<pre>
Quel est le mot ? <b>Hello</b>
1. Afficher en majuscules
2. Afficher en miniscules
3. Afficher sa longueur
4. Quitter
Votre choix : <b>2</b>
Hello en minuscules : hello
</pre>

<pre>
Quel est le mot ? <b>Hello</b>
1. Afficher en majuscules
2. Afficher en miniscules
3. Afficher sa longueur
4. Quitter
Votre choix : <b>3</b>
Hello a une longueur de 5
</pre>

<pre>
Quel est le mot ? <b>Hello</b>
1. Afficher en majuscules
2. Afficher en miniscules
3. Afficher sa longueur
4. Quitter
Votre choix : <b>4</b>
</pre>

<pre>
Quel est le mot ? <b>Hello</b>
1. Afficher en majuscules
2. Afficher en miniscules
3. Afficher sa longueur
4. Quitter
Votre choix : <b>unChoix</b>
Votre choix est invalide
</pre>


<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		// affichage de la question
		Console.Write("Quel est le mot ? ");

		// lecture et assignation du mot de l'utilisateur
		string mot = Console.ReadLine();

		// afficahe du menu
		Console.WriteLine("1. Afficher en majuscules");
		Console.WriteLine("2. Afficher en miniscules");
		Console.WriteLine("3. Afficher sa longueur");
		Console.WriteLine("4. Quitter");
		Console.Write("Votre choix : ");
		
		// on lit le choix de l'utilisateur
		int choix;
		int.TryParse(Console.ReadLine(), out choix);
		
		if (choix == 1) {
			Console.WriteLine("{0} en majuscules : {1}", mot, mot.ToUpper());			
		} else if (choix == 2) {
			Console.WriteLine("{0} en minuscules : {1}", mot, mot.ToLower());			
		} else if (choix == 3) {
			Console.WriteLine("{0} a une longueur de {1}", mot, mot.Length);
		} else if (choix == 4) {
			// ne rien faire
		} else {
			Console.WriteLine("Votre choix est invalide");
		}
	}
}
```
</details>
