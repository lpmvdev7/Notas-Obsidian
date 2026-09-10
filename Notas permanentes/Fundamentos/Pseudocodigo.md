Tipo: Nota permanente
Fecha: 2026-08-24
Referencias:
* https://www.youtube.com/watch?v=NJavXHU5MW8
Temas: #Pseudocodigo
### ¿Que es el pseudocodigo?
El pseudocodigo es el conjunto de instrucciones claras y ordenadas que nos ayudan a entender el proceso que conlleva el completar una tarea. 

### ¿Para que sirve el pseudocodigo en programación?
El pseudocodigo es de gran utilidad en el desarrollo de software ya que por lo general, el desarrollo de software consiste principalmente en entender el problema del usuario y el primer paso para entender esa problemática es plasmarla en sentencias que como humanos entendamos.

### ¿Como escribir pseudocodigo?
Escribir pseudocodigo es algo muy sencillo, únicamente tenemos que seguir algunas pocas convenciones que nos ayudaran a identificar el flujo de nuestro programa, estas convenciones son palabras clave que usaremos a lo largo de nuestro pseudocodigo.

A continuación tenemos un pseudocodigo que describe un programa cuyo objetivo es imprimir un mensaje si un numero es par y en caso contrario un mensaje diferente si ese numero no es par.
```bash
Inicio
Pedir un numero al usuario
Calcular el resto de dividir dicho numero entre dos
Si el resto es 0 Entonces
	Mostrar "El numero es par"
Si no
	Mostrar "El numero es impar"
Fin Si
Fin
```

El pseudocodigo anterior se puede traducir a código real, por ejemplo a Python.
```python
numero = int(input("Introduce un numero:"))
resto = numero % 2
if resto == 0:
	print("El numero es par")
else:
	print("El numero es impar")
```

### Ejercicios de pseudocodigo
##### Ejercicio 1 
Crea un programa que pida las calificaciones del usuario y calcule el promedio
```bash
# Pseudocodigo
Inicio
	Pedir numero de materias al usuario
	Por cada materia
		Pedir calificacion al usuario
		Guardar calificacion de la materia
	Sumar calificaciones y dividir entre el numero de calificaciones
	Mostrar promedio
Fin
```

```python
# Codigo python
materias = int(input("Coloca el numero de materias"))
calificaciones = []

for materia in range(materias):
    calificacion = int(input("¿Cual fue tu calificacion en esta materia"))
    calificaciones.append(calificacion)

promedio = (sum(calificaciones)/len(calificaciones))
print(f"El promedio es de {promedio}")
```

##### Ejercicio 2
Crear un sistema de calificaciones que pida una calificación de 0 al 100 y en base a eso clasifique el desempeño de los alumnos en base a estos rangos.
```
90-100 --> A
80-89  --> B
70-79  --> C
60-69  --> D
0-59  --> F
```

```bash
# Pseudocodigo
Inicio
	Pedir calificacion al usuario
	Si la calificacion >= 90 y <= 100
		imprimir "Tu desemepeño es A"
	Sino si calificacion >= 80 y <= 89
		imprimir "Tu desempeño es B"
	Sino si calificacion >= 70 y <= 79
		imprimir "Tu desempeño es C"
	Sino si calificacion >= 60 y <= 69
		imprimir "Tu desempeño es D"
	Sino
		imprimir "Tu desempeño es F"
Fin
```

```python
# Codigo python
calificacion = int(input("Ingresa un numero: "))

if calificacion >= 90 and calificacion <= 100:
    print("Tu desempeño es A")
elif calificacion >= 80 and calificacion <= 89:
    print("Tu desempeño es B")
elif calificacion >= 70 and calificacion <= 79:
    print("Tu desempeño es C")
elif calificacion >= 60 and calificacion <= 69:
    print("Tu desempeño es D")
else:
    print("Tu desempeño es F")

```

>El pseudocodigo no sigue convenciones estrictas sino mas bien lenguaje natural, esto es de gran utilidad para los ingenieros en software debido a que nos sirve como un puente de planificación de lógica antes de la implementacion real, convirtiendo así la parte de la implementacion en un paso mas sencillo ya sin importar el lenguaje de programación, nuestra lógica sigue siendo la misma.
### Notas Relacionadas
[[Pseudocodigo]]
[[Diagramado en Ingenieria de Software]]
[[Variables]]
[[Algebra de Bool]]
[[Operadores de comparacion]]
[[Estructuras de control]]
[[Condicionales]]
[[Switch Case]]
[[Ciclo for]]
[[Ciclo while]]
[[Funciones]]
[[Estructuras de Datos]]
[[Algoritmos]]



