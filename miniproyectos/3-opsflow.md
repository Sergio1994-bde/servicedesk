# Miniproyectos · OpsFlow (etapas 18 a 22)

Final de la [hoja de ruta](../HOJA_DE_RUTA.md). Aquí juntas lo aprendido: pantallas como en ServiceDesk
y un servidor con base de datos como en BookingCore.

**La idea en una frase:** una aplicación para llevar un almacén en la que las existencias nunca pueden
quedar por debajo de cero y siempre se sabe de dónde viene cada cambio.

Casi nada es nuevo: lo difícil es que todas las partes encajen. Por eso los miniproyectos son más breves
y remiten a los anteriores.

---

## Etapa 18 · Cimientos

### 18.1 · Dibujar el almacén

**Qué vas a hacer:** decidir en papel qué información se guarda.

**Pasos:**
1. Dibuja las cajas: productos, proveedores, pedidos, líneas de pedido y movimientos.
2. Escribe los datos de cada una. Un movimiento necesita: producto, tipo (entrada, salida o ajuste), cantidad, fecha, quién lo hizo y por qué.
3. Decide cómo sabrás las existencias de un producto.

**Está bien cuando:** con el dibujo delante puedes contestar "¿cuántas unidades hay del producto X y por qué?".

### 18.2 · Todo arranca con una sola orden

**Qué vas a hacer:** preparar el repositorio y el arranque conjunto.

**Pasos:**
1. Crea un repositorio con dos carpetas: `frontend/` y `backend/`.
2. Crea en cada una el proyecto vacío correspondiente (como en los miniproyectos 5.1 y 12.1).
3. Escribe el archivo de Docker Compose que enciende la base de datos y el servidor juntos.

**Está bien cuando:** una sola orden lo levanta todo y el servidor contesta a `/hola`.

### 18.3 · Productos

**Qué vas a hacer:** crear, listar, ver y modificar productos desde el servidor.

**Está bien cuando:** puedes hacer las cuatro cosas con tu programa de peticiones, los datos absurdos se rechazan (precio negativo, nombre vacío) y las tablas se crean solas al arrancar.

### 18.4 · Proveedores

**Qué vas a hacer:** lo mismo, para proveedores, y relacionar cada producto con su proveedor.

**Está bien cuando:** al pedir un producto ves también quién lo suministra.

---

## Etapa 19 · El corazón: existencias y movimientos

### 19.1 · Entradas

**Qué vas a hacer:** registrar que llega mercancía.

**Está bien cuando:** registras una entrada de 10 unidades y las existencias del producto suben 10, y el movimiento queda apuntado con fecha y autor.

### 19.2 · Salidas, con límite

**Qué vas a hacer:** registrar que sale mercancía, sin permitir números rojos.

**Está bien cuando:** con 10 unidades puedes sacar 10, pero al intentar sacar 11 recibes un mensaje claro y las existencias no cambian.

### 19.3 · Ajustes y el historial

**Qué vas a hacer:** permitir correcciones (por ejemplo, tras un recuento) y consultar todo lo ocurrido.

**Pasos:**
1. Un ajuste exige escribir el motivo.
2. Crea la consulta del historial de un producto, del más reciente al más antiguo.
3. Los movimientos no se borran ni se modifican nunca: un error se corrige con otro movimiento.

**Está bien cuando:** sumando y restando los movimientos del historial obtienes exactamente las existencias actuales.

### 19.4 · La prueba de las prisas, otra vez

**Qué vas a hacer:** asegurar el límite cuando llegan muchas salidas a la vez.

**Pasos:**
1. Con 10 unidades, lanza a la vez veinte salidas de 1 unidad.
2. Aplica lo aprendido en los miniproyectos 14.2 y 14.3.

**Está bien cuando:** siempre se aceptan exactamente diez salidas y las existencias terminan en cero, nunca por debajo.

### 19.5 · Pedidos

**Qué vas a hacer:** registrar pedidos a proveedores, con varios productos cada uno.

**Pasos:**
1. Un pedido tiene un proveedor y una o más líneas (producto y cantidad).
2. Al marcar el pedido como recibido, se crea una entrada por cada línea.

