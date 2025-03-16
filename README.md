# challenge-amigo-secreto_esp-main
Muestra una aplicacacion de juego llamado amigo secreto
Mi Primer Proyecto: Jugando al Amigo Secreto 🎁
Este proyecto es una aplicación web sencilla que permite a los usuarios agregar nombres de amigos a una lista y realizar un sorteo aleatorio para elegir un "amigo secreto". A continuación, te explico paso a paso cómo está construido el código.

1️⃣ Estructura del Proyecto
El proyecto está compuesto por tres archivos principales:

HTML (index.html): Define la estructura de la página.
CSS (style.css): Se encarga del diseño y la apariencia.
JavaScript (app.js): Contiene la lógica del programa.
2️⃣ Código HTML: La Estructura de la Página
El archivo HTML contiene el contenido visual y está dividido en tres partes principales:

📌 a) Encabezado (<header>)
Aquí se muestra el título de la página y una imagen representativa del juego.

html
Copiar
Editar
<header class="header-banner">
    <h1 class="main-title">Amigo Secreto</h1>
    <img src="assets/amigo-secreto.png" alt="Imagen representativa de amigo secreto">
</header>
🔹 Explicación:

Se usa un <h1> para el título principal.
Se incluye una imagen con <img> para darle un toque visual.
📌 b) Sección de Entrada (<section>)
Este bloque contiene el formulario donde los usuarios pueden ingresar nombres.

html
Copiar
Editar
<section class="input-section">
    <h2 class="section-title">Digite el nombre de sus amigos</h2>
    <div class="input-wrapper">
        <input type="text" id="amigo" class="input-name" placeholder="Escribe un nombre">
        <button class="button-add" onclick="agregarAmigo()">Añadir</button>
    </div>
</section>
🔹 Explicación:

Un campo <input> donde los usuarios pueden escribir el nombre de un amigo.
Un botón <button> que llama a la función agregarAmigo() cuando se presiona.
📌 c) Lista de Amigos y Botón de Sorteo
html
Copiar
Editar
<ul id="listaAmigos" class="name-list"></ul>
<ul id="resultado" class="result-list" aria-live="polite"></ul>

<div class="button-container">
    <button class="button-draw" id="elegirAmigo" onclick="sortearAmigo()">
        <img src="assets/play_circle_outline.png" alt="Ícono para sortear">
        Sortear amigo
    </button>
</div>
🔹 Explicación:

<ul id="listaAmigos"> mostrará los nombres ingresados.
<ul id="resultado"> mostrará el nombre del amigo secreto seleccionado.
Un botón <button> que ejecuta sortearAmigo() para hacer el sorteo.
3️⃣ Código CSS: Diseño y Estilos
El archivo CSS define los colores, tamaños y posiciones de los elementos.

🔹 Colores personalizados (Variables CSS)

css
Copiar
Editar
root {
    --color-primary: #4B69FD;
    --color-secondary: #FFF9EB;
    --color-button: #fe652b;
    --color-text: #444444;
}
🔹 Diseño del fondo y alineación

css
Copiar
Editar
body {
    height: 100vh;
    background-color: var(--color-primary);
    display: flex;
    justify-content: center;
    align-items: center;
}
🔹 Botón de añadir

css
Copiar
Editar
.button-add {
    background-color: var(--color-tertiary);
    border-radius: 0 25px 25px 0;
}
🔹 Botón de sorteo

css
Copiar
Editar
.button-draw {
    background-color: var(--color-button);
    color: var(--color-white);
}
.button-draw:hover {
    background-color: var(--color-button-hover);
}
4️⃣ Código JavaScript: La Lógica del Programa
Aquí está el código en JavaScript, encargado de hacer que la aplicación funcione.

📌 a) Declaración de Variables
js
Copiar
Editar
let listaDeAmigos = []; // Lista vacía para almacenar los nombres
Se crea un array vacío para almacenar los nombres ingresados.
📌 b) Función para Limpiar el Campo de Entrada
js
Copiar
Editar
function limpiarCaja() {
    document.getElementById('amigo').value = '';
}
Cada vez que se ingresa un nombre, esta función borra el campo de entrada.
📌 c) Función para Agregar un Amigo
js
Copiar
Editar
function agregarAmigo() {
    let amigo = document.getElementById("amigo").value.trim();

    if (amigo.length < 3) {
        alert("Debes ingresar un nombre válido antes de pulsar el botón.");
        limpiarCaja();
        return;
    }

    listaDeAmigos.push(amigo);
    actualizarLista();
    limpiarCaja();
}
🔹 Explicación:

Se obtiene el valor del campo <input> y se eliminan espacios en blanco.
Si el nombre tiene menos de 3 letras, se muestra una alerta.
Si el nombre es válido, se agrega a la lista.
Se actualiza la lista en la interfaz.
Se limpia el campo de entrada.
📌 d) Función para Mostrar la Lista en la Página
js
Copiar
Editar
function actualizarLista() {
    let ul = document.getElementById("listaAmigos");
    ul.innerHTML = ""; // Limpiar lista antes de actualizar

    listaDeAmigos.forEach(amigo => {
        let li = document.createElement("li");
        li.textContent = amigo;
        ul.appendChild(li);
    });
}
Cada vez que se agrega un nombre, esta función actualiza la lista en la pantalla.
📌 e) Función para Elegir un Amigo Secreto
js
Copiar
Editar
function sortearAmigo() {
    if (listaDeAmigos.length === 0) {
        alert("Agrega al menos un nombre antes de sortear.");
        return;
    }

    let indiceAleatorio = Math.floor(Math.random() * listaDeAmigos.length);
    let amigoElegido = listaDeAmigos[indiceAleatorio];

    document.getElementById("resultado").textContent = `🎉 El amigo secreto es: ${amigoElegido}! 🎉`;
}
🔹 Explicación:

Si la lista está vacía, se muestra una alerta.
Se genera un número aleatorio entre 0 y la cantidad de amigos en la lista.
Se selecciona un amigo al azar y se muestra en la pantalla.
🎯 5️⃣ ¿Cómo Funciona el Juego?
1️⃣ El usuario ingresa los nombres de sus amigos.
2️⃣ Cada nombre se añade a la lista al presionar "Añadir".
3️⃣ Cuando todos los nombres están agregados, se presiona "Sortear Amigo".
4️⃣ El sistema elige un amigo al azar y lo muestra en la pantalla.

✨ Conclusión
Este proyecto es una excelente forma de aprender a manejar listas en JavaScript, manipulación del DOM y eventos en una página web. Se puede mejorar agregando animaciones, efectos de sonido o estilos más avanzados. 🚀

👉 ¿Listo para probarlo y compartirlo con tus amigos? 🎉





