---
layout: splash
permalink: /test1/
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



.arch-card {
  position: relative;
  width: 250px;
  height: 200px;
  margin: 0 auto;
  background: var(--cyan);
  
  border-radius: 22px;
  border: 4px solid var(--box-stroke);
  
  
  cursor: pointer;

  display: flex;
  flex-direction: column;
}


.pos-von-neumann        { grid-row: 1; grid-column: 1; }
.pos-caches             { grid-row: 1; grid-column: 2; }
.pos-machine-arch       { grid-row: 2; grid-column: 2; }
.pos-gpu                { grid-row: 2; grid-column: 3; }
.pos-mpi                { grid-row: 3; grid-column: 3; }
.pos-shared-memory      { grid-row: 3; grid-column: 4; }
.pos-vectorisation      { grid-row: 1; grid-column: 4; }
.pos-roofline           { grid-row: 1; grid-column: 5; }
.pos-strong-scaling     { grid-row: 2; grid-column: 5; }
.pos-weak-scaling       { grid-row: 2; grid-column: 6; }



.arch-card:hover {
  transform: translateY(-2px);
  filter: brightness(0.97);
  background: var(--pink);
}

.arch-card .title {
  font-weight: 700;
  font-size: 30px;
  text-align: center;
  line-height: 1.2;
  margin-left:1rem;
  margin-right:1rem;
}





.connections {
  position: absolute;
  top: 0;
  left: 0;
  pointer-events: none;
  z-index: 0;
}

.graph-grid {
  display: grid;
  width: 100vw;
  margin-left: calc(50% - 50vw);
  margin-right: calc(50% - 50vw);
  grid-template-columns: repeat(6, 1fr);
  grid-template-rows: repeat(5, 1fr);
  gap: 60px;
  position: relative; /* para el SVG */
}



.arch-card.active {
  background: var(--pink);
  opacity: 1;
  transform: translateY(-2px);
}

.arch-card.active .title {
  font-size: 22px;
}

.arch-card.active .card-content {
  justify-content: flex-start;
}

.arch-card.active .actions {
  display: flex;
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





.card-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  gap: 1px;
}



.arch-card .actions {
  display: none;
  width: 100%;
  gap: 10px;
  flex-direction: column;
}






.btn {
  text-decoration: none;
  background: #ffffff;
  color: #042f39;
  margin-bottom: 5px;
  border-radius: 10px;
  font-size: 20px;
  font-weight: 600;
  text-align: center;
}

.btn.secondary {
  background: rgba(255,255,255,0.85);
}

.arch-card.before {
  background: #DACDA2; 
  opacity: 1;
}


.arch-card.after {
  background: #00AEEF; 
  opacity: 1;
}



.instructions {
  position: absolute;
  width: 450px;
  height: 200px;
  background: var(--purple);
  border-radius: 22px;
  border: 1px solid var(--box-stroke);
  box-sizing: border-box;
  padding: 20px;
  cursor: pointer;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  box-shadow: 0 6px 0 rgba(0, 0, 0, 0.45);
  transition: opacity 0.2s ease, background 0.2s ease, transform 0.1s ease;
    
  z-index: 1;
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

.close-btn {
  position: absolute;
  top: 12px;
  right: 16px;
  font-size: 32px;
  background: none;
  border: none;
  color: white;
  cursor: pointer;
}

/* Responsive */
@media (max-width: 720px) {
  .card {
    transform: scale(0.8);
    transform-origin: center top;
  }
}


.canvas {
  position: relative;

  transform-origin: top left; /* importante para escalar desde la esquina */
}




  </style>




<div class="section" id="canvas">

<div class="graph-grid">
    
<svg id="connections" class="connections" width="1920" height="1200"
     viewBox="0 0 1920 1200" preserveAspectRatio="xMinYMin slice">
 <defs>
  <!-- Flecha normal -->
<marker id="arrow-end"
  viewBox="0 0 10 10"
  refX="10"
  refY="5"
  markerWidth="10"
  markerHeight="10"
  orient="auto"
          markerUnits="userSpaceOnUse">
    <path d="M 0 0 L 10 5 L 0 10 z" fill="context-stroke"/>
  </marker>

  <!-- Flecha invertida -->
  <marker id="arrow-start"
          viewBox="0 0 10 10"
          refX="1"
          refY="5"
          markerWidth="6"
          markerHeight="6"
          orient="auto"
          markerUnits="userSpaceOnUse">
    <path d="M 10 0 L 0 5 L 10 10 z" fill="context-stroke"/>
  </marker>
</defs>

</svg>




<div
  id="von-neumann"
  class="arch-card pos-von-neumann"
  onclick="nodeClick(this, event);"

>
  <div class="card-content">
    <div class="title">Von Neumann Architecture</div>

    <div class="actions">
<a class="btn" href="#" onclick="openVideo('3ru-v3sAdqw',
'Von Neumann Architecture',
'Professor Tobias Weinzierl'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>




      <a class="btn secondary" href="#">Additional material</a>
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
<a class="btn" href="#" onclick="openVideo('wPjtwACmaUg',
'Caches',
'Professor Tobias Weinzierl'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>

      <a class="btn secondary" href="#">Additional material</a>
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
<a class="btn" href="#" onclick="openVideo('wPjtwACmaUg',
'Machine Architectures (Flynn’s Taxonomy)',
'Dr. Mladen Ivkovic'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>

      <a class="btn secondary" href="#">Additional material</a>
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
<a class="btn" href="#" onclick="openVideo('wPjtwACmaUg',
'GPU Architecture',
'Dr. Christopher Marcotte'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>


      <a class="btn secondary" href="#">Additional material</a>
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
<a class="btn" href="#" onclick="openVideo('wPjtwACmaUg',
'MPI',
'Dr. Christopher Marcotte'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>


      <a class="btn secondary" href="#">Additional material</a>
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


      <a class="btn secondary" href="#">Additional material</a>
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
<a class="btn" href="#" onclick="openVideo('wPjtwACmaUg',
'Shared-Memory Parallel Paradigms',
'Dr. Mladen Ivkovic'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>


      <a class="btn secondary" href="#">Additional material</a>
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
<a class="btn" href="#" onclick="openVideo('wPjtwACmaUg',
'Roofline',
'Professor Tobias Weinzirl'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>




      <a class="btn secondary" href="#">Additional material</a>
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
<a class="btn" href="#" onclick="openVideo('wPjtwACmaUg',
'Strong Scaling',
'Dr. Christopher Marcotte'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>



      <a class="btn secondary" href="#">Additional material</a>
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
<a class="btn" href="#" onclick="openVideo('wPjtwACmaUg',
'Weak Scaling',
'Dr. Christopher Marcotte'
);
event.stopPropagation(); return false;">
  Watch lecture