**Está bien cuando:** recibir un pedido de tres productos sube las existencias de los tres, y si algo falla a mitad no sube ninguna.

---

## Etapa 20 · Las pantallas

Reutiliza todo lo que puedas de ServiceDesk: listas, filtros, formularios, avisos de carga y de error.

### 20.1 · Entrar con una cuenta de verdad

**Qué vas a hacer:** una entrada que, esta vez sí, comprueba quién eres.

**Pasos:**
1. Añade al servidor cuentas y dos tipos de persona (como en la etapa 15).
2. Haz la pantalla de entrada, que ahora pregunta al servidor.

**Está bien cuando:** con una contraseña incorrecta no entras, y una petición directa al servidor sin identificarte también se rechaza.

### 20.2 · Pantalla de productos

**Qué vas a hacer:** lista de productos con sus existencias, buscador, filtros y páginas; y formulario para crear y editar.

**Está bien cuando:** creas un producto desde la pantalla y aparece en la lista.

### 20.3 · Pantalla de movimientos

**Qué vas a hacer:** desde la ficha de un producto, registrar una entrada, una salida o un ajuste, y ver su historial.

**Está bien cuando:** al intentar una salida mayor que las existencias, ves en pantalla el mensaje que envía el servidor.

### 20.4 · Proveedores y pedidos

**Qué vas a hacer:** las pantallas que faltan.

**Está bien cuando:** creas un pedido con dos productos, lo marcas como recibido y las existencias cambian en la pantalla de productos.

### 20.5 · Los números de un vistazo

**Qué vas a hacer:** una pantalla de inicio con tres o cuatro datos sencillos (número de productos, productos sin existencias, movimientos de hoy).

**Está bien cuando:** cada número coincide con lo que ves en las listas. No hacen falta gráficos.

---

## Etapa 21 · Comprobar el conjunto

### 21.1 · Pruebas de cada parte

**Qué vas a hacer:** pruebas del servidor (reglas y base de datos) y de las pantallas (como en las etapas 9 y 17).

**Está bien cuando:** cada regla del almacén tiene su prueba, incluida la de las prisas.

### 21.2 · Pruebas del recorrido entero

**Qué vas a hacer:** dos o tres pruebas que manejan el navegador solas, de principio a fin.

**Pasos:** usa una herramienta como Playwright para automatizar: entrar → crear producto → registrar entrada → registrar salida → comprobar existencias.

**Está bien cuando:** el recorrido completo se ejecuta solo y termina en verde.

### 21.3 · Pruebas que se lanzan solas

**Qué vas a hacer:** que GitHub ejecute todas las pruebas cada vez que subes cambios.

**Está bien cuando:** un commit que rompe algo aparece marcado en rojo en GitHub.

### 21.4 · Instrucciones de arranque

**Qué vas a hacer:** el README final.

**Está bien cuando:** otra persona, con Docker instalado y nada más, arranca la aplicación entera siguiendo tus pasos.

---

## Etapa 22 · Demostración pública

### 22.1 · Comparar antes de elegir

**Qué vas a hacer:** una tabla con dos o tres servicios donde publicar, su precio y sus límites.

**Está bien cuando:** sabes cuánto costará al mes (lo ideal: nada) y qué ocurre si superas el límite gratuito. No es obligatorio pagar.

### 22.2 · Publicar con datos de ejemplo

**Qué vas a hacer:** dejar una versión visitable.

**Pasos:**
1. Carga datos de demostración creíbles.
2. Crea una cuenta de visitante y pon sus datos en el README.
3. Explica en el README los límites de la demostración.

**Está bien cuando:** alguien entra con la cuenta de visitante y completa el recorrido de 21.2 a mano.

---

## Para una segunda entrega

Cuando todo lo anterior esté terminado y probado, puedes añadir, de uno en uno:

- Cargar y descargar productos desde una hoja de cálculo (archivo CSV).
- Avisos cuando un producto tiene pocas existencias.
- Un registro más detallado de quién hizo qué.
- Documentos adjuntos a pedidos.

**Recuerda:** una pantalla vistosa no sustituye a un control correcto del almacén. Primero las reglas, las pruebas y el historial fiable.
