Tipo: Nota permanente
Fecha: 2026-07-30
Referencias:
* Linux.pdf
Temas: #Procesamiento-texto #Archivos #Comandos 
### Uso de awk para condicionales
Uno de los usos mas potentes del comando awk es el uso de condicionales, awk nos permite crear condicionales con el objetivo de filtrar de manera mas eficiente las columnas que mas nos interesan, esta característica es muy útil debido a sus uso en archivos con datos cuantitativos.

Para ejemplificar el uso de awk con condicionales me he descargado un archivo.csv que contiene información de los artistas que mas escucha la gente en spotify en el año 2025.
Las columnas del archivo serian las siguientes:
```bash
rank,
track,
artist,
billed_artist_count,
is_collaboration,
spotify_streams_total,
daily_streams,
daily_streams_rank,
daily_stream_share_pct,
wrapped_global_top10_rank,
```
El archivo cuenta con 730 registros lo cual es excelente para mostrar como el comando awk puede ayudarnos en estos casos.

### Ejemplos
#### Ejemplo 1 
Supongamos que únicamente queremos el nombre de los artistas pertenecientes al top 10 del rank, la sentencia awk seria la siguiente:
```bash
awk -F ',' '$1 <= 10 {print $1 " " $3}' most_streamed_spotify_2025.csv

1 Alex Warren
2 Bad Bunny
3 HUNTR/X
4 Bad Bunny
5 Taylor Swift
6 Bad Bunny
7 Olivia Dean
8 Bad Bunny
9 W Sound
10 Bad Bunny

```

#### Ejemplo 2
En este segundo ejemplo mostramos las canciones que se encuentran en el top 5 y que ademas aparecen en el top 10 del wrapped global.
```bash
awk -F ',' '$1 < 6 && $10 > 0 {print $2 " " $3}' most_streamed_spotify_2025.csv 
Ordinary Alex Warren
DtMF Bad Bunny
Golden HUNTR/X
```

### Notas Relacionadas
[[awk]]
[[awk-variables]]
[[Uso de operadores logicos en la terminal]]
[[Algebra de Bool]]
