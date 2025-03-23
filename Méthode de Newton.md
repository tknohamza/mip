# Méthode de Newton


### <a name="objectifs"></a> objectifs


> Calculez l'approximation de x par la méthode de newton.


Premièrement, installer :


```shell
import numpy as np
```


> [!TIP]
> utiliser `command prompt` pour installer resources.


</p>
<h3 align="center">Newton</h3>
<p align="center">
</p>

Vous devez vous assurer que Xn donnée inclus dans [a,b]:

```shell
import numpy as np

def newton_interpolation(x_values, y_values, x):
    """
    Interpolation de Newton pour approximer la valeur de f(x).
    
    Paramètres:
    x_values : liste des abscisses des points
    y_values : liste des ordonnées correspondantes
    x : valeur où l'on veut estimer f(x)
    
    Retourne:
    y : approximation de f(x) par le polynôme de Newton
    """
    n = len(x_values)
    divided_diff = np.zeros((n, n))
    
    # Remplissage de la première colonne avec les valeurs y
    divided_diff[:, 0] = y_values
    
    # Calcul des différences divisées
    for j in range(1, n):
        for i in range(n - j):
            divided_diff[i][j] = (divided_diff[i + 1][j - 1] - divided_diff[i][j - 1]) / (x_values[i + j] - x_values[i])
    
    # Calcul du polynôme de Newton
    y_approx = divided_diff[0, 0]
    product_term = 1.0
    for j in range(1, n):
        product_term *= (x - x_values[j - 1])
        y_approx += divided_diff[0, j] * product_term
    
    return y_approx

# Exemple d'utilisation
x_points = [1, 2, 3, 4]
y_points = [2, 3, 5, 7]
x_eval = 2.5

result = newton_interpolation(x_points, y_points, x_eval)
print(f"L'estimation de f({x_eval}) est : {result:.6f}")

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
