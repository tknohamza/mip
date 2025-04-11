# Méthode de la Sécante


### <a name="objectifs"></a> objectifs


> Calculez l'approximation de x par la méthode de la sécante.


Premièrement, installer :


```shell
pip install numpy
```

> [!IMPORTANT]
> utiliser `command prompt` pour installer resources.


</p>
<h3 align="center">La sécante</h3>
<p align="center">
</p>

> [!TIP]
> Assurez-vous que `numpy` est installé.

Vous devez vous assurer que Xn et Xn+1 Donnée inclus dans [a,b]:

```shell
def secante(f, x0, x1, tol=1e-6, max_iter=100):
    """
    Trouve une racine de f(x) en utilisant la méthode de la sécante.
    
    Paramètres:
    f : fonction f(x)
    x0, x1 : deux estimations initiales de la racine
    tol : tolérance d'arrêt
    max_iter : nombre maximal d'itérations
    
    Retourne:
    x : une approximation de la racine ou None si la méthode échoue
    """
    for _ in range(max_iter):
        if abs(f(x1) - f(x0)) < tol:
            print("Dénominateur trop proche de zéro, échec de la méthode.")
            return None
        
        x2 = x1 - f(x1) * (x1 - x0) / (f(x1) - f(x0))
        
        if abs(x2 - x1) < tol:
            return x2  # Convergence atteinte
        
        x0, x1 = x1, x2  # Mise à jour des points
    
    print("La méthode de la sécante n'a pas convergé.")
    return None

# Exemple d'utilisation
def f(x):
    return x**3 - x - 1  # Fonction continue

x0, x1 = 1, 2  # Estimations initiales

racine = secante(f, x0, x1)
if racine is not None:
    print(f"Une racine approximative est : {racine:.6f}")
else:
    print("Aucune racine trouvée.")

# by : tknohamza
```

> [!NOTE]
> La fonction f, g, h,... en remplace xⁿ par :
```
x⁰ : x**0
x¹ : x**1
x² : x**2 ... xⁿ : x**n
```

> [!NOTE]
La fonction f, g, h,... en remplace xⁿ par :
```
A*x**n avec A : coefficient Xⁿ
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
