# AFIP Person project for Spring Boot

_alta, baja, modificaci贸n y b煤squeda de una persona en base de datos de AFIP_

## Comenzando 馃殌

_Estas instrucciones te permitir谩n obtener una copia del proyecto en funcionamiento en tu m谩quina local para prop贸sitos de desarrollo y pruebas._

Mira **Deployment** para conocer como desplegar el proyecto.


### Pre-requisitos 馃搵

_https://eclipse.c3sl.ufpr.br/oomph/epp/2022-09/R/eclipse-inst-jre-win64.exe_
_https://download.oracle.com/java/18/archive/jdk-18.0.2.1_windows-x64_bin.msi_
_https://dlcdn.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.zip_
_https://cdn.mysql.com//Downloads/MySQLInstaller/mysql-installer-community-8.0.31.0.msi_
_https://objects.githubusercontent.com/github-production-release-asset-2e65be/56899284/46a05b7f-9609-4e38-bfdf-810544c8da0d?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20221116%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20221116T134452Z&X-Amz-Expires=300&X-Amz-Signature=540f2bd64d3ecfeb24b5615fc10533712d890a648ad3f8ae5243f13ec6d70af0&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=56899284&response-content-disposition=attachment%3B%20filename%3DInsomnia.Core-2022.6.0.exe&response-content-type=application%2Foctet-stream_

```

### Instalaci贸n 馃敡

_Registrar variable de entorno JAVA_HOME para t煤 JDK_

_Procedimiento_
1. En el panel de control:...
2. Pulse el bot贸n Variables de entorno.
3. Pulse el bot贸n Nuevo en la secci贸n de variables del sistema.
4. A帽ada el nombre de variable JAVA_HOME y especifique una v铆a de acceso al directorio JDK.
5. Guarde los cambios.

```
Ejemplo: C:\Program Files (x86)\Java\jdk1.8.0_351
```
_Registrar variable Path_

_Procedimiento_
1. Pulse el bot贸n Editar.
2. Pulse el bot贸n Nuevo.
3. A帽ada la especificaci贸n v铆a de acceso %JAVA_HOME%\bin.
4. Pulse el bot贸n Aceptar.
5. Guarde los cambios.

```
Ejemplo: %JAVA_HOME%\bin
```

_Registrar variable de entorno MAVEN_HOME para t煤 MAVEN_

_Procedimiento_
1. En el panel de control:...
2. Pulse el bot贸n Variables de entorno.
3. Pulse el bot贸n Nuevo en la secci贸n de variables del sistema.
4. A帽ada el nombre de variable JAVA_HOME y especifique una v铆a de acceso al directorio MAVEN.
5. Guarde los cambios.

```
Ejemplo: C:\Program Files (x86)\apache-maven-3.8.6
```
_Registrar variable Path_

_Procedimiento_
1. Pulse el bot贸n Editar.
2. Pulse el bot贸n Nuevo.
3. A帽ada la especificaci贸n v铆a de acceso %MAVEN_HOME%\bin.
4. Pulse el bot贸n Aceptar.
5. Guarde los cambios.

```
Ejemplo: %MAVEN_HOME%\bin
```

_para corroborar instalaci贸n y registro de variable correcta de JDK, presionar combinaci贸n de teclas: tecla Windows + r, y escribir en la ventana de ejecuci贸n lo siguiente: cmd, dentro de la consola escribir lo siguiente: java -version seguido de tecla enter_
_para corroborar instalaci贸n y registro de variable correcta de MAVEN, presionar combinaci贸n de teclas: tecla Windows + r, y escribir en la ventana de ejecuci贸n lo siguiente: cmd, dentro de la consola escribir lo siguiente: mvn -v seguido de tecla enter_

## Ejecutando las pruebas 鈿欙笍

_ALTA de usuario_

### Analice las pruebas end-to-end 馃敥

_Aqu铆 vamos a proceder a probar el alta de un usuario en AFIP_

```
para la siguiente ruta: http://localhost:8080/person vamos a elegir el m茅todo POST en Insomnia enviando el siguiente JSON

