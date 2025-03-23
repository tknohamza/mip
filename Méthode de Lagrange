import numpy as np

def lagrange_interpolation(x_values, y_values, x):
    """
    Interpolation de Lagrange pour approximer la valeur de f(x).
    
    Paramètres:
    x_values : liste des abscisses des points
    y_values : liste des ordonnées correspondantes
    x : valeur où l'on veut estimer f(x)
    
    Retourne:
    y : approximation de f(x) par le polynôme de Lagrange
    """
    n = len(x_values)
    y = 0
    
    for i in range(n):
        L_i = 1
        for j in range(n):
            if i != j:
                L_i *= (x - x_values[j]) / (x_values[i] - x_values[j])
        y += L_i * y_values[i]
    
    return y

# Exemple d'utilisation
x_points = [1, 2, 3, 4]
y_points = [2, 3, 5, 7]
x_eval = 2.5

result = lagrange_interpolation(x_points, y_points, x_eval)
print(f"L'estimation de f({x_eval}) est : {result:.6f}")