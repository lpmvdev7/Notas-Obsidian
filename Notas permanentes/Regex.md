Tipo: Nota permanente
Fecha: 2026-07-28
Referencias:
* Linux.pdf
* https://www.youtube.com/watch?v=V_DzcyGTXW0
Temas: 
### ¿Que es Regex?
Nosotros como humanos podemos distinguir patrones en texto, nos es posible distinguir un correo en un parrafo o un numero de celular, para las computadoras esto no es asi, ellas necesitan un lenguaje especial para poder reconocer esos patrones.
Regex es el lenguaje universal de reconocimiento de patrones en texto que les permite a los computadores reconocer números de teléfono, correos, nombres completos y muchos otros patrones en texto.
![](https://ayudawp.com/wp-content/uploads/2023/09/redirecciones-regex-wordpress.jpg)
### ¿Que usos tiene regex?
Regex tiene una gran cantidad de usos, aquí están algunos de los que se me ocurren:
* Regex nos ayuda a distinguir correos corporativos y correos personales 
* Regex nos ayuda al procesamiento de información
* Con Regex podemos buscar en archivos que contiene grandes cantidades de datos en formato texto.

### Como se utiliza Regex
Para saber como utilizar regex tenemos que conocer su sintaxis mas básica.
```bash
/ (regex) / modificador
```
Dentro de esta sintaxis básica, regex nos provee de una serie de elementos que nos ayudaran a identificar patrones en texto, esos elementos son los siguientes:
* Modificadores
* Metacaracteres
* Limites
* Cuantificadores
* Conjuntos
* Grupos

#### Modificadores
Los modificadores son letras que se agregan para cambiar el comportamiento global de una expresión regular

| Modificador | Nombre      | ¿Que hace?                                                        |
| ----------- | ----------- | ----------------------------------------------------------------- |
| i           | insensitive | Acepta mayusculas y minusculas                                    |
| g           | global      | Busca todas las coincidencias en el texto, no solo la primera     |
| m           | multiline   | Cambia como se interpretan ^ y $ para que funcionen en cada linea |
| s           | dotAll      | Permite que el punto coincida también con saltos de linea         |
| u           | unicode     | Compatible con texto Unicode como emojis, acentos etc.            |
```bash
# Sintaxis de uso para los modificadores
/ (regex) /i
/ (regex) /g
/ (regex) /m
/ (regex) /s
/ (regex) /u

# Uso combinado
/ (regex) /gi
```

#### Metacaracteres
Caracteres especiales de una expresión regular que tienen un significado propio.

| Metacaracter | Definicion                                  |
| ------------ | ------------------------------------------- |
| .            | Cualquier caracter (excepto salto de linea) |
| \d           | Cualquier digito (0-9)                      |
| \D           | Negacion de digitos                         |
| \w           | Caracteres de palabra                       |
| \W           | Negacion de los caracteres de palabra       |
| \s           | Espacios                                    |
| \S           | Negacion de espacios                        |
```bash
# Con esta expresion podemos encontrar todos los caracteres de una palabra
/\w/g
```


#### Limites
Caracteres en regex que nos ayudan a buscar posiciones dentro del texto, nos ayudan a indicar en donde debe ocurrir una coincidencia.

| Caracter | Uso                                                       |
| -------- | --------------------------------------------------------- |
| \b       | Encuentra el limite de una palabra                        |
| \B       | Negacion de encontrar el limite de una palabra            |
| ^        | Inicio de una cadena (el modificador m debe estar activo) |
| $        | Fin de una cadena (el modificador m debe estar activo)    |
```bash
# Con esta expresion encontramos todas aquellas palabras que inicien con la letra "B"
/\bB/g
```

#### Cuantificadores
Caracteres regex que nos ayudan a verificar cuantas veces aparece un carácter en un texto dado.

| Cuantificador | Significado         |
| ------------- | ------------------- |
| *             | 0 o mas veces       |
| +             | 1 o mas veces       |
| ?             | 0 o 1 (opcional)    |
| {n}           | Exactamente n veces |
| {n,}          | n o mas veces       |
| {n,m}         | Entre n y m veces   |
```bash
#Encontrar todas las palabras que aparezcan de 2 a 5 veces en un texto.
/e{2,5}/g
```

#### Conjuntos
Las clases de caracteres nos permiten hacer coincidir cualquiera de los caracteres especificados dentro de corchetes [].

| Signos | Definicion                                        |
| ------ | ------------------------------------------------- |
| []     | Caracteres dentro de los brackets                 |
| [^]    | Negacion de los caracteres dentro de los brackets |
```bash
# Encontrar todas las palabras que empiecen con g
\b[g][a-z]\gi
```

#### Grupos
Sección de una expresión regular delimitada por paréntesis. Su función es tratar varias expresiones como una sola unidad.

| Signos | Definicion     |
| ------ | -------------- |
| ( )    | Crear un grupo |
| \|     | Uno u otro     |
```bash

# Encontrar todas los archivos cuya extension sea .csv o .xlsx 
/ventas\.(csv|xlsx)/gi

```


#### Lookahead
Un lookahead es una forma de decirle a regex "antes de seguir avanzando, hecha un vistazo hacia adelante y comprueba si hay algo, pero no lo consumas, no lo incluyas en el match" 
```bash
(?=patron)
```

### Sitios para practicar regex
Aquí esta una lista de algunos sitios web para practicar regex.
* https://regex101.com/
* https://regexr.com/

### Ejemplos
>Validar un numero de teléfono con formato **123-456-7890**
```bash
/^\d{3}-\d{3}-\d{4}$/
```

>Validar un correo electrónico simple **(usuario@dominio.com)**
```bash
/^[\w.-]+@[\w-]+(\.[\w-]+)+$/
```

>Validar un numero de tarjeta de crédito con formato **XXXX-XXXX-XXXX-XXX**
```bash
/^\d{4}-\d{4}-\d{4}-\d{4}$/
```

>Validar una contraseña fuerte: mínimo 8 caracteres, al menos una mayúscula, una minúscula, un numero y un símbolo (!@#$%^&*).
```bash
/(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[!@#$%^&*]).{8,}/g
```

### Notas Relacionadas
[[find - expresiones de busqueda]]


