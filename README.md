# PetCARE
Application for caring pets

### Resumen
Hoy en día, cada vez son más las familias que optan por adoptar animales de compañía, generando una creciente demanda de servicios especializados orientados al bienestar animal. Esta tendencia ha impulsado la digitalización de dichos servicios para optimizar la salud y calidad de vida tanto de los animales como de sus cuidadores. Sin embargo, los animales requieren atención continua para mitigar problemas derivados de factores ambientales y conductuales, por ello presentamos PetCare, una aplicación para la gestión integral de mascotas.
PetCare asiste a los propietarios en el seguimiento del bienestar de sus animales y fomenta la concienciación sobre los factores de riesgo que pueden afectarles. La plataforma integra funcionalidades para mejorar la interacción con servicios veterinarios, de adiestramiento, estética y cuidado complementario, incrementando la eficiencia y trazabilidad de la atención prestada, además de ofrecer un espacio digital para gestionar actividades, consultas e historiales clínicos.
Con este TFG se busca crear una aplicación innovadora que permita gestionar el estado de las mascotas y promover la interacción social para facilitar la contratación de servicios tanto primarios como complementarios. En definitiva, PetCare aspira a ser una plataforma integral que combine tecnología, comunidad y bienestar, poniendo la salud animal al alcance de todos.

### Abstract
Nowadays, more and more families are choosing to adopt pets, generating a growing demand for specialized services focused on animal welfare. This trend has driven the digitalization of such services to optimize the health and quality of life of both animals and their caregivers. However, animals require continuous attention to mitigate problems arising from environmental and behavioral factors, which is why we present PetCare, an application for the comprehensive management of pets.
PetCare assists owners in monitoring their animals' wellbeing and raises awareness about the risk factors that may affect them. The platform integrates functionalities to improve interaction with veterinary, training, grooming and complementary care services, increasing the efficiency and traceability of the care provided, while also offering a digital space to manage activities, consultations and clinical records.
This final degree project aims to create an innovative application that allows users to manage their pets' condition and promote social interaction to facilitate the hiring of both primary and complementary services. In short, PetCare aspires to be a comprehensive platform that combines technology, community and wellbeing, putting animal health within everyone's reach.


## Manual del desarrollador
Este apéndice recoge todos los pasos necesarios para instalar las dependencias del proyecto, configurar el entorno de desarrollo y ejecutar la aplicación PetCare desde cero. El objetivo es que cualquier persona interesada en estudiar o extender el sistema pueda hacerlo sin necesidad de conocimientos previos sobre el entorno. Cabe mencionar que estas instrucciones están pensadas para ser ejecutadas en un entorno Windows, utilizando la terminal PowerShell.
Pasos previos a la ejecución
En este apartado se detallan todos los programas y herramientas que deben estar instalados en el sistema, así como los pasos que hay que seguir, en el orden indicado, para dejar el entorno completamente preparado antes de arrancar la aplicación.
1.	Instalar Git para poder clonar el repositorio y ejecutar los comandos de control de versiones. Se puede descargar desde el siguiente enlace: https://git-scm.com/
2.	Instalar Node.js, que incluye el gestor de paquetes npm necesario para instalar las dependencias del proyecto. Se puede descargar desde: https://nodejs.org/es
3.	Instalar XAMPP, que proporciona el servidor de la base de datos MySQL/MariaDB utilizado por la aplicación. Xampp puede descargarse desde: https://www.apachefriends.org/. Una vez instalado, abrir el Panel de Control de XAMPP e iniciar el módulo MySQL.  El módulo Apache no es necesario para ejecutar la aplicación, pero sí para acceder a phpMyAdmin y así importar la base de datos, por lo que se recomienda su activación.
4.	Clonar el repositorio desde GitHub, ejecutando el siguiente comando en PowerShell:
git clone https://github.com/TFG-2025-26/PetCARE.git 
5.	Acceder al directorio del proyecto:
cd PetCARE
6.	Instalar todas las dependencias del proyecto con npm:
npm install
7.	Crear el fichero de configuración .env en la raíz del proyecto. Este fichero debe contener las variables de entorno necesarias para el correcto funcionamiento de la aplicación. A continuación, se muestra la estructura que debe tener, rellenando los campos indicados:
SESSION_SECRET=tu_clave_secreta_de_sesion
DB_NAME=petcare
PORT=3000
En el campo SESSION_SECRET debe establecerse una cadena de texto larga y aleatoria, que se utilizará para firmar las cookies de la sesión.  Los campos DB_NAME y PORT son opcionales y toman los valores petcare y 3000 respectivamente en caso de no ser especificados.
8.	Importar el esquema de la base de datos. Para ello es necesario tener iniciado el módulo MySQL en XAMPP y acceder a phpMyAdmin a través del navegador en la dirección  http://localhost/phpmyadmin. Una vez dentro, seguir los pasos que se describen a continuación:
a.	Hacer click en la pestaña “Bases de datos” y crear una nueva base de datos con el nombre petcare, seleccionando la codificación utf8mb4_general_ci.
b.	Seleccionar la base de datos petcare recién creada en el panel lateral izquierdo.
c.	Hacer click en la pestaña “Importar” de la barra superior.
d.	Seleccionar el fichero petcareDB.sql que se encuentra en la raíz del proyecto.
e.	Hacer click en “Importar” para ejecutar el script SQL y crear todas las tablas con sus datos iniciales.
Una vez importado el fichero petcareDB.sql, la base de datos quedará configurada con todas las tablas necesarias para el funcionamiento de la aplicación. El único dato inicial incluido en el script es una cuenta de administrador creada por defecto con las siguientes credenciales:
•	Nombre de usuario: admin
•	Contraseña: Admin1234!
Se recomienda modificar la contraseña de esta cuenta tras el primer acceso.
Una vez completados todos estos pasos, el entorno queda listo y se puede proceder con la ejecución de la aplicación.
Ejecución habitual de la aplicación
Antes de arrancar el servidor de la aplicación, es imprescindible asegurarse de que el módulo MySQL de XAMPP está en ejecución, ya que la aplicación establece la conexión con la base de datos en el momento del arranque. Una vez verificado esto, se puede lanzar la aplicación de dos maneras distintas en función del entorno que se desee utilizar.
Para ejecutar la aplicación en modo desarrollo, que recarga el servidor automáticamente ante cualquier cambio en el código gracias a la herramienta nodemon, se debe ejecutar el siguiente comando:
	npm run dev