{
	"name" : "Ricardo Jose",
	"lastName" : "Traversaro",
	"cuil" : "20297524527",
	"dni" : "29752452",
	"email" : "telteodorologan@gmail.com"
}
```

### Y las pruebas de estilo de codificaci贸n 鈱笍

_nos deber铆a devolver algo similar a lo siguiente:_

{
	"id": 1,
	"email": "telteodorologan@gmail.com",
	"dni": "29752452",
	"cuil": "20297524527",
	"name": "Ricardo Jose",
	"lastName": "Traversaro",
	"birthday": null
}

```
como ver谩n en el campo id s茅 nos asigno el valor 1, eso quiere decir que ya tenemos nuestro primer registro almacenado en la base de datos

_MODIFICACI脫N de usuario_

### Analice las pruebas end-to-end 馃敥

_Aqu铆 vamos a proceder a probar la modificaci贸n de un usuario en AFIP_

```
para la siguiente ruta: http://localhost:8080/person vamos a elegir el m茅todo POST en Insomnia enviando el siguiente JSON

{
	"id" : "1",
	"name" : "Ricardo Jose",
	"lastName" : "Traversaro",
	"cuil" : "20297524527",
	"dni" : "29752452",
	"email" : "deltalogan@yahoo.com.ar"
}
```

### Y las pruebas de estilo de codificaci贸n 鈱笍

_nos deber铆a devolver algo similar a lo siguiente:_

{
	"id": 1,
	"email": "deltalogan@yahoo.com.ar",
	"dni": "29752452",
	"cuil": "20297524527",
	"name": "Ricardo Jose",
	"lastName": "Traversaro",
	"birthday": null
}

```
como ver谩n el campo id es el mismo (1), pero est谩 vez s茅 actualiz贸 la casilla de correo electr贸nico con el nuevo valor en la base de datos

_BAJA de usuario_

### Analice las pruebas end-to-end 馃敥

_Aqu铆 vamos a proceder a probar la baja de un usuario en AFIP_

```
para la siguiente ruta: http://localhost:8080/person/1 vamos a elegir el m茅todo DELETE en Insomnia

```

### Y las pruebas de estilo de codificaci贸n 鈱笍

_nos deber铆a devolver algo similar a lo siguiente:_

Se elimin贸 el usuario con id1

```
como ver谩n, utilizando el m茅todo DELETE en el Insomina desde la siguiente ruta: http://localhost:8080/person/1 (teniendo en cuenta que despu茅s de lo que sigue de person/ es el n煤mero de id de la persona), podremos eliminar un usuario en la base de datos

_B脷SQUEDA de usuario_

### Analice las pruebas end-to-end 馃敥

_Aqu铆 vamos a proceder a probar la b煤squeda de un usuario en AFIP_

```
para la siguiente ruta: http://localhost:8080/person/query?cuil=20297524527 vamos a elegir el m茅todo GET en Insomnia

```

### Y las pruebas de estilo de codificaci贸n 鈱笍

_nos deber铆a devolver algo similar a lo siguiente:_

[
	{
		"id": 5,
		"email": "deltalogan@yahoo.com.ar",
		"dni": "29752452",
		"cuil": "20297524527",
		"name": "Ricardo Jose",
		"lastName": "Traversaro",
		"birthday": null
	}
]

```
como ver谩n, utilizando el m茅todo GET en el Insomina desde la siguiente ruta: http://localhost:8080/person/query?cuil=20297524527 (teniendo en cuenta que despu茅s de lo que sigue de person/query? es el atributo que s茅 gener贸 previamente como servicio de b煤squeda seguido del s铆mbolo = y el valor que s茅 quiera buscar)
```

## Despliegue 馃摝

_recordar desde el IDE de Eclipse dirigirse a Help 鈫? Eclipse Marketplace鈥? 鈫? en el cuadro de b煤squeda escribir lo siguiente: Spring Tools 4_

## Construido con 馃洜锔?

_Herramientas que s茅 utilizaron para est茅 proyecto_

* [Maven](https://maven.apache.org/) - Manejador de dependencias
* [MySql](https://www.mysql.com/) - Motor de base de datos
* [Insomnia](https://insomnia.rest/) - Aplicaci贸n que nos permite realizar pruebas API
* [Eclipse](https://www.eclipse.org/) - IDE - Entorno de desarrollo integrado
* [Java](https://www.java.com/es/) - JVM

## Versionado 馃搶

Usamos [SemVer](http://semver.org/) para el versionado. Para todas las versiones disponibles, mira los [tags en este repositorio](https://github.com/tu/proyecto/tags).

## Autores 鉁掞笍

_Autores_

* **Ricardo Jos茅 Traversaro** - *Trabajo Inicial* [mailto:telteodorologan@gmail.com]
