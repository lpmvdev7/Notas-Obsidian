Tipo: Nota permanente
Fecha: 2026-08-24
Referencias:
* 
Temas: #Diagramas #Diagrama-flujo
### ¿Que es un diagrama de flujo?
Un diagrama de flujo es el conjunto de formas geométricas que conectadas nos ayuda a representar de forma visual un algoritmo, en otras palabras un diagrama de flujo es una forma visual de representar algoritmos
### Formas geométricas básicas en algoritmos
![[flow-diagram-shapes.png]]

### Ejemplo de Diagramas de flujo

#### Ejercicio 1 
Tenemos el siguiente problema:
>Elabora un programa que pida la edad de una persona y en base a ello determine si es mayor o menor de edad

```bash
# Pseudocodigo
Inicio
	usuario ingresa edad
	Si edad usuario mayor o igual a 18
		imprimir "Es mayor de edad"
	Si no
		imprimir "Es menor de edad"
Fin
```

![[DiagramaFlujo-ejercicio1.excalidraw|1000]]

```python
edad = int(input("Ingresa tu edad: "))
if edad >= 18:
    print("Es mayor de edad")
else:
    print("Es menor de edad")
```

#### Ejercicio 2
Tenemos el siguiente problema
>Crear un programa que permita al usuario:
>1. Consultar saldo
>2. Depositar dinero
>3. Retirar dinero
>4. Salir

```bash
# Pseudocodigo
Inicio
	Mostrar menu a usuario
		1. Consultar saldo
		2. Depositar
		3. Retirar
		4. Salir
		Usuario elige un numero de opcion
		Mientras opcion usuario != 4
			Si usuario igual a 1
				mostrar saldo
			Sino usuario igual a 2
				preguntar cantidad a depositar
				Si cantidad a depositar <= 0
					imprimir "Colocar una cantidad valida"
				Sino
					Sumar deposito al saldo
					Mostrar el nuevo saldo
					Mostrar saldo depositado
			Sino usuario igual a 3
				preguntar cantidad a retirar
				Si cantidad a retirar <= 0
					imprimir "Colocar una cantidad valida"
				Sino 
					Restar retiro al saldo
					Mostrar nuevo saldo
					Mostrar cantidad retirada
			Sino
				Terminar aplicacion
		Fin mientras
Fin
```

![[cajero-automatico-diagramaflujo.excalidraw | 1000]]

```python
menu = """
    1. Consultar Saldo \n
    2. Depositar \n
    3. Retirar \n
    4. Salir
"""
saldo = 0
opcion_usuario = 0

print(menu)
while opcion_usuario != 4:
    opcion_usuario = int(input("Elige una opcion: "))
    
    # Funcionalidad para consultar Saldo
    if opcion_usuario == 1:
        print(saldo)
    # Funcionalidad de Deposito
    elif opcion_usuario == 2:
        cantidad_deposito = int(input("Cual es la cantidad a depositar? "))
        if cantidad_deposito < 0:
            print("Coloca una cantidad valida")
        else:
            saldo = cantidad_deposito + saldo
            print(f"Saldo actual: {saldo}")
            print(f"Cantidad depositada: {cantidad_deposito}")
    
    # Funcionalidad para retirar Saldo
    elif opcion_usuario == 3:
        cantidad_retiro = int(input("Cual es la cantidad a retirar? "))
        if cantidad_retiro < 0:
            print("Coloca una cantidad valida")
        else:
            saldo = saldo - cantidad_retiro
            print(f"Saldo actual: {saldo}")
            print(f"Cantidad retirada: {cantidad_retiro}")
```

https://plantuml.com/es/ 
### Notas Relacionadas
[[Pseudocodigo]]
[[Algoritmos]]


