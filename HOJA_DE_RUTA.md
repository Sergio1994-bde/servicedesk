# Hoja de ruta · ServiceDesk → BookingCore → OpsFlow

Ruta de desarrollo para una persona que empieza en desarrollo web. Se basa en el documento
*Portfolio de desarrollo web: tres proyectos, tres capacidades* (septiembre de 2026).

## Cómo usar este documento

- **Avanza en orden.** Cada etapa da por sabido lo de la anterior.
- **No pases de etapa hasta cumplir el apartado "Hecho cuando".** Es la única regla estricta.
- **Marca las casillas** (`- [x]`) y haz un commit cada vez que termines un cambio con sentido.
- **Las horas son orientativas.** No hay plazo universal: ajústalas a tus asignaturas y a tu tiempo real.
- **Una tecnología nueva por etapa.** Si en una etapa te ves aprendiendo dos cosas a la vez, párate y divide.

Cada etapa tiene cuatro partes: qué **aprendes**, qué **construyes**, cuándo está **hecha** y dónde **consultar**.

## Miniproyectos

Cada etapa está desglosada en tareas pequeñas, explicadas paso a paso y sin tecnicismos:

- [Miniproyectos de ServiceDesk](miniproyectos/1-servicedesk.md) (etapas 0 a 10)
- [Miniproyectos de BookingCore](miniproyectos/2-bookingcore.md) (etapas 11 a 17)
- [Miniproyectos de OpsFlow](miniproyectos/3-opsflow.md) (etapas 18 a 22)

Este documento es el mapa; esos tres son las instrucciones del día a día.

## Vista general

| Bloque | Etapas | Resultado | Esfuerzo orientativo |
|---|---|---|---|
| Preparación | 0 | Entorno listo y repositorio ordenado | 3–5 h |
| **1 · ServiceDesk** (frontend) | 1–10 | Aplicación React publicada con pruebas | 120–180 h |
| **2 · BookingCore** (backend) | 11–17 | API REST con PostgreSQL y pruebas de concurrencia | 120–180 h |
| **3 · OpsFlow** (full stack) | 18–22 | Interfaz + API + base de datos integradas | 100–160 h |

---

## Punto de partida (estado del repositorio hoy)

Ya existe un primer commit con `index.html` y varios archivos vacíos. Antes de seguir conviene arreglar esto:

- [x] Renombrar `ticket-detalil.html` → `ticket-detalle.html` (errata en el nombre). Usa `git mv` para que Git registre el cambio.
- [x] Corregir el `<title>` de `index.html`: pone "ServiceDesck".
- [x] La rama se llama `master`; GitHub usa `main` por defecto. Renómbrala con `git branch -m master main`.
- [ ] `README.md`, `css/styles.css` y tres páginas HTML están vacíos: se rellenan en las etapas 1 y 2.
- [ ] Node.js no está instalado en este equipo. No hace falta hasta la etapa 5.

---

## Etapa 0 · Entorno y Git (3–5 h)

**Aprendes:** a moverte por la terminal, y el ciclo básico de Git: modificar → `add` → `commit` → `push`.

**Construyes:**
- [ ] Instalar en VS Code las extensiones *Live Server* y *Prettier*.
- [x] Crear una cuenta de GitHub y un repositorio remoto vacío llamado `servicedesk`.
- [x] Conectar el repositorio local con el remoto y subir el primer commit.
- [x] Resolver los puntos del apartado anterior, **un commit por cada arreglo**.
- [x] Escribir tres líneas en `README.md`: qué es el proyecto, en qué estado está y cómo abrirlo.

**Hecho cuando:** ves tus commits en GitHub y sabes explicar qué hacen `git status`, `git add`, `git commit` y `git push`.

**Consulta:** MDN · *Aprender desarrollo web* (sección de Git y GitHub).

