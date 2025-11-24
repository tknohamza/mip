# Exercice : (Facultatif)

### <a name="objectifs"></a> objectifs


> unknown


Premièrement,


> [!IMPORTANT]
> utiliser `vscode` ou `cmd` ou `compiler online` pour exécutez le code.


</p>
<h3 align="center">Solution :</h3>
<p align="center">
</p>

> [!TIP]
> Assurez-vous que `python 3.13` est installé.

Vous devez vous assurer que 5 voitures difficiles soient incluses dans ce programme. Dans ce cas, je prends 2 voitures :

```shell
class Car:

    def __init__(self, brand, fuel, model: str, price: float):
        self.brand, self.fuel, self.model, self.price = brand, fuel, model, price

def main():
    cars = []

    print(" SAISIE DES INFORMATIONS (2 Voitures): ")

    for i in range(2):
        print(f"\nVoiture {i + 1}:")
        brand = input("Entrez la marque : ")
        fuel = input("Entrez le type de carburant (Diesel/Essence) : ")
        model = input("Entrez le modèle (Mois et Année) : ")
    
        while True:
            try:
                price = float(input("Entrez le prix DH : "))
                break
            except ValueError:
                print("Erreur : entrer un nombre valide pour le prix.")
        
        cars.append(Car(brand, fuel, model, price))


    print("\n LISTE DES VOITURES :")

    print(f"{'Marque':<15} {'Type carburant':<20} {'Modèle':<20} {'Prix':<10}")
    print("-" * 65)
    
    for car in cars:
        print(f"{car.brand:<15} {car.fuel:<20} {car.model:<20} {int(car.price)}")


    print("\n RECHERCHE : ")
    while True:
        search_brand = input("Entrez la marque à rechercher : ")
        search_fuel = input("Entrez le type de carburant à rechercher : ")
        
        found = False
        for car in cars:
            if (car.brand.lower() == search_brand.lower() and 
                car.fuel.lower() == search_fuel.lower()):
                found = True
                break
        
        if found:
            print(">>> Voiture disponible!")
        else:
            print(">>> Voiture non disponible!")
        
        continuer = input("\nVoulez-vous chercher une autre voiture ? (Y/N) : ")
        if continuer.lower() != 'y':
            print("Fin :)")
            break

if __name__ == "__main__":
 main()

```

> [!NOTE]
> Si :
le nombre des voiture x > 2 , changer le paramètre `2` par `x` :
```
# exemple : localisation, Line [10~12]

    print(" SAISIE DES INFORMATIONS (x=5 Voitures): ")

    for i in range(x=5):
```

---

### EXPLICATION - AI :

J'ai divisé mon code ( que j'ai créé - Sans recourir à AI ) en parties `8 Parties` et j'ai demandé à l'intelligence artificielle `Gemini 3 PRO` de l'expliquer, puis j'ai supervisé son organisation et son amélioration. | 75min 😵‍💫

1. La Définition de la Classe:

```shell

class Car:

```
- `class` : C'est le mot-clé qui dit à Python "Je veux créer un nouveau type d'objet".

- `Car` : C'est le nom de la classe. Par convention, en Python, les noms de classes commencent toujours par une majuscule (PascalCase).

2. Le Constructeur :

```shell

def __init__(self, brand, fuel, model: str, price: float):

```
- `def` : Début d'une fonction (méthode).

- `__init__` : C'est une méthode "magique" spéciale. Elle s'exécute automatiquement dès que tu crées une nouvelle voiture (ex: `ma_voiture = Car(...)`).

- `self` : Cela représente l'objet lui-même (la voiture spécifique que tu es en train de créer). Cela permet au code de distinguer "cette voiture-ci" des autres voitures.

- Les paramètres (`brand`, `fuel`, etc.) : Ce sont les ingrédients nécessaires pour créer la voiture.

- `: str` / `: float` : C'est ce qu'on appelle des Type Hints (indices de type).

- `model: str` signifie "on s'attend à ce que le modèle soit du texte (string)".

- `price: float` signifie "on s'attend à ce que le prix soit un nombre à virgule".

3. L'Assignation des Variables :

```shell

self.brand, self.fuel, self.model, self.price = brand, fuel, model, price

```
- Ce que ça fait : Ça prend les valeurs que tu donnes (à droite du `=`) et ça les stocke à l'intérieur de l'objet (dans le `self`, à gauche).

- Maintenant, la voiture "connaît" sa propre marque, son carburant, etc.