Para ejecutar la aplicación en modo producción, sin el mecanismo de recarga automática, el comando a utilizar es el siguiente:
	npm start
En ambos casos, una vez arrancado el servidor, la aplicación quedará accesible desde el navegador en la dirección http://localhost:3000, o en el puerto que se haya configurado en la variable de entorno PORT del fichero .env.
Ejecución de las pruebas
El proyecto cuenta con dos tipos de pruebas que pueden ejecutarse de forma independiente: las pruebas unitarias, que no requieren ninguna base de datos activa, y las pruebas de integración, que sí necesitan conexión con la base de datos. A continuación, se detalla cómo ejecutar cada una de ellas.
1.	Para ejecutar las pruebas unitarias, basta con tener el proyecto instalado correctamente. No es necesario que XAMPP esté en ejecución. El comando a utilizar es el siguiente:
npm test
2.	Para ejecutar las pruebas de integración, es necesario que el módulo MySQL de XAMPP esté activo. Además, estas pruebas utilizan una base de datos de pruebas separada denominada petcare_test para no alterar los datos de la aplicación principal. Dicha base de datos debe crearse previamente en phpMyAdmin siguiendo el mismo procedimiento descrito en el apartado anterior, importando el mismo fichero petcareDB.sql pero seleccionando petcare_test como destino. Una vez creada, el comando para lanzar las pruebas de integración es:
npm run test:db
Estructura de directorios del proyecto
En este apartado se describe la estructura general del proyecto, explicando el propósito de cada fichero y directorio que lo compone, con el objetivo de facilitar la navegación por el código y la comprensión del sistema. Los ficheros y directorios presentes en la raíz del sistema son los siguientes:
●	app.js: fichero principal de la aplicación. Es el punto de entrada del servidor, donde se inicializan Express, los middlewares globales, el motor de plantillas EJS, las rutas, el servidor HTTP y la instancia de Socket.IO para el chat en tiempo real.
●	db.js: módulo encargado de crear y exportar el pool de conexiones a la base de datos MySQL. Al utilizar un único pool compartido en toda la aplicación se optimiza el uso de conexiones y se evita la sobrecarga de abrir una conexión nueva en cada petición.
●	petcareDB.sql: script SQL que contiene el esquema completo de la base de datos, incluyendo la definición de todas las tablas, relaciones y datos iniciales necesarios para el funcionamiento de la aplicación.
●	package.json: fichero de configuración del proyecto Node.js. Contiene el nombre, la versión, los scripts disponibles (start, dev, test, test:db) y la lista de dependencias tanto de producción como de desarrollo.
●	package-lock.json: fichero generado automáticamente por npm al instalar las dependencias. Registra la versión de cada paquete instalado.
●	jest.config.js: configuración del framework de pruebas Jest para las pruebas unitarias. Define el entorno de ejecución, los ficheros de setup y los patrones de búsqueda de test, excluyendo explícitamente las pruebas de integración.
●	jest.config.db.js: configuración alternativa de Jest exclusiva para las pruebas de integración. Establece la variable de entorno DB_NAME=petcare_test antes de cargar cualquier módulo, de modo que la aplicación utilice la base de datos de pruebas en lugar de la principal.
●	jest.env.setup.js: fichero de setup que se ejecuta antes que cualquier módulo durante las pruebas de integración, estableciendo la variable de entorno DB_NAME=petcare_test.
●	jest.setup.js: fichero de setup común a todos los tipos de prueba. Se encarga de suprimir la salida de console.error durante la ejecución de los tests para mantener la salida de la terminal más limpia.
●	.env: fichero de variables de entorno, no incluido en el repositorio por razones de seguridad. Debe crearse manualmente siguiendo las instrucciones del apartado E.1.
A continuación, se describe el contenido de cada directorio del proyecto:
routes/
Este directorio contiene los routers de Express, que definen los endpoints HTTP de la aplicación y los asocian a los controladores correspondientes. Cada fichero agrupa las rutas relacionadas con un módulo funcional concreto de la aplicación:
●	authRouter.js: rutas relacionadas con la autenticación, como el registro, inicio y cierre de sesión.
●	userRouter.js: rutas para la gestión del perfil de usuario, incluyendo la visualización y edición de datos personales, tanto para usuarios normales como para empresas
●	petRouter.js: rutas para la gestión de mascotas, que cubren el registro, edición, eliminación y consulta del perfil de cada animal, así como el seguimiento de su historial médico.
●	servicesRouter.js: rutas relacionadas con los servicios ofrecidos en la aplicación, como la publicación de anuncios, la gestión de citas y la comunicación entre usuarios.
●	contentRouter.js: rutas para la gestión de contenido de la comunidad, incluyendo los foros y los artículos.
●	adminRouter.js: rutas del panel de administración, accesibles únicamente para usuarios con rol de administrador. Permiten gestionar usuarios, moderar contenido y revisar reportes.
●	_tests_/: subdirectorio que contiene los ficheros de las pruebas de integración
controllers/
Este directorio contiene los controladores de la aplicación, que encapsulan la lógica de negocio asociada a cada módulo. Los controladores reciben las peticiones provenientes de los routers, interactúan con la base de datos a través del pool definido en db.js y devuelven la respuesta correspondiente:
●	authController.js: lógica de registro, inicio y cierre de sesión, incluyendo el hash de contraseñas con bcrypt y la gestión de la sesión.
●	userController.js: lógica de consulta y actualización del perfil de usuario y empresa, así como la subida de imágenes de perfil.
●	petController.js: lógica de gestión de mascotas, incluyendo el historial de vacunas, tratamientos y patologías.
●	servicesController.js: lógica de publicación y consulta de anuncios, gestión de citas entre usuarios y empresas, y búsqueda de empresas por tipo de servicio.
●	contentController.js: lógica de creación, edición y eliminación de foros y artículos, así como la gestión de los comentarios en los foros.
●	adminController.js: lógica del panel de administración para la moderación de usuarios, contenido y resolución de reportes.
●	chatController.js: lógica de gestión de conversaciones y mensajes del sistema de chat.
●	citasController.js: lógica de gestión de citas del usuario. Incluye la lógica para consultar las reservas activas del usuario, así como para gestionar la cancelación de citas.
●	_tests_/: subdirectorio que contiene las pruebas unitarias de cada controlador, con un fichero test independiente por cada uno de ellos.
middlewares/
Este directorio contiene los middlewares de la aplicación, que se ejecutan antes de que la petición llegue al controlador correspondiente:
●	authMiddleware.js: contiene los diferentes middlewares de autenticación y autorización de la aplicación.
handlers/
Este directorio contiene los manejadores de errores de la aplicación:
●	httpErrors.js: define las funciones auxiliares para la creación y el manejo centralizado de errores HTTP. Incluye la función createHttpError, que genera objetos de error con código de estado y la selección del mensaje de error por defecto según el código de estado.
sockets/
Este directorio contiene la lógica del sistema de mensajería en tiempo real de la aplicación:
●	chatSocket.js: módulo que gestiona todos los eventos de Socket.IO relacionados con el chat. Controla la conexión y desconexión de usuarios, el envío y recepción de mensajes en tiempo real, la gestión de conversaciones y la notificación de nuevos mensajes no leídos.
views/
Este directorio contiene todas las plantillas EJS que definen la interfaz de usuario de la aplicación. EJS permite incrustar código JavaScripts en el HTML para generar páginas dinámicas en el servidor. Las plantillas cubren todas las vistas de la aplicación, desde las páginas de autenticación hasta los perfiles de usuario y mascotas, el sistema de foros, el chat, etc. Además, contiene un subdirectorio plantillas/ con los componentes parciales reutilizables a lo largo de toda la aplicación, como el navbar, el footer y los distintos modales de confirmación, error y reporte.
public/
Este directorio contiene todos los recursos estáticos de la aplicación, es decir, los ficheros que el servidor envía directamente al navegador sin procesamiento adicional. Se organiza en tres subdirectorios:
●	css/: contiene el fichero styles.css con todos los estilos de la aplicación.
●	js/: contiene los scripts JavaScript del lado del cliente, con un fichero por cada vista que requiere lógica en el navegador.
●	images/: contiene las imágenes estáticas de la aplicación, como las imágenes por defecto para perfiles y mascotas.


