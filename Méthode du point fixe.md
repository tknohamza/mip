# Méthode du point fix


### <a name="objectifs"></a> objectifs


> Calculez l'approximation de x par la méthode du point fix.


Premièrement, installer :


```shell
import numpy as np
```


> [!TIP]
> utiliser `command prompt` pour installer resources.


</p>
<h3 align="center">Point fix</h3>
<p align="center">
</p>

Vous devez vous assurer que Xn donnée et Xn+1 = g(Xn):

```shell
def point_fixe(g, x0, tol=1e-6, max_iter=100):
    """
    Trouve une solution de l'équation x = g(x) en utilisant la méthode du point fixe.
    
    Paramètres:
    g : fonction de récurrence g(x)
    x0 : point de départ
    tol : tolérance d'arrêt
    max_iter : nombre maximal d'itérations
    
    Retourne:
    x : une approximation de la solution ou None si la convergence échoue
    """
    x = x0
    for _ in range(max_iter):
        x_next = g(x)
        if abs(x_next - x) < tol:
            return x_next  # Convergence atteinte
        x = x_next
    
    print("La méthode du point fixe n'a pas convergé.")
    return None

# Exemple d'utilisation
def g(x):
    return (x**3 - 1) / 2  # Fonction g(x) définie pour x = g(x)

x0 = 1.5  # Point de départ
solution = point_fixe(g, x0)
if solution is not None:
    print(f"Une solution approximative est : {solution:.6f}")
else:
    print("Aucune solution trouvée.")

# by : tknohamza
```

> [!NOTE]
> Il existe toujours une possibilité d'erreur, nous n'en assumons donc aucune responsabilité.

## <a name="Copyright"></a> Copyright
tknohamza © 2025

> Merci de nous avoir contactés ici. Si vous avez des commentaires, n'hésitez pas à nous contacter :
tknohamzacontact@gmail.com
N'oubliez pas de nous suivre sur :
<a href="https://facebook.com/tknohamza">Facebook</a>, <a href="https://instagram.com/r/tknohamza">Instagram</a>, <a href="https://twitter.com/tknohamza">Twitter</a>, <a href="https://t.me/tknohamzachannel">Telegram</a>
