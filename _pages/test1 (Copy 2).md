---
layout: splash
permalink: /
title: ""          # quita el título
search: false      # desactiva la barra de búsqueda
---



<style>

:root {
  --bg: #042f39; /* page background */
  --purple: #6c2a68; /* header/panel */
  --cyan: #17aee0; /* boxes */
  --box-stroke: #ffffff;
  --panel-dark: #4b1f45;
  --muted: #cfc8b5;
  --light: #ffffff;
  --pink: #CBA8B1;
}



body {
  background: var(--bg);
  color: var(--light);
}


.graph-grid {
  display: grid;
  position: relative;

  margin-top: 1rem;
 row-gap: 30px !important;   /* vertical entre filas */
column-gap: 10px; 

  /* ===== DESKTOP (layout principal) ===== */
  grid-template-columns: repeat(6, 1fr);
  grid-template-rows: repeat(4, minmax(180px, auto));

  grid-template-areas:
    "von caches . vector roofline ."
    ". machine gpu . strong weak"
    ". . mpi shared . ."
    ". . . . . ."
    ". . . . . .";

  justify-items: center;
  align-items: center;
}




.card-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  gap: 1px;
}


.card-content: hoover{
background: #064756;      /* fondo ligeramente más claro / verde azulado */
  transform: translateY(-2px);  /* sube un poquito */
  box-shadow: 0 4px 8px rgba(0,0,0,0.4); /* sombra más marcada */
  filter: brightness(1.1);   /* un pequeño brillo */

}

.arch-card {
  position: relative;
  width: 150px;
  height: 150px;
  margin: 0 auto;
  background: var(--cyan);
  
  border-radius: 22px;
  border: 4px solid var(--box-stroke);
  
  
  cursor: pointer;

  display: flex;
  flex-direction: column;
}



.arch-logos {
  width: 200px;
  height: 150px;

  border-radius: 24px;

  display: grid;
  grid-template-rows: auto 1fr auto;
  gap: 18px;

  padding: 24px 22px;
  cursor: default;
}


.pos-cc                 { grid-row: 1; grid-column: 6; }
.pos-von-neumann        { grid-row: 1; grid-column: 1; }
.pos-caches             { grid-row: 1; grid-column: 2; }
.pos-machine-arch       { grid-row: 2; grid-column: 2; }
.pos-gpu                { grid-row: 2; grid-column: 3; }
.pos-mpi                { grid-row: 3; grid-column: 3; }
.pos-shared-memory      { grid-row: 4; grid-column: 4; }
.pos-vectorisation      { grid-row: 1; grid-column: 4; }
.pos-roofline           { grid-row: 1; grid-column: 5; }
.pos-strong-scaling     { grid-row: 2; grid-column: 5; }
.pos-weak-scaling       { grid-row: 2; grid-column: 6; }
.pos-instructions      { grid-row: 3; grid-column: 1; }
.pos-link              { grid-row: 4; grid-column: 1; }
.pos-logos             { grid-row: 3; grid-column: 6; }




.arch-card:hover {
  transform: translateY(-2px);
  filter: brightness(0.97);
  background: var(--pink);
}

.arch-card .title {
  font-weight: 700;
  font-size: 20px;
  text-align: center;
  line-height: 1.2;
  margin-left:0.1rem;
  margin-right:0.1rem;
}


.arch-card.active {
  background: var(--pink);
  opacity: 1;
  transform: translateY(-2px);
  display: flex;
  align-items: center;
}

.arch-card.active .title {
  font-size: 15px;
  margin-bottom:0.1rem !important;
    margin-top:0.1rem !important;
}

.arch-card.active .btn {
  background: var(--bg);  /* fondo blanco */
  color: #ffffff ;     /* texto oscuro (para contraste con fondo blanco) */
  font-weight: 600;
  font-size: 12px;
  width: 130px;
  text-align: center;
  border-radius: 22px;
}

