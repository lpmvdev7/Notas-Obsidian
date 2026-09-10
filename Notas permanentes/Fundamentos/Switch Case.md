Tipo: Nota permanente
Fecha: 2026-08-26
Referencias:
* 
Temas: #Condicionales #Switch-case
### ¿Que es un Switch Case?
Un Switch Case es una estructura de datos en programación que nos permite ejecutar diferentes bloques de código según el valor exacto de una variable. Es como darle a nuestro programa un menú de opciones.

```python
# Switch en python (Disponible desde la version 3.10)
hora = 8
match hora:
	case 8:
		print("Desayuno")
	case 14:
		print("Comida")
	case 21:
		print("Cena")
	case _:
		print("No toca comer")
```

```javascript
// Javascript
let hora = 8;
switch (hora){
	case 8:
		console.log("Desayuno")
		break;
	case 14:
		console.log("Comida")
		break;
	case 21:
		console.log("Cena")
		break;
	default:
		console.log("No toca comer")
}
```

### ¿Cuando usar un switch case en lugar de un if?
Usa switch case para evaluar una única variable contra múltiples valores exactos y usa condicionales if para lógica mas complejas.
### Notas Relacionadas
[[Condicionales]]



