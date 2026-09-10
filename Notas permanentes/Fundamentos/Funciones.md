Tipo: Nota permanente
Fecha: 2026-08-26
Referencias:
* 
Temas: 
### ¿Que son las Funciones?
Las funciones, en el ámbito de la ingeniería de software, son bloques de código reutilizables que encapsulan una determinada lógica o tarea.
Una función nos permite definir una lógica una sola vez y posteriormente ejecutarla tantas veces como sea necesario, evitando así duplicar código.

### Ejemplo de uso de funciones
Tenemos el siguiente programa que calcula el precio final de los productos después de aplicarles un descuento. 
Echando un vistazo al código podemos ver que mucha de lógica que se ejecuta en el programa puede ser encapsulada en una función.

```javascript
// Codigo sin funciones
let producto1 = "Laptop";
let precio1 = 15000;
let descuento1 = 0.10;

let precioFinal1 = precio1 - (precio1 * descuento1);

console.log("Producto:", producto1);
console.log("Precio original:", precio1);
console.log("Descuento:", descuento1 * 100 + "%");
console.log("Precio final:", precioFinal1);


let producto2 = "Mouse";
let precio2 = 800;
let descuento2 = 0.15;

let precioFinal2 = precio2 - (precio2 * descuento2);

console.log("Producto:", producto2);
console.log("Precio original:", precio2);
console.log("Descuento:", descuento2 * 100 + "%");
console.log("Precio final:", precioFinal2);


let producto3 = "Teclado";
let precio3 = 1200;
let descuento3 = 0.20;

let precioFinal3 = precio3 - (precio3 * descuento3);

console.log("Producto:", producto3);
console.log("Precio original:", precio3);
console.log("Descuento:", descuento3 * 100 + "%");
console.log("Precio final:", precioFinal3);
```

```javascript
// Codigo con funciones
const productosInfo = [
	{
		nombre: "Laptop",
		precio: 1500,
		descuento: 0.10
	},
	{
		nombre: "Mouse",
		precio: 800,
		descuento: 0.15
	},
	{
		nombre: "Teclado",
		precio: 1200,
		descuento: 0.20
	},
]

function calcularPrecioFinal(nombre, precio, descuento){
	let precioFinal = precio - (precio * descuento)
	let objetoFinal = {
		"Producto": nombre,
		"Precio original": precio,
		"Descuento": descuento,
		"Precio Final": precioFinal
	}
	return objetoFinal
}

function calcularPrecioFinalProductos(){
	let productos_descuento = []
	for (let i = 0; i < productosInfo.length; i++){
		let nombres = productosInfo[i].nombre
		let precios = productosInfo[i].precio
		let descuentos = productosInfo[i].descuento
		let calculos = calcularPrecioFinal(nombres, precios, descuentos)
		productos_descuento.push(calculos)
	}
	console.log(productos_descuento)
	return productos_descuento
}

calcularPrecioFinalProductos()

```

Con la solución que he propuesto el código se vuelve mas reutilizable y mucho mas mantenible, es por esta razón que las funciones son un aspecto muy importante en programación.
### Notas Relacionadas
[[Estructuras de control]]
[[Estructuras de Datos]]
[[Algoritmos]]
[[Pseudocodigo]]


