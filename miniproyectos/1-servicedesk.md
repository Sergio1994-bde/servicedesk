# Miniproyectos · ServiceDesk (etapas 0 a 10)

Cada etapa de la [hoja de ruta](../HOJA_DE_RUTA.md) está partida aquí en tareas pequeñas.
Cada una se puede terminar en una o dos sentadas y deja algo que se ve funcionando.

**Cómo leer cada miniproyecto**

- **Qué vas a hacer:** el resultado, en una frase.
- **Pasos:** el orden recomendado.
- **Está bien cuando:** la comprobación que te dice que has terminado.
- **Palabra nueva:** el nombre técnico de lo que acabas de usar, para que puedas buscarlo.

Al terminar cada miniproyecto, guarda tu trabajo con un commit que diga qué has hecho.

---

## Etapa 0 · Preparar el ordenador

### 0.1 · Ver tu página en el navegador

**Qué vas a hacer:** abrir `index.html` en el navegador y que se actualice solo cada vez que guardes.

**Pasos:**
1. Abre la carpeta `servicedesk` en VS Code.
2. Instala la extensión *Live Server* (icono de los cuadraditos en la barra izquierda).
3. Clic derecho sobre `index.html` → *Open with Live Server*.
4. Cambia el texto del título, guarda y mira el navegador.

**Está bien cuando:** el cambio aparece en el navegador sin que tengas que recargar.

### 0.2 · Arreglar tres despistes

**Qué vas a hacer:** corregir tres errores pequeños que ya hay en el proyecto, guardando cada arreglo por separado.

**Pasos:**
1. El archivo `ticket-detalil.html` está mal escrito. En la terminal: `git mv ticket-detalil.html ticket-detalle.html`. Guarda el cambio con un commit.
2. En `index.html`, la pestaña del navegador dice "ServiceDesck". Corrígelo. Otro commit.
3. Cambia el nombre de la rama principal: `git branch -m master main`.

**Está bien cuando:** `git log --oneline` muestra un commit por cada arreglo y `git status` dice que no queda nada pendiente.

**Palabra nueva:** *commit* = una foto del proyecto en un momento dado, con una nota que explica qué cambió.

### 0.3 · Guardar una copia en internet

**Qué vas a hacer:** subir el proyecto a GitHub para tener copia de seguridad y poder enseñarlo.

**Pasos:**
1. Crea una cuenta en GitHub.
2. Crea un repositorio nuevo llamado `servicedesk`, **vacío** (sin README ni nada marcado).
3. GitHub te mostrará dos o tres órdenes para "subir un repositorio que ya existe". Cópialas en tu terminal.

**Está bien cuando:** entras en la página del repositorio en GitHub y ves tus archivos y tus commits.

**Palabra nueva:** *push* = enviar tus commits a GitHub.

### 0.4 · La carta de presentación

**Qué vas a hacer:** escribir en `README.md` qué es este proyecto.

**Pasos:**
1. Escribe tres cosas: qué es ServiceDesk, en qué punto está y cómo abrirlo.
2. Haz commit y súbelo.

**Está bien cuando:** el texto aparece en la portada del repositorio en GitHub.

---

## Etapa 1 · El esqueleto de las páginas (HTML)

En esta etapa las páginas quedarán feas. Es normal: ahora solo importa que el contenido esté bien ordenado.

### 1.1 · La puerta de entrada

**Qué vas a hacer:** una página con un formulario para iniciar sesión.

**Pasos:**
1. En `index.html`, añade un formulario con dos campos: correo y contraseña.
2. Pon encima de cada campo un texto que diga qué hay que escribir.
3. Añade un botón "Entrar". De momento, que al pulsarlo lleve a `tickets.html`.

**Está bien cuando:** al hacer clic sobre el texto "Correo", el cursor salta al campo de correo.

**Palabra nueva:** *label* = el texto unido a un campo. Sin él, quien usa un lector de pantalla no sabe qué escribir.

### 1.2 · El menú que se repite

**Qué vas a hacer:** un menú con los mismos enlaces en todas las páginas.

**Pasos:**
1. Crea un menú con enlaces a "Incidencias", "Nueva incidencia" y "Salir".
2. Cópialo en `tickets.html`, `ticket-detalle.html` y `ticket-form.html`.

