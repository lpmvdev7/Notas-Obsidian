Tipo: Nota permanente
Fecha: 2026-09-09
Referencias:
* 
Temas: #Bash-script #heredocs
### ¿Que son los heredocs?
Un heredoc es un bloque de texto de varias lineas que se escribe tal cual dentro del código de un script.
Los heredocs pueden ser usados para muchas cosas como escribir textos muy largos o escribir codigo HTML.

```bash
cat << EOF
Hola mundo
Esto es un heredoc
EOF
```
Por convención se utiliza el delimitador EOF (End of File), este nos ayuda a marcar donde empieza y donde termina el bloque de texto.

Aquí tenemos un ejemplo de como podemos utilizar los heredocs para crear código html.
```bash
cat << EOF > pagina.html
<!DOCTYPE html>
<html lang="es">
<head>
	<meta charset="UTF-8">
	<title>Mi Pagina</title>
</head>
<body>
	<h1>Hola Mundo</h1>
	<p>Esta pagina fue generada con un heredoc</p>
</body>
</html>
EOF
```

Sabiendo esto podemos usar los heredocs para crear apps web que nos muestren el estado de nuestro computador.
```bash
#!/bin/bash
disk_usage=$(df -h | awk 'NR==4 {print $5}')
cat << EOF > pagina.html
<!DOCTYPE html>
<html lang="es">
<head>
	<meta charset="UTF-8">
	<title>Mi Pagina</title>
</head>
<body>
	<h1>Hola Mundo</h1>
	<p>El uso de disco es $disk_usage</p>
</body>
</html>
EOF
```

### Ejercicio con heredocs
Un script llamado **server_report.sh** que se encarga de generar un archivo llamado **server_report.html**.
Esta pagina HTML debe contener la siguiente información real del computador.
1. Nombre del servidor
2. Fecha y hora
3. Tiempo encendido
4. Uso de disco
5. Memoria RAM
6. Servicios.
```bash
#!/bin/bash
servicios=("nginx" "docker" "ssh" "cron") 

generate_html(){
cat << EOF > index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>server report</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <div>
            <span>Server name</span>
            <p>$1</p>
        </div>
        <div>
            <span>Tiempo encendido</span>
            <p>$2</p>
        </div>
        <div>
            <span>Fecha y hora</span>
            <p>$3</p>
        </div>
    </header>
    <main>
        <section>
            <div>
                <span>Uso de disco</span>
                <p>$4</p>
            </div>
            <div>
                <span>Memoria RAM</span>
                <p>$5</p>
            </div>
        </section>
        <section>
            $(
                for servicio in "${servicios[@]}"
                do
                    if [[ $(systemctl is-active $servicio) != "active" ]]; then
                        echo "
                        <div>
                            <header>
                                <figure style='background-color: red;'></figure>
                                <span>Inactivo</span>
                            </header>
                            <p>$servicio</p>
                        </div>
                        "
                    else
                        echo "
                        <div>
                            <header>
                                <figure></figure>
                                <span>Activo</span>
                            </header>
                            <p>$servicio</p>
                        </div>
                        "
                    fi
                done
            )
        </section>
    </main>
</body>
</html>
EOF
}

generate_css(){
cat << EOF > styles.css
@import url('https://fonts.googleapis.com/css2?family=Intel+One+Mono:ital,wght@0,300..700;1,300..700&display=swap');
/* Mobile first */
*{
    background-color: #110F0F;
}

body{
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.inactive{
    background-color: red;
}

header{
    display: grid;
    grid-template-columns: repeat(2,1fr);
    grid-template-areas:
        "header header"
        "footer1 footer2"
    ;
    gap: 10px;
}
header div{
    background-color: #1C1B1B;
    display: flex;
    flex-direction: column;
    padding: 10px;
    border-radius: 10px;
}

header div:nth-child(1){
    grid-area: header;
}

header div:nth-child(2){
    grid-area: footer1;
}

header div:nth-child(3){
    grid-area: footer2;
}

header div span{
    color: white;
    font-weight: bold;
    background: none;
    font-size: 12px;
}
header div p{
    color: #98DB2B;
    font-family: "Intel One Mono", monospace;
    font-size: 30px;
    background: none;
    font-weight: bold;
    margin: 0;
}

/* Seccion main */
main{
    display: flex;
    flex-direction: column;
    gap: 10px;
}

main section:nth-child(1){
    display: flex;
    flex-direction: column;
    gap: 10px;
}

main section:nth-child(1) div{
    background-color: #1C1B1B;
    padding: 10px;
    border-radius: 10px;
}

main section:nth-child(1) div span{
    color: white;
    background: none;
    font-size: 12px;
    font-weight: bolder;
}

main section:nth-child(1) div  p{
    color: #98DB2B;
    font-family: "Intel One Mono", monospace;
    margin: 0;
    font-size: 100px;
    background: none;
    text-align: center;
    font-weight: bold;
}

main section:nth-child(2){
    display: grid;
    grid-template-columns: repeat(2,1fr);
    grid-template-rows: repeat(2,1fr);
    gap: 10px;
}

main section:nth-child(2) div{
    background-color: #1C1B1B;
    padding: 10px;
    display: flex;
    flex-direction: column;
    gap: 10px;
    border-radius: 10px;
}

main section:nth-child(2) div header{
    background: none;
    width: 50%;
    align-self: center;
    display: flex;
    justify-content: center;
    align-items: center;
}

main section:nth-child(2) div header figure{
    width: 15px;
    height: 15px;
    background-color: #98DB2B;
    margin: 0;
    border-radius: 100%;
}
main section:nth-child(2) div header span{
    background: none;
    font-size: 15px;
    color: white;
}
main section:nth-child(2) div p{
    color: #98DB2B;
    font-family: "Intel One Mono", monospace;
    margin: 0;
    background: none;
    font-size: 30px;
    text-align: center;
    font-weight: bold;
}


@media(min-width:768px){
    header{
        grid-template-columns: repeat(3,1fr);
        grid-template-areas: none;
    }
    header div:nth-child(1),
    header div:nth-child(2),
    header div:nth-child(3){
        grid-area: auto;
    }

    main section:nth-child(1){
        display: flex;
        flex-direction: row;
    }
    main section:nth-child(1) div{
        width: 100%;
    }
    main section:nth-child(2){
        display: flex;
        flex-direction: column;
    }
    main section:nth-child(2) div{
        display: flex;
        flex-direction: row-reverse;
        justify-content: space-between;
    }
    main section:nth-child(2) div header{
        width: auto;
    }
}
EOF
}

host=$(hostname)
up_time=$(uptime -p | awk '{ print $2 "h " $4"m"}')
hour=$(date | grep -Eo "\b[0-9]{2}:[0-9]{2}\b")
disk_usage=$(df -h | awk 'NR==4 { print $5 }')
ram=$(free -h | awk 'NR==2 { print $2 }')

generate_html $host "$up_time" $hour $disk_usage $ram
generate_css
```

### Notas Relacionadas
[[Ciclos for en bash]]
[[Subshells]]
[[Bash Scripting]]