.arch-card.active .btn:hover {
  background: #064756;      /* fondo ligeramente más claro / verde azulado */
  transform: translateY(-2px);  /* sube un poquito */
  box-shadow: 0 4px 8px rgba(0,0,0,0.4); /* sombra más marcada */
  filter: brightness(1.1);   /* un pequeño brillo */
}






.arch-card.active .card-content {
  display: flex;
  flex-direction: column;
  justify-content: center;  
  align-items: center;      
  height: 100%;
  gap: 1px;                
}

.arch-card.active .actions {
  display: flex;
  flex-direction: column;
  justify-content: center; 
  align-items: center;
  gap: 2px;               
}





.arch-card.connected {
  background: #0fb3a2; 
  opacity: 1;
}

.arch-card.unrelated {
  background: #042F39;     
  color: #064756;           
  opacity: 1;
  border: 4px solid #064756;
}



.arch-card.unrelated .title {
  color: #064756;
}



.arch-card .actions {
  display: none;
  width: 100%;
  gap: 10px;
  flex-direction: column;
}




.arch-card.before {
  background: #DACDA2; /* amarillo */
}

.arch-card.connected {
  background: #F3B495; /* ← esto cámbialo a naranja */
}

.arch-card.after {
  background: #00AEEF; /* azul */
}


.arch-card.unrelated {
  background: #042F39;
  color: #064756;
  opacity: 1;
  border: 4px solid #064756;
}

.arch-card.unrelated .title {
  color: #064756;
}



#arrows-layer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 0;
}

.graph-grid {
  position: relative;
  z-index: 1;
}




.arrow {
  stroke: #355f6b;
  stroke-width: 2;
  fill: none;
    stroke-linejoin: round;
  stroke-linecap: round;
}


.arrow.active {
  opacity: 1;
}

.arrow-before {
  stroke: #DACDA2;                 /* amarillo */
  stroke-dasharray: 6 6;           /* DISCONTINUA */
}

.arrow-required {
  stroke: #F3B495;                 /* naranja */
}

.arrow-after {
  stroke: #00AEEF;                 /* azul */
}




.video-modal {
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.75);
  display: none;
  align-items: center;
  justify-content: center;
  z-index: 9999;
}

.video-modal-content {
  background: #CBA8B1;
  border-radius: 16px;
  padding: 24px;
  width: 90%;
  max-width: 900px;
  color: white;
  position: relative;
}

.video-modal h2 {
  margin: 0 0 4px 0;
  font-size: 50px;
  text-align: center;
   color: #042f39;
}

.video-modal p {
  margin: 0 0 16px 0;
  opacity: 0.85;
    color: #042f39;
}

.video-wrapper {
  position: relative;
  padding-top: 56.25%; /* 16:9 */
}

.video-wrapper iframe {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  border-radius: 12px;
}

.arch-ins {
  width: 300px;
  min-height: 100px;

  background: #042f39; 


  padding: 24px;
  cursor: default;
}


.arch-ins:hover {
  transform: translateY(-3px);
  filter: brightness(1.05);
}



.arch-ins .title {
  font-size: 30px;
  font-weight: 800;
  letter-spacing: 0.5px;
  text-transform: uppercase;
  text-align: center;
  color: #ffe8a3;
}

.arch-ins p {
  font-size: 14px;
  line-height: 1.55;
  color: #f3eee2;
  text-align: center;
  opacity: 0.9;
}


.legend {
  display: grid;
  grid-template-columns: 1fr;
  gap: 12px;
  margin-top: 12px;
}

.legend-item {
  display: grid;
  grid-template-columns: 30px 1fr; /* caja + texto */
  align-items: center;
  column-gap: 12px;

  font-size: 17px;
  font-weight: 500;
  color: #ffffff;

  margin: 0; /* 🔴 elimina desplazamientos */
}

.legend-item h1{
  font-size: 14px !important;
  margin-left:30px !important;
  margin-top: 15px!important;
}

.legend h1{
font-size:15px;
margin-left:10px;
 font-weight: 500;
  color: #ffffff;
}


