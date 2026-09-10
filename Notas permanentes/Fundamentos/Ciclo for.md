Tipo: Nota permanente
Fecha: 2026-08-26
Referencias:
* #Estructuras-control #Ciclo-for
Temas: 
### ¿Que son los ciclos for?
Los ciclos for son una estructura de control en programación que se repite un numero determinado de veces.
Por ejemplo, en mi experiencia profesional los utilice para renderizar contenido dinamicamente en paginas web.

```python
for i in range(0,5):
	print(i) # 0 1 2 3 4 5

for i in "Python":
		print(i) # P y t h o n 
		

nombres = ["Javier", "Ariana", "Miguel", "Leonardo"]
for nombre in nombres:
	print(nombre)
```

```javascript
for (let i = 0; i <= 5; i++){
	console.log(i)
}

let nombre = "javascript"
for (let i = 0; i < nombre.length; i++) {
	console.log(nombre[i]);
}

const SISTEMAS_OPERATIVOS = ["Windows", "MacOS", "Linux"]
for (const os of SISTEMAS_OPERATIVOS){
	console.log(os);
}

for (let i = 0; i < SISTEMAS_OPERATIVOS.length; i++){
	console.log(SISTEMAS_OPERATIVOS[i])
}

```
### Notas Relacionadas
[[Ciclo while]]


