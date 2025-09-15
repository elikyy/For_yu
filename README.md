<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>No debiste entrar</title>
  <style>
    body {
      background-color: black;
      color: #ff0000;
      font-family: "Courier New", monospace;
      text-align: center;
      padding: 50px;
      overflow: hidden;
    }
    h1 {
      animation: parpadeo 2s infinite;
    }
    @keyframes parpadeo {
      0%, 49% { text-shadow: 0 0 15px red; }
      50%, 100% { text-shadow: none; }
    }
    .mensaje {
      margin-top: 100px;
      font-size: 24px;
      opacity: 0;
      transition: opacity 1s ease-in-out;
    }
    .visible {
      opacity: 1;
    }
    .imagen-oculta {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      opacity: 0;
      transition: opacity 1s;
    }
  </style>
</head>
<body>
  <h1>👁 Has sido observado 👁</h1>
  <p class="mensaje" id="texto">¿Por qué sigues leyendo...?</p>

  <!-- Imagen inquietante -->
  <img src="https://i.ibb.co/XDWy3Dq/cara-borroso.jpg" class="imagen-oculta" id="imagen">

  <!-- Sonido ambiente -->
  <audio id="sonido" loop>
    <source src="https://www.fesliyanstudios.com/play-mp3/4385" type="audio/mpeg">
  </audio>

  <script>
    const mensajes = [
      "No hay salida.",
      "Mira detrás de ti...",
      "Ellos ya saben dónde estás.",
      "Tus ojos no son tuyos.",
      "La página nunca termina..."
    ];
    let i = 0;
    const texto = document.getElementById("texto");
    const imagen = document.getElementById("imagen");
    const sonido = document.getElementById("sonido");

    // Cambiar textos cada 4s
    setInterval(() => {
      texto.classList.remove("visible");
      setTimeout(() => {
        texto.textContent = mensajes[i];
        texto.classList.add("visible");
        i = (i + 1) % mensajes.length;
      }, 1000);
    }, 4000);

    // Mostrar imagen de vez en cuando
    setInterval(() => {
      imagen.style.opacity = 1;
      setTimeout(() => imagen.style.opacity = 0, 1500);
    }, 10000);

    // Reproducir sonido al hacer clic
    document.body.addEventListener("click", () => {
      sonido.play();
      alert("👁 Ya es demasiado tarde...");
    });
  </script>
</body>
</html>