</a>

      <a class="btn secondary" href="#">Additional material</a>
    </div>
  </div>
</div>


</div>

</div>
  </section>
  
  
  
  




<!-- ===== Video Modal ===== -->
<div id="video-modal" class="video-modal" onclick="closeVideo()">
  <div class="video-modal-content" onclick="event.stopPropagation()">
    <button class="close-btn" onclick="closeVideo()">×</button>

    <h2 id="video-title"></h2>
    <p id="video-lecturer"></p>

    <div class="video-wrapper">
      <iframe
        id="video-iframe"
        src=""
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen>
      </iframe>
    </div>
  </div>
</div>


<script>

const forward = {};   // id → hijos
const backward = {};  // id → padres

 


function clipLineBothEnds(a, b, cardA, cardB) {
  const aClipped = clipLineToCard(b, a, cardA);
  const bClipped = clipLineToCard(a, b, cardB);
  return { a: aClipped, b: bClipped };
}


const graph = {};   // relaciones nodo → nodos conectados
const lines = [];   // referencias a las líneas SVG

  // Define aquí tus conexiones (MUY limpio)
  window.onload = () => {
    connect("von-neumann", "caches");
    connect("von-neumann", "machine-architectures");
    connect("machine-architectures", "GPU");
    connect("machine-architectures", "MPI");
    connect("MPI", "shared-memory");
    connect("shared-memory", "strong-scaling");
    connect("caches", "vectorisation");
    connect("vectorisation", "roofline");
    connect("strong-scaling", "weak-scaling");
  };
</script>



<script>
  // ======== Configuración del diseño base (usa tus medidas originales) ========
  const DESIGN_W = 1920;
  const DESIGN_H = 1200;

  // ======== Referencias ========
  const canvas = document.getElementById('canvas');        // contenedor del lienzo
  const svg     = document.getElementById('connections');   // <svg> de líneas

  // Guardamos el factor de escala actual para invertir coordenadas al trazar
  let _currentScale = 1;
  function getCurrentScale() { return _currentScale; }

  // ======== Escalado proporcional del canvas ========
  function scaleCanvas() {
    const vw = window.innerWidth;
    const vh = window.innerHeight;
    const scale = Math.min(vw / DESIGN_W, vh / DESIGN_H);
    _currentScale = scale;
    if (canvas) canvas.style.transform = `scale(${scale})`;
  }

  // ======== Utilidades de geometría ========
  function centerOf(el) {
    // centro del elemento en coordenadas del "diseño base" (no escaladas)
    const r = el.getBoundingClientRect();
    const parent = canvas.getBoundingClientRect();
    const s = getCurrentScale();
    return {
      x: (r.left - parent.left) / s + (r.width  / s) / 2,
      y: (r.top  - parent.top ) / s + (r.height / s) / 2
    };
  }

