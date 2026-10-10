# Miniproyectos · BookingCore (etapas 11 a 17)

Continuación de la [hoja de ruta](../HOJA_DE_RUTA.md). Aquí no hay pantallas: construyes el programa que
trabaja "en la trastienda", recibe peticiones y decide qué se puede hacer y qué no.

**La idea en una frase:** un sistema para reservar salas en el que es imposible que dos personas se queden
con la misma sala a la misma hora.

Este proyecto irá en un repositorio propio, distinto de ServiceDesk.

Cada miniproyecto tiene las mismas partes que en ServiceDesk: **qué vas a hacer**, **pasos**,
**está bien cuando** y, a veces, **palabra nueva**.

---

## Etapa 11 · Las bases: Java y la base de datos

### 11.1 · Montar el taller

**Qué vas a hacer:** instalar las herramientas y comprobar que funcionan.

**Pasos:**
1. Instala el JDK (la versión que uséis en clase), Maven y Docker Desktop.
2. Escribe un programa Java que muestre "Hola" y ejecútalo.
3. Arranca una base de datos PostgreSQL con Docker, siguiendo la guía oficial de la imagen.
4. Conéctate a ella con un programa cliente (DBeaver, por ejemplo).

**Está bien cuando:** tu programa saluda y el cliente muestra la base de datos vacía.

**Palabra nueva:** *contenedor* = una caja con un programa ya instalado dentro, que se enciende y se apaga sin ensuciar tu ordenador.

### 11.2 · Dibujar antes de construir

**Qué vas a hacer:** decidir en papel qué información hay que guardar.

**Pasos:**
1. Dibuja tres cajas: personas, salas y reservas.
2. Dentro de cada una, escribe qué datos necesita (una reserva: quién, qué sala, desde cuándo, hasta cuándo, si está cancelada).
3. Une con flechas lo que está relacionado.

**Está bien cuando:** puedes explicar el dibujo en voz alta en un minuto.

### 11.3 · Crear las tablas a mano

**Qué vas a hacer:** pasar el dibujo a la base de datos.

**Pasos:**
1. Crea una tabla por cada caja.
2. Mete a mano tres personas, tres salas y cinco reservas.
3. Intenta crear una reserva para una sala que no existe.

**Está bien cuando:** la base de datos rechaza esa reserva imposible.

**Palabra nueva:** *clave foránea* = la regla que obliga a que una reserva apunte a una sala y a una persona que existen de verdad.

### 11.4 · La pregunta clave

**Qué vas a hacer:** preguntar a la base de datos si una sala está libre.

**Pasos:**
1. Piensa primero la regla en papel: dos reservas chocan si una empieza antes de que termine la otra **y** termina después de que la otra empiece.
2. Escribe la consulta que busca reservas que choquen con "sala 3, mañana de 10:00 a 11:00".
3. Pruébala con cinco casos: justo antes, justo después, solapada al principio, solapada al final y metida dentro.

**Está bien cuando:** aciertas los cinco casos. Una reserva que acaba a las 10:00 **no** choca con otra que empieza a las 10:00.

---

## Etapa 12 · El primer servidor

### 12.1 · Un servidor que contesta

**Qué vas a hacer:** un programa que se queda encendido esperando peticiones.