**Está bien cuando:** puedes llegar a cualquier página desde cualquier otra sin tocar la barra de direcciones.

### 1.3 · La lista de incidencias

**Qué vas a hacer:** una tabla con cinco o seis incidencias inventadas.

**Pasos:**
1. En `tickets.html`, crea una tabla con columnas: título, prioridad, estado y responsable.
2. Inventa incidencias creíbles ("No puedo acceder al correo", "La impresora de la planta 2 no imprime"…).
3. Haz que el título de cada una sea un enlace a `ticket-detalle.html`.

**Está bien cuando:** la tabla tiene una fila de encabezados y al pulsar un título se abre la ficha.

### 1.4 · La ficha de una incidencia

**Qué vas a hacer:** una página que muestra todos los datos de una sola incidencia.

**Pasos:**
1. En `ticket-detalle.html`, muestra título, descripción larga, prioridad, estado, responsable y fecha.
2. Añade dos enlaces: "Editar" y "Volver a la lista".

**Está bien cuando:** alguien que no conoce el proyecto entiende de un vistazo cuál es el problema y quién lo lleva.

### 1.5 · El formulario para dar de alta

**Qué vas a hacer:** la página donde se crea una incidencia nueva.

**Pasos:**
1. En `ticket-form.html`, añade: título (una línea), descripción (varias líneas), prioridad (lista desplegable con alta, media, baja) y responsable.
2. Añade los botones "Guardar" y "Cancelar".

**Está bien cuando:** puedes rellenar todo el formulario usando solo la tecla Tab para pasar de un campo a otro.

### 1.6 · Pasar la revisión

**Qué vas a hacer:** comprobar que las cuatro páginas están bien escritas.

