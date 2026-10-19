<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Para Liz Maribel💗</title>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    min-height: 100vh;
    font-family: Georgia, serif;
    background: linear-gradient(135deg, #ff758c, #ffb6c1, #ffc3a0);
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    text-align: center;
    color: #8b1238;
}

.pantalla {
    display: none;
    background: rgba(255,255,255,0.92);
    width: 90%;
    max-width: 470px;
    padding: 35px 25px;
    border-radius: 25px;
    box-shadow: 0 10px 40px #a32b4b55;
    animation: aparecer 0.8s ease;
    position: relative;
    z-index: 2;
}

.pantalla.activa {
    display: block;
}

h1 {
    color: #e63966;
    font-size: 30px;
}

p {
    font-size: 18px;
    line-height: 1.7;
}

.corazon {
    font-size: 70px;
    animation: latir 1s infinite;
}

button {
    border: none;
    border-radius: 30px;
    padding: 14px 27px;
    font-size: 17px;
    cursor: pointer;
    transition: transform 0.2s;
}

button:active {
    transform: scale(0.95);
}

.boton-si, .boton-comenzar, .boton-carta {
    background: #ff477e;
    color: white;
    box-shadow: 0 5px 15px #ff477e55;
}

.boton-si:hover, .boton-comenzar:hover, .boton-carta:hover {
    background: #e62964;
}

#botonNo {
    position: fixed;
    background: #eeeeee;
    color: #555;
    z-index: 10;
}

.botones {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
    min-height: 90px;
    position: relative;
}

#carta {
    background: #fff0f3;
    border: 2px dashed #ff8fab;
    border-radius: 15px;
    padding: 20px;
    margin-top: 20px;
    text-align: left;
}

#carta h2 {
    text-align: center;
    color: #d63362;
}

.firma {
    text-align: right;
    color: #e63966;
    font-style: italic;
}

.flotante {
    position: fixed;
    bottom: -40px;
    pointer-events: none;
    z-index: 1;
    animation: subir 6s linear forwards;
}

@keyframes latir {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.15); }
}

@keyframes aparecer {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}

@keyframes subir {
    to {
        transform: translateY(-110vh) rotate(360deg);
        opacity: 0;
    }
}
</style>
</head>

<body>

<!-- PANTALLA INICIAL -->
<section class="pantalla activa" id="inicio">
    <div class="corazon">💖</div>
    <p>Hay alguien que hace mis días más bonitos...</p>
    <h1>Liz Maribel ❤️</h1>
    <p>
        Preparé algo especial para ti.
        Quiero decirte algo que llevo guardado en mi corazón.
    </p>
    <button class="boton-comenzar" onclick="comenzar()">
        Abrir sorpresa 💌
    </button>
</section>

<!-- PANTALLA DE DECLARACIÓN -->
<section class="pantalla" id="pregunta">
    <div class="corazon">💘</div>
    <h1>Liz Maribel...</h1>
    <p>
        Eres una persona muy especial para mí.
        Me haces sonreír y quería tener el valor de preguntarte...
    </p>
    <h2>¿Quieres ser mi novia? ❤️</h2>
    <div class="botones">
        <button class="boton-si" onclick="aceptar()">
            ¡Sí! 💖
        </button>
    </div>
    <p style="font-size:14px;">
        Elige con el corazón 💕
    </p>
</section>
<!-- BOTÓN NO QUE SE MUEVE -->
<button id="botonNo"
        onmouseenter="moverNo()"
        ontouchstart="moverNo()"
        onclick="moverNo()">
    No 💔
</button>

<!-- PANTALLA FINAL -->
<section class="pantalla" id="final">
    <div class="corazon">🥹💗</div>
    <h1>¡Gracias, Liz Maribel! 💖</h1>
    <p>
        No sabes lo feliz que me hace que hayas llegado hasta aquí.
        Tengo algo más que quiero compartir contigo...
    </p>
    <button class="boton-carta" onclick="abrirCarta()">
        💌 Abrir mi carta
    </button>
    <div id="carta" style="display:none;">
        <h2>Para Liz Maribel 💌</h2>
        <p>
            Quiero que sepas que eres una persona muy especial
            para mí. Desde que llegaste a mi vida, hay momentos
            que se han vuelto más bonitos gracias a ti.
        </p>
        <p>
            Me gusta tu forma de ser, tu sonrisa y esa manera
            tan especial que tienes de hacerme sentir feliz.
        </p>
        <p>
            No sé qué nos espera en el futuro, pero me gustaría
            conocerte cada día más, compartir risas, crear
            recuerdos bonitos y estar presente en los buenos
            y malos momentos.
        </p>
        <p>
            No prometo ser perfecto, pero sí tratarte con cariño,
            respetarte, escucharte y valorar lo especial que eres.
        </p>
        <p>
            Gracias por existir, Liz Maribel.
            Espero que esta pequeña sorpresa te saque una sonrisa,
            porque la preparé pensando en ti. ❤️
        </p>
        <p class="firma">
            Con mucho cariño,<br>
            Alguien que te quiere mucho(Osea yo jeje). 💗
        </p>
    </div>
</section>

<script>
const botonNo = document.getElementById("botonNo");

function mostrarPantalla(id) {
    document.querySelectorAll(".pantalla").forEach(p => {
        p.classList.remove("activa");
    });

    document.getElementById(id).classList.add("activa");
}

function comenzar() {
    mostrarPantalla("pregunta");
    botonNo.style.display = "block";

    // Coloca el botón cerca del centro al iniciar.
    botonNo.style.left = "calc(50% + 65px)";
    botonNo.style.top = "calc(50% + 115px)";
}

function moverNo() {
    const margen = 15;

    const maxX = window.innerWidth - botonNo.offsetWidth - margen;
    const maxY = window.innerHeight - botonNo.offsetHeight - margen;

    const x = margen + Math.random() * Math.max(0, maxX - margen);
    const y = margen + Math.random() * Math.max(0, maxY - margen);

    botonNo.style.left = x + "px";
    botonNo.style.top = y + "px";
}

function aceptar() {
    botonNo.style.display = "none";
    mostrarPantalla("final");
    crearCorazones();
}

function abrirCarta() {
    document.getElementById("carta").style.display = "block";
    crearCorazones();

    document.querySelector(".boton-carta").style.display = "none";
}

function crearCorazones() {
    for (let i = 0; i < 25; i++) {
        setTimeout(() => {
            const corazon = document.createElement("div");

            corazon.className = "flotante";
            corazon.textContent = ["❤️", "💖", "💕", "💗"][
                Math.floor(Math.random() * 4)
            ];

            corazon.style.left = Math.random() * 100 + "vw";
            corazon.style.fontSize =
                (Math.random() * 20 + 15) + "px";

            document.body.appendChild(corazon);

            setTimeout(() => corazon.remove(), 6000);
        }, i * 120);
    }
}

// Ocultar el botón No al cargar la página.
botonNo.style.display = "none";
</script>

</body>
</html>