#link.arch-ins {
  width: 300px;
  min-height: auto;
  padding: 12px 16px;

  display: flex;
  justify-content: center;
  align-items: center;

  background: var(--pink);
  border-radius: 16px;
  border: 2px solid var(--box-stroke);
  box-shadow: 0 4px 6px rgba(0,0,0,0.3);
  transition: transform 0.2s, filter 0.2s;
}




#link.arch-ins a {
  font-size: 20px;
  font-weight: 600;
  color: #042f39;
  text-align: center;
  width: 100%;
  margin: 0;
  cursor: pointer;
}



.logo-small {
  max-width: 100px;
  max-height:100px;
  width: auto; height: auto; object-fit: contain; display: block;
}

.logo-medium {
  max-width: 200px;
  max-height:200px;
  width: auto; height: auto; object-fit: contain; display: block;
}

.logo-large {
  max-width: 200px;
  max-height:200px;
  width: auto; height: auto; object-fit: contain; display: block;
}


.color-box.before {
  background: #DACDA2;
}

.color-box.connected {
  background: #F3B495;
}

.color-box.after {
  background: #00AEEF;
}

.arch-ins .card-content p {
  color: #FFF8DC;
}

.color-box {
  width: 50px;
  height: 50px;
  border-radius: 8px;
  border: 2px solid var(--box-stroke);
  margin: 0; /* 🔑 clave */
}


/* colores según tus clases */
.color-box.before {
  background: #DACDA2; /* amarillo */
}

.color-box.connected {
  background: #F3B495; /* naranja */
}

.color-box.after {
  background: #00AEEF; /* azul */
}

.page-title-box {
  width: 100%;
  max-width: 1100px;

  background: linear-gradient(180deg, #6c2a68 0%, #4b1f45 100%);
  border-radius: 26px;
  border: 1px solid var(--box-stroke);

  box-shadow:
    0 12px 28px rgba(0,0,0,0.45),
    inset 0 1px 0 rgba(255,255,255,0.15);

  padding: 28px 36px;
  margin: 0 auto 32px auto;

  text-align: center;
}

.page-title-box h1 {
  font-size: 25px;
  font-weight: 900;
  letter-spacing: 1px;
  text-transform: uppercase;

  color: #ffffff;
  margin-top: 0.15rem;
    margin-bottom: 0.15rem;
}

.page-title-box p {
  font-size: 15px;
  line-height: 1.5;
  color: #f3eee2;
  opacity: 0.9;
  margin: 0;
}







.canvas-scale {
  transform-origin: top center;
}

@media (max-width: 768px) {
body {
  background: var(--bg);
}
  .canvas-scale {
    transform: scale(0.7);
  }
}


.initial-content,
.page-content,
#main {
  overflow: visible !important;
}




</style>







<br>

<div class="page-title-box">
  <h1>High-Performance Computing Concepts</h1>
</div>



<div class="canvas-scale">
  <div class="graph-grid">

    <svg id="arrows-layer"></svg>

    <!-- cards aquí -->





<div
  id="instructions"
  class="arch-ins pos-instructions"
>
  

  <div class="legend">
    <div class="legend-item">
      <span class="color-box before"></span>
     <h1> Previous suggested lecture</h1>
    </div>
    <div class="legend-item">
      <span class="color-box connected"></span>
      <h1>Previous required lecture</h1>
    </div>
    <div class="legend-item">
      <span class="color-box after"></span>
     <h1> Next suggested lecture</h1>
    </div>
  </div>

  
</div>


<div id="link" class="arch-ins pos-link">
  <a href="https://training-academy.dirac.ac.uk/course/section.php?id=66">
    Access the full course on the DiRAC Training Academy
  </a>
</div>





<div
  id="logos"
  class="arch-logos pos-logos"
>
  

  <div class="legend">
<div class="legend">
  <img src="https://github.com/mzhc13/high-performance-computing-concepts-course/blob/main/assets/images/durham.png?raw=true" class="logo-large" alt="Durham">
  <img src="https://github.com/mzhc13/high-performance-computing-concepts-course/blob/main/assets/images/ukri.png?raw=true" class="logo-medium" alt="UKRI">
  <img src="https://github.com/mzhc13/high-performance-computing-concepts-course/blob/main/assets/images/dirac.png?raw=true" class="logo-small" alt="DiRAC">
