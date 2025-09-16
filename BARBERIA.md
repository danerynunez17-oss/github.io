<!DOCTYPE html>


<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Elegant Barbershop</title>

  <base href="imagenes/" />

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html, body {
      height: 100%;
      overflow-x: hidden;
      font-family: Arial, sans-serif;
    }

    body {
      background: transparent;
      color: white;
      text-align: center;
      position: relative;
    }

    .fondo-gradiente {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle at 20% 30%, rgba(255,0,150,0.4), transparent 40%),
                  radial-gradient(circle at 80% 70%, rgba(0,200,255,0.4), transparent 50%),
                  linear-gradient(45deg, #ff00cc,#3333ff,#00ffcc,#ff6600);
      background-size: 300% 300%;
      animation: mover 10s infinite linear alternate;
      z-index: -1;
    }

    @keyframes mover { 
      0% { background-position:0% 50%; }
      50% { background-position:100% 50%; }
      100% { background-position:0% 50%; }
    }

    h1 {
      color:red;
      font-size:50px;
      text-shadow:2px 2px 3px yellow;
      animation:parpadeo 1s infinite;
      margin-top:30px;
    }

    @keyframes parpadeo {
      0%,100% { opacity:1; }
      50% { opacity:0.6; }
    }

    .barra-busqueda {
      margin:10px auto;
      max-width:400px;
    }

    .barra-busqueda input {
      padding:10px;
      width:80%;
      border-radius:20px;
      border:none;
      outline:none;
    }

    .barberia {
      display:flex;
      justify-content:center;
      flex-wrap:wrap;
      gap:20px;
      margin:20px auto;
      padding:10px;
      max-width:1200px;
    }

    .rodillo {
      width:200px;
      background-color:rgba(0,0,0,0.6);
      border-radius:10px;
      padding:10px;
      border:2px solid crimson;
      transition:transform 0.3s, box-shadow 0.3s;
      overflow:hidden;
    }

    .rodillo:hover {
      transform:scale(1.05);
      box-shadow:0 0 15px yellow;
    }

    .rodillo img {
      width:100%;
      height:180px;
      object-fit:cover;
      border-radius:10px;
      cursor:pointer;
      display:block;
    }

	  .rodillo h3 {
	  margin: 10px 0 5px 0;
	  font-size: 18px;
	  color: #fff;
	  height: 40px;               /* altura fija para todos los títulos */
	  overflow: hidden;           /* corta el exceso de texto */
	  text-overflow: ellipsis;    /* opcional: muestra "..." si es muy largo */
	  display: -webkit-box;
	  -webkit-line-clamp: 2;      /* máximo 2 líneas */
	  -webkit-box-orient: vertical;
	}


    .rodillo p {
      color:lightgreen;
      margin-bottom:5px;
    }

    /* Modales */
    .modal {
      display:none;
      position:fixed;
      top:0;
      left:0;
      width:100%;
      height:100%;
      background:rgba(0,0,0,0.8);
      justify-content:center;
      align-items:center;
      z-index:1000;
    }

    .contenido-modal {
      background:#222;
      padding:30px;
      border-radius:10px;
      text-align:center;
      color:white;
      max-width:400px;
      width:90%;
      position:relative;
      animation:aparecer 0.3s ease;
    }

    .contenido-modal h2 {
      margin-bottom:15px;
      color:yellow;
      text-shadow:1px 1px 3px black;
    }

    .contenido-modal p, .contenido-modal li {
      margin:5px 0;
    }

    .cerrar-modal {
      position:absolute;
      top:10px;
      right:15px;
      background:crimson;
      border:none;
      color:white;
      font-size:20px;
      border-radius:5px;
      cursor:pointer;
    }

    .cerrar-modal:hover {
      background-color:darkred;
    }

    @keyframes aparecer {
      from { transform:scale(0.9); opacity:0; }
      to { transform:scale(1); opacity:1; }
    }

    .botonera-horizontal {
  display: flex;
  justify-content: center; /* centra horizontalmente */
  gap: 15px;               /* espacio entre botones */
  margin: 20px 0;          /* espacio arriba y abajo */
}

.botonera-horizontal button {
  padding: 12px 20px;
  font-size: 16px;
  border-radius: 30px;
  border: none;
  cursor: pointer;
  background: linear-gradient(135deg, #007bff, #00c6ff);
  color: white;
  transition: transform 0.2s, filter 0.3s;
}

.botonera-horizontal button:hover {
  transform: scale(1.1);
  filter: brightness(1.1);
}
    

    .boton-flotante:hover {
      transform:scale(1.1);
      filter:brightness(1.1);
    }

    #boton-horario { bottom:140px; }
    #boton-reserva { bottom:80px; }
    #boton-contacto { bottom:20px; }

    /* Formulario reserva */
    .contenido-modal input, .contenido-modal textarea {
      width:100%;
      padding:10px;
      margin:8px 0;
      border-radius:5px;
      border:none;
    }

    .contenido-modal button[type="submit"] {
      margin-top:10px;
      padding:10px 15px;
      background:green;
      border:none;
      border-radius:5px;
      color:white;
      cursor:pointer;
      width:100%;
    }

    .contenido-modal button[type="submit"]:hover {
      background:darkgreen;
    }

    #info-img {
      width:100%;
      max-height:400px;
      object-fit:contain;
      border-radius:10px;
    }

    #info-precio {
      color: lightgreen;
      font-weight: bold;
      margin-top:5px;
    }
    
  </style>
  
