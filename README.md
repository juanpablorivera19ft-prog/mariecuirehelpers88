<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
  <title>Marie Curie Helpers</title>
  <meta name="description" content="Plataforma abierta para ponerse al día con las clases grabadas y resumidas con IA.">
  <style>
:root {
  --bg: #f6f7fb;
  --card: #ffffff;
  --ink: #1d2230;
  --muted: #667085;
  --brand: #d92d3a;
  --brand-dark: #b21f2b;
  --accent: #7b4fd1;
  --line: #e4e7ef;
  --ok: #1a9b5b;
  --radius: 14px;
}
@media (prefers-color-scheme: dark) {
  :root {
    --bg: #12141b; --card: #1c1f2a; --ink: #eceef5; --muted: #9aa1b5; --line: #2c3040;
  }
}
* { box-sizing: border-box; }
body {
  margin: 0; background: var(--bg); color: var(--ink);
  font-family: system-ui, -apple-system, "Segoe UI", Roboto, sans-serif; line-height: 1.5;
}
a { color: var(--accent); }
.topbar {
  display: flex; align-items: center; gap: 12px; padding: 12px 20px;
  background: var(--brand); color: #fff; position: sticky; top: 0; z-index: 10;
}
.brand { color: #fff; text-decoration: none; font-weight: 800; letter-spacing: .06em; text-transform: uppercase; font-size: 1.1rem; }
.badge { background: #fff; color: var(--brand); font-weight: 700; border-radius: 99px; padding: 2px 10px; font-size: .75rem; }
.menu-btn { display: none; background: none; border: 0; color: #fff; font-size: 1.4rem; cursor: pointer; }

.layout { display: grid; grid-template-columns: 220px 1fr; min-height: calc(100vh - 100px); }
.sidebar { background: var(--card); border-right: 1px solid var(--line); padding: 16px 10px; }
.sidebar h3 { margin: 0 10px 8px; font-size: .75rem; text-transform: uppercase; letter-spacing: .08em; color: var(--muted); }
.sidebar a {
  display: block; padding: 9px 12px; border-radius: 10px; color: var(--ink);
  text-decoration: none; margin-bottom: 2px;
}
.sidebar a:hover { background: var(--bg); }
.sidebar a.active { background: var(--brand); color: #fff; }
.content { padding: 24px; max-width: 1000px; width: 100%; outline: none; }

h1 { margin: 0 0 4px; font-size: 1.6rem; }
.sub { color: var(--muted); margin: 0 0 20px; }

.grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(210px, 1fr)); gap: 14px; }
.card {
  background: var(--card); border: 2px solid var(--line); border-radius: var(--radius);
  padding: 16px; text-decoration: none; color: inherit; display: block; transition: .15s;
}
.card:hover { border-color: var(--brand); transform: translateY(-2px); }
.card .subject { font-size: .75rem; font-weight: 700; color: var(--accent); text-transform: uppercase; letter-spacing: .05em; }
.card h4 { margin: 6px 0; font-size: 1.05rem; }
.card .meta { color: var(--muted); font-size: .85rem; }

.back { display: inline-block; margin-bottom: 12px; text-decoration: none; font-weight: 600; }
.tabs { display: flex; gap: 6px; flex-wrap: wrap; margin: 16px 0; border-bottom: 1px solid var(--line); }
.tab {
  background: none; border: 0; padding: 10px 14px; cursor: pointer; color: var(--muted);
  font-weight: 600; border-bottom: 3px solid transparent; font-size: .95rem;
}
.tab.active { color: var(--brand); border-bottom-color: var(--brand); }

.panel { background: var(--card); border: 1px solid var(--line); border-radius: var(--radius); padding: 20px; margin-bottom: 16px; }
.panel h3 { margin-top: 0; }

.player { display: flex; align-items: center; gap: 14px; border: 2px solid var(--brand); border-radius: var(--radius); padding: 12px 16px; }
.play {
  width: 44px; height: 44px; border-radius: 50%; border: 2px solid var(--brand); background: none;
  color: var(--brand); font-size: 1.1rem; cursor: pointer; flex: none;
}
.wave { flex: 1; display: flex; align-items: center; gap: 2px; height: 48px; cursor: pointer; }
.wave i { flex: 1; background: var(--line); border-radius: 2px; min-width: 2px; }
.wave i.done { background: var(--brand); }
.time { font-variant-numeric: tabular-nums; color: var(--muted); font-size: .85rem; flex: none; }

.summary li { margin-bottom: 8px; }
.tag { display: inline-block; background: var(--bg); border: 1px solid var(--line); border-radius: 99px; padding: 2px 10px; font-size: .8rem; margin: 2px 4px 2px 0; }
.ai-note { color: var(--muted); font-size: .85rem; margin-top: 12px; }

.resource { display: flex; gap: 14px; align-items: center; padding: 12px 0; border-bottom: 1px solid var(--line); }
.resource:last-child { border-bottom: 0; }
.thumb { width: 96px; height: 60px; border: 2px solid var(--brand); border-radius: 8px; display: grid; place-items: center; font-size: 1.4rem; flex: none; }

.quiz { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 14px; }
.q { border: 1px solid var(--line); border-radius: 12px; padding: 14px; }
.q p { margin: 0 0 8px; font-weight: 600; }
.q label { display: block; padding: 6px 8px; border-radius: 8px; cursor: pointer; }
.q label:hover { background: var(--bg); }
.q label.right { background: color-mix(in srgb, var(--ok) 20%, transparent); }
.q label.wrong { background: color-mix(in srgb, var(--brand) 20%, transparent); }
.btn {
  background: var(--brand); color: #fff; border: 0; padding: 10px 20px; border-radius: 10px;
  font-weight: 700; cursor: pointer; margin-top: 14px; font-size: .95rem;
}
.btn:hover { background: var(--brand-dark); }
.result { font-weight: 700; margin-top: 12px; }

.emojis { display: flex; gap: 12px; flex-wrap: wrap; margin: 12px 0; }
.emoji {
  font-size: 2.2rem; background: none; border: 2px solid var(--line); border-radius: 50%;
  width: 68px; height: 68px; cursor: pointer; transition: .15s;
}
.emoji:hover, .emoji.sel { border-color: var(--brand); transform: scale(1.1); }
.empty { color: var(--muted); }

.drop {
  display: flex; flex-direction: column; align-items: center; gap: 4px; text-align: center;
  border: 2px dashed var(--brand); border-radius: var(--radius); padding: 28px 16px;
  cursor: pointer; color: var(--muted); transition: .15s;
}
.drop strong { color: var(--brand); }
.drop:hover, .drop.over { background: color-mix(in srgb, var(--brand) 8%, transparent); }
.fgrow { flex: 1; min-width: 0; word-break: break-word; }
.fgrow .meta { color: var(--muted); font-size: .8rem; }
.mini {
  border: 1px solid var(--line); background: none; color: var(--ink); border-radius: 8px;
  padding: 6px 10px; font-size: .8rem; cursor: pointer; text-decoration: none; flex: none;
}
.mini:hover { border-color: var(--brand); }
.mini.danger { color: var(--brand); }
details.panel > summary { cursor: pointer; font-weight: 700; color: var(--brand); }
.form { display: grid; gap: 12px; margin-top: 14px; max-width: 480px; }
.form label { display: grid; gap: 4px; font-weight: 600; font-size: .9rem; }
.form input, .form select {
  font: inherit; padding: 9px 10px; border: 1px solid var(--line); border-radius: 8px;
  background: var(--bg); color: var(--ink);
}

.footer { text-align: center; color: var(--muted); font-size: .8rem; padding: 18px; }

@media (max-width: 720px) {
  .layout { grid-template-columns: 1fr; }
  .menu-btn { display: block; }
  .sidebar { display: none; border-right: 0; border-bottom: 1px solid var(--line); }
  .sidebar.open { display: block; }
  .content { padding: 16px; }
}

</style>
</head>
<body>
  <header class="topbar">
    <button id="menuBtn" class="menu-btn" aria-label="Abrir menú">☰</button>
    <a href="#" class="brand">Marie Curie Helpers</a>
    <span class="badge">PoC</span>
  </header>

  <div class="layout">
    <nav id="sidebar" class="sidebar" aria-label="Materias"></nav>
    <main id="app" class="content" tabindex="-1"></main>
  </div>

  <footer class="footer">
    Código abierto bajo licencia MIT · Grado 10B · Proyecto de tecnología
  </footer>

  <script>
// Clases de ejemplo. Reemplázalas por las reales o por una llamada a tu API.
// Para usar audio real: pon el archivo en grabaciones/ y escribe media: "grabaciones/mi-clase.mp3"
// En preguntas, "ok" es el índice de la respuesta correcta (0 = A, 1 = B, 2 = C).
window.MATERIAS = ["Arts", "Behavior", "Chemistry", "Computational Thinking", "Competencias Socioemocionales", "Economy and Politics", "English", "Español", "Philosophy", "Physical Education", "Physics", "Research", "Trigonometry"];
window.CLASES = [
  {
    id: "fis-mrua",
    materia: "Physics",
    titulo: "Movimiento uniformemente acelerado",
    fecha: "2026-10-20",
    media: "",
    resumen: [
      "En el MRUA la aceleración es constante, así que la velocidad cambia la misma cantidad en cada segundo.",
      "Ecuaciones clave: v = v₀ + a·t y x = x₀ + v₀·t + ½·a·t².",
      "En una gráfica velocidad–tiempo, la pendiente es la aceleración y el área bajo la recta es el desplazamiento."
    ],
    etiquetas: ["cinemática", "aceleración", "gráficas"],
    recursos: [
      { titulo: "Cinemática en Khan Academy", url: "https://es.khanacademy.org/science/physics", tipo: "link" },
      { titulo: "Simulaciones de movimiento (PhET)", url: "https://phet.colorado.edu/es/", tipo: "link" }
    ],
    preguntas: [
      { q: "¿Qué permanece constante en el MRUA?", op: ["La velocidad", "La aceleración", "La posición"], ok: 1 },
      { q: "En una gráfica v–t, la pendiente representa…", op: ["La aceleración", "El desplazamiento", "El tiempo"], ok: 0 },
      { q: "Un carro parte del reposo y acelera 2 m/s². ¿Qué velocidad tiene a los 5 s?", op: ["5 m/s", "7 m/s", "10 m/s"], ok: 2 }
    ]
  },
  {
    id: "lit-simbolismo",
    materia: "Español",
    titulo: "Simbolismo y Modernismo",
    fecha: "2026-10-22",
    media: "",
    resumen: [
      "El Simbolismo surge en Francia a finales del siglo XIX y busca sugerir ideas con imágenes y musicalidad, no describirlas.",
      "El Modernismo hispanoamericano toma esa estética y la combina con lo exótico y el cuidado formal; su figura central es Rubén Darío.",
      "Ambos rechazan el realismo y valoran el arte por el arte."
    ],
    etiquetas: ["siglo XIX", "poesía", "Rubén Darío"],
    recursos: [
      { titulo: "Biblioteca Virtual Miguel de Cervantes", url: "https://www.cervantesvirtual.com/", tipo: "link" }
    ],
    preguntas: [
      { q: "¿Qué busca el Simbolismo?", op: ["Describir la realidad con detalle", "Sugerir ideas mediante símbolos", "Criticar la política"], ok: 1 },
      { q: "¿Quién es la figura central del Modernismo hispanoamericano?", op: ["Rubén Darío", "Gabriel García Márquez", "Miguel de Cervantes"], ok: 0 },
      { q: "¿Qué corriente rechazan ambos movimientos?", op: ["El Romanticismo", "El Realismo", "El Barroco"], ok: 1 }
    ]
  },
  {
    id: "fil-epistemologia",
    materia: "Philosophy",
    titulo: "Epistemología moderna y contemporánea",
    fecha: "2026-10-27",
    media: "",
    resumen: [
      "La epistemología estudia qué es el conocimiento, cómo se obtiene y cuáles son sus límites.",
      "En la modernidad se enfrentan el racionalismo (la razón es la fuente del conocimiento) y el empirismo (lo es la experiencia).",
      "Kant propone una síntesis: sin experiencia no hay contenido, y sin categorías de la razón no hay comprensión."
    ],
    etiquetas: ["conocimiento", "racionalismo", "empirismo", "Kant"],
    recursos: [
      { titulo: "Stanford Encyclopedia of Philosophy", url: "https://plato.stanford.edu/", tipo: "link" }
    ],
    preguntas: [
      { q: "Para el empirismo, la fuente del conocimiento es…", op: ["La razón", "La experiencia", "La fe"], ok: 1 },
      { q: "¿Quién propone una síntesis entre racionalismo y empirismo?", op: ["Descartes", "Hume", "Kant"], ok: 2 },
      { q: "¿Qué estudia la epistemología?", op: ["El conocimiento y sus límites", "La moral", "La belleza"], ok: 0 }
    ]
  },
  {
    id: "cie-sulforafano",
    materia: "Research",
    titulo: "Compuestos antioxidantes en los brotes",
    fecha: "2026-10-29",
    media: "",
    resumen: [
      "Los antioxidantes neutralizan radicales libres, moléculas que dañan las células y aceleran el envejecimiento.",
      "Los brotes de brócoli contienen glucorafanina, que se convierte en sulforafano cuando la planta se corta o se muele.",
      "La extracción depende del disolvente, la temperatura y el tiempo de contacto."
    ],
    etiquetas: ["antioxidantes", "extracción", "brócoli"],
    recursos: [
      { titulo: "Introducción a los radicales libres", url: "https://es.khanacademy.org/science/biology", tipo: "link" }
    ],
    preguntas: [
      { q: "¿Qué hacen los antioxidantes?", op: ["Producen radicales libres", "Neutralizan radicales libres", "Aumentan la temperatura"], ok: 1 },
      { q: "¿En qué se convierte la glucorafanina?", op: ["Sulforafano", "Glucosa", "Clorofila"], ok: 0 },
      { q: "¿Qué factor influye en la extracción?", op: ["El color del frasco", "El disolvente utilizado", "La hora del día"], ok: 1 }
    ]
  }
];

</script>
  <script>
(() => {
  const $ = s => document.querySelector(s);
  const esc = s => String(s ?? "").replace(/[&<>"']/g, c => ({ "&": "&amp;", "<": "&lt;", ">": "&gt;", '"': "&quot;", "'": "&#39;" }[c]));
  const app = $("#app"), sidebar = $("#sidebar");
  const slug = s => s.normalize("NFD").replace(/[\u0300-\u036f]/g, "").toLowerCase().replace(/[^a-z0-9]+/g, "-").replace(/^-|-$/g, "");
  const fmtTime = t => isFinite(t) ? Math.floor(t / 60) + ":" + String(Math.floor(t % 60)).padStart(2, "0") : "0:00";
  const fmtSize = b => b > 1048576 ? (b / 1048576).toFixed(1) + " MB" : Math.max(1, Math.round(b / 1024)) + " KB";
  const fmtDate = d => { try { return new Date(d + "T12:00:00").toLocaleDateString("es-CO", { day: "numeric", month: "short", year: "numeric" }); } catch { return d; } };
  const store = {
    get: (k, d) => { try { return JSON.parse(localStorage.getItem(k)) ?? d; } catch { return d; } },
    set: (k, v) => { try { localStorage.setItem(k, JSON.stringify(v)); } catch {} }
  };

  // ---------- IndexedDB (archivos y clases propias) ----------
  let db = null;
  const openDB = () => new Promise(res => {
    try {
      const r = indexedDB.open("marie-curie-helpers", 1);
      r.onupgradeneeded = () => {
        r.result.createObjectStore("files", { keyPath: "id", autoIncrement: true }).createIndex("clase", "clase");
        r.result.createObjectStore("clases", { keyPath: "id" });
      };
      r.onsuccess = () => res(r.result);
      r.onerror = () => res(null);
    } catch { res(null); }
  });
  const run = (name, mode, fn) => new Promise(res => {
    if (!db) return res(mode === "readonly" ? [] : null);
    try {
      const t = db.transaction(name, mode);
      const req = fn(t.objectStore(name));
      t.oncomplete = () => res(req ? req.result : null);
      t.onerror = t.onabort = () => res(mode === "readonly" ? [] : null);
    } catch { res(mode === "readonly" ? [] : null); }
  });
  const filesOf = id => run("files", "readonly", s => s.index("clase").getAll(id));
  const addFile = f => run("files", "readwrite", s => s.add(f));
  const delFile = id => run("files", "readwrite", s => s.delete(id));
  const customClasses = () => run("clases", "readonly", s => s.getAll());
  const saveClass = c => run("clases", "readwrite", s => s.put(c));

  let todas = [];
  const cargar = async () => { todas = (window.CLASES || []).concat(await customClasses()); };
  const materias = () => [...new Set((window.MATERIAS || []).concat(todas.map(c => c.materia)))].sort((a, b) => a.localeCompare(b, "es"));

  // ---------- Barra lateral ----------
  function renderSidebar(activa) {
    sidebar.innerHTML = "<h3>Materias</h3>" +
      `<a href="#" class="${activa === "" ? "active" : ""}">Todas las clases</a>` +
      materias().map(m => `<a href="#m-${slug(m)}" class="${activa === m ? "active" : ""}">${esc(m)}</a>`).join("");
    sidebar.classList.remove("open");
  }

  // ---------- Inicio y materias ----------
  function cards(lista) {
    if (!lista.length) return `<p class="empty">Todavía no hay clases aquí.</p>`;
    return `<div class="grid">` + lista.map(c => `
      <a class="card" href="#c-${c.id}">
        <div class="subject">${esc(c.materia)}</div>
        <h4>${esc(c.titulo)}</h4>
        <div class="meta">${esc(fmtDate(c.fecha))}</div>
      </a>`).join("") + `</div>`;
  }

  function vistaInicio(materia) {
    const lista = materia ? todas.filter(c => c.materia === materia) : todas;
    renderSidebar(materia || "");
    app.innerHTML = `
      <h1>${materia ? esc(materia) : "Clases"}</h1>
      <p class="sub">Elige la clase que te perdiste o que quieres repasar.</p>
      ${cards(lista)}
      <details class="panel" style="margin-top:20px">
        <summary>＋ Subir una clase nueva</summary>
        <form class="form" id="nuevaClase">
          <label>Título<input name="titulo" required maxlength="80"></label>
          <label>Materia<input name="materia" required list="listaMaterias" maxlength="40" value="${esc(materia || "")}"></label>
          <datalist id="listaMaterias">${materias().map(m => `<option value="${esc(m)}">`).join("")}</datalist>
          <label>Fecha<input name="fecha" type="date" required value="${new Date().toISOString().slice(0, 10)}"></label>
          <label>Audio o video (opcional)<input name="archivo" type="file" accept="audio/*,video/*"></label>
          <button class="btn" type="submit">Crear clase</button>
        </form>
      </details>`;
    $("#nuevaClase").onsubmit = async e => {
      e.preventDefault();
      const f = new FormData(e.target);
      const c = { id: "u" + Date.now(), materia: f.get("materia").trim(), titulo: f.get("titulo").trim(), fecha: f.get("fecha"), resumen: [], recursos: [], preguntas: [], propia: true };
      await saveClass(c);
      const a = f.get("archivo");
      if (a && a.size) await addFile({ clase: c.id, name: a.name, type: a.type, size: a.size, blob: a });
      await cargar();
      location.hash = "#c-" + c.id;
    };
  }

  // ---------- Clase ----------
  let tab = "video";
  const TABS = [["video", "Video y resumen"], ["practica", "Práctica"], ["evaluar", "Evaluar"], ["proceso", "Mi proceso"], ["archivos", "Archivos"]];

  async function vistaClase(id) {
    const c = todas.find(x => x.id === id);
    if (!c) { renderSidebar(""); app.innerHTML = `<a class="back" href="#">← Volver</a><p class="empty">No encontramos esa clase.</p>`; return; }
    renderSidebar(c.materia);
    app.innerHTML = `
      <a class="back" href="#m-${slug(c.materia)}">← ${esc(c.materia)}</a>
      <h1>${esc(c.titulo)}</h1>
      <p class="sub">${esc(c.materia)} · ${esc(fmtDate(c.fecha))}</p>
      <div class="tabs" role="tablist">${TABS.map(([k, n]) => `<button class="tab ${k === tab ? "active" : ""}" role="tab" data-t="${k}">${n}</button>`).join("")}</div>
      <div id="panel"></div>`;
    app.querySelectorAll(".tab").forEach(b => b.onclick = () => { tab = b.dataset.t; vistaClase(id); });
    const p = $("#panel");
    if (tab === "video") await tabVideo(c, p);
    else if (tab === "practica") tabPractica(c, p);
    else if (tab === "evaluar") tabEvaluar(c, p);
    else if (tab === "proceso") tabProceso(c, p);
    else await tabArchivos(c, p);
  }

  async function tabVideo(c, p) {
    const archivos = await filesOf(c.id);
    const m = archivos.find(f => /^(audio|video)\//.test(f.type));
    const src = m ? URL.createObjectURL(m.blob) : (c.media || "");
    const esVideo = m ? m.type.startsWith("video/") : /\.(mp4|webm|mov)$/i.test(src);
    const barras = Array.from({ length: 64 }, (_, i) => 18 + Math.round(Math.abs(Math.sin(i * 1.7 + c.id.length) * Math.cos(i * 0.45)) * 80));
    p.innerHTML = `
      <div class="panel">
        ${src ? (esVideo ? `<video id="med" src="${esc(src)}" playsinline style="width:100%;border-radius:10px;margin-bottom:12px"></video>` : `<audio id="med" src="${esc(src)}" preload="metadata"></audio>`) : ""}
        <div class="player">
          <button class="play" id="play" aria-label="Reproducir" ${src ? "" : "disabled"}>▶</button>
          <div class="wave" id="wave">${barras.map(h => `<i style="height:${h}%"></i>`).join("")}</div>
          <span class="time" id="time">0:00 / 0:00</span>
        </div>
        ${src ? "" : `<p class="ai-note">Esta clase todavía no tiene grabación. Súbela en la pestaña Archivos.</p>`}
      </div>
      <div class="panel summary">
        <h3>Resumen de la clase</h3>
        ${c.resumen.length ? `<ul>${c.resumen.map(r => `<li>${esc(r)}</li>`).join("")}</ul>` : `<p class="empty">Esta clase aún no tiene resumen.</p>`}
        ${(c.etiquetas || []).map(t => `<span class="tag">${esc(t)}</span>`).join("")}
        ${c.resumen.length ? `<p class="ai-note">Resumen generado con IA. Compáralo con tus apuntes.</p>` : ""}
      </div>`;
    const med = $("#med"); if (!med) return;
    const bars = [...document.querySelectorAll("#wave i")], time = $("#time"), play = $("#play");
    const pintar = () => {
      const d = med.duration || 0, r = d ? med.currentTime / d : 0;
      bars.forEach((b, i) => b.classList.toggle("done", i / bars.length < r));
      time.textContent = fmtTime(med.currentTime) + " / " + fmtTime(d);
    };
    play.onclick = () => med.paused ? med.play() : med.pause();
    med.onplay = () => { play.textContent = "❚❚"; play.setAttribute("aria-label", "Pausar"); };
    med.onpause = med.onended = () => { play.textContent = "▶"; play.setAttribute("aria-label", "Reproducir"); };
    med.ontimeupdate = med.onloadedmetadata = pintar;
    $("#wave").onclick = e => {
      const r = e.currentTarget.getBoundingClientRect();
      if (med.duration) med.currentTime = ((e.clientX - r.left) / r.width) * med.duration;
    };
  }

  function tabPractica(c, p) {
    p.innerHTML = `<div class="panel"><h3>Material de práctica</h3>` +
      (c.recursos.length ? c.recursos.map(r => `
        <div class="resource">
          <div class="thumb">${r.tipo === "video" ? "🎬" : "🔗"}</div>
          <div class="fgrow"><a href="${esc(r.url)}" target="_blank" rel="noopener">${esc(r.titulo)}</a><div class="meta">${esc(r.url.replace(/^https?:\/\//, "").split("/")[0])}</div></div>
        </div>`).join("") : `<p class="empty">Aún no hay material recomendado para esta clase.</p>`) + `</div>`;
  }

  function tabEvaluar(c, p) {
    if (!c.preguntas.length) { p.innerHTML = `<div class="panel"><p class="empty">Esta clase todavía no tiene preguntas.</p></div>`; return; }
    p.innerHTML = `<div class="panel"><h3>Evaluación corta</h3>
      <div class="quiz">${c.preguntas.map((q, i) => `
        <div class="q"><p>${i + 1}. ${esc(q.q)}</p>
        ${q.op.map((o, j) => `<label><input type="radio" name="q${i}" value="${j}"> ${"ABC"[j]}) ${esc(o)}</label>`).join("")}</div>`).join("")}
      </div>
      <button class="btn" id="calif">Calificar</button><div class="result" id="res" aria-live="polite"></div></div>`;
    $("#calif").onclick = () => {
      let ok = 0;
      c.preguntas.forEach((q, i) => {
        const labs = [...app.querySelectorAll(`input[name=q${i}]`)].map(r => r.parentElement);
        labs.forEach(l => l.classList.remove("right", "wrong"));
        const sel = app.querySelector(`input[name=q${i}]:checked`);
        labs[q.ok].classList.add("right");
        if (sel && +sel.value === q.ok) ok++; else if (sel) labs[+sel.value].classList.add("wrong");
      });
      $("#res").textContent = `Obtuviste ${ok} de ${c.preguntas.length}.`;
    };
  }

  function tabProceso(c, p) {
    const caras = ["😞", "🙁", "😐", "🙂", "😄"], nombres = ["Muy difícil", "Difícil", "Regular", "Bien", "Muy bien"];
    const sel = store.get("mch-proceso-" + c.id, 0);
    p.innerHTML = `<div class="panel"><h3>¿Cómo te fue con esta clase?</h3>
      <div class="emojis">${caras.map((e, i) => `<button class="emoji ${sel === i + 1 ? "sel" : ""}" data-v="${i + 1}" aria-label="${i + 1} de 5: ${nombres[i]}">${e}</button>`).join("")}</div>
      <p class="result" id="msg">${sel ? `Tu calificación: ${sel} de 5 (${nombres[sel - 1]}).` : ""}</p></div>`;
    p.querySelectorAll(".emoji").forEach(b => b.onclick = () => {
      const v = +b.dataset.v; store.set("mch-proceso-" + c.id, v);
      p.querySelectorAll(".emoji").forEach(x => x.classList.toggle("sel", x === b));
      $("#msg").textContent = `Guardado: ${v} de 5 (${nombres[v - 1]}).`;
    });
  }

  async function tabArchivos(c, p) {
    const lista = await filesOf(c.id);
    p.innerHTML = `<div class="panel"><h3>Archivos de la clase</h3>
      <label class="drop" id="drop"><strong>Haz clic o arrastra archivos aquí</strong><span>Audio, video, imágenes o PDF</span>
        <input type="file" id="fin" multiple accept="audio/*,video/*,image/*,.pdf,application/pdf" hidden></label>
      <div id="lista">${lista.length ? lista.map(f => `
        <div class="resource">
          <div class="thumb">${f.type.startsWith("image/") ? `<img src="${URL.createObjectURL(f.blob)}" alt="" style="width:100%;height:100%;object-fit:cover;border-radius:6px">` : f.type.startsWith("audio/") ? "🎧" : f.type.startsWith("video/") ? "🎬" : "📄"}</div>
          <div class="fgrow">${esc(f.name)}<div class="meta">${fmtSize(f.size)}</div></div>
          <button class="mini danger" data-del="${f.id}">Eliminar</button>
        </div>`).join("") : `<p class="empty" style="margin-top:12px">Aún no hay archivos.</p>`}</div></div>`;
    const subir = async fs => { for (const f of fs) await addFile({ clase: c.id, name: f.name, type: f.type, size: f.size, blob: f }); vistaClase(c.id); };
    const drop = $("#drop");
    $("#fin").onchange = e => subir(e.target.files);
    drop.ondragover = e => { e.preventDefault(); drop.classList.add("over"); };
    drop.ondragleave = () => drop.classList.remove("over");
    drop.ondrop = e => { e.preventDefault(); drop.classList.remove("over"); subir(e.dataTransfer.files); };
    p.querySelectorAll("[data-del]").forEach(b => b.onclick = async () => {
      if (!b.dataset.sure) { b.dataset.sure = 1; b.textContent = "¿Seguro?"; return; }
      await delFile(+b.dataset.del); vistaClase(c.id);
    });
  }

  // ---------- Rutas ----------
  async function ruta() {
    const h = location.hash.slice(1);
    if (h.startsWith("c-")) await vistaClase(h.slice(2));
    else vistaInicio(h.startsWith("m-") ? (materias().find(m => slug(m) === h.slice(2)) || "") : "");
    app.focus({ preventScroll: true });
  }
  let anterior = "";
  window.addEventListener("hashchange", () => {
    if (anterior !== location.hash) tab = "video";
    anterior = location.hash; ruta();
  });
  $("#menuBtn").onclick = () => sidebar.classList.toggle("open");

  (async () => { db = await openDB(); await cargar(); anterior = location.hash; ruta(); })();
})();

</script>
</body>
</html>