</div>

  </div>

</div>


<div
  id="logos"
  class="arch-logos pos-cc"
>
  <div class="legend">
  
  <img src="https://github.com/mzhc13/high-performance-computing-concepts-course/blob/main/assets/images/cc.png?raw=true" alt="Logo 1">
  </div>

</div>








<div
  id="von-neumann"
  class="arch-card pos-von-neumann"
  onclick="nodeClick(this, event);"

>
   <div class="card-content">
    <div class="title">Von Neumann Architecture</div>

    <div class="actions">
<a class="btn" href="#" onclick="openVideo('3ru-v3sAdqw?si=Jj8Koun21HpjFCLY',
'Von Neumann Architecture',
'Professor Tobias Weinzierl'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>

      <a class="btn secondary" href="https://training-academy.dirac.ac.uk/course/section.php?id=57">Additional material</a>
    </div>
  </div>
</div>



  
  
  


  
  
<div
  id="caches"
  class="arch-card pos-caches"
  onclick="nodeClick(this, event);"

>
  <div class="card-content">
    <div class="title">Caches</div>

    <div class="actions">
<a class="btn" href="#" onclick="openVideo('ZPXYoJJo8qA?si=ZlX967WyjtxgpLWm',
'Caches',
'Professor Tobias Weinzierl'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>

      <a class="btn secondary" href="https://training-academy.dirac.ac.uk/course/section.php?id=66">Additional material</a>
    </div>
  </div>
</div>


<div
  id="machine-architectures"
  class="arch-card pos-machine-arch"
 onclick="nodeClick(this, event);"

>

  <div class="card-content">
    <div class="title">Machine Architectures (Flynn’s Taxonomy)</div>

    <div class="actions">
<a class="btn" href="#" onclick="openVideo('jWFImJ-5Gtg?si=BBZou2CJvwDj7EC-',
'Machine Architectures (Flynn’s Taxonomy)',
'Dr. Mladen Ivkovic'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>

      <a class="btn secondary" href="https://training-academy.dirac.ac.uk/course/section.php?id=67">Additional material</a>
    </div>
  </div>
</div>
  
  
  

 <div
  id="GPU"
  class="arch-card pos-gpu"
  onclick="nodeClick(this, event);"

>


  <div class="card-content">
    <div class="title">GPU Architecture</div>

    <div class="actions">
<a class="btn" href="#" onclick="openVideo('8axA0RUaxRA?si=kwFcCVbDKzJw3vw4',
'GPU Architecture',
'Dr. Christopher Marcotte'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>


      <a class="btn secondary" href="https://training-academy.dirac.ac.uk/course/section.php?id=60">Additional material</a>
    </div>
  </div>
</div>




 <div
  id="MPI"
  class="arch-card pos-mpi"
  onclick="nodeClick(this, event);"

>


  <div class="card-content">
    <div class="title">MPI</div>

    <div class="actions">
<a class="btn" href="#" onclick="openVideo('i-88l2K9824?si=5hG4_gn3DE3_r6Tq',
'MPI',
'Dr. Christopher Marcotte'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>


      <a class="btn secondary" href="https://training-academy.dirac.ac.uk/course/section.php?id=61">Additional material</a>
    </div>
  </div>
</div>


 <div
  id="vectorisation"
  class="arch-card pos-vectorisation"
  onclick="nodeClick(this, event);"

>


  <div class="card-content">
    <div class="title">Vectorisation</div>

    <div class="actions">
<a class="btn" href="#" onclick="openVideo('wPjtwACmaUg',
'Vectorisation',
'Dr. Thomas Flynn'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>


      <a class="btn secondary" href="https://training-academy.dirac.ac.uk/course/section.php?id=62">Additional material</a>
    </div>
  </div>
</div>


 <div
  id="shared-memory"
  class="arch-card pos-shared-memory"
  onclick="nodeClick(this, event);"

