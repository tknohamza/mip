# TC MIP : Génie des Technologies Industrielles S4


### <a name="objectifs"></a> objectifs


>• Créer, afficher et manipuler des tableaux NumPy.
• Utiliser des fonctions NumPy pour effectuer des opérations mathématiques avancées sur les tableaux.
• Effectuer des opérations matricielles en utilisant NumPy.
• Résoudre des systèmes d'équations linéaires en utilisant la méthode d'élimination de Gauss avec NumPy.


Premièrement, installer :


```shell
import numpy as np
```


> [!TIP]
> utiliser `command prompt` pour installer resources.


</p>
<h3 align="center">Exercice 1</h3>
<p align="center">
</p>


1. Créez un tableau NumPy arr1 contenant les nombres de 0 à 9 et affichez-le.


```shell
arr1 = np.arange(10)
print("arr1:", arr1)
```

2. Créez un tableau arr2 de forme (3, 3) rempli de zéros et affichez-le.


```shell
arr2 = np.zeros((3, 3))
print("arr2:\n", arr2)
```


3. Créez un tableau arr3 de forme (2, 4) rempli de nombres aléatoires entre 0 et 10 et affichez-le.


```shell
arr3 = np.random.uniform(0, 10, (2, 4))
print("arr3:\n", arr3)
```

4. Créez un tableau arr4 de forme (5,) contenant des nombres espacés linéairement entre 0 et 100 (inclus) et affichez-le.


```shell
arr4 = np.linspace(0, 100, 5)
print("arr4:", arr4)
```

5. Affichez la forme (shape), le type de données (dtype) et la dimension (ndim) de arr3.


```shell
print("Forme de arr3:", arr3.shape)
print("Type de données de arr3:", arr3.dtype)
print("Dimension de arr3:", arr3.ndim)
```


</p>
<h3 align="center">Exercice 2</h3>
<p align="center">
</p>

N'oubliez jamais d'installer :

```shell
import numpy as np
```

> [!TIP]
> utiliser `command prompt` pour installer resources.


1. Calculez la somme de tous les éléments de arr1.


```shell
arr1 = np.arange(10)
somme_arr1 = np.sum(arr1)
print("Somme de arr1:", somme_arr1)
```

2. Calculez la moyenne des éléments de arr3.


```shell
arr3 = np.random.uniform(0, 10, (2, 4))
moyenne_arr3 = np.mean(arr3)
print("Moyenne de arr3:", moyenne_arr3)
```

3. Calculez le produit des éléments de arr1.


```shell
arr1 = np.arange(10)
produit_arr1 = np.prod(arr1)
print("Produit de arr1:", produit_arr1)
```

4. Calculez la racine carrée de chaque élément de arr4.


```shell
arr4 = np.linspace(0, 100, 5)
racine_carree_arr4 = np.sqrt(arr4)
print("Racine carrée de arr4:", racine_carree_arr4)
```

5. Calculez le logarithme naturel de chaque élément de arr3.


```shell
arr3 = np.random.uniform(0, 10, (2, 4))
log_naturel_arr3 = np.log(arr3)
print("Logarithme naturel de arr3:\n", log_naturel_arr3)
```

</p>
<h3 align="center">Exercice 3</h3>
<p align="center">
</p>

N'oubliez jamais d'installer :

```shell
import numpy as np
```

> [!TIP]
> use `command prompt` to download resources.


1. Créez deux matrices mat1 et mat2 de forme (2, 2) avec des valeurs de votre choix.


```shell
mat1 = np.array([[1, 2], [3, 4]])
mat2 = np.array([[5, 6], [7, 8]])
```

2. Calculez le produit matriciel de mat1 et mat2.


```shell
produit_mat = np.dot(mat1, mat2)
print("Produit matriciel de mat1 et mat2 :\n", produit_mat)
```

3. Calculez la transposée de mat1.


```shell
transposee_mat1 = mat1.T
print("Transposée de mat1 :\n", transposee_mat1)
```

4. Calculez le déterminant de mat2.


```shell
determinant_mat2 = np.linalg.det(mat2)
print("Déterminant de mat2 :", determinant_mat2)
```

5. Calculez l'inverse de mat2.


```shell
inverse_mat2 = np.linalg.inv(mat2)
print("Inverse de mat2 :\n", inverse_mat2)
```

</p>
<h3 align="center">Exercice 4</h3>
<p align="center">
</p>

N'oubliez jamais d'installer :

```shell
import numpy as np
```

> [!TIP]
> use `command prompt` to download resources.


1. Considérons le système d'équations linéaires suivant :
    2x + y - z = 5
    x + 3y + z = 7
    x - y + 2z = 3


```shell
mat1 = np.array([[1, 2], [3, 4]])
mat2 = np.array([[5, 6], [7, 8]])
```

2. Créez une matrice augmentée Aaug en combinant la matrice des coefficients et le vecteur des termes constants.


```shell
A = np.array([[2, 1, -1], [1, 3, 1], [1, -1, 2]])
b = np.array([5, 7, 3])
Aaug = np.concatenate((A, b.reshape(-1, 1)), axis=1)
```

3. Appliquez la méthode d'élimination de Gauss pour transformer la matrice augmentée Aaug en une forme échelonnée.


```shell
def elimination_gauss(Aaug):
    n = len(Aaug)
    for i in range(n):
        # Assurez-vous que le coefficient principal (pivot) est non nul.
        if Aaug[i, i] == 0:
            for j in range(i + 1, n):
                if Aaug[j, i] != 0:
                    Aaug[[i, j]] = Aaug[[j, i]]
                    break
        # Multipliez la ligne i par un facteur approprié pour que le pivot soit 1 (si nécessaire).
        pivot = Aaug[i, i]
        Aaug[i] = Aaug[i] / pivot
        # Soustrayez des multiples de la ligne i des lignes suivantes pour annuler les coefficients en dessous du pivot.
        for j in range(i + 1, n):
            facteur = Aaug[j, i]
            Aaug[j] = Aaug[j] - facteur * Aaug[i]
    return Aaug

Aaug_echelonnee = elimination_gauss(Aaug.copy())
print("Matrice augmentée échelonnée :\n", Aaug_echelonnee)
```

4. Résolvez le système en utilisant la substitution arrière.


```shell
def substitution_arriere(Aaug_echelonnee):
    n = len(Aaug_echelonnee)
    x = np.zeros(n)
    for i in range(n - 1, -1, -1):
        x[i] = Aaug_echelonnee[i, n] - np.dot(Aaug_echelonnee[i, i + 1:n], x[i + 1:n])
    return x

solution = substitution_arriere(Aaug_echelonnee)
print("Solution du système :\n", solution)
```

5. Vérifiez la solution en calculant Ax et en comparant avec b.


```shell
verification = np.dot(A, solution)
print("Vérification : Ax =", verification)
print("b =", b)
```


> [!NOTE]
> Il existe toujours une possibilité d'erreur, nous n'en assumons donc aucune responsabilité.