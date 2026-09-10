Tipo: Nota permanente
Fecha: 2026-08-25
Referencias:
* 
Temas: #Operadores-comparacion
### ¿Que son los operadores de comparación?
Los operadores de comparación son el conjunto de símbolos que nos ayudan a comparar dos valores en un programa, el resultado de esa comparación es un booleano.

| Operador | Significado       |
| -------- | ----------------- |
| ==       | Igual a           |
| !=       | Diferente de      |
| >        | Mayor que         |
| <        | Menor que         |
| >=       | Mayor o igual que |
| <=       | Menor o igual que |
### Ejemplos

#### Operador ==
Un programa debe verificar si la edad de una persona es exactamente 18 años. La edad debe ser guardada en una variables y muestra True o False dependiendo de si tiene exactamente esa edad
```python
edad = int(input("Cual es tu edad? "))
resultado = bool
if edad == 18:
	resultado = True
	print(resultado)
else:
	resultado = False
	print(resultado)
```

#### Operador !=
Un sistema debe verificar si la contraseña introducida por un usuario es diferente de la contraseña almacenada.
```python
contraseña = input("Coloca la contraseña: ")
contraseña_guardada = "ef3t343f3g"
if contraseña != contraseña_guardada:
	print("Contraseña erronea")
```

#### Mayor que >
Un programa debe determinar si la temperatura actual es mayor a 30 grados.
```python
temperatura = 31
temperatura_permitida = 30
if temperatura > temperatura_permitida:
	print("Temperatura excedida")
else:
	print("Temperatura correcta")
```

#### Menor que <
Un programa debe terminar si la cantidad de dinero que tiene una persona es menor a $100
```python
saldo = 90
if saldo < 100:
	print("Cantidad inferior")
else:
	print("Cantidad superada")
```

#### Mayor o igual que >=
Para aprobar un curso, un estudiante necesita obtener una calificación de 70 o mas. El programa debe determinar si el estudiante aprobó.
```python
calificacion = 90
if calificacion > 70:
	print("Estudiante aprobado")
```

#### Menor o igual que <=
Un estacionamiento permite vehículos que tengan un peso máximo de 2,000 kg. El programa debe determinar si un vehículo puede entrar según su peso.
```python
vehiculo_peso = 1900
if vehiculo_peso <= 2000:
	print("Bienvenido al estacionamiento")
```
### Notas Relacionadas
[[Algebra de Bool]]
[[Condicionales]]

