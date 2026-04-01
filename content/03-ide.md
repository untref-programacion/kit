# IDE

Un _entorno de desarrollo integrado_ (Integrated Development Environment en inglés) es un programa que agrupa todas las herramientas necesarias para el ciclo de vida del desarrollo de un software en una sola interfaz. A diferencia de un editor simple, un IDE "entiende" el proyecto de forma semántica y no solo como archivos de texto.

Se suele optimizar para un lenguaje de programación o ecosistema en específico (como **Java**, **.NET** o **aplicaciones móviles**).

## Componentes fundamentales

Para considerar a un programa como IDE, debe tener ciertas herramientas mínimo:

- **Editor de código fuente:** Con autocompletado inteligente ([IntelliSense](https://code.visualstudio.com/docs/editing/intellisense)) y análisis semántico.
- **Herramientas de automatización de compilación:** Gestión de procesos de _build_, en el caso de Java pudiendo ser [Maven](https://maven.apache.org/) o [Gradle](https://gradle.org/).
- **Depurador (Debugger):** Herramientas para inspeccionar la memoria, las variables y el flujo de ejecución en tiempo real.
- **Integración de control de versiones:** Manejo de [Git](https://git-scm.com/) / [GitHub](https://github.com/) / [GitLab](https://about.gitlab.com/) nativo.
- **Gestor de dependencias:** Interfaz para administrar librerías externas.
- **Terminal:** Consola integrada para ejecución y lectura de logs.
- **Explorador de Bases de Datos:** Capacidad de conexión, consulta y edición de esquemas SQL/NoSQL.

## Ejemplos de IDEs

- **Java:** [Eclipse](https://eclipseide.org/) / [IntelliJ IDEA](https://www.jetbrains.com/idea/)
- **C# / .NET:** [Visual Studio](https://visualstudio.microsoft.com/)
- **Desarrollo web:** [WebStorm](https://www.jetbrains.com/webstorm/)
- **Go:** [GoLand](https://www.jetbrains.com/go/)
- **Mobile:** [Android Studio](https://developer.android.com/studio)

## IDE vs Editor de Texto

Un editor de texto es un **programa más ligero**, hecho principalmente para la **edición de archivos de texto plano**. Suele ser más versátil y rápido que un IDE, que está centrado en **proyectos completos**.

Un editor de texto puede extender su funcionalidad mediante _plugins_ o _LSPs_, los cuales permiten imitar el comportamiento de un IDE.

### Ventajas del IDE

Un IDE tiene capacidades que un editor de texto no trae por defecto, y que difícilmente iguale con extensiones:

- **Refactorización:** Cambiar el nombre de una clase o método en todo el proyecto sin romper referencias, ya que el IDE comprende el código.
- **Generación de [Boilerplate](https://elblogdelprogramador.com/posts/boilerplate-la-importancia-del-estilo-de-codigo-en-programacion/#gsc.tab=0):** Creación automática de _constructores_, _getters_, _setters_ y métodos comunes.
- **Análisis de errores:** Detección de posibles _bugs_, variables no usadas, posibles _nulls_, antes de la compilación del código.
- **Navegación inteligente:** Capacidad de saltar a la definición de una función/método/clase incluso si está en una librería ya compilada.
- **Pruebas unitarias integradas:** Ejecución y reporte visual de tests con cobertura de código.
- **Profiling:** Herramientas que miden el uso de CPU y memoria de la aplicación en ejecución.

### Ejemplos de editores de texto

- [Visual Studio Code](https://code.visualstudio.com/).
- [Vim](https://www.vim.org/).
- [Sublime Text](https://www.sublimetext.com/).

### Un poco más de contexto

```{iframe} https://www.youtube.com/embed/_J-ybg4j52s
---
width: 100%
---
```

---

## ¿Cuándo elegir un IDE?

La elección puede depender de varios factores, como estos:

- **Complejidad del proyecto:** Proyectos grandes, empresariales, los cuales suelen tener muchas clases, podrían requerir un IDE.
- **Hardware:** Un IDE, al tener muchas herramientas, es más pesado, por lo que en equipos limitados puede ser un problema.
- **Curva de aprendizaje:** Los IDEs (aunque también puede suceder en editores de texto) tienen menús y muchas opciones las cuales pueden ser confusas en un principio.
- **Lenguaje:** En lenguajes de programación como Java o C#, el uso de un IDE suele ser lo estándar. En otros lenguajes como Go, con editores de texto se suele cubrir las necesidades básicas.