function connect(from, to, dashed = false) {
  const aEl = document.getElementById(from);
  const bEl = document.getElementById(to);
  if (!aEl || !bEl) return;

  forward[from] = forward[from] || new Set();
  backward[to]  = backward[to]  || new Set();
  forward[from].add(to);
  backward[to].add(from);

  const aCenter = centerOf(aEl);
  const bCenter = centerOf(bEl);

  const clipped = clipLineBothEnds(aCenter, bCenter, aEl, bEl);

  const line = document.createElementNS(
    'http://www.w3.org/2000/svg',
    'line'
  );

  line.setAttribute('x1', clipped.a.x);
  line.setAttribute('y1', clipped.a.y);
  line.setAttribute('x2', clipped.b.x);
  line.setAttribute('y2', clipped.b.y);

  line.dataset.from = from;
  line.dataset.to   = to;

  if (dashed) line.setAttribute('stroke-dasharray', '4,6');

  line.setAttribute('stroke', '#ffffff');
  line.setAttribute('stroke-width', '6');
  line.setAttribute('marker-end', 'url(#arrow-end)');

  svg.appendChild(line);
  lines.push(line);
}



  function redrawConnections() {
  if (!svg) return;

  // Guardamos el <defs> de la flecha
  const defs = svg.querySelector('defs');

  // Limpiamos todo el SVG
  svg.innerHTML = '';

  // Volvemos a poner el <defs>
  if (defs) svg.appendChild(defs);
  
  lines.length = 0;

    connect("von-neumann", "caches");
    connect("von-neumann", "machine-architectures");
    connect("machine-architectures", "GPU");
    connect("machine-architectures", "vectorisation");
    connect("machine-architectures", "MPI"); 
    connect("MPI", "strong-scaling", true); 
    connect("MPI", "shared-memory", true); 
    connect("GPU", "vectorisation", true); 
    connect("GPU", "shared-memory", true); 
    connect("shared-memory", "strong-scaling", true);
    connect("caches", "vectorisation");
    connect("vectorisation", "roofline");
    connect("strong-scaling", "weak-scaling");
  }

  // ======== Ciclo de vida ========
  function onResize() {
    scaleCanvas();
    redrawConnections();
  }

  window.addEventListener('load', onResize);
  window.addEventListener('resize', onResize);

  // ======== Ejemplo de handler de click (opcional) ========






function nodeClick(node, event) {
  event.stopPropagation();

  const id = node.id;
  const cards = document.querySelectorAll('.arch-card');

  cards.forEach(c =>
    c.classList.remove('active', 'before', 'after', 'connected', 'unrelated')
  );

  node.classList.add('active');

  lines.forEach(l => {
    l.classList.remove('before-line', 'after-line', 'dimmed-line');
    l.removeAttribute('marker-start');
    l.setAttribute('marker-end', 'url(#arrow-end)');
  });

  const after = forward[id] || new Set();
  after.forEach(child => {
    document.getElementById(child)?.classList.add('after');

    lines.forEach(l => {
      if (l.dataset.from === id && l.dataset.to === child) {
        l.classList.add('after-line');
      }
    });
  });

  const before = backward[id] || new Set();
  before.forEach(parent => {
    document.getElementById(parent)?.classList.add('before');

    lines.forEach(l => {
      if (l.dataset.from === parent && l.dataset.to === id) {
        l.classList.add('before-line');
        l.removeAttribute('marker-end');
        l.setAttribute('marker-start', 'url(#arrow-start)');
      }
    });
  });

  lines.forEach(l => {
    if (
      !l.classList.contains('before-line') &&
      !l.classList.contains('after-line')
    ) {
      l.classList.add('dimmed-line');
    }
  });

  cards.forEach(c => {
    if (
      !c.classList.contains('active') &&
      !c.classList.contains('before') &&
      !c.classList.contains('after')
    ) {
      c.classList.add('unrelated');
    }
  });
}








window.nodeClick = nodeClick;

  // Expón nodeClick si lo usas en HTML inline
  window.nodeClick = nodeClick;
  
  
</script>


<script>
function openVideo(videoId, title, lecturer) {
  const modal = document.getElementById('video-modal');
  const iframe = document.getElementById('video-iframe');

  document.getElementById('video-title').textContent = title;
  document.getElementById('video-lecturer').textContent = lecturer;

  iframe.src = `https://www.youtube.com/embed/${videoId}?autoplay=1`;

  modal.style.display = 'flex';
}

function closeVideo() {
  const modal = document.getElementById('video-modal');
  const iframe = document.getElementById('video-iframe');

  iframe.src = ''; // para parar el vídeo
  modal.style.display = 'none';
}
</script>