>


  <div class="card-content">
    <div class="title">Shared-Memory Parallel Paradigms</div>

    <div class="actions">
<a class="btn" href="#" onclick="openVideo('iwb17_aCSRA?si=NGorUytvUqWRMWEZ',
'Shared-Memory Parallel Paradigms',
'Dr. Mladen Ivkovic'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>


      <a class="btn secondary" href="https://training-academy.dirac.ac.uk/course/section.php?id=93">Additional material</a>
    </div>
  </div>
</div>






 <div
  id="roofline"
  class="arch-card pos-roofline"
  onclick="nodeClick(this, event);"

>


  <div class="card-content">
    <div class="title">Roofline</div>

    <div class="actions">
<a class="btn" href="#" onclick="openVideo('uhYFZrqe9VY?si=TbG28ic8nFSU0kAm',
'Roofline',
'Professor Tobias Weinzirl'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>




      <a class="btn secondary" href="https://training-academy.dirac.ac.uk/course/section.php?id=63">Additional material</a>
    </div>
  </div>
</div>


 <div
  id="strong-scaling"
  class="arch-card pos-strong-scaling"
  onclick="nodeClick(this, event);"

>


  <div class="card-content">
    <div class="title">Strong Scaling</div>

    <div class="actions">
<a class="btn" href="#" onclick="openVideo('99VgSkjLQM4?si=YqCN8fMLu2iB4Tt6',
'Strong Scaling',
'Dr. Christopher Marcotte'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>



      <a class="btn secondary" href="https://training-academy.dirac.ac.uk/course/section.php?id=65">Additional material</a>
    </div>
  </div>
</div>

 <div
  id="weak-scaling"
  class="arch-card pos-weak-scaling"
  onclick="nodeClick(this, event);"

>
   <div class="card-content">
    <div class="title">Weak Scaling</div>

    <div class="actions">
<a class="btn" href="#" onclick="openVideo('dVZqpXi5BRE?si=pNSgIwWY38rt4W12',
'Weak Scaling',
'Dr. Christopher Marcotte'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>

      <a class="btn secondary" href="https://training-academy.dirac.ac.uk/course/section.php?id=64">Additional material</a>
    </div>
  </div>
</div>



<!-- Modal para video -->
<div id="video-modal" class="video-modal" onclick="closeVideo()">
  <div class="video-modal-content" onclick="event.stopPropagation();">
    <h2 id="video-title">Title</h2>
    <p id="video-lecturer">Lecturer</p>
    <div class="video-wrapper">
      <iframe id="video-iframe" src="" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
    </div>
    <button onclick="closeVideo()" style="position:absolute;top:10px;right:10px;font-size:20px;background:none;border:none;color:#042f39;cursor:pointer;">×</button>
  </div>
</div>



</div>

</div>




<script>
/* =========================
   RELACIONES ENTRE NODOS
========================= */

