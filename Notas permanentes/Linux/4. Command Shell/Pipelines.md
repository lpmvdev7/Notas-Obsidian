Tipo: Nota literatura | Nota permanente
Fecha: 2026-07-20
Referencias:
* Linux.pdf 
Temas: #Comandos #Flujos-estandar #Linux 
### Pipelines en linux
Los pipelines  son una funcionalidad de las terminales en linux que nos permiten pasar como argumento el output de un comando a otro comando, de esta manera encadenamos comandos y creamos diferentes combinaciones que nos ayudan a resolver mas problemas.
![](https://i.ytimg.com/vi/fkIRfBECcE8/sddefault.jpg)

Aquí tenemos un ejemplos muy básico de un pipeline, a continuación explico lo que esta sucediendo en este:
1. Imprimimos un mensaje en consola
2. El mensaje en consola lo pasamos como argumento al comando cowsay el cual es un comando que se encarga de imprimir un personaje diciendo una frase, pasamos este comando como argumento al ultimo.
3. El comando lolcat recibe como argumento cowsay y lo que hace es imprimir el personaje a color.
Como podemos cada comando necesita del anterior para producir el resultado.
>**Los pipelines se podrían definir como la concatenación de comandos, en la cual la salida de uno sirve como entrada para el otro, generando así una cadena de transformación de datos , cuyo resultado nosotros adecuamos a nuestras necesidades como ingenieros**
```bash
echo "Hola linux" | cowsay -f tux | lolcat
 ____________
< Hola linux >
 ------------
   \
    \
        .--.
       |o_o |
       |:_/ |
      //   \ \
     (|     | )
    /'\_   _/`\
    \___)=(___/

```


### Notas Relacionadas
[[Flujos estandar en Linux]]
[[comandos-linux]]