**Pasos:**
1. Entra en [validator.w3.org](https://validator.w3.org/) y pega el contenido de cada página.
2. Corrige los errores que salgan, uno a uno.

**Está bien cuando:** las cuatro páginas pasan sin errores.

---

## Etapa 2 · El aspecto (CSS)

### 2.1 · La paleta

**Qué vas a hacer:** elegir colores y tipo de letra, y apuntarlos en un único sitio.

**Pasos:**
1. Elige un color principal, uno de fondo, uno de texto y uno para errores.
2. Guárdalos al principio de `css/styles.css` con un nombre cada uno.
3. Aplica el fondo, el color de texto y la letra a toda la página.

**Está bien cuando:** cambias el color principal en una sola línea y cambia en todas las páginas.

**Palabra nueva:** *variable CSS* = un valor con nombre que se reutiliza.

### 2.2 · La cabecera en una línea

**Qué vas a hacer:** colocar el nombre de la aplicación a la izquierda y el menú a la derecha.

**Está bien cuando:** la cabecera se ve igual en las cuatro páginas y los enlaces no están pegados entre sí.

**Palabra nueva:** *Flexbox* = la forma de colocar elementos en fila o en columna y repartir el espacio.

### 2.3 · Una tabla que se lee bien

**Qué vas a hacer:** dar aire a la tabla de incidencias.

**Pasos:**
1. Añade espacio dentro de cada celda y una línea fina entre filas.
2. Destaca la fila de encabezados.
3. Haz que la fila cambie de color al pasar el ratón por encima.

**Está bien cuando:** puedes seguir una fila con la vista de izquierda a derecha sin perderte.

### 2.4 · Formularios cómodos

**Qué vas a hacer:** ordenar los campos de los formularios y marcar bien cuál está activo.

**Pasos:**
1. Pon cada texto encima de su campo y deja espacio entre un campo y el siguiente.
2. Haz que el campo donde está el cursor tenga un borde bien visible.
3. Diferencia el botón principal ("Guardar") del secundario ("Cancelar").

**Está bien cuando:** al avanzar con Tab siempre sabes en qué campo estás.

### 2.5 · Etiquetas de color

**Qué vas a hacer:** que la prioridad y el estado se distingan de un vistazo.

**Pasos:**
1. Convierte "alta", "media" y "baja" en pequeñas etiquetas con fondo de color.
2. Haz lo mismo con los estados (abierta, en curso, resuelta).

**Está bien cuando:** se distinguen también en blanco y negro, porque cada etiqueta lleva su texto y no depende solo del color.

### 2.6 · Que quepa en el móvil

**Qué vas a hacer:** adaptar las páginas a pantallas estrechas.

**Pasos:**
1. Pulsa F12 en el navegador y activa la vista de móvil.
2. Revisa las cuatro páginas a 375 de ancho y apunta lo que se rompe.
3. Arréglalo: el menú puede pasar a ocupar dos líneas; la tabla puede esconder la columna menos importante.

**Está bien cuando:** en móvil no hay que desplazarse hacia los lados en ninguna página.

**Palabra nueva:** *media query* = una regla de estilo que solo se aplica a partir de cierto ancho de pantalla.

---

## Etapa 3 · Que la página reaccione (JavaScript)

Es la etapa más larga y la más importante. No tengas prisa.

### 3.1 · El primer botón que hace algo

**Qué vas a hacer:** comprobar que sabes conectar un programa a una página.

**Pasos:**
1. Crea `js/app.js` y enlázalo desde `tickets.html`.
2. Haz que escriba un mensaje en la consola del navegador (F12 → pestaña *Console*).
3. Añade un botón de prueba que, al pulsarlo, cambie un texto de la página. Luego bórralo.

**Está bien cuando:** ves tu mensaje en la consola y el texto cambia al pulsar.

### 3.2 · La lista sale de los datos

**Qué vas a hacer:** dejar de escribir las incidencias a mano en la página.

**Pasos:**
1. Crea `js/datos.js` con la lista de incidencias: cada una con su número, título, descripción, prioridad, estado y responsable.
2. Borra las filas de la tabla en `tickets.html` (deja solo los encabezados).
3. Escribe una función que recorra la lista y cree una fila por incidencia.

**Está bien cuando:** añades una incidencia en `datos.js`, guardas y aparece en la tabla sin tocar el HTML.

### 3.3 · El buscador

**Qué vas a hacer:** un cuadro de texto que filtra la lista mientras escribes.

**Está bien cuando:** al escribir "correo" solo quedan las incidencias con esa palabra en el título, escribas en mayúsculas o en minúsculas.

### 3.4 · Los filtros

**Qué vas a hacer:** dos desplegables para ver solo un estado o una prioridad.

**Está bien cuando:** buscador y filtros funcionan a la vez (por ejemplo: "impresora" + prioridad alta), y hay una opción "Todas" para quitar el filtro.

### 3.5 · Ordenar por columna

**Qué vas a hacer:** ordenar la lista al pulsar un encabezado.

**Pasos:**
1. Al pulsar "Título", ordena de la A a la Z. Al pulsar otra vez, de la Z a la A.
2. Haz lo mismo con prioridad, cuidando que "alta" quede antes que "media" y esta antes que "baja" (no por orden alfabético).
3. Marca con una flecha qué columna manda.

**Está bien cuando:** el orden se mantiene aunque después uses el buscador.

### 3.6 · El formulario avisa de los errores

**Qué vas a hacer:** impedir que se guarde una incidencia incompleta.

**Pasos:**
1. Al pulsar "Guardar", comprueba que el título y la descripción no están vacíos.
2. Si falta algo, muestra un mensaje **junto al campo** que falla, no una ventana emergente.
3. Si todo está bien, muestra "Incidencia guardada".

**Está bien cuando:** el mensaje de error desaparece al corregir el campo.

### 3.7 · Que no se pierda al recargar

**Qué vas a hacer:** conservar las incidencias nuevas aunque cierres el navegador.

**Pasos:**
1. Al guardar el formulario, añade la incidencia a la lista y guarda la lista en el navegador.
2. Al abrir `tickets.html`, lee primero lo guardado; si no hay nada, usa los datos de ejemplo.

**Está bien cuando:** creas una incidencia, cierras el navegador, lo abres y sigue en la lista.

**Palabra nueva:** *localStorage* = un pequeño almacén que cada navegador guarda para cada página web.

---

## Etapa 4 · Pedir los datos a otro sitio

### 4.1 · Los datos en su propio archivo

**Qué vas a hacer:** sacar las incidencias del programa y ponerlas en un archivo de datos aparte.

**Pasos:**
1. Crea `db.json` con las incidencias de ejemplo.
2. Haz que la página pida ese archivo al cargar, en lugar de leer `datos.js`.

**Está bien cuando:** la lista se ve igual que antes. Ojo: esto solo funciona abriendo la página con Live Server, no con doble clic sobre el archivo.

**Palabra nueva:** *fetch* = la orden para pedir datos a una dirección. La respuesta tarda un poco, y el programa tiene que saber esperar.

### 4.2 · "Cargando…"

**Qué vas a hacer:** mostrar un aviso mientras llegan los datos.

**Pasos:**
1. Muestra "Cargando incidencias…" antes de pedir los datos y quítalo cuando lleguen.
2. Para verlo, activa una conexión lenta: F12 → pestaña *Network* → desplegable de velocidad → *Slow 4G* (o similar).

**Está bien cuando:** con conexión lenta se ve el aviso y nunca una tabla vacía sin explicación.

### 4.3 · Cuando algo sale mal

**Qué vas a hacer:** dar un mensaje útil si los datos no llegan o no hay nada que mostrar.

**Pasos:**
1. Cambia a propósito el nombre del archivo en tu código para que falle. Muestra "No se han podido cargar las incidencias" y un botón "Reintentar".
2. Devuelve el nombre correcto.
3. Si la búsqueda no encuentra nada, muestra "No hay incidencias que coincidan".

**Está bien cuando:** en ningún caso la página se queda en blanco.

### 4.4 · Guardar esta versión para siempre

**Qué vas a hacer:** marcar este punto del proyecto antes de reescribirlo.

**Pasos:**
1. Comprueba que todo está guardado con commit.
2. Ejecuta `git tag v0-estatico` y después `git push --tags`.

**Está bien cuando:** en GitHub aparece la etiqueta `v0-estatico`.

---

## Etapa 5 · Herramientas nuevas (TypeScript)

### 5.1 · Montar el taller

**Qué vas a hacer:** instalar lo necesario y crear el proyecto nuevo.

**Pasos:**
1. Instala Node.js (la versión marcada como LTS) desde su página oficial.
2. Crea una rama nueva: `git switch -c react`.
3. Mueve los archivos de la versión anterior a una carpeta `version-estatica/`.
4. En la carpeta del proyecto, ejecuta `npm create vite@latest .` y elige *React* y *TypeScript*. Si pregunta qué hacer con los archivos que ya existen, elige conservarlos.
5. Ejecuta `npm install` y después `npm run dev`.

**Está bien cuando:** el navegador muestra la página de ejemplo en la dirección que indica la terminal.

**Palabra nueva:** *npm* = el programa que descarga las piezas hechas por otras personas que tu proyecto necesita.

### 5.2 · Describir cómo es una incidencia

**Qué vas a hacer:** escribir una "ficha modelo" que diga qué datos tiene una incidencia y qué valores se admiten.

**Pasos:**
1. Crea `src/tipos.ts`.
2. Define que la prioridad solo puede ser alta, media o baja; y el estado, abierta, en curso o resuelta.
3. Define la incidencia con todos sus campos.

**Está bien cuando:** escribes a propósito una prioridad "urgentísima" y el editor la subraya en rojo antes de ejecutar nada.

**Palabra nueva:** *tipo* = una descripción de qué forma deben tener los datos. El editor te avisa si no la cumples.

### 5.3 · Traer lo que ya sabías hacer

**Qué vas a hacer:** pasar al proyecto nuevo las funciones de buscar, filtrar y ordenar.

**Está bien cuando:** las tres funciones están en un archivo propio, no tienen avisos en rojo y dan el mismo resultado que en la versión anterior.

---

## Etapa 6 · Construir con piezas (React)

Antes de empezar, haz entero el tutorial de la sección *Learn* de la web de React.

### 6.1 · Tu primera pieza: la etiqueta

**Qué vas a hacer:** convertir la etiqueta de color en una pieza reutilizable.

**Pasos:**
1. Crea una pieza que reciba un estado ("abierta") y pinte la etiqueta con su color.
2. Úsala tres veces en la página, con tres estados distintos.

**Está bien cuando:** para pintar una etiqueta solo hace falta una línea.

**Palabra nueva:** *componente* = una pieza de la pantalla con su contenido y su comportamiento, que se puede usar muchas veces.

### 6.2 · La fila y la lista

**Qué vas a hacer:** montar la tabla de incidencias con piezas.

**Pasos:**
1. Crea la pieza "fila", que recibe una incidencia y la pinta.
2. Crea la pieza "lista", que recibe muchas incidencias y pinta una fila por cada una.
3. De momento, usa datos escritos en el propio programa.

**Está bien cuando:** la tabla se ve en pantalla y ninguna pieza ocupa más de una pantalla de código.

### 6.3 · El buscador y los filtros, otra vez

**Qué vas a hacer:** recuperar la búsqueda, los filtros y la ordenación.

**Está bien cuando:** funcionan igual que en la versión anterior, usando las funciones del miniproyecto 5.3.

**Palabra nueva:** *estado* = lo que la pantalla tiene que recordar (por ejemplo, lo que has escrito en el buscador). Cuando cambia, React vuelve a pintar lo necesario.

### 6.4 · Pasar de página

**Qué vas a hacer:** mostrar las incidencias de diez en diez.

**Pasos:**
1. Añade incidencias de ejemplo hasta tener al menos veinticinco.
2. Muestra solo diez, con botones "Anterior" y "Siguiente" y el texto "Página 1 de 3".

**Está bien cuando:** "Anterior" no se puede pulsar en la primera página, y al buscar algo vuelves a la página 1.

### 6.5 · Recuperar el aspecto

**Qué vas a hacer:** traer los estilos de la etapa 2.

**Está bien cuando:** la lista nueva se parece a la de la versión estática, también en móvil.

---

## Etapa 7 · Varias pantallas y un servidor de mentira

### 7.1 · Un servidor de mentira

**Qué vas a hacer:** poner en marcha un programa que se comporta como un servidor real, pero vive en tu ordenador.

**Pasos:**
1. Copia `db.json` al proyecto nuevo.
2. En otra terminal, ejecuta `npx json-server db.json`.
3. Abre en el navegador la dirección que te indica, terminada en `/tickets`.

**Está bien cuando:** ves la lista de incidencias como texto en el navegador.

**Palabra nueva:** *API* = el "mostrador" al que tu página pide y envía datos.

### 7.2 · Todas las peticiones en un mismo archivo

**Qué vas a hacer:** reunir en un solo sitio todo lo que habla con el servidor.

**Pasos:**
1. Crea `src/api/tickets.ts` con cuatro funciones: traer todas, traer una, crear y modificar.
2. Haz que la lista use la primera, con sus avisos de "cargando" y de error.

**Está bien cuando:** ninguna pantalla contiene la dirección del servidor; solo está en ese archivo.

### 7.3 · Cada pantalla, su dirección

**Qué vas a hacer:** que la aplicación tenga varias pantallas, cada una con su dirección.

**Pasos:**
1. Instala React Router.
2. Crea cinco direcciones: entrada, lista, ficha, nueva y editar. De momento, cada una muestra solo su nombre.
3. Convierte el menú en enlaces entre ellas.

**Está bien cuando:** los botones de atrás y adelante del navegador funcionan como esperas.

### 7.4 · La ficha, por su número

**Qué vas a hacer:** que la dirección `/tickets/3` muestre la incidencia número 3.

**Está bien cuando:** al pulsar una incidencia en la lista se abre su ficha, y si escribes a mano un número que no existe aparece "Esta incidencia no existe".

### 7.5 · Página perdida y entrada simulada

**Qué vas a hacer:** dos remates de navegación.

**Pasos:**
1. Crea una pantalla para direcciones que no existen, con un enlace para volver a la lista.
2. Haz que el formulario de entrada lleve a la lista al pulsar "Entrar", sin comprobar nada.
3. Escribe un comentario en el código que diga claramente que no es una protección real.

**Está bien cuando:** una dirección inventada muestra tu pantalla y no una en blanco.

---

## Etapa 8 · Crear y editar

### 8.1 · Dar de alta una incidencia

**Qué vas a hacer:** que el formulario guarde de verdad en el servidor de mentira.

**Está bien cuando:** rellenas el formulario, pulsas "Guardar", vuelves a la lista y la incidencia nueva está ahí; además aparece dentro de `db.json`.

### 8.2 · El mismo formulario, para editar

**Qué vas a hacer:** reutilizar el formulario para modificar una incidencia que ya existe.

**Pasos:**
1. Al entrar en "Editar", el formulario aparece ya relleno.
2. Al guardar, se modifica esa incidencia en lugar de crearse otra.

**Está bien cuando:** hay un solo formulario en el código y sirve para las dos cosas.

### 8.3 · Avisos y teclado

**Qué vas a hacer:** pulir el formulario.

**Pasos:**
1. Mensaje de error junto a cada campo; al fallar, el cursor va al primer campo con error.
2. Mientras se guarda, el botón dice "Guardando…" y no se puede pulsar dos veces.
3. Si el servidor falla, se avisa y **no se pierde lo escrito**.

**Está bien cuando:** creas y editas una incidencia sin tocar el ratón.

---

## Etapa 9 · Comprobar que funciona (y que sigue funcionando)

### 9.1 · La primera prueba automática

**Qué vas a hacer:** escribir un pequeño programa que comprueba otro programa.

**Pasos:**
1. Instala Vitest.
2. Escribe una prueba para la función de ordenar: le das tres incidencias desordenadas y compruebas que salen en orden.
3. Ejecuta `npm test`.

**Está bien cuando:** la prueba sale en verde, y si rompes la función a propósito sale en rojo.

### 9.2 · Probar las pantallas

**Qué vas a hacer:** pruebas que usan la pantalla como lo haría una persona.

**Pasos:**
1. Instala React Testing Library.
2. Prueba 1: la lista muestra las incidencias que recibe.
3. Prueba 2: al elegir un estado en el filtro, quedan menos filas.
4. Prueba 3: al enviar el formulario vacío aparecen los mensajes de error.
5. Prueba 4: al enviar un formulario correcto se envían los datos esperados.

**Está bien cuando:** las cuatro pruebas pasan sin necesidad de tener el servidor de mentira encendido.

### 9.3 · Revisión de accesibilidad

**Qué vas a hacer:** comprobar que la aplicación la puede usar todo el mundo.

**Pasos:**
1. F12 → pestaña *Lighthouse* → marca *Accessibility* → analiza cada pantalla.
2. Corrige los avisos (los más habituales: poco contraste, campos sin texto asociado).
3. Recorre toda la aplicación solo con el teclado.

**Está bien cuando:** no quedan avisos graves y puedes hacer el recorrido completo sin ratón.

---

## Etapa 10 · Enseñarlo al mundo

### 10.1 · Que funcione sin tu ordenador

**Qué vas a hacer:** preparar la demostración para que no dependa del servidor de mentira, que solo existe en tu equipo.

**Pasos:**
1. Elige una solución: lo más sencillo es que la versión publicada lea los datos de ejemplo de un archivo y guarde los cambios en el navegador (como en el miniproyecto 3.7).
2. Como en 7.2 pusiste todas las peticiones en un solo archivo, solo tendrás que cambiar ese.

**Está bien cuando:** apagas el servidor de mentira y la aplicación sigue funcionando en modo demostración.

### 10.2 · Publicar

**Qué vas a hacer:** conseguir una dirección pública.

**Pasos:**
1. Une la rama `react` con `main`.
2. Elige un servicio gratuito (GitHub Pages, Netlify o Vercel) y sigue su guía para proyectos de Vite.
3. Abre la dirección desde el móvil.

**Está bien cuando:** otra persona puede abrir el enlace y completar el recorrido lista → ficha → crear.

### 10.3 · El README definitivo

**Qué vas a hacer:** explicar el proyecto a quien llegue de nuevas.

**Pasos:**
1. Qué hace, con una captura de pantalla y el enlace a la demostración.
2. Cómo ponerlo en marcha en otro ordenador, paso a paso.
3. Con qué está hecho.
4. **Qué no hace:** la entrada es simulada y no protege nada; los datos se guardan solo en el navegador.

**Está bien cuando:** una persona sigue tus instrucciones en otro ordenador y lo arranca sin preguntarte.

---

## Después: tres mejoras opcionales

Solo cuando todo lo anterior esté terminado, y de una en una:

- **Mejora A · Datos más cómodos.** Sustituir tu forma de pedir datos por TanStack Query. Está bien cuando has borrado código y todo sigue funcionando.
- **Mejora B · Formularios más cómodos.** Sustituir tus comprobaciones manuales por React Hook Form y Zod.
- **Mejora C · Pruebas que se lanzan solas.** Configurar GitHub Actions para que ejecute las pruebas cada vez que subes cambios. Está bien cuando ves la marca verde junto a tu commit en GitHub.