const relations = {
"von-neumann": {
  suggestedPrev: [],
  requiredPrev: [],
  next: [
    { id: "caches", portFrom: "R", portTo: "L" },
    { id: "machine-architectures", portFrom: "B", portTo: "L" }
  ]
}


,

  "caches": {
    suggestedPrev: [],
    requiredPrev: [ 
    { id: "von-neumann", portFrom: "L", portTo: "R" }],
    next: [
    { id: "vectorisation", portFrom: "R", portTo: "L" }]
  },

"vectorisation": {
  suggestedPrev: [
    { id:"GPU", portFrom: "BL", portTo: "TR" },
    { id:"shared-memory", portFrom: "B", portTo: "T" }
  ],
  requiredPrev: [
    { id:"caches", portFrom: "L", portTo: "R" },
    { id:"machine-architectures", portFrom: "TR", portTo: "BL" }
  ],
  next: [
    {id: "roofline",  portFrom: "R", portTo: "L" }
  ]
}
,

  "machine-architectures": {
  suggestedPrev: [],
  requiredPrev: [
  {id: "von-neumann", portFrom: "L", portTo: "B"}],
  next: [
    {id: "vectorisation", portFrom: "BL", portTo: "TR"},
    {id: "GPU", portFrom: "R", portTo: "L"},
    {id: "MPI", portFrom: "B", portTo: "L"},
    {id: "shared-memory", portFrom: "B", portTo: "BL"}
  ]
},

GPU: {
  suggestedPrev: [],
  requiredPrev: [{id: "machine-architectures", portFrom: "R", portTo: "L"}],
  next: [
    {id: "vectorisation", portFrom: "TR", portTo: "BL"},
    {id: "shared-memory", portFrom: "R", portTo: "TL"}
  ]
},

"shared-memory": {
  suggestedPrev: [
    {id: "MPI", portFrom: "L", portTo: "B"},
    {id: "GPU", portFrom: "TL", portTo: "R"}
  ],
  requiredPrev: [
  {id: "machine-architectures", portFrom: "BL", portTo: "B"}],
  next: [
    {id: "strong-scaling", portFrom: "R", portTo: "B"},
    {id: "vectorisation", portFrom: "T", portTo: "B"}
  ]
},


"MPI": {
  suggestedPrev: [],
  requiredPrev: [
  {id: "machine-architectures", portFrom: "L", portTo: "B"}],
  next: [
    {id: "strong-scaling", portFrom: "R", portTo: "BL"},
    {id: "shared-memory", portFrom: "B", portTo: "L"}
  ]
},

"roofline": {
  suggestedPrev: [],
  requiredPrev: [
  {id: "vectorisation", portFrom: "L", portTo: "R"}],
  next: []
},


"strong-scaling": {
  suggestedPrev: [
    {id: "MPI", portFrom: "R", portTo: "L"},
    {id: "shared-memory", portFrom: "B", portTo: "R"}
  ],
  requiredPrev: [],
  next: [
    {id: "weak-scaling", portFrom: "R", portTo: "L"}
  ]
},





"weak-scaling": {
  suggestedPrev: [],
  requiredPrev: [{id:
  "strong-scaling", portFrom: "L", portTo: "R"}],
  next: []
  }
};


/* =========================
   CLICK EN UNA CARD
========================= */


function intersectRect(cx, cy, hw, hh, dx, dy) {
  const tx = dx !== 0 ? hw / Math.abs(dx) : Infinity;
  const ty = dy !== 0 ? hh / Math.abs(dy) : Infinity;
  const t = Math.min(tx, ty);
  return {
    x: cx + dx * t,
    y: cy + dy * t
  };
}

function getPort(rect, port) {
  const x0 = rect.left;
  const y0 = rect.top;
  const w = rect.width;
  const h = rect.height;

  switch (port) {
    case "TL": return { x: x0,         y: y0 };
    case "T":  return { x: x0 + w/2,   y: y0 };
    case "TR": return { x: x0 + w,     y: y0 };

    case "L":  return { x: x0,         y: y0 + h/2 };
    case "R":  return { x: x0 + w,     y: y0 + h/2 };

    case "BL": return { x: x0,         y: y0 + h };
    case "B":  return { x: x0 + w/2,   y: y0 + h };
    case "BR": return { x: x0 + w,     y: y0 + h };
  }
}





function applyArrowStyle(line, type) {
  if (!type) return;
  line.classList.add("active", `arrow-${type}`);
}

</script>


<script>
// Abre el modal con el video
function openVideo(videoId, title, lecturer) {
  const modal = document.getElementById("video-modal");
  const iframe = document.getElementById("video-iframe");
  const titleEl = document.getElementById("video-title");
  const lecturerEl = document.getElementById("video-lecturer");

  // Seteamos contenido
  iframe.src = `https://www.youtube.com/embed/${videoId}?autoplay=1`;
  titleEl.textContent = title;
  lecturerEl.textContent = lecturer;

  // Mostramos el modal
  modal.style.display = "flex";
}

// Cierra el modal y detiene el video
function closeVideo() {
  const modal = document.getElementById("video-modal");
  const iframe = document.getElementById("video-iframe");

  // Ocultamos
  modal.style.display = "none";

  // Detenemos el video
  iframe.src = "";
}
</script>



