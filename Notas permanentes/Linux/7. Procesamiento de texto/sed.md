Tipo: Nota permanente
Fecha: 2026-07-30
Referencias:
* Linux.pdf
Temas: #Linux #Procesamiento-texto #Archivos 
### ¿Que hace el comando sed?
El comando sed nos permite la edición de archivos de texto desde la linea de comandos, sin la necesidad de meternos al archivo abriendo editores como vim o nano.

La sintaxis básica de uso del comando es la siguiente:
```bash
sed 's/viejo/nuevo/g' archivo.txt
```

Para ejemplificar un uso básico del comando supongamos que tenemos el siguiente texto en el cual una persona describa cuanto ama a los gatos.
```text
Hay algo indescriptible en la forma en que esta persona mira a su gato. Cada mañana, lo primero que busca con los ojos es a su gato, acurrucado entre las sábanas como si fuera el centro del universo. Le habla en voz baja, casi en secreto, y le dice que ese gato es lo más importante de su vida.

No hay ausencia que le pese más que la de su gato cuando sale de viaje. Le manda fotos a sus amigos: "miren a mi gato durmiendo", "miren a mi gato jugando con la cortina". Su celular está lleno de fotos de ese gato, cientos, quizás miles, cada una capturando un instante distinto de esa criatura que ronronea felicidad.

Cuando llega cansada del trabajo, lo único que la reconforta es sentarse en el sofá y dejar que su gato se le suba encima, ronroneando suavemente, como si supiera exactamente lo que necesita. Ella lo acaricia con ternura infinita, susurrándole que es el mejor gato del mundo, que nunca podría amar a nadie como ama a su gato.

Ese gato no es solo una mascota. Es compañía, es consuelo, es la razón por la que sonríe al llegar a casa. Y ella lo sabe: mientras tenga a su gato cerca, nunca estará realmente sola.
```

Si queremos sustituir todas las apariciones de la palabra **gato** por la palabra **perro**, lo podemos hacer con sed.
```bash
sed 's/gato/perro/g' archivo.txt
```

```text
Hay algo indescriptible en la forma en que esta persona mira a su perro. Cada mañana, lo primero que busca con los ojos es a su perro, acurrucado entre las sábanas como si fuera el centro del universo. Le habla en voz baja, casi en secreto, y le dice que ese perro es lo más importante de su vida.

No hay ausencia que le pese más que la de su perro cuando sale de viaje. Le manda fotos a sus amigos: "miren a mi perro durmiendo", "miren a mi perro jugando con la cortina". Su celular está lleno de fotos de ese perro, cientos, quizás miles, cada una capturando un instante distinto de esa criatura que ronronea felicidad.

Cuando llega cansada del trabajo, lo único que la reconforta es sentarse en el sofá y dejar que su perro se le suba encima, ronroneando suavemente, como si supiera exactamente lo que necesita. Ella lo acaricia con ternura infinita, susurrándole que es el mejor perro del mundo, que nunca podría amar a nadie como ama a su perro.

Ese perro no es solo una mascota. Es compañía, es consuelo, es la razón por la que sonríe al llegar a casa. Y ella lo sabe: mientras tenga a su perro cerca, nunca estará realmente sola.
```

### Notas Relacionadas
[[comandos-linux]]