**Pasos:**
1. Genera el proyecto en [start.spring.io](https://start.spring.io/).
2. Añade una dirección `/hola` que conteste con un saludo.
3. Arráncalo y abre esa dirección en el navegador.

**Está bien cuando:** el navegador muestra el saludo.

### 12.2 · Tablas que se crean solas

**Qué vas a hacer:** que el programa prepare la base de datos al arrancar.

**Pasos:**
1. Añade Flyway al proyecto.
2. Copia en un archivo de migración las órdenes de creación de tablas del miniproyecto 11.3.
3. Borra la base de datos y arranca el programa.

**Está bien cuando:** las tablas aparecen sin que hayas escrito nada a mano.

**Palabra nueva:** *migración* = un archivo numerado con cambios para la base de datos. Aplicados en orden, reconstruyen siempre la misma estructura.

### 12.3 · Enseñar las salas

**Qué vas a hacer:** la primera petición útil: pedir la lista de salas.

**Pasos:**
1. Instala un programa para enviar peticiones (Bruno, Postman o similar).
2. Crea la dirección que devuelve todas las salas y otra que devuelve una sola por su número.

**Está bien cuando:** pides una sala que no existe y la respuesta dice "no encontrada" en lugar de un error raro.

### 12.4 · ¿Está libre?

**Qué vas a hacer:** una dirección que responde si una sala está libre en un horario.

**Está bien cuando:** responde bien a los cinco casos del miniproyecto 11.4.

### 12.5 · Hacer una reserva

**Qué vas a hacer:** una dirección que guarda una reserva nueva.

**Pasos:**
1. Recibe la sala, la persona, el inicio y el fin.
2. Guárdala y devuelve la reserva creada con su número.

**Está bien cuando:** creas una reserva y luego la ves en la base de datos. Todavía no comprueba choques: eso llega en la etapa 14.

---

## Etapa 13 · No fiarse de lo que llega

### 13.1 · Rechazar lo absurdo

**Qué vas a hacer:** que el servidor no acepte reservas sin sentido.

**Pasos:** rechaza las reservas sin fecha, las que terminan antes de empezar, las que están en el pasado y las de salas que no existen.

**Está bien cuando:** cada uno de esos cuatro casos recibe una respuesta que explica qué está mal.

### 13.2 · Todos los errores, con la misma forma

**Qué vas a hacer:** que cualquier error del servidor se explique igual.

**Pasos:**
1. Decide una forma única: un código, un mensaje para personas y, si hace falta, el campo que falla.
2. Aplícala en un solo sitio del programa, para todas las direcciones.

**Está bien cuando:** por muy mal que hagas una petición, nunca recibes el error genérico "500".

**Palabra nueva:** *código de estado* = el número que resume cómo ha ido una petición (200 bien, 400 petición incorrecta, 404 no existe, 409 choca con algo, 500 fallo del servidor).

---

## Etapa 14 · La regla que da sentido al proyecto

Es la parte más difícil y la que más vale en una entrevista. Ve despacio.

### 14.1 · Rechazar una reserva que choca

**Qué vas a hacer:** impedir la reserva si la sala ya está ocupada.

**Pasos:** antes de guardar, comprueba si hay choque; si lo hay, responde con el código 409 y un mensaje claro.

**Está bien cuando:** la segunda reserva para el mismo hueco se rechaza.

### 14.2 · La prueba de las prisas

**Qué vas a hacer:** descubrir que lo anterior no basta.

**Pasos:**
1. Escribe una prueba que lance veinte peticiones **a la vez** para la misma sala y la misma hora.
2. Cuenta cuántas reservas se han guardado.

**Está bien cuando:** la prueba **falla** alguna vez (se guardan dos o más). Ese fallo es el descubrimiento: has visto el problema con tus propios ojos.

**Por qué pasa:** dos peticiones preguntan "¿está libre?" en el mismo instante, las dos reciben un "sí" y las dos guardan.

### 14.3 · Arreglarlo de verdad

**Qué vas a hacer:** que solo una de las veinte peticiones consiga la sala.

**Pasos:**
1. Lee sobre dos soluciones: que la propia base de datos vigile que no haya choques, o que la sala quede "cogida" mientras se decide.
2. Elige una y aplícala.
3. Ejecuta la prueba de las prisas veinte veces seguidas.

**Está bien cuando:** las veinte veces se guarda exactamente una reserva y las otras diecinueve reciben el 409.

**Palabra nueva:** *transacción* = un grupo de operaciones que se hacen todas o ninguna, sin que nadie vea el trabajo a medias.

### 14.4 · Explicarlo por escrito

**Qué vas a hacer:** contar en el README qué problema había y cómo lo resolviste.

**Está bien cuando:** alguien que no programa entiende por qué "comprobar y luego guardar" no era suficiente.

---

## Etapa 15 · Quién puede hacer qué

### 15.1 · Crear una cuenta

**Qué vas a hacer:** que una persona pueda registrarse con correo y contraseña.

**Está bien cuando:** miras la tabla de personas y la contraseña **no se puede leer**: está guardada transformada.

### 15.2 · Identificarse

**Qué vas a hacer:** que el servidor sepa quién hace cada petición.

**Pasos:**
1. Añade Spring Security.
2. Deja abiertas solo las direcciones de registro y de entrada; el resto exige identificarse.

**Está bien cuando:** una petición sin identificar recibe "no autorizado", y la reserva se guarda a nombre de quien la pide, sin que tenga que decir quién es.

### 15.3 · Dos tipos de persona

**Qué vas a hacer:** distinguir entre usuarios normales y administración.

**Está bien cuando:** solo administración puede crear o borrar salas, y una prueba lo demuestra.

### 15.4 · Cancelar una reserva

**Qué vas a hacer:** permitir cancelaciones con sus reglas.

**Pasos:**
1. Cada persona puede cancelar solo sus reservas; administración, cualquiera.
2. No se puede cancelar una reserva que ya ha pasado.
3. Una reserva cancelada deja la sala libre.

**Está bien cuando:** una prueba demuestra que una persona no puede cancelar la reserva de otra.

---

## Etapa 16 · Buscar y documentar

### 16.1 · Buscar reservas por partes

**Qué vas a hacer:** consultar reservas sin recibirlas todas de golpe.

**Pasos:**
1. Devuelve las reservas de veinte en veinte, indicando cuántas hay en total.
2. Permite filtrar por sala y por fechas.

**Está bien cuando:** con cien reservas de prueba, puedes pedir la página 3 y obtener solo esas veinte.

### 16.2 · El manual de uso

**Qué vas a hacer:** una página que lista todas las direcciones del servidor y cómo usarlas.

**Está bien cuando:** abres esa página en el navegador y puedes probar una petición desde ella.

**Palabra nueva:** *OpenAPI* = un formato estándar para describir qué ofrece un servidor.

---

## Etapa 17 · Dejarlo presentable

### 17.1 · Probar las reglas

**Qué vas a hacer:** pruebas rápidas para cada regla (fechas, choques, permisos, cancelaciones).

**Está bien cuando:** cada regla tiene al menos una prueba de "se permite" y otra de "se rechaza".

### 17.2 · Probar con una base de datos real

**Qué vas a hacer:** pruebas que arrancan una base de datos de usar y tirar.

**Pasos:** usa Testcontainers para que cada tanda de pruebas levante su propia base de datos y la elimine al acabar.

**Está bien cuando:** las pruebas pasan en un ordenador que no tiene PostgreSQL instalado, solo Docker.

### 17.3 · Empaquetar y explicar

**Qué vas a hacer:** que cualquiera pueda arrancar el proyecto.

**Pasos:**
1. Prepara el archivo que permite arrancar el servidor dentro de un contenedor.
2. Escribe el README: qué hace, cómo arrancarlo, cómo lanzar las pruebas y qué no hace.

**Está bien cuando:** otra persona lo arranca siguiendo solo el README.

---

## Lo que no hay que añadir

Pagos, varios servidores pequeños comunicándose entre sí, colas de mensajes o sistemas para gestionar muchos
contenedores. Ninguno hace falta para demostrar lo que este proyecto quiere demostrar.
