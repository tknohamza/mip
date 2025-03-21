# TP
1er install

```shell
import numpy as np
```

> [!TIP]
> use `command prompt` to download resources.


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


> [!NOTE]
> Il existe toujours une possibilité d'erreur, nous n'en assumons donc aucune responsabilité.