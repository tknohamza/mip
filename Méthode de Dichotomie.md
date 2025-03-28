# Méthode de Dichotomie


### <a name="objectifs"></a> objectifs


> Calculez l'approximation de x par la méthode de dichotomie.


Premièrement, installer :


```shell
pip install numpy
```


> [!TIP]
> utiliser `command prompt` pour installer resources.


</p>
<h3 align="center">Dichotomie</h3>
<p align="center">
</p>

Vous devez vous assurer que f(a) × f(b) toujours < 0 :

```shell
def dichotomie(f, a, b, tol=1e-6, max_iter=100):
    """
    Trouve une racine de f(x) dans [a, b] en utilisant la méthode de dichotomie.
    
    Paramètres:
    f : fonction continue f(x)
    a, b : bornes de l'intervalle [a, b] (f(a) et f(b) doivent être de signes opposés)
    tol : tolérance d'arrêt
    max_iter : nombre maximal d'itérations
    
    Retourne:
    c : une approximation de la racine de f(x) ou None si aucune racine n'est trouvée
    """
    if f(a) * f(b) > 0:
        print("La méthode de dichotomie ne s'applique pas : f(a) et f(b) doivent être de signes opposés.")
        return None
    
    for _ in range(max_iter):
        c = (a + b) / 2  # Milieu de l'intervalle
        fc = f(c)
        
        if abs(fc) < tol or (b - a) / 2 < tol:
            return c  # Retourne l'approximation de la racine
        
        if f(a) * fc < 0:
            b = c  # La racine est dans [a, c]
        else:
            a = c  # La racine est dans [c, b]
    
    return (a + b) / 2  # Retourne la meilleure approximation trouvée

# Exemple d'utilisation
def f(x):
    return x**3 - x - 1  # Fonction continue

a, b = 1, 2  # Intervalle contenant une racine

racine = dichotomie(f, a, b)
if racine is not None:
    print(f"Une racine approximative est : {racine:.6f}")
else:
    print("Aucune racine trouvée.")

# by : tknohamza
```

> [!NOTE]
La fonction f, g, h,... en remplace xⁿ par :
```
x⁰ : x**0
x¹ : x**1
x² : x**2
.
.
xⁿ : x**n
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
