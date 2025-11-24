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
                price = float(input("Entrez le prix : "))
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
# exemple : localisation, Line [10 ~ 12]

    print(" SAISIE DES INFORMATIONS ( x=5 Voitures): ")

    for i in range( x=5 ):
```

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
