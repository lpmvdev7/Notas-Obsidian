Tipo: Nota permanente
Fecha: 2026-07-30
Referencias:
* Linux.pdf
* Claude
Temas: #Archivos #Procesamiento-texto #Comandos 
### Las variables en awk
El comando awk nos permite el uso de varias palabras reservadas que nos ayudaran a explotar de mejor manera la funcionalidad del comando, a continuación estaré hablando de cada una.

Con el objetivo de ejemplificar el uso de awk con las palabras reservadas estaré utilizando un archivo csv que contiene información de jugadores de fútbol, las columnas de ese archivo son las siguientes:
```bash
name
full_name
birth_date
age
height_cm
weight_kgs
positions
nationality
overall_rating
potential
value_euro
wage_euro
preferred_foot
international_reputation
weak_foot
skill_moves
body_type
release_clause_euro
national_team
national_rating
national_team_position
national_jersey_number
crossing
finishing
heading_accuracy
short_passing
volleys
dribbling
curve
freekick_accuracy
long_passing
ball_control
acceleration
sprint_speed
agility
reactions
balance
shot_power
jumping
stamina
strength
long_shots
aggression
interceptions
positioning
vision
penalties
composure
marking
standing_tackle
sliding_tackle
```

### Ejemplos
#### BEGIN
En este ejemplo utilizamos awk para filtrar a todos aquellos jugadores brasileños que cumplan las siguientes condiciones:
* Nacionalidad = Brazil
* Overall_Rating mayor a 85

Notese que utilizamos **BEGIN** para dar una pista de que tratan los datos que estamos mostrando.
```bash
awk -F "," 'BEGIN{print "=== Top brazil players ==="}   $8 == "Brazil" && $9 >85 {print $2}' fifa_players.csv
```

#### END
En este ejemplo utilizamos awk haciendo prácticamente lo mismo que en el ejemplo anterior solo que esta vez utilizamos **END** para terminar de mostrar un bloque de datos.
```bash
awk -F "," '$8 == "Brazil" && $9 >85 {print $2} END{print "==== FIN TOP BRAZIL===="}' fifa_players.csv 
```

#### NR
En este ejemplo usamos **NR** para imprimir la linea numero 2 del archivo.csv.
```bash
 awk -F ',' 'NR==2' fifa_players.csv 
```

#### OFS
>**OFS** significa **Output Field Separator** (Separador de Campos de Salida). Es una variable interna de AWK que define **qué carácter se usa para unir los campos cuando los imprimes con comas dentro de `print`**.
```bash
echo "Juan:30:Ventas" | awk -F':' 'BEGIN{OFS="-"} {print $1, $2, $3}'
```
### Notas Relacionadas
[[awk]]
[[awk-condicionales]]