4. La méthode `main` :

```shell

def main():
    cars = []

```
- `def main()`: : C'est une fonction définie à l'intérieur de la classe.

- Attention : Telle qu'elle est écrite (sans `self` et indentée dans la classe), c'est un peu inhabituel en Python. Souvent, `main()` est placée en dehors de la classe, tout en bas du fichier.

- `cars = []` : Cela crée une liste vide appelée `cars`. Le but probable est de stocker plusieurs objets Car dans cette liste plus tard (comme un garage).

5. La Boucle de Saisie (Input Loop) :

```shell

print(" SAISIE DES INFORMATIONS (2 Voitures): ")
for i in range(2):
    print(f"\nVoiture {i + 1}:")
    # ... input ...

```
- `for i in range(2):` : C'est une boucle qui va tourner exactement 2 fois.

- `f"\nVoiture {i + 1}:"` : C'est une f-string.

- Au premier tour, `i` vaut 0, donc ça affiche "Voiture 1".

- Au deuxième tour, `i` vaut 1, donc ça affiche "Voiture 2".

- Ensuite, le programme te demande la marque, le carburant et le modèle via `input()`

6. Prix :


```shell

while True:
    try:
        price = float(input("Entrez le prix : "))
        break
    except ValueError:
        print("Erreur : entrer un nombre valide pour le prix.")

```
Le problème : Si l'utilisateur tape "vingt mille" (texte) au lieu de ` (nombre)`, le programme planterait normalement.

La solution :

- `while True` : On boucle à l'infini tant que l'utilisateur se trompe.

- `try` : Le code "essaie" de convertir le texte en nombre (`float`). Si ça marche, il fait `break` (il sort de la boucle).

- `except ValueError` : Si l'utilisateur a écrit du texte, Python capture l'erreur ici et affiche un message gentil au lieu de crasher.

Une fois les infos valides, on crée la voiture et on l'ajoute à la liste : `cars.append(Car(brand, fuel, model, price))`

7. L'Affichage DU Tableau:

```shell

print(f"{'Marque':<15} {'Type carburant':<20} ...")
print("-" * 65)
for car in cars:
    print(f"{car.brand:<15} {car.fuel:<20} ...")

```
Ici, tu utilises une syntaxe de formatage avancée pour faire des colonnes alignées :

- `:<15` signifie : "Réserve un espace de 15 caractères et aligne le texte à gauche (le `<` pointe vers la gauche)".

- Si la marque est "BMW" (3 lettres), Python ajoutera 12 espaces vides après pour garder la colonne droite.

- `int(car.price)` : Tu convertis le prix en entier pour l'affichage (pour ne pas avoir .0 à la fin).

8. Recherche :

```shell

while True:
    # ... saisie recherche ...
    found = False
    for car in cars:
        if (car.brand.lower() == search_brand.lower() and
            car.fuel.lower() == search_fuel.lower()):
            found = True
            break

```
- La logique : Tu parcours ta liste `cars` une par une.

- `.lower()` : C'est crucial ! Cela transforme tout en minuscules.

- Ainsi, si l'utilisateur cherche "bmw" et que la voiture est enregistrée comme "BMW", l'ordinateur comprend que c'est pareil.

- `found` (Drapeau) : C'est une variable booléenne (Vrai/Faux). Au début, on suppose qu'on n'a rien trouvé (`False`). Si on trouve une correspondance, on la passe à `True` et on arrête de chercher (`break`).

9 . Le point d'entrée :

```shell

if __name__ == "__main__":
    main()

```
C'est la protection standard en Python. Elle dit : "Si ce fichier est lancé directement (pas importé par un autre fichier), alors exécute la fonction `main()`". C'est comme la clé de contact pour démarrer la voiture.

---

> [!WARNING]
> Il existe toujours une possibilité d'erreur, nous n'en assumons donc aucune responsabilité.

</p>
<h3 align="center">Copyright © 2025</h3>
<p align="center">
</p>

> Merci de nous avoir contactés ici. Si vous avez des commentaires, n'hésitez pas à nous contacter :
tknohamzacontact@gmail.com
N'oubliez pas de nous suivre sur :
<a href="https://facebook.com/tknohamza">Facebook</a>, <a href="https://instagram.com/r/tknohamza">Instagram</a>, <a href="https://twitter.com/tknohamza">Twitter</a>, <a href="https://t.me/tknohamzachannel">Telegram</a>
