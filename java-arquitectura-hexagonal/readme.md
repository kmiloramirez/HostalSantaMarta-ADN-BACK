#### Jenkinsfile-Sonar

Este bloque contiene los archivos de configuración necesarios para un ambiente de integración continua.

Los archivos de configuración que se encuentran en este bloque son:

#### Jenkinsfile
Dentro de este archivo se encuentra un Job (Tipo Pipeline). Este job permite definir el ciclo de vida completo de la aplicación (descargar código, compilar, test, publicar, desplegar, etc.) mediante código. De esta forma, resulta mucho más sencillo replicar los diferentes pasos con distintas aplicaciones y gestionar mejor los cambios en cada paso. Se puede visualizar en un solo job cada paso del ciclo de vida, lo que anteriormente se configuraba con varios jobs de estilo libre encadenados y visibles en un Build Pipeline.

#### Jenkinsfile (Pipeline Declarativo)
Un pipeline declarativo es aquel que podemos crear, editar o configurar mediante una estructura definida que nos ayuda a entender y predecir los pasos del pipeline.

#### Sintaxis básica de un Pipeline Declarativo

- **Pipeline {}**: Identificamos dónde empieza y termina el pipeline así como los pasos que tiene.
- **Agent**: Especificamos cuando se ejecuta el pipeline. Uno de los comandos más utilizados es any, para ejecutar el pipeline siempre y cuando haya un ejecutor libre en Jenkins.
- **Stages**: Bloque donde se definen una serie de estados a realizar dentro del pipeline. 
- **Stage**: Bloque que define una serie de tareas realizadas dentro del pipeline, por ejemplo: Build. test, deploy, etc. Podemos utilizar varios plugins en Jenkins para visualizar el estado o el progreso de estos estados
- **Steps**: Son todos los pasos a realizar dentro de un stage. Podemos definir uno o varios pasos.
- **Step**:  Es una tarea simple dentro del pipeline. Fundamentalmente es un paso donde se le dice a Jenkins qué hacer en un momento específico o paso del proceso. Por ejemplo, para ejecutar un comando en shell podemos tener un paso en el que tengamos la línea sh “ls” para mostrar el listado de ficheros de una carpeta. 

![enter image description here] https://drive.google.com/file/d/1fsO6rVax0tAWmbTil4fRY24bpw3e8GsM/view?usp=sharing

#### Requerimientos: 

 - Proyecto Gradle (Como mínimo la estructura del Proyecto)
 - Repositorio en GitHub con el contenido del Proyecto
 - Correo electrónico para reportar un fallo de jenkins
 - Los archivos Jenkinsfile y sonar-project.properties deben ser guardados en la raíz del proyecto


#### sonar-project

sonar-project.properties contiene las propiedades de análisis. Con este archivo se simplifica la línea que ejecuta del SonarScanner dado que la instrucción no tendrá “quemadas” las propiedades y al estar en la raíz del proyecto hace que no sea necesario especificar la ruta y nombre de éste. Siendo así, el sonar scanner “leerá” el archivo .properties y posteriormente mandará el análisis al SonarQube Server configurado e identificado en Jenkins con ​withSonarQubeEnv(​'Sonar'​).
 
Hash de git relacionado: 44dd4ccd