> **Repaso de los comandos de Git** (para releer antes de empezar la etapa 1):
> - **`git status`**: muestra qué archivos has cambiado desde el último commit, para saber qué está listo para guardar.
> - **`git add`**: elige qué cambios entran en el próximo commit, como meter cosas en una caja antes de cerrarla.
> - **`git commit`**: guarda esa caja como una foto del proyecto con una nota que explica qué contiene.
> - **`git push`**: envía esa foto a GitHub para tener una copia fuera de tu ordenador.
>
> Orden habitual: `git status` → `git add` → `git commit` → `git push`.

---

# Proyecto 1 · ServiceDesk (frontend)

Aplicación para gestionar incidencias informáticas. Objetivo final: recorrido **lista → detalle → creación/edición**
con datos de demostración, usable en móvil y con teclado, con pruebas y publicada.

### Etapa 1 · HTML: la estructura (10–15 h)

**Aprendes:** etiquetas semánticas (`header`, `nav`, `main`, `section`), listas, tablas, enlaces y formularios (`label`, `input`, `select`, `textarea`, `button`).

**Construyes** (sin CSS todavía, tiene que verse feo y entenderse igual):
- [ ] `index.html`: formulario de inicio de sesión (correo y contraseña).
- [ ] `tickets.html`: tabla con 5–6 incidencias inventadas (título, prioridad, estado, responsable).
- [ ] `ticket-detalle.html`: todos los datos de una incidencia.
- [ ] `ticket-form.html`: formulario con título, descripción, prioridad y responsable.
- [ ] Un menú de navegación igual en todas las páginas, con enlaces que funcionen.