</head>

<body>

  <div class="fondo-gradiente"></div>

  <h1>ELEGANT BARBERSHOP</h1>
  
  <p>Haz Clic En Un Corte Para Ver Más Información</p>
  
  <div class="botonera-horizontal">
  <button id="boton-horario">⏰ Horario</button>
  <button id="boton-reserva">📅 Reservar Cita</button>
  <button id="boton-contacto">📞 Contacto</button>
</div>
  
  
  <div class="barra-busqueda">
    <input type="text" id="buscador" placeholder="Buscar corte por nombre..." />
  </div>

  <h2 style="margin:20px 0;">Cortes Populares</h2>
  <div class="barberia" id="galeria"></div>

  <!-- Modales -->
  
  <!-- Modal detalle -->
  
  <div id="modal" class="modal">
    <div class="contenido-modal">
      <button class="cerrar-modal" id="cerrar">&times;</button>
      <img id="info-img" src="" alt="">
      <p id="info-text"></p>
      <p id="info-precio"></p>
    </div>
  </div>

  <!-- Modal contacto -->
  
  <div id="modal-contacto" class="modal">
    <div class="contenido-modal">
      <button class="cerrar-modal" id="cerrar-contacto">&times;</button>
      <h2>Contáctanos</h2>
      <p>📞 Teléfono: 123-456-789</p>
      <p>📱 <a href="https://wa.me/34600123456" target="_blank" style="color:lightgreen;">WhatsApp</a></p>
      <p>📧 Email: <a href="mailto:info@barbershop.com" style="color:lightblue;">info@barbershop.com</a></p>
    </div>
  </div>

  <!-- Modal reserva -->
  
  <div id="modal-reserva" class="modal">
    <div class="contenido-modal">
      <button class="cerrar-modal" id="cerrar-reserva">&times;</button>
      <h2>Reservar Cita</h2>
      <form id="form-reserva">
        <input type="text" id="nombre" placeholder="Tu nombre" required>
        <input type="tel" id="telefono" placeholder="Teléfono" required>
        <input type="date" id="fecha" required>
        <input type="time" id="hora" required>
        <textarea id="comentarios" placeholder="Comentarios adicionales (opcional)"></textarea>
        <button type="submit">Confirmar Reserva</button>
      </form>
      <p id="mensaje-exito" style="display:none; color:lightgreen; margin-top:10px;">
        ✅ ¡Tu Cita Ha Sido Reservada Con Exito!
        
      </p>
      
    </div>
    
  </div>

  <!-- Modal horario -->
  <div id="modal-horario" class="modal">
    <div class="contenido-modal">
      <button class="cerrar-modal" id="cerrar-horario">&times;</button>
      <h2>Horario de Atención</h2>
      <ul style="list-style:none; padding:0;">
        <li>Lunes - Viernes: 09:00 - 20:00</li>
        <li>Sábado: 10:00 - 18:00</li>
        <li>Domingo: Cerrado</li>
        
      </ul>
      
    </div>
    
  </div>

 
  <script>
  
    const cortes = [
      { nombre: "FADE", imagen: "fade.webp", descripcion: "Corte Degradado Moderno y Elegante.", precio: "€15" },
      { nombre: "POMPADOUR", imagen: "pompadour.jpg", descripcion: "Corte Clásico Con Volumen Hacia Atrás.", precio: "€18" },
      { nombre: "UNDERCUT", imagen: "undercut.png", descripcion: "Laterales Rapados y Parte Superior Larga.", precio: "€20" },
      { nombre: "BUZZ", imagen: "buzz.jpg", descripcion: "Corte Al Ras, Muy Fácil De Mantener.", precio: "€10" },
      { nombre: "FRANCESA CLARA", imagen: "francesa_clara.jpg", descripcion: "Corte Francesa Con Flequillo Claro.", precio: "€16" },
      { nombre: "FRANCESA OSCURA", imagen: "francesa_oscura.jpg", descripcion: "Estilo Francesa Con Toque Oscuro.", precio: "€16" },
      { nombre: "MELENA", imagen: "melena.webp", descripcion: "Cabello Largo Con Estilo Suelto.", precio: "€22" },
      { nombre: "MILITAR", imagen: "militar.jpg", descripcion: "Muy Corto, Estilo Disciplinado.", precio: "€12" },
      { nombre: "MOHICANO", imagen: "mohicano.jpg", descripcion: "Líneas Atrevidas y Laterales Rasurados.", precio: "€19" },
      { nombre: "MULLET", imagen: "mullet.jpg", descripcion: "Corto Adelante, Largo Atrás. Retro y Atrevido.", precio: "€17" },
      { nombre: "TOP KNOT", imagen: "top_knot.jpg", descripcion: "Recogido Superior Con Estilo Samurái Moderno.", precio: "€21" },
      { nombre: "UNDERCUT BUN", imagen: "undercut_bun.jpg", descripcion: "Moño Con Lados Rapados.", precio: "€20" },
      { nombre: "CURLY TAPER", imagen: "curly_taper.jpg", descripcion: "Rizos Con Desvanecido Natural.", precio: "€18" },
      { nombre: "TAPER FADE", imagen: "taper_fade.jpg", descripcion: "Clásico Desvanecido Gradual.", precio: "€15" },
      { nombre: "FLAT TOP", imagen: "flat_top.webp", descripcion: "Parte Superior Plana Con Estilo Retro.", precio: "€14" },
      { nombre: "BRO FLOW", imagen: "bro_flow.jpg", descripcion: "Cabello Suelto Con Movimiento Natural.", precio: "€19" },
      { nombre: "FRENCH CROP", imagen: "french_crop.jpg", descripcion: "Flequillo Corto Con Textura Frontal.", precio: "€16" },
      { nombre: "SKIN FADE", imagen: "skin_fade.jpg", descripcion: "Desvanecido Que Llega a Piel.", precio: "€18" },
      { nombre: "SLICK BACK", imagen: "slick_back.jpg", descripcion: "Peinado Hacia Atrás Con Gel.", precio: "€17" },
      { nombre: "COMB OVER", imagen: "comb_over.jpg", descripcion: "Peinado Con Raya Marcada a Un Lado.", precio: "€16" },
    ];

    const galeria = document.getElementById("galeria");
    const modal = document.getElementById("modal");
    const infoImg = document.getElementById("info-img");
    const infoText = document.getElementById("info-text");
    const infoPrecio = document.getElementById("info-precio");
    const cerrar = document.getElementById("cerrar"); 
    const buscador = document.getElementById("buscador");

    function cargarGaleria(filtro = "") {
      galeria.innerHTML = "";
      const filtrados = cortes.filter(corte => corte.nombre.toLowerCase().includes(filtro.toLowerCase()));
      filtrados.sort(() => Math.random() - 0.5);
      filtrados.forEach(corte => {
        const div = document.createElement("div");
        div.className = "rodillo";
        div.innerHTML = `
          <h3>${corte.nombre}</h3>
          <p>Precio: ${corte.precio}</p>
          <img src="${corte.imagen}" alt="Corte ${corte.nombre}" data-descripcion="${corte.descripcion}" data-precio="${corte.precio}" loading="lazy">
        `;
        galeria.appendChild(div);
      });
      
    }

    cargarGaleria();

    galeria.addEventListener("click", e => {
      if (e.target.tagName === "IMG") {
        modal.style.display = "flex";
        infoImg.src = e.target.src;
        infoText.textContent = e.target.getAttribute("data-descripcion");
        infoPrecio.textContent = "Precio: " + e.target.getAttribute("data-precio");
      }
      
    });

    cerrar.addEventListener("click", () => modal.style.display = "none");
    modal.addEventListener("click", e => { if (e.target === modal) modal.style.display = "none"; });
    buscador.addEventListener("input", e => cargarGaleria(e.target.value));

    // Modal Contacto
    const botonContacto = document.getElementById("boton-contacto");
    const modalContacto = document.getElementById("modal-contacto");
    const cerrarContacto = document.getElementById("cerrar-contacto");
    botonContacto.addEventListener("click", () => modalContacto.style.display = "flex");
    cerrarContacto.addEventListener("click", () => modalContacto.style.display = "none");
    modalContacto.addEventListener("click", e => { if(e.target===modalContacto) modalContacto.style.display="none"; });

    // Modal Reserva
    const botonReserva = document.getElementById("boton-reserva");
    const modalReserva = document.getElementById("modal-reserva");
    const cerrarReserva = document.getElementById("cerrar-reserva");
    const formReserva = document.getElementById("form-reserva");
    const mensajeExito = document.getElementById("mensaje-exito");
    botonReserva.addEventListener("click", () => modalReserva.style.display = "flex");
    cerrarReserva.addEventListener("click", () => { modalReserva.style.display="none"; formReserva.reset(); mensajeExito.style.display="none"; });
    modalReserva.addEventListener("click", e => { if(e.target===modalReserva){ modalReserva.style.display="none"; formReserva.reset(); mensajeExito.style.display="none"; } });
    formReserva.addEventListener("submit", e => { e.preventDefault(); mensajeExito.style.display="block"; setTimeout(()=>{ modalReserva.style.display="none"; formReserva.reset(); mensajeExito.style.display="none"; },2000); });

 
    // Modal Horario
    const botonHorario = document.getElementById("boton-horario");
    const modalHorario = document.getElementById("modal-horario");
    const cerrarHorario = document.getElementById("cerrar-horario");
    botonHorario.addEventListener("click", ()=>modalHorario.style.display="flex");
    cerrarHorario.addEventListener("click", ()=>modalHorario.style.display="none");
    modalHorario.addEventListener("click", e=>{if(e.target===modalHorario) modalHorario.style.display="none";});
    
  </script> 
  
</body>

</html>
