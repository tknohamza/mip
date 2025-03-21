# TP

Premièrement, installer :


```shell
import numpy as np
```


> [!TIP]
> utiliser `command prompt` pour installer resources.


### <a name="exercice-1"></a> Exercice 1


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


### <a name="exercice-2"></a> Exercice 2

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

### <a name="exercice-3"></a> Exercice 3

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


> [!NOTE]
> Il existe toujours une possibilité d'erreur, nous n'en assumons donc aucune responsabilité.