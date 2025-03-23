# Décomposition LU

### <a name="objectifs"></a> objectifs


> Calculez la Matrice L et U


Premièrement, installer :


```shell
pip install numpy
```


> [!TIP]
> utiliser `command prompt` pour installer resources.


</p>
<h3 align="center">L & U</h3>
<p align="center">
</p>

Vous devez vous assurer que le pivot soit toujours ≠ 0 :

```shell
# Décomposition LU

import numpy as np

def lu_decomposition(A):
    """
    Calcule la décomposition LU d'une matrice A.

    Args:
        A: La matrice carrée pour laquelle la décomposition LU est calculée.

    Returns:
        Un tuple contenant les matrices triangulaires inférieure (L) et supérieure (U).
    """
    n = len(A)
    L = np.zeros((n, n))
    U = np.zeros((n, n))

    for i in range(n):
        L[i][i] = 1  # Les éléments diagonaux de L sont 1

        for j in range(i, n):
            U[i][j] = A[i][j] - sum(L[i][k] * U[k][j] for k in range(i))

        for j in range(i + 1, n):
            L[j][i] = (A[j][i] - sum(L[j][k] * U[k][i] for k in range(i))) / U[i][i]

    return L, U

# Exemple d'utilisation
A = np.array([[2, -1, 4, 1],
              [4, -1, 5, 1],
              [-2, 2, -2, 3],
              [0, 3, -9, 4]], dtype=float)
L, U = lu_decomposition(A)
print("L:")
print(L)
print("U:")
print(U)

# by : tknohamza
```

> [!NOTE]
> Il existe toujours une possibilité d'erreur, nous n'en assumons donc aucune responsabilité.


</p>
<h3 align="center">Copyright</h3>
<p align="center">
</p>

tknohamza © 2025

> Merci de nous avoir contactés ici. Si vous avez des commentaires, n'hésitez pas à nous contacter :
tknohamzacontact@gmail.com
N'oubliez pas de nous suivre sur :
<a href="https://facebook.com/tknohamza">Facebook</a>, <a href="https://instagram.com/r/tknohamza">Instagram</a>, <a href="https://twitter.com/tknohamza">Twitter</a>, <a href="https://t.me/tknohamzachannel">Telegram</a>
