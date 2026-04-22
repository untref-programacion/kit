# Git: Control de versiones

[Git](https://git-scm.com/) es un sistema de **control de versiones** (**VSC** o _Version Control System_) distribuido, diseñado por [Linus Torvalds](https://github.com/torvalds), y que en la actualidad, es mantenido principalmente por [Junio Hamano](https://github.com/gitster). Su función principal es poder rastrear cambios en el código fuente, facilitando la colaboración y el retorno a estados anteriores del proyecto de forma eficiente.

Como todo comando, se utiliza de la forma:

$$
ejecutable + comando + [flag \ / \ opciones] + [argumentos]
$$

Por ejemplo:

```sh
git commit -m "este es un commit"
```

En este caso:

- Se ejecuta el programa `git`.
- Se utiliza el comando `commit`.
- Se utiliza el flag `-m` para indicar que lleva un mensaje (m de _message_).
- Se escribe el mensaje como string.

## Filosofía

La filosofía de Git se basa en varios pilares que lo diferencian de sistemas más antiguos como **SVN**:

### Sistema Distribuido

A diferencia de los sistemas centralizados, donde hay un único servidor con el historial, en Git, cada colaborador tiene una **copia local completa** del repositorio.

- **Seguridad**: Si el servidor principal falla o se corrompe, cualquier copia local de los desarrolladores puede usarse para restaurar el proyecto íntegramente.
- **Independencia**: Podés hacer commits, ver el historial y crear ramas sin conexión a internet. Solo necesitás red para sincronizar con otros.

### Snapshots en vez de Diferencias

Mientras que otros sistemas almacenan la información como una lista de cambios en los archivos (deltas), Git toma los datos como un conjunto de **instantáneas o snapshots**.

- Cada vez que hacés un commit, Git toma una "foto" del aspecto de todos tus archivos en ese momento y guarda una referencia a esa captura.
- Si un archivo no se modifica, Git no lo guarda nuevamente, sino que crea un enlace al archivo anterior idéntico que ya está almacenado.

### Integridad

Todo en Git se identifica por un algoritmo de hashing. Esto garantiza que sea imposible cambiar el contenido de un archivo o un mensaje de commit sin que Git se dé cuenta, porque el hash cambiaría. Esto hace que el historial sea **inmutable** y **rastreable**.

## Comandos básicos

Estos son los pilares para empezar con un repositorio local.

- `git init`: Inicializa un nuevo repositorio Git en el directorio actual en el que se está.
- `git status`: Muestra el estado actual del árbol de trabajo (archivos modificados, en staging, etc.).
- `git add <archivo>`: Agrega archivos al **Staging Area**. Se puede usar `git add .` para agregar todos los archivos.
- `git commit -m "mensaje de commit"`: Registra los cambios guardados en el Staging Area en el historial, con el mensaje.
- `git log`: Muestra el historial de commits realizados.
- `git diff`: Muestra qué cosas se cambiaron exactamente.

## Comandos más utilizados

Existen comandos que se van a utilizar en el día a día para trabajar con ramas y repositorios remotos.

- `git branch`: Lista, crea o elimina ramas.
- `git switch <rama>`: Cambia de la rama actual a la indicada.
- `git merge <rama>`: Fusiona la rama especificada en la rama en la que se está parado actualmente.
- `git remote add origin <url>`: Vincula el repositorio local con un servidor remoto.
- `git push origin <rama>`: Sube los commits locales al repositorio remoto.
- `git pull`: Descarga y fusiona los cambios del remoto en la rama actual.

## Comandos menos utilizados

Hay comandos que no son tan utilizados, pero que son muy útiles para situaciones específicas, o para corrección de errores.

- `git stash`: Guarda temporalmente los cambios no commiteados para limpiar el directorio de trabajo.
- `git pop`: Recupera los cambios guardados anteriormente con `stash`.
- `git reset --hard <commit>`: Revierte el estado del proyecto a un commit específico, borrando todo lo anterior.
- `git rebase`: Aplica los cambios de una rama sobre otra, manteniendo el historial lineal.
- `git cherry-pick <commit>`: Trae un commit específico de otra rama a la actual.

## Práctica

Si bien la mejor forma de aprender este tipo de cosas es con tiempo y práctica en proyectos reales (ya sean universitarios o de trabajo), se propone una pequeña actividad para empezar a familiarizarse con el flujo de trabajo.

### Preparación

1. Parate en la carpeta de un proyecto de código y ejecutá creá un repositorio nuevo.
2. Creá un archivo nuevo o modificá otro, agregalo al Staging Area y creá un commit para ese cambio.

### Ramificación

1. Creá una rama para un nuevo ejercicio o funcionalidad.
2. Cambiá a esa rama.
3. Hacé las modificaciones pertinentes.
4. Agregá al Staging Area y creá un commit.

### Fusión (_merge_)

1. Cambiá a la rama `main` nuevamente.
2. Hacé un merge de la rama creada antes a la rama principal.
3. Verificá que los cambios estén plasmados en los archivos y en el historial de commits.

## Buenas prácticas

Para mantener un repositorio sano y legible, más que nada en proyectos profesionales, y preferentemente en proyectos universitarios, existen diferentes prácticas que ayudan a este propósito:

- **Commits atómicos**: Un commit debe representar un cambio pequeño. Que en un commit hayan muchos cambios, y encima diferentes, es una mala señal.
- **Mensajes claros**: Usar el imperativo (por ejemplo, "Se agrega autenticación de usuario" en vez de "Agregué cosas"). Ni hablar de mensajes del estilo "ancodn" o "cosas".
- **No subir basura**: Utilizar siempre un archivo `.gitignore`, que sirve para que git ignore ciertos archivos y no los suba. Esto sirve para no subir binarios, carpetas innecesarias, archivos de configuración de IDEs, archivos compilados, o archivos con claves privadas.
- **Pull antes de Push**: Asegurarse siempre de tener la versión más reciente del repositorio remoto antes de subir los cambios, así evitar conflictos evitables. Incluso es bueno hacerlo antes de empezar a escribir código en el momento que se arranca una jornada.

## Otros

### Flujo de trabajo (_Workflow_)

Git opera mediante tres estados principales para gestionar el código:

1. **Working Directory**: El directorio físico donde se modifican los archivos.
2. **Staging Area (Index)**: El área donde se preparan los cambios que van a entrar en el próximo commit.
3. **Repository (`.git`)**: El lugar donde se almacenan permanentemente las capturas del historial.

### Gestión de ramas (_branches_)

Esta funcionalidad permite crear ramas (bifurcaciones) para desarrollar nuevas funcionalidades o corregir errores, sin afectar la línea principal de desarrollo.

Esto permite mantener una rama principal que se mantenga siempre estable.

- La rama principal suele llamarse `master`, o `main` en repositorios más actuales.
- Se recomienda el uso de ramas temporales para tareas específicas que se integran después a la rama principal una vez fueron testeadas y aprobadas.

### Conflictos

Existen situaciones de conflicto que ocurren cuando Git no puede decidir automáticamente qué cambios mantener al intentar fusionar dos ramas. Esto pasa generalmente cuando se modifican la **misma línea** del **mismo archivo** con contenido diferentes.

Cuando hay un conflicto, Git pausa el proceso de `merge` y marca los archivos afectados. Al abrirlos, se puede ver algo así:

```txt
<<<<<<< HEAD
Contenido en la rama donde estás parado (ej. main)
=======
Contenido que viene de la rama que querés mergear (ej. feature)
>>>>>>> feature-branch
```

#### ¿Cómo resolver esto?

1. **Editar**: Abrir el archivo y elegir con qué código quedarse (borrando las marcas `<<<<`, `====`, `>>>>`).
2. **Marcar como resuelto**: Ejecutar `git add <archivo-con-conflicto>`.
3. **Finalizar**: Ejecutar `git commit` para cerrar la fusión.

### Otros sistemas de control de versiones

Aunque Git es el más conocido o usado, existen otros programas que sirven para esto, algunos con filosofías diferentes.

Ejemplos:

- [Mercurial](https://www.mercurial-scm.org/)
- [Fossil](https://fossil-scm.org/home/doc/trunk/www/index.wiki)
- [Bazaar](https://documentation.help/Bazaar-help/introducing_bazaar.html)
- [Subversion](https://subversion.apache.org/)
- [Perforce Helix Core](https://www.perforce.com/products/helix-core)
- [Monotone](https://www.monotone.ca/)
- [Darcs](https://darcs.net/)

## Un poco más de información

```{iframe} https://www.youtube.com/embed/i-XD1bwqzPI
---
width: 100%
---
```
