# TP2 – Analyse numérique :


---

Exercice 1 : Interpolation de Newton

```shell
import numpy as np

# Function to compute divided differences
def differences_divisees(x, y):
    n = len(y)
    coef = np.copy(y).astype(float)
    for j in range(1, n):
        coef[j:n] = (coef[j:n] - coef[j-1:n-1]) / (x[j:n] - x[0:n-j])
    return coef

# Function to evaluate the Newton polynomial
def evaluer_polynome_direct(x_points, coeffs, x):
    n = len(coeffs)
    result = coeffs[-1]
    for i in range(n-2, -1, -1):
        result = result * (x - x_points[i]) + coeffs[i]
    return result

# Example: Applying the functions
x_points = np.array([0, 1, 2])
y_points = np.array([1, 2, 5])
coeffs = differences_divisees(x_points, y_points)
print("Coefficients:", coeffs)

x_eval = 1.5
val = evaluer_polynome_direct(x_points, coeffs, x_eval)
print(f"P({x_eval}) = {val}")
```


---

Exercice 2 : Intégration numérique

```shell
import numpy as np

# Méthode des trapèzes
def integration_trapeze(f, a, b, n):
    h = (b - a) / n  # Calcul du pas
    x = np.linspace(a, b, n+1)  # Discrétisation de l'intervalle
    y = f(x)  # Évaluation de la fonction sur les points
    return h * (y[0] / 2 + np.sum(y[1:-1]) + y[-1] / 2)

# Méthode de Simpson
def integration_simpson(f, a, b, n):
    if n % 2 != 0:
        raise ValueError("n doit être pair pour Simpson")  # Vérification de la parité de n
    h = (b - a) / n
    x = np.linspace(a, b, n+1)
    y = f(x)
    return h / 3 * (y[0] + 4 * np.sum(y[1:-1:2]) + 2 * np.sum(y[2:-2:2]) + y[-1])

# Définition de la fonction à intégrer
f = lambda x: x**2
a, b, n = 0, 1, 4  # Bornes et nombre de subdivisions

# Affichage des résultats
print("Trapèzes:", integration_trapeze(f, a, b, n))
print("Simpson:", integration_simpson(f, a, b, n))
```

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
