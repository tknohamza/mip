# TP2


Voici les grandes lignes des réponses attendues pour les exercices du TP2 – Analyse numérique avec NumPy :


---

Exercice 1 : Interpolation de Newton

1. Fonction differences_divisees(x, y) :

import numpy as np

def differences_divisees(x, y):
    n = len(y)
    coef = np.copy(y).astype(float)
    for j in range(1, n):
        coef[j:n] = (coef[j:n] - coef[j-1:n-1]) / (x[j:n] - x[0:n-j])
    return coef

2. Fonction evaluer_polynome_direct(x_points, coeffs, x) :

def evaluer_polynome_direct(x_points, coeffs, x):
    n = len(coeffs)
    result = coeffs[-1]
    for i in range(n-2, -1, -1):
        result = result * (x - x_points[i]) + coeffs[i]
    return result

3. Application aux points (0, 1), (1, 2), (2, 5) :

x_points = np.array([0, 1, 2])
y_points = np.array([1, 2, 5])
coeffs = differences_divisees(x_points, y_points)
print("Coefficients:", coeffs)

x_eval = 1.5
val = evaluer_polynome_direct(x_points, coeffs, x_eval)
print(f"P({x_eval}) = {val}")

Résultat attendu : Coefficients = [1, 1, 1], donc le polynôme est P(x) = 1 + x + x(x-1).


---

Exercice 2 : Intégration numérique

1. Méthode des trapèzes :

def integration_trapeze(f, a, b, n):
    h = (b - a) / n
    x = np.linspace(a, b, n+1)
    y = f(x)
    return h * (y[0] / 2 + np.sum(y[1:-1]) + y[-1] / 2)

2. Méthode de Simpson :

def integration_simpson(f, a, b, n):
    if n % 2 != 0:
        raise ValueError("n doit être pair pour Simpson")
    h = (b - a) / n
    x = np.linspace(a, b, n+1)
    y = f(x)
    return h / 3 * (y[0] + 4 * np.sum(y[1:-1:2]) + 2 * np.sum(y[2:-2:2]) + y[-1])

3. Application à f(x) = x² sur [0, 1], avec n = 4 :

f = lambda x: x**2
a, b, n = 0, 1, 4

print("Trapèzes:", integration_trapeze(f, a, b, n))
print("Simpson:", integration_simpson(f, a, b, n))

Résultat attendu :

Trapèzes ≈ 0.335

Simpson ≈ 0.333 (exact pour un polynôme de degré ≤ 2)



---

Si tu veux les sorties exactes ou une visualisation graphique, je peux les générer aussi. Tu veux que je le fasse ?