Tipo: Nota permanente
Fecha: 2026-07-17
Referencias: 
* https://youtu.be/InBm1uDgmKg?si=TJJ0FgowEBlG-Ssw 
Temas: #Logica #Programacion
### ¿Que es el Algebra de Bool?
El algebra de bool es un conjunto de reglas que se utilizan ampliamente en programación para ayudarnos a nosotros los ingenieros a manipular valores que solo puede ser verdaderos o falsos, es decir valores booleanos.
![](https://upload.wikimedia.org/wikipedia/commons/6/6c/George_Boole.jpg)

### ¿Por qué necesitamos los valores booleanos en ingeniería de software?
Los valores booleanos son muy importantes en ingeniería de software, por poner un ejemplo muy global, a la hora de desarrollar sistemas, estamos mejorando un proceso, naturalmente en ese proceso se toman decisiones, esas decisiones en muchas ocasiones pasan por valores booleanos, aquí hablo de algunos ejemplos:
* Un sistema que verifica la edad de sus usuarios
* Un sistema de autenticación, esto prácticamente esta presente en cualquier software del mundo
* Una cadena de ejecución de instrucciones que se cumplen si la otra ya fue ejecutada.
Como vimos en los ejemplos anteriores, la lógica de bool es omnipresente en el desarrollo de software, sin ella tendríamos sistemas prácticamente INUTILES.
En sistemas de software hacemos uso de la lógica de bool a través de dos formas: **Los operadores de comparación y los operadores booleanos**

### Operadores de comparación
Los operadores de comparación nos ayudan como desarrolladores de software a equiparar dos valores, devolviendo así un valor booleano.
Aquí están algunos operadores de comparación.
( == ) igual a
( != ) distinto que
( > ) mayor que
( < ) menor que
( >= ) mayor o igual que
( <= ) menor o igual que

Todos estos valores nos ayudan a comparar valores en nuestras aplicaciones o sistemas.

### Operadores booleanos
Los operadores booleanos nos ayudan a crear lógica compleja en nuestras aplicaciones, esto mediante la combinación de valores booleanos que nosotros como desarrolladores manipulamos con el fin de que ocurran ciertos escenarios dadas ciertas condiciones. 
Por ejemplo: 
>Tenemos una pagina web que necesita verificar la mayoría de edad del usuario y que este tenga una credencial INE, aquí podemos ver que con este enunciado damos pie a una condición en la que las dos condicionante para entrar se deben cumplir SI o SI:
>"Usuario es mayor de edad y tiene INE, puede entrar al sitio"
>"Usuario es mayor de edad  pero NO tiene INE, no puede entrar al sitio"

Ahora que ya vimos con un pequeño ejemplo el porque los operadores booleanos son importantes, conozcamos a los operadores:
* AND: Este operador devuelve verdadero si ambos valores comparados son verdaderos 
* OR: Devuelve verdadero si al menos uno de los valores es verdadero
* NOT: Se le conoce como la negación lógica, devuelve verdadero si el valor es falso y devuelve falso si el valor es verdadero.

#### Las Tablas de Verdad
Las tablas de verdad nos ayudan a visualizar todos las combinaciones posibles que se pueden hacer con los operadores booleanos y los resultados que estas generan.

##### AND
| A     | B     | A && B |
| ----- | ----- | ------ |
| TRUE  | TRUE  | TRUE   |
| TRUE  | FALSE | FALSE  |
| FALSE | TRUE  | FALSE  |
| FALSE | FALSE | FALSE  |
##### OR
| A     | B     | A \|\| B |
| ----- | ----- | -------- |
| TRUE  | TRUE  | TRUE     |
| TRUE  | FALSE | TRUE     |
| FALSE | TRUE  | TRUE     |
| FALSE | FALSE | FALSE    |
##### NOT
| A     | !A    |
| ----- | ----- |
| TRUE  | FALSE |
| FALSE | TRUE  |

#### La precedencia
La precedencia nos habla del orden en el cual se deben evaluar los operadores booleanos, el cual seria el siguiente:
1. NOT
2. AND
3. OR
La precedencia nos ayuda a saber que operaciones evaluar primero cuando tenemos un enunciado muy grande, en casos en los que el enunciado sea demasiado grande lo que podemos hacer es usar parentesis () y aplicar estas reglas.

#### Ejemplos a papel 
En la siguiente imagen de 4 ejemplos que he creado, podemos ver como se resuelven los ejercicios de algebra de bool, para ello siempre tuve en cuenta resolver primeros los paréntesis siguiendo el orden de precedencia.
Es decir que si en el ejercicio encontraba un paréntesis me iba a resolver este primero y si en el paréntesis me encontraba un NOT y un OR el primero que resolvía era el NOT, dado el orden de precedencia.
![[algebra-bool-ejercicios.png]]

#### Ejemplos con código
>**Inicio de Sesión**
>A continuación voy a realizar un pequeño ejemplo en código Javascript donde podemos ver como se utiliza la lógica booleana para aplicarla a un problema real de inicio de sesión en una aplicación, para ello debemos tener en cuenta que necesitamos comprobar que el usuario existe y que la contraseña ingresada es correcta.

```javascript
var user = "Pablo"
var password = "1234"

var userInput = "Pablo"
var passwordInput = "1234"

if(user == userInput && password == passwordInput){
	console.log("Bienvenido a la aplicacion")
}
```

>**Acceso a un dashboard**
>Podemos utilizar la lógica booleana para verificar si el usuario autenticado puede ver el dashboard.

```python
userInfo = {
	nombre = "Pablo",
	isAdmin = true
	isLogged = true
}

if userInfo["isAdmin"] and userInfo["isLogged"]:
    print("Puedes ver el dashboard")

```
### Notas Relacionadas
[[Condicionales]]
[[Bash Scripting]]
[[Diagramas de Flujo]]
[[Uso de operadores logicos en la terminal]]


