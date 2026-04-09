# Línea de comandos

Una **línea de comandos** o **CLI** (_Command Line Interface_) es una interfaz de texto que permite interactuar con el sistema operativo sin utilizar interfaces gráficas **GUI** (_Graphic User Interface_).

## Conceptos básicos

Existen 3 conceptos que suelen confundirse o usarse como sinónimos cuando se habla respecto a este tema, los cuales son la **terminal**, la **shell** y la **línea de comandos**.

### Terminal / Emulador de terminal

Es un programa que abre la ventana de línea de comandos. Actualmente los programas que se utilizan son en realidad **emuladores de terminal**, aunque se le siga refiriendo como terminal.

Aunque los sistemas operativos traen un emulador de terminal por defecto, se puede utilizar otro.

Sirve como la "presentación". Su función principal es capturar la entrada del teclado y enviarla a la shell, además de renderizar el texto que retorna esta misma.

Los emuladores modernos no muestran solo texto, sino que muchas veces gestionan aceleración por GPU para renderizado, permitiendo tener programas en terminal que pueden mostrar imágenes (por ejemplo, [yazi](https://yazi-rs.github.io/), explorador de archivos sobre terminal), soporte de ligaduras de fuentes, protocolos de imágenes y gestión de múltiples ventanas o paneles.

#### Ejemplos de emulador de terminal

- [Windows Terminal](https://github.com/microsoft/terminal) (Windows)
- [iTerm2](https://iterm2.com/) (MacOS)
- [Kitty](https://sw.kovidgoyal.net/kitty) (Linux / MacOS)
- [Alacritty](https://alacritty.org/) (Linux / MacOS / Windows)

### Shell

Es el intérprete que procesa y ejecuta los comandos, retornando la salida. Es el "cerebro" de la operación. Funciona como un bucle infinito conocido como **REPL** (Read-Eval-Print-Loop):

- **Read**: Lee lo que el usuario escribe.
- **Eval**: Evalúa y busca si es un comando interno o un programa instalado en el sistema (usando la variable `$PATH`).
- **Print**: Imprime el resultado en pantalla.
- **Loop**: Vuelve a esperar otra instrucción.

La shell también es un lenguaje de programación en sí misma, por lo que se pueden crear _scripts_ para automatizar tareas repetitivas o complejas, manejar variables de entorno y controlar el flujo de procesos.

#### Ejemplos de shell

- [Bash](https://www.gnu.org/software/bash/)
- [Zsh](https://www.zsh.org/)
- [PowerShell](https://microsoft.com/PowerShell)
- [Fish](https://fishshell.com/)
- [Nushell](https://www.nushell.sh/)

### Línea de comandos (CLI)

Es el espacio en el cual se escriben las instrucciones. Es la interfaz de interacción, y a diferencia de una GUI en donde el usuario está limitado a botones y menús diseñados por un programador, la CLI da un control granular sobre el sistema operativo.

Se basa en **unir programas pequeños**. En vez de que un programa muy grande haga todo, se utiliza la línea de comandos para encadenar distintos programas pequeños especializados en una sola cosa, obteniendo mejores resultados que una interfaz gráfica.

> Detalle: Los comandos, son programas en sí, por lo que cuando se ejecuta algún comando como por ejemplo `ls` o `cd`, se está ejecutando un programa. Así mismo, cuando se le pasan _flags_ y/o argumentos, estos mismos son tomados por dicho programa para generar un comportamiento diferente.

## Estructura de un comando

Mayormente, los comandos siguen la siguiente sintaxis:

$$
comando + [opciones] + [argumentos]
$$

Por ejemplo, con el siguiente comando:

```bash
ls -l /home/usuario
```

- `ls`: Es el comando base, que lista el contenido del directorio.
- `-l`: Es la opción (comunmente dicho _flag_) que modifica el comportamiento. En este caso pide la lista en un formato largo.
- `/home/usuario`: Es el argumento dado, el cual es el lugar en el que quiero listar.

## Comandos básicos

### Navegación de archivos

| Comando (bash)       | Comando (CMD / PowerShell)               | Descripción                                   |
| -------------------- | ---------------------------------------- | --------------------------------------------- |
| `pwd`                | `cd` (sin argumentos)                    | Muestra la ruta del directori actual.         |
| `ls`                 | `dir`                                    | Lista los archivos y carpetas del directorio. |
| `cd <directorio>`    | `cd <directorio>`                        | Cambia el directorio.                         |
| `mkdir <directorio>` | `mkdir <directorio>` o `md <directorio>` | Crea un nuevo directorio.                     |

> En PowerShell, muchos comandos Unix-like como `ls` o `cd` funcionan ya que son "alias" internos, aunque el contenido real de Windows sea otro.

### Gestión de archivos

| Comando (bash)          | Comando (CMD / PowerShell)                                  | Descripción                                            |
| ----------------------- | ----------------------------------------------------------- | ------------------------------------------------------ |
| `touch <nombre>`        | `type nul > <nombre>` (CMD) o `ni <nombre>` (PowerShell)    | Crea un archivo vacío.                                 |
| `cp <origen> <destino>` | `copy <origen> <destino>`                                   | Copia archivos o carpetas.                             |
| `mv <origen> <destino>` | `move <origen> <destino>`                                   | Mueve o renombra archivos.                             |
| `rm <archivo>`          | `del <archivo>`                                             | Elimina un archivo.                                    |
| `rm -rf <carpeta>`      | `rmdir /s <carpeta>` (CMD) o `rmdir <carpeta>` (Powershell) | Elimina una carpeta y su contenido de forma recursiva. |

> A tener en cuenta: Los comandos de eliminación, no mueven los archivos a una papelera de reciclaje como los programas de gestión de archivos normales.

### Visualización y edición

| Comando (bash)   | Comando (CMD / PowerShell) | Descripción                                                                                   |
| ---------------- | -------------------------- | --------------------------------------------------------------------------------------------- |
| `cat <archivo>`  | `type <archivo>`           | Muestra el contenido de una archivo en la terminal.                                           |
| `less <archivo>` | `more <archivo>`           | Permite leer un archivo largo moviéndose con las flechas.                                     |
| `nano` / `vim`   | `notepad`                  | Ejecuta un programa de edición de texto. Si agregás el nombre de un archivo de texto lo abre. |

### Permisos y superusuario (Unix like)

| Comando (bash) | Comando (CMD / PowerShell) | Descripción                                                        |
| -------------- | -------------------------- | ------------------------------------------------------------------ |
| `sudo`         | `runas`                    | Ejecuta un comando con permisos de administrador (_SuperUser Do_). |
| `chmod`        | `icacls`                   | Cambia los permisos de un archivo (lectura, escritura, ejecución). |

> A tener en cuenta:
>
> - No es recomendable ejecutar comandos DESCONOCIDOS con permisos de administrador.
> - Si querés buscar un comando que usaste antes, podés presionar `ctrl + R` y escribir una parte del comando que te acuerdes.
> - En Windows recientemente se añadió `sudo` como comando en versiones más nuevas de Windows 11.

## Tuberías y redirección

La línea de comandos permite conectar comandos mediante tuberías o _pipes_.

- `>`: Redirige la salida a un archivo sobreescribiendo lo anterior.
- `>>`: Agrega la salida al final de un archivo sin sobreescribir lo anterior.
- `|`: Pasa la salida de un comando como entrada para el siguiente.

## Personalización

Así como la terminal por defecto se puede ver como un bloque negro con muchas palabras que al principio no parecen tener sentido, esta misma se puede personalizar completamente.

Existen frameworks que permiten aumentar las funcionalidades de una shell, como lo son [oh-my-zsh](https://ohmyz.sh/) para zsh u [oh-my-bash](https://ohmybash.nntoan.com/) para bash.

También se le pueden aplicar temas al prompt, para ver el estado de git, nivel de batería, hora, y más cosas, dependiendo del programa que se instale.

> El prompt, es el indicador visual que indica que la shell está lista para ejecutar comandos.

Así mismo, los emuladores de terminal más modernos permiten muchas configuraciones como transparencias, cambio de fuentes, y demás.

Se pueden aplicar alias (atajos personalizados) para ciertos comandos que utilizamos seguido y no siempre nos acordamos, o por simple comodidad.

## Un poco más de contexto

```{iframe} https://www.youtube.com/embed/1YxHXBsVNGQ
---
width: 100%
---
```

---

### Actividad práctica: Estructura de un proyecto

```{important} Importante
Es una buena práctica NO usar espacios al nombrar las carpetas o directorios, ya que al trabajar con la terminal, agregar un espacio actúa como un separador de argumentos; si un nombre tiene espacios, la shell va a interpretar que son dos elementos distintos. Se recomienda usar guión medio (`-`) o guión bajo (`_`) según el contexto o la convención del proyecto.
```

Imaginá que empezaste el cuatrimestre y necesitás estructurar tu espacio de trabajo para la materia. El objetivo es crear la estructura necesaria para que, cuando abras el IDE, puedas importar la carpeta y que reconozca todo automáticamente sin problemas.

#### Paso 1: Navegación y Creación

Primero, vas a crear la jerarquía de carpetas. En **Git Bash**, ejecutá estos comandos uno por uno:

```bash
# Ir a Documentos (o donde guardes tus proyectos).
cd ~/Documentos

# Crear la ruta completa del proyecto.
# Se usa el flag '-p' para crear carpetas intermedias si no existen.
mkdir -p eclipse-workspace/algoritmos_y_programacion_i/src

# Entrar a la carpeta de código fuente.
cd eclipse-workspace/algoritmos_y_programacion_i/src
```

#### Paso 2: Creación y edición de código

Ahora creá el punto de entrada del programa.

1. **Crear el archivo:**

   ```bash
   touch App.java
   ```

2. **Editarlo:**

   Abrí el archivo con el editor que prefieras desde la terminal (podés usar `nano App.java` para editar el archivo desde la terminal con el programa ejecutado).

3. **Pegar el código:**

   ```java
   public class App {
       public static void main(String[] args) {
           System.out.println("Hello, World!");
       }
   }
   ```

La estructura te debería quedar de esta forma:

```txt
|-Documentos/
  |-eclipse-workspace/
    |-algoritmos_y_programacion_i/
      |-src/
        |-App.java
```

#### Paso 3: Verificación y ejecución

Antes de pasar al entorno gráfico, verificá que esté todo bien.

- **Ver el contenido:** Asegurate de que no haya errores de sintaxis.

  ```bash
  cat App.java
  ```

- **Comprobar Java:** Verificá que el compilador esté disponible.

  ```bash
  java --version
  ```

- **Correr el programa:** Ejecutá el archivo directamente.

  ```bash
  java App.java
  ```

### Próximos pasos: De la Terminal al IDE

Ahora que ya tenés la "base" creada por consola, vas a poder usar tu IDE para abrir el proyecto y trabajar desde ahí con futuros ejercicios.
