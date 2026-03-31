# Variables de Entorno

Las variables de entorno son valores con nombre que se guardan en la terminal y a los que los programas pueden acceder mientras se ejecutan.

## Por qué es importante

Permiten configurar el comportamiento de programas sin modificar el código. Muchas herramientas las usan para cosas como idioma, rutas, credenciales o configuraciones.

Esto funciona porque cuando un programa se ejecuta, el sistema operativo le provee un conjunto de variables de entorno como parte de su contexto de ejecución. El programa puede leer esos valores durante su inicio o en tiempo de ejecución y decidir su comportamiento en base a ellos. Por ejemplo, puede cambiar el idioma en el que muestra mensajes, elegir dónde buscar archivos o activar o desactivar ciertas funcionalidades.

Esto funciona porque las variables de entorno actúan como una forma estándar y externa de pasar configuración, separando el código de los detalles del entorno en el que se ejecuta. De esta manera un mismo programa puede comportarse de forma diferente según cómo esté configurado, sin necesidad de ser modificado.

```{tip}
Mirá que estos temas sirven también para Windows, ahora que sabés que existen podés tratar de googlear: "cómo guardo una variable de entorno en windows".
```

## Un poco de contexto

```{iframe} https://www.youtube.com/embed/C8bH7d-4ga8
---
width: 100%
---
```

## Ejemplos (¡probalos!)

Todos los ejemplos requieren del uso de la terminal. Deberás abrir una terminal para trabajar con ellos.

- Ver todas las variables existentes:

```bash
env
```

- Imprimir una variable concreta:

```bash
echo $HOME
```

- Definir una variable para la sesión actual (temporal) y usarla:

```bash
export MI_VAR="hola mundo"
echo $MI_VAR
```

- Hacer una variable persistente (ejemplo para bash):

```bash
# Añadir al final de ~/.bashrc
echo 'export OTRA_VAR="valor persistente"' >> ~/.bashrc
# Cerrá la terminal y abrí otra
echo $OTRA_VAR
```

Con estos comandos se puede inspeccionar el entorno actual, probar valores y escoger si una variable debe ser temporal o persistente.

## Verificando lo aprendido

Realizá los siguientes ejercicios en tu terminal y tomá nota de lo que sucede.

1) Definir y leer

```bash
export PRUEBA="hola-prueba"
echo $PRUEBA
```

¿Qué devuelve `echo`? ¿Qué pasa si cerrás la terminal y abrís otra?

2) Leer una variable ya existente

```bash
echo $HOME
echo $PATH
```

¿Qué tipo de información contiene cada una?

3) Cómo afecta una variable a un comando

```bash
MI_VAR="valorTemporal" env | grep MI_VAR
```

¿El valor persiste después de ejecutar el comando? ¿Por qué?

4) Reconocer la sintaxis `$NOMBRE`

```bash
echo $MI_VAR
echo MI_VAR
```

Explicá la diferencia entre usar `$MI_VAR` y escribir `MI_VAR` sin el signo `$`. ¿En qué situaciones verías cada forma?

Opcional: Hacé persistente una variable y comprobá que se mantiene tras cerrar la terminal.

Pista: oʌᴉɥɔɹɐ unƃlɐ ɐ ɐlɹɐƃǝɹƃɐ sɐqǝp sɐzᴉnb
