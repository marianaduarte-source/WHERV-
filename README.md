<img width="2016" height="703" alt="image" src="https://github.com/user-attachments/assets/91b857ba-7af1-4e6d-8329-2bb98a15599e" />

**GRADIO:**
Gradio es una librería de código cuyo propósito es facilitar el desarrollo del frontend de prototipos, modelos de IA y aplicaciones. Esta actúa como una Interfaz Gráfica de Usuario (GUI) que se coloca directamente sobre el código de Python. En otras palabras, Gradio se encarga de “embellecer” el código con componentes interactivos, facilitando así el empleo del programa sin la necesidad de tener un conocimiento amplio de programación ni usar tanto la terminal. 
**LIBRERIAS COMPLEMENTARIAS**
-	GOOGLE-GENAI: Es la librería oficial de Google empleada para conectar el proyecto con Gemini 2.5 Flash y generar los itinerarios. 
-	REQUESTS: Se emplea para conectarse con servidores externos mediante protocolos HTTP. Se ha utilizado para obtener los datos de las tasas de cambio de un URL. 
-	PYTHON-DOTENV: Permite cargar variables desde un archivo “.env” para proteger credenciales. En el proyecto, se utilizó para proteger el API Key de Google genai.

**CASO DE USO:** Aunque a todos nos agrade viajar, a nadie le gusta el tedioso proceso de armar el itinerario de viaje. Los usuarios deben investigar qué actividades hacer, si estos se alinean con sus gustos particulares, condiciones en las que se viaja, integrantes, etc. No hay manera alguna en la que es posible hacer esto sin navegar por decenas de sitios en la web. Por ello, se pretenderá emplear Gradio para generar una aplicación web interactiva que optimice dicho proceso.  
**FUNCIONES**
1.	gr.Blocks(): Permite al programador controlar el diseño de la página. Delimita el espacio digital donde se van a renderizar, agrupar y conectar todos los componentes lógicos.
2.	gr.Row() y gr.Column(): Componentes de diseño espacial, acomodando los datos en columnas y filas. 
3.	gr.Textbox():  Empleado para recibir y mostrar palabras. 
4.	gr.Dropdown(): Es una lista que contiene opciones fijas, lo cual evita los errores ortográficos cuando el usuario ingresa los datos. 
5.	gr.Button(): Botón interactivo que reacciona cuando el usuario hace clic en él, iniciando así el programa. 
6.	gr.Markdown(): renderiza texto y ecuaciones en LaTex. En esta ocasión fue usado para añadir los títulos, subtítulos y divisiones. 
7.	gr.Slider(): barra interactiva que permite al usuario deslizar su cursor en ella para seleccionar sus datos. 
8.	gr.CheckboxGroup(): Casillas de selección múltiple.
9.	gr.Radio(): Botones de selección de opción única. 
10.	gr.Gallery(): Componente que renderiza una cuadrícula de imágenes.
11.	gr.HTML(): Bloque de código que permite agregar etiquetas iframes (páginas web dentro de otras) en la interfaz.
web dentro de otras) en la interfaz.

**FUNCIONES DEL BACKEND**
-	**generar_itinerario:** Empleando 8 variables y limpiando las entradas de texto (.strip()), define el contenido de campos dentro de un prompt con restricciones de formato que, con el empleo de Gemini, devuelve un itinerario. 
-	**posible_presupuesto:** Hace una proyección de fondos multiplicando el precio diario por los días y el número de personas. También calcula un 15% de contingencia y devuelve el total con dicha cifra agregada. 
-	**viabilidad_financiera:** Evalúa el presupuesto del viaje en dólares y se conecta con un bloque try-except a una API externa para convertir la cifra en diferentes monedas con la tasa de cambio actual. En dado caso que la conexión falle, este usará tasas fijas. 
-	**actualizar_mapa:** Toma el destino ingresado en la caja de texto, limpia los caracteres que no son compatibles y devuelve un iframe que muestra el mapa del lugar. 
-	**imagenes:** Formatea el destino del viaje y genera 3 URL de imágenes dinámicas utilizando (loremflickr) basados en etiquetas (skyline, monument, hotel).

**IMPORTANTE**
**VIRTUAL ENVIRONMENT:** Para ejecutar adecuadamente el proyecto, es necesario configurar un entorno virtual antes de correr la aplicación. 
Un entorno virtual es una herramienta que crea un espacio aislado dentro de la computadora, evitando que las librerías necesarias para la ejecución del programa entren en conflicto con otros paquetes instalados. También mantiene un sistema operativo limpio de instalaciones innecesarias y que estas se preserven dentro de la carpeta del proyecto. 
Si no es activado, la aplicación web no funcionará. 
**Links de apoyo para instalación de virtual environment:** 
-	https://youtu.be/nBpxdq9-O08?si=qyZQuGC4hltUAEU8
-	https://gradio.app/main/guides/installing-gradio-in-a-virtual-environment

**ENLACE:** Cuando se corre el programa, la terminal proporcionará dos URL, cualquiera de los dos permitirá el uso del sitio. Sin embargo, es importante mencionar que el segundo es el que permite compartirlo con otros. También es necesario saber que los enlaces no se actualizan y si se realizan cambios en el código, estos no serán reflejados en el frontend. Por ello, es necesario volver a correr el código, copiar el nuevo enlace y pegarlo en el buscador.  

**POSIBLES PROBLEMAS PARA ENFRENTAR**
**“ModuleNotFoundError: No module named ‘dotenv’ (o ‘gradio’)**
Ocurre cuando se intenta ejecutar el programa sin usar el entorno virtual creado anteriormente o se intenta correr con el Python global de la computadora. Por ello, Python no es capaz de usar los paquetes o librerías que fueron instaladas. 
Es necesario asegurarse que el entorno esté activado desde la terminal o haber creado la terminal como tal. 
**1.	Para crear la terminal**
python3 -m venv gradio-env #”gradio-env” es el nombre del entorno, es posible cambiarle el nombre. 
**2.	Para activar el entorno**
Mac: source /gradio-env/bin/activate
Windows: .\gradio-env\Scripts\activate
Para saber si el entorno ha sido activado, debería aparecer un paréntesis en la terminal con el nombre del entorno (gradio-env).

**CONFIGURACION API KEY**
Para poder emplear Gemini en el programa, es necesario crear un API Key. Por motivos de seguridad, este no se incluye en el código. Por ello, es necesario realizar lo siguiente: 
1.	Crear un documento nombrado “.env” (es exactamente como debe ser nombrado) donde esta estará resguardada.
2.	Una vez abierto el archivo, reemplaza el texto entre comillas por tu llave: 
GEMINI_API_KEY="TU_CADENA_DE_API_KEY_AQUÍ"
3.	Guarda el archivo
Es debido a esto que se ha utilizado la librería python-dotenv y el módulo nativo os, pues estos son los que permiten gestionar los archivos ocultos del sistema e integrar la llave de forma segura.