<script>
const svg = document.getElementById("arrows-layer");

function createArrowheads(svg) {
  const defs = document.createElementNS("http://www.w3.org/2000/svg", "defs");
  defs.innerHTML = `
    <marker id="arrowhead-end"
      markerWidth="10"
      markerHeight="7"
      refX="10"
      refY="3.5"
      orient="auto"
      markerUnits="strokeWidth">
      <polygon points="0 0, 10 3.5, 0 7"
               fill="context-stroke"/>
    </marker>

    <marker id="arrowhead-start"
      markerWidth="10"
      markerHeight="7"
      refX="0"
      refY="3.5"
      orient="auto"
      markerUnits="strokeWidth">
      <polygon points="10 0, 0 3.5, 10 7"
               fill="context-stroke"/>
    </marker>
  `;
  svg.appendChild(defs);
}


createArrowheads(svg);


// Genera un key único para cada par (sin importar el orden)
function pairKey(a, b) {
  return [a, b].sort().join("__");
}

// Crea una línea base entre dos cards
function createBaseLine(a, b, portFrom = "R", portTo = "L") {
  const from = document.getElementById(a);
  const to   = document.getElementById(b);
  if (!from || !to) return null;

  const r1 = from.getBoundingClientRect();
  const r2 = to.getBoundingClientRect();
  const parent = document.querySelector(".graph-grid").getBoundingClientRect();

  const p1 = getPort(r1, portFrom); // punto de salida
  const p2 = getPort(r2, portTo);   // punto de llegada

  // coordenadas relativas al SVG
  p1.x -= parent.left; p1.y -= parent.top;
  p2.x -= parent.left; p2.y -= parent.top;

  // determinar dirección inicial del codo según puerto origen
  let mid = { x: p1.x, y: p1.y };
  // **Añadir margen**
  const margin = 12; // px, ajusta a tu gusto
  switch (portFrom) {
    case "L": p1.x -= margin; break;
    case "R": p1.x += margin; break;
    case "T": p1.y -= margin; break;
    case "B": p1.y += margin; break;
  }

  switch (portTo) {
    case "L": p2.x -= margin; break;
    case "R": p2.x += margin; break;
    case "T": p2.y -= margin; break;
    case "B": p2.y += margin; break;
  }
  
  if (portFrom === "L") mid.x = p2.x;         // salir horizontalmente
  else if (portFrom === "R") mid.x = p2.x;    // salir horizontalmente
  else if (portFrom === "T") mid.y = p2.y;    // salir vertical
  else if (portFrom === "B") mid.y = p2.y;    // salir vertical
  else if (portFrom === "TL" || portFrom === "TR") mid.y = p2.y;
  else if (portFrom === "BL" || portFrom === "BR") mid.y = p2.y;

  // crear path ortogonal: origen -> codo -> destino
  const path = document.createElementNS("http://www.w3.org/2000/svg", "path");
  path.setAttribute(
    "d",
    `M ${p1.x} ${p1.y}
     L ${mid.x} ${mid.y}
     L ${p2.x} ${p2.y}`
  );

  path.classList.add("arrow");
  svg.appendChild(path);
  return path;
}



// Dibuja relación entre dos nodes y asigna tipo según dirección
function drawRelation(from, rel) {
  const to = typeof rel === "string" ? rel : rel.id;
  const portFrom = rel.portFrom || "R";
  const portTo   = rel.portTo   || "L";

  const key = pairKey(from, to);

  let line = document.querySelector(`.arrow[data-key="${key}"]`);
  if (!line) {
    line = createBaseLine(from, to, portFrom, portTo);
    if (!line) return;

    line.dataset.key = key;
    line.dataset.a = from;
    line.dataset.b = to;
  }
}



// Aplica el estilo correcto según tipo de flecha
function applyArrowStyle(line, type) {
  if (!type) return;
  line.classList.add("active", `arrow-${type}`);
}