**Hecho cuando:** puedes ir de una página a cualquier otra solo con enlaces, cada campo de formulario tiene su `<label>`, y el [validador del W3C](https://validator.w3.org/) no da errores.

**Consulta:** MDN · *Estructurando contenido con HTML*.

### Etapa 2 · CSS: el diseño (15–20 h)

**Aprendes:** selectores, modelo de caja, Flexbox, Grid, variables CSS y *media queries*.

**Construyes:**
- [ ] Variables de color, tipografía y espaciado en `:root`.
- [ ] Cabecera y menú con Flexbox.
- [ ] La tabla de incidencias legible; en móvil, que no obligue a desplazarse en horizontal.
- [ ] Formularios con campos alineados y estados `:focus` visibles.
- [ ] Etiquetas de color para prioridad y estado (que además lleven texto, no solo color).

**Hecho cuando:** las cuatro páginas se usan bien a 375 px y a 1280 px de ancho (pruébalo con las herramientas de desarrollo del navegador, tecla F12).

**Consulta:** MDN · *Fundamentos de estilo con CSS*.

### Etapa 3 · JavaScript: la interacción (25–35 h)

**Aprendes:** variables, funciones, arrays y objetos, `map`/`filter`/`sort`, el DOM y los eventos.

**Construyes:**
- [ ] Un archivo `js/datos.js` con un array de incidencias (dejas de escribirlas a mano en el HTML).
- [ ] Pintar la tabla de `tickets.html` a partir de ese array.
- [ ] Buscador por título y filtro por estado y prioridad.
- [ ] Ordenar al pulsar la cabecera de una columna.
- [ ] Validar el formulario: campos obligatorios y mensaje de error junto al campo.
- [ ] Guardar las incidencias nuevas en `localStorage` para que no se pierdan al recargar.

**Hecho cuando:** puedes crear una incidencia en el formulario y verla en la lista tras recargar la página.

**Consulta:** MDN · *JavaScript: scripts dinámicos del lado del cliente*.

### Etapa 4 · Datos asíncronos y API simulada (10–15 h)

**Aprendes:** qué es una API y JSON, los verbos HTTP (GET, POST, PUT, DELETE), `fetch`, promesas y `async/await`.

**Construyes:**
- [ ] Mover los datos a un archivo `db.json`.
- [ ] Cargar la lista con `fetch` en lugar de leer el array directamente.
- [ ] Mostrar tres estados: **cargando**, **error** y **sin resultados**.

**Hecho cuando:** si cambias el nombre del archivo JSON para provocar un fallo, la página muestra un mensaje claro en vez de quedarse en blanco.

> **Punto de control.** Etiqueta esta versión: `git tag v0-estatico`. Es tu red de seguridad y también un buen
> "antes y después" para enseñar en una entrevista. A partir de aquí el proyecto se reescribe con React.

### Etapa 5 · TypeScript y herramientas (10–15 h)

**Aprendes:** qué es Node.js y npm, tipos básicos, `interface`, tipos unión (`"alta" | "media" | "baja"`).

**Construyes:**
- [ ] Instalar Node.js (versión LTS).
- [ ] Crear el proyecto con Vite usando la plantilla de React + TypeScript, en una rama nueva.
- [ ] Definir los tipos `Ticket`, `Prioridad` y `Estado`.
- [ ] Reescribir en TypeScript las funciones de filtrar y ordenar de la etapa 3.

**Hecho cuando:** `npm run dev` arranca el proyecto y TypeScript te avisa si intentas asignar una prioridad que no existe.

**Consulta:** *TypeScript Handbook*.

### Etapa 6 · React: componentes (20–30 h)

**Aprendes:** componentes, JSX, *props*, `useState`, `useEffect`, renderizado de listas y condicional.

**Construyes:**
- [ ] Componentes `Cabecera`, `ListaTickets`, `FilaTicket`, `EtiquetaEstado` y `Filtros`.
- [ ] La lista con búsqueda, filtros y ordenación, ahora con estado de React.
- [ ] Paginación (por ejemplo, 10 incidencias por página).
- [ ] Reutilizar el CSS de la etapa 2.

**Hecho cuando:** la pantalla de lista hace lo mismo que en la versión estática y ningún componente supera unas 100 líneas.

**Consulta:** React · *Learn* (haz el tutorial completo antes de empezar).

### Etapa 7 · Rutas y API simulada (15–20 h)

**Aprendes:** React Router (rutas, parámetros como `/tickets/42`, navegación) y un servidor de API simulado (`json-server` es el más sencillo).

**Construyes:**
- [ ] Rutas: `/login`, `/tickets`, `/tickets/:id`, `/tickets/nuevo`, `/tickets/:id/editar`.
- [ ] Un archivo `api/tickets.ts` con todas las llamadas (`listar`, `obtener`, `crear`, `actualizar`).
- [ ] Pantalla de detalle que carga la incidencia por su `id`.
- [ ] Estados de carga, error y "no encontrada" en cada pantalla.
- [ ] Inicio de sesión **simulado** que solo sirve para practicar navegación.

**Hecho cuando:** el recorrido lista → detalle → volver funciona, y una dirección inexistente muestra una página 404 propia.

### Etapa 8 · Formularios (10–15 h)

**Aprendes:** formularios controlados, validación y envío de datos con POST y PUT.

**Construyes:**
- [ ] Un único componente `FormularioTicket` que sirva para crear y para editar.
- [ ] Errores junto a cada campo y foco en el primer campo erróneo.
- [ ] Botón deshabilitado mientras se envía y mensaje de confirmación al terminar.

**Hecho cuando:** puedes crear y editar una incidencia **usando solo el teclado** (Tab, Enter, flechas).

### Etapa 9 · Pruebas y accesibilidad (15–20 h)

**Aprendes:** Vitest, React Testing Library y comprobaciones básicas de accesibilidad.

**Construyes:**
- [ ] Prueba: la lista muestra las incidencias que devuelve la API.
- [ ] Prueba: filtrar por estado reduce los resultados.
- [ ] Prueba: enviar el formulario vacío muestra los errores.
- [ ] Prueba: crear una incidencia válida llama a la API con los datos correctos.
- [ ] Pasar Lighthouse (pestaña de las herramientas de desarrollo) y corregir los avisos de accesibilidad.

**Hecho cuando:** `npm test` pasa en verde y cubre los tres flujos: listar, ver detalle y crear/editar.

### Etapa 10 · Publicación y README (5–10 h)

**Construyes:**
- [ ] Publicar en un servicio gratuito (GitHub Pages, Netlify o Vercel).
- [ ] README completo: qué hace, captura de pantalla, cómo ejecutarlo, tecnologías y **límites**.
- [ ] En los límites, decir claramente que el inicio de sesión es simulado y no protege datos reales.

**Hecho cuando:** alguien que no conoce el proyecto puede abrir el enlace, usarlo y entender qué no hace.

### ServiceDesk v2 (opcional, después de terminar)

Mejoras de una en una, cada una en su rama:
- [ ] **TanStack Query** para sustituir los `useEffect` + `fetch` de carga de datos.
- [ ] **React Hook Form + Zod** para sustituir la validación manual.
- [ ] **GitHub Actions** que ejecute las pruebas en cada `push`.

**No lo añadas:** Redux, microservicios ni un panel complejo. No hacen falta en este proyecto.

---

# Proyecto 2 · BookingCore (backend)

API para reservar salas o recursos. La regla decisiva: **dos personas no pueden reservar la misma sala a la misma hora**.
No tiene interfaz propia; se prueba con un cliente HTTP.

### Etapa 11 · Java y SQL básicos (25–35 h)

**Aprendes:** clases, colecciones y excepciones en Java; `SELECT`, `INSERT`, `JOIN` y claves foráneas en SQL.

**Construyes:**
- [ ] Instalar JDK, Maven, Docker y PostgreSQL (en un contenedor).
- [ ] Dibujar el modelo de datos en papel: `usuario`, `recurso`, `reserva`.
- [ ] Crear las tablas a mano con SQL y escribir la consulta que encuentra reservas que se solapan.

**Hecho cuando:** sabes escribir sin ayuda la consulta "¿está libre la sala 3 mañana de 10:00 a 11:00?".

> La versión de Java y de Spring Boot se decide al empezar, según lo que uséis en clase.

### Etapa 12 · Primera API con Spring Boot (20–25 h)

**Aprendes:** controladores, servicios, repositorios, Spring Data JPA y migraciones con Flyway.

**Construyes:**
- [ ] Proyecto generado con Spring Initializr.
- [ ] Migración de Flyway que crea las tablas.
- [ ] `GET /recursos` y `GET /recursos/{id}/disponibilidad`.
- [ ] `POST /reservas` (todavía sin comprobar solapamientos).

**Hecho cuando:** borras la base de datos, arrancas la aplicación y las tablas se recrean solas.

**Consulta:** Spring · *Building REST services*.

### Etapa 13 · Validación y errores (10–15 h)

**Construyes:**
- [ ] Validar entradas: fechas obligatorias, fin posterior al inicio, no reservar en el pasado.
- [ ] Un formato de error único para toda la API, con códigos HTTP correctos (400, 404, 409).

**Hecho cuando:** ninguna petición incorrecta devuelve un error 500.

### Etapa 14 · La regla de no solapamiento (20–30 h)

Es la parte más difícil y más valiosa del proyecto. Dedícale tiempo.

**Aprendes:** transacciones, bloqueos y restricciones en la base de datos.

**Construyes:**
- [ ] Rechazar con 409 una reserva que se solape con otra.
- [ ] Una **prueba de concurrencia**: lanzar muchas peticiones simultáneas para el mismo hueco y comprobar que solo una se guarda.
- [ ] Una estrategia que haga pasar esa prueba siempre (por ejemplo, una restricción de exclusión en PostgreSQL o un bloqueo en la transacción).

**Hecho cuando:** la prueba de concurrencia pasa 20 veces seguidas.

> **Trampa habitual:** "comprobar si está libre y luego guardar" falla cuando dos peticiones llegan a la vez.
> Que funcione al probarlo a mano no demuestra nada.

### Etapa 15 · Seguridad y roles (15–20 h)

**Construyes:**
- [ ] Registro e inicio de sesión reales con Spring Security (contraseñas cifradas).
- [ ] Roles de usuario y administración, comprobados **en el servidor**.
- [ ] Cancelar reservas: cada persona solo las suyas; administración, cualquiera.

**Hecho cuando:** una prueba demuestra que un usuario no puede cancelar la reserva de otro.

### Etapa 16 · Búsquedas y documentación (10–15 h)

- [ ] Búsqueda paginada de reservas con filtros por fecha y recurso.
- [ ] Documentación OpenAPI accesible desde el navegador.

### Etapa 17 · Calidad y entrega (15–20 h)

- [ ] Pruebas unitarias con JUnit y Mockito para las reglas de negocio.
- [ ] Pruebas de integración con Testcontainers (base de datos real de ensayo).
- [ ] `Dockerfile` y README con instrucciones de arranque y límites.

**No lo añadas:** pagos, microservicios, Kafka ni Kubernetes.

---

# Proyecto 3 · OpsFlow (full stack)

Inventario, proveedores, pedidos y movimientos de almacén. Une lo aprendido en los dos anteriores.
La regla decisiva: **el stock nunca puede quedar por debajo de cero**.

### Etapa 18 · Diseño y núcleo del backend (25–35 h)

- [ ] Modelo de datos: `producto`, `proveedor`, `pedido`, `linea_pedido`, `movimiento`.
- [ ] API de productos y proveedores (crear, listar, editar).
- [ ] Repositorio con dos carpetas (`frontend/` y `backend/`) y Docker Compose para arrancarlo todo junto.

**Hecho cuando:** un solo comando levanta base de datos y API.

### Etapa 19 · Movimientos y stock (25–35 h)

- [ ] Registrar entradas, salidas y ajustes; cada uno queda en el historial.
- [ ] El stock se calcula o actualiza dentro de una transacción.
- [ ] Rechazar salidas que dejen el stock negativo, **también con peticiones simultáneas** (reutiliza lo aprendido en la etapa 14).

**Hecho cuando:** una prueba de concurrencia demuestra que el stock no baja de cero, y el historial explica cada cambio.

### Etapa 20 · Interfaz (25–40 h)

- [ ] Pantallas de productos, proveedores, pedidos y movimientos (reutiliza patrones de ServiceDesk).
- [ ] Inicio de sesión real contra tu API, con roles.
- [ ] Búsqueda, filtros, paginación e indicadores sencillos.

**Hecho cuando:** crear un producto, registrar una entrada y una salida, y ver el stock actualizado funciona de principio a fin desde el navegador.

### Etapa 21 · Calidad e integración continua (15–25 h)

- [ ] Pruebas en cada capa y dos o tres recorridos completos.
- [ ] GitHub Actions que ejecute todas las pruebas.
- [ ] README que permita arrancar la aplicación desde cero.

### Etapa 22 · Demostración pública (10–20 h)

- [ ] Comparar precios y límites reales de los servicios **antes** de elegir. No es obligatorio pagar.
- [ ] Publicar con datos de demostración.

**Para una segunda entrega:** importación/exportación CSV, avisos de stock bajo, registro de actividad detallado y documentos asociados.

---

## Método de trabajo (vale para los tres proyectos)

1. Define qué puede hacer una persona.
2. Construye la versión mínima.
3. Pruébala con ejemplos reales y con casos de error.
4. Documenta cómo ejecutarla y qué límites tiene.
5. Haz un commit por cambio significativo.

## Errores frecuentes al empezar

- **Saltar a React sin saber JavaScript.** Las etapas 3 y 4 son las que más rinden; no las acortes.
- **Copiar código que no entiendes.** Si no puedes explicar una línea, todavía no está terminada.
- **Ver tutoriales sin escribir.** Por cada hora de vídeo o lectura, al menos otra tecleando.
- **Querer que quede bonito antes de que funcione.** Primero funciona, luego se pule.
- **Commits gigantes del tipo "cambios".** Pequeños y con un mensaje que diga qué cambió.
- **Añadir tecnologías porque suenan bien.** Cada proyecto tiene su lista de "no lo añadas"; respétala.

## Antes de fijar versiones

La selección de tecnologías es una propuesta revisable. Antes de empezar cada proyecto, revisa los requisitos de
las ofertas a las que quieras presentarte y la documentación oficial vigente.
