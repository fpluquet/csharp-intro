# Boucles for

**intro**

- Utiliser des boucles (for, while, do/while, ...)

> Ajouter des exos de lecture
> Transformer les exos pour retirer les fonctions

## Exercice

Utilisez des boucles afin de construire un triangle rectangle formé par le caractère étoile (\*). 
Affichez-en ```nbLignes``` lignes, où ```nbLignes``` est entré au clavier par l'utilisateur. 

Exemple de sortie :
```
Combien de lignes voulez-vous afficher ? 8
*
**
***
****
*****
******
*******
********
```

<details>
	<summary>Solution</summary>

```csharp
using System;
					
public class Program
{
	public static void Main()
	{
		int nbLignes;
		
		Console.Write("Combien de lignes voulez-vous afficher ? ");
		nbLignes = int.Parse(Console.ReadLine());
		
		for(int i = 1; i <= nbLignes; i++) {
			for(int j = 1; j <= i; j++) {
				Console.Write("*");
			}
			Console.WriteLine();
		}
	}
}
```
</details>

## Exercice

Créez une fonction qui renvoie ```true``` si une chaîne contient des espaces. Sinon renvoie ```false```. Pour y arriver, lisez chaque caractère de la chaîne de caractère via une boucle ```for```.  


Exemple:

containSpaces("Thomas") ➞ False

containSpaces("Hello World!") ➞ True

containSpaces(" ") ➞ True

containSpaces("") ➞ False

<details>
	<summary>Solution</summary>

```csharp

```
</details>

## Exercice

Créez une fonction qui compte le nombre de syllabes d’un mot. Chaque syllabe est séparée par un tiret -.

Exemple:

nbrOfSlab("prin-temps") ➞ 2

nbrOfSlab("ar-rê-te") ➞ 3

nbrOfSlab("ther-mo-mè-tre") ➞ 4

<details>
	<summary>Solution</summary>

```csharp

```
</details>