// Dibujar todas las relaciones definidas en `relations`
Object.entries(relations).forEach(([from, rel]) => {
  rel.next.forEach(r => drawRelation(from, r));
  rel.requiredPrev.forEach(r => drawRelation(r.id, { ...r, id: from }));
});


function styleArrowByNode(line, node, direction) {
  line.classList.add("active");

  if (node.classList.contains("connected")) {
    line.classList.add("arrow-required");
  } 
  else if (node.classList.contains("before")) {
    line.classList.add("arrow-before");
  } 
  else if (node.classList.contains("after")) {
    line.classList.add("arrow-after");
  }

  orientArrow(line, direction);
}


function orientArrow(line, fromSelected) {
  line.removeAttribute("marker-start");
  line.removeAttribute("marker-end");

  if (fromSelected === "to") {
    // flecha va hacia la card seleccionada
    line.setAttribute("marker-start", "url(#arrowhead-start)");
  } else {
    // flecha sale de la card seleccionada
    line.setAttribute("marker-end", "url(#arrowhead-end)");
  }
}


// Función al hacer click en una card
function nodeClick(card, event) {
  event.stopPropagation();
  const allCards = document.querySelectorAll(".arch-card");
  const id = card.id;

  // 1️⃣ limpiar estados
  allCards.forEach(c => {
    c.classList.remove("active","before","after","connected","unrelated");
  });

  // 2️⃣ marcar activa
  card.classList.add("active");

  // 3️⃣ colorear según relaciones
  if (relations[id]) {
const { suggestedPrev = [], requiredPrev = [], next = [] } = relations[id];

suggestedPrev.forEach(rel => {
  const rid = typeof rel === "string" ? rel : rel.id;
  const el = document.getElementById(rid);
  if (el) el.classList.add("before");
});

requiredPrev.forEach(rel => {
  const rid = typeof rel === "string" ? rel : rel.id;
  const el = document.getElementById(rid);
  if (el) el.classList.add("connected");
});

next.forEach(rel => {
  const rid = typeof rel === "string" ? rel : rel.id;
  const el = document.getElementById(rid);
  if (el) el.classList.add("after");
});


  }

  // 4️⃣ marcar unrelated
  allCards.forEach(c => {
    if (
      c !== card &&
      !c.classList.contains("before") &&
      !c.classList.contains("after") &&
      !c.classList.contains("connected")
    ) c.classList.add("unrelated");
  });

  // 5️⃣ actualizar flechas
const arrows = document.querySelectorAll(".arrow");

arrows.forEach(line => {
  line.classList.remove(
    "active",
    "arrow-before",
    "arrow-required",
    "arrow-after"
  );
  line.removeAttribute("marker-start");
  line.removeAttribute("marker-end");

  // la card seleccionada es A → flecha sale de ella
  if (line.dataset.a === id) {
    const other = document.getElementById(line.dataset.b);
    if (other) {
      styleArrowByNode(line, other, "from");
      // mover al final para que quede encima
      line.parentNode.appendChild(line);
    }
  } 
  // la card seleccionada es B → flecha va hacia ella
  else if (line.dataset.b === id) {
    const other = document.getElementById(line.dataset.a);
    if (other) {
      styleArrowByNode(line, other, "to");
      // mover al final para que quede encima
      line.parentNode.appendChild(line);
    }
  }
});




}


// Función para resetear todas las cards y flechas
function resetDiagram() {
  const allCards = document.querySelectorAll(".arch-card");
  const allArrows = document.querySelectorAll(".arrow");

  // Limpiar clases de las cards
  allCards.forEach(c => {
    c.classList.remove("active","before","after","connected","unrelated");
  });

  // Limpiar flechas
  allArrows.forEach(line => {
    line.classList.remove("active","arrow-before","arrow-required","arrow-after");
    line.removeAttribute("marker-start");
    line.removeAttribute("marker-end");
  });
}

// Click en el fondo del grid
document.querySelector(".graph-grid").addEventListener("click", function(e){
  // Solo si se hace click en el fondo, no en una card
  if (e.target === this) {
    resetDiagram();
  }
});
</script>
