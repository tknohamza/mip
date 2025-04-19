# TP2


Voici les grandes lignes des réponses attendues pour les exercices du TP2 – Analyse numérique avec NumPy :


---

Exercice 1 : Interpolation de Newton

import numpy as np

def differences_divisees(x, y):
  """
  Calcule les coefficients des différences divisées de Newton.

  Args:
    x: Liste ou array NumPy des abscisses des points.
    y: Liste ou array NumPy des ordonnées des points.

  Returns:
    Array NumPy contenant les coefficients (f[x0], f[x0,x1], ...).
  """
  n = len(y)
  coeffs = np.copy(y).astype(float)
  for j in range(1, n):
    # La boucle interne calcule chaque différence divisée d'ordre j
    # Elle va de la dernière différence possible vers la première pour éviter d'écraser les valeurs nécessaires
    for i in range(n - 1, j - 1, -1):
      coeffs[i] = (coeffs[i] - coeffs[i-1]) / (x[i] - x[i-j])
  # Les coefficients sont les éléments coeffs[0], coeffs[1], ..., coeffs[n-1] après calculs
  # Mais comme on a modifié coeffs en place de manière descendante,
  # les coefficients finaux sont coeffs[j] pour l'ordre j.
  # Plus simplement, la diagonale supérieure du tableau implicite:
  # f[x0], f[x0,x1], f[x0,x1,x2], ... sont coeffs[0], coeffs[1], coeffs[2], ...
  # après que la boucle externe pour j=1 ait calculé coeffs[1], coeffs[2], ...
  # et que la boucle pour j=2 ait calculé coeffs[2], coeffs[3], ... etc.
  # Donc, les coefficients retournés sont bien ceux de la première ligne du tableau usuel.
  return coeffs # Renvoie le tableau complet, les coeffs sont la diagonale coeffs[0], coeffs[1]...coeffs[n-1]

def evaluer_polynome_direct(x_points, coeffs, x_eval):
  """
  Évalue le polynôme de Newton en utilisant les coefficients des différences divisées.

  Args:
    x_points: Liste ou array NumPy des abscisses des points d'interpolation.
    coeffs: Liste ou array NumPy des coefficients des différences divisées (calculés par differences_divisees).
    x_eval: Le point (ou array de points) où évaluer le polynôme.

  Returns:
    La valeur du polynôme au(x) point(s) x_eval.
  """
  n = len(coeffs) - 1
  # Utilise la méthode de Horner imbriquée pour l'évaluation
  P = coeffs[n]
  for k in range(n - 1, -1, -1):
    P = coeffs[k] + (x_eval - x_points[k]) * P
  return P

# Application à l'exemple donné
x_points = np.array([0, 1, 2])
y_points = np.array([1, 2, 5])

# 1. Calculer les coefficients
coefficients = differences_divisees(x_points, y_points)
print(f"Points x: {x_points}")
print(f"Points y: {y_points}")
print(f"Coefficients des différences divisées: {coefficients}")
# Note: Le tableau retourné contient plus que les coefficients diagonaux.
# Les coefficients du polynôme P(x) = c0 + c1(x-x0) + c2(x-x0)(x-x1) + ...
# sont la *première ligne* du tableau des différences divisées,
# qui sont f[x0], f[x0,x1], f[x0,x1,x2], ...
# Dans notre implémentation, ces coefficients correspondent à coeffs[0], coeffs[1], ..., coeffs[n-1].
coeffs_polynome = np.diag(np.fliplr(coefficients.reshape(-1,1))) # Extrait la diagonale principale f[x0], f[x0,x1]..
coeffs_polynome = coefficients # L'implémentation retourne déjà les bons coefficients dans l'ordre

print(f"Les coefficients du polynôme P(x) = c0 + c1(x-x0) + c2(x-x0)(x-x1) sont: {coeffs_polynome}")
# Vérification (exemple du PDF): Les coefficients sont f[0]=1, f[0,1]=1, f[0,1,2]=1 

# 2. Évaluer le polynôme (par exemple en x=1.5)
x_a_evaluer = 1.5
valeur_polynome = evaluer_polynome_direct(x_points, coeffs_polynome, x_a_evaluer)
print(f"La valeur du polynôme interpolateur en x = {x_a_evaluer} est: {valeur_polynome}")

# Vérification manuelle pour x=1.5:
# P(x) = 1 + 1*(x-0) + 1*(x-0)*(x-1)
# P(1.5) = 1 + 1*(1.5) + 1*(1.5)*(0.5) = 1 + 1.5 + 0.75 = 3.25
print(f"Vérification manuelle pour P(1.5): 1 + 1*(1.5) + 1*(1.5)*(0.5) = {1 + 1*(1.5) + 1*(1.5)*(0.5)}")


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