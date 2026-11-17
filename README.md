<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Calendario Cultural del Maule · Prototipo</title>
<style>
:root{--bg:#f4f6fa;--surface:#fff;--text:#1d2433;--muted:#5b667a;--blue:#0f69c4;--blue-soft:#e6f0fb;--red:#d4283c;--line:#d9dfea;color-scheme:light;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0f1521;--surface:#171f2e;--text:#e8ecf4;--muted:#9aa6bb;--blue:#6aa8f0;--blue-soft:#1b2a42;--red:#ff6b7a;--line:#2a3550;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#0f1521;--surface:#171f2e;--text:#e8ecf4;--muted:#9aa6bb;--blue:#6aa8f0;--blue-soft:#1b2a42;--red:#ff6b7a;--line:#2a3550;color-scheme:dark}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--text);font:16px/1.5 system-ui,-apple-system,"Segoe UI",Roboto,Arial,sans-serif}
.stripe{height:6px;background:linear-gradient(90deg,var(--blue) 0 66%,var(--red) 66%)}
.note{background:var(--blue-soft);color:var(--text);font-size:13px;text-align:center;padding:6px 12px;border-bottom:1px solid var(--line)}
header{background:var(--surface);border-bottom:1px solid var(--line)}
.wrap{max-width:1100px;margin:0 auto;padding:0 16px}
header .wrap{padding:18px 16px}
h1{margin:0;font-size:24px;color:var(--blue)}
header p{margin:4px 0 0;color:var(--muted);font-size:14px}
main.wrap{display:grid;grid-template-columns:1fr 280px;gap:20px;padding-top:20px;padding-bottom:32px}
@media(max-width:820px){main.wrap{grid-template-columns:1fr}}
.card{background:var(--surface);border:1px solid var(--line);border-radius:8px;padding:16px}
.bar{display:flex;align-items:center;justify-content:space-between;margin-bottom:10px}
.bar h2{margin:0;font-size:20px;text-transform:capitalize}
.bar button{border:1px solid var(--line);background:var(--surface);color:var(--blue);border-radius:6px;padding:6px 12px;font-size:16px;cursor:pointer}
.grid{display:grid;grid-template-columns:repeat(7,1fr);gap:4px}
.dow{font-size:12px;font-weight:600;color:var(--muted);text-align:center;padding:4px 0}
.day{position:relative;min-height:58px;border:1px solid var(--line);background:var(--surface);color:var(--text);border-radius:6px;padding:4px 6px;text-align:left;font:inherit;cursor:default}
.day.has{cursor:pointer;background:var(--blue-soft)}
.day.sel{outline:2px solid var(--blue)}
.day.today .n{background:var(--red);color:#fff;border-radius:50%;display:inline-block;min-width:22px;text-align:center}
.day.off{visibility:hidden}
.n{font-size:13px;font-weight:600}
.badge{position:absolute;right:5px;bottom:5px;background:var(--blue);color:#fff;font-size:11px;font-weight:700;border-radius:10px;padding:0 7px}
.day.has:hover::after,.day.has:focus-visible::after{content:attr(data-tip);position:absolute;z-index:5;left:50%;bottom:calc(100% + 4px);transform:translateX(-50%);white-space:nowrap;background:var(--text);color:var(--bg);font-size:12px;padding:4px 8px;border-radius:4px;pointer-events:none}
#list h3{margin:0 0 8px;font-size:17px}
.ev{display:grid;grid-template-columns:56px 1fr;gap:10px;padding:10px 0;border-top:1px solid var(--line)}
.ev .t{font-weight:700;color:var(--blue)}
.ev b{display:block}
.ev small{color:var(--muted)}
.ev a{color:var(--blue);font-size:14px}
.empty{color:var(--muted)}
aside h2{margin:0 0 6px;font-size:17px;color:var(--blue)}
aside p{font-size:14px;color:var(--muted);margin:0 0 12px}
.lnk{display:block;border:1px solid var(--blue);color:var(--blue);background:var(--surface);text-decoration:none;border-radius:6px;padding:10px 12px;margin-bottom:8px;font-weight:600;font-size:15px}
.lnk:hover{background:var(--blue-soft)}
.lnk span{display:block;font-weight:400;font-size:12px;color:var(--muted)}
.tools{margin-bottom:16px}.tools input,.tools select{width:100%;font:inherit;padding:10px 12px;border:1px solid var(--line);border-radius:6px;background:var(--bg);color:var(--text)}.tools .row{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin:8px 0}.tools small{color:var(--muted);font-size:12px}.sr{position:absolute;left:-9999px}#res{margin-bottom:16px}#res h3{margin:0 0 4px;font-size:17px}.r{display:block;width:100%;text-align:left;border:0;border-top:1px solid var(--line);background:none;color:var(--text);padding:10px 0;font:inherit;cursor:pointer}.r small{display:block;color:var(--muted)}.r:hover b{color:var(--blue)}
.steps{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-top:20px}
@media(max-width:820px){.steps{grid-template-columns:1fr}}
.steps .card b{color:var(--red)}
footer{text-align:center;color:var(--muted);font-size:13px;padding:0 16px 24px}
</style>
</head>
<body>
<div class="stripe"></div>
<div class="note">Prototipo para presentación · Las actividades de este calendario son datos de ejemplo</div>
<header><div class="wrap">
<h1>Calendario Cultural del Maule</h1>
<p>Todas las actividades de los centros culturales, ordenadas por día y con enlace a la publicación original.</p>
</div></header>
<main class="wrap">
<section>
<div class="card tools">
<label for="q" class="sr">Buscar actividad</label>
<input id="q" type="search" placeholder="Buscar: ajedrez, circo, taller de cerámica…" autocomplete="off">
<div class="row"><select id="tipo" aria-label="Tipo de actividad"></select><select id="centro" aria-label="Centro cultural"></select></div>
<small>Los tipos se asignan automáticamente leyendo el texto de la publicación (simulado en este prototipo).</small>
</div>
<div class="card" id="res" style="display:none" aria-live="polite"></div>
<div class="card">
<div class="bar"><button id="prev" aria-label="Mes anterior">‹</button><h2 id="mes"></h2><button id="next" aria-label="Mes siguiente">›</button></div>
<div class="grid" id="cal"></div>
</div>
<div class="card" id="list" style="margin-top:16px" aria-live="polite"></div>
<div class="steps">
<div class="card"><b>1.</b> El centro cultural publica su actividad en Instagram, como ya lo hace.</div>
<div class="card"><b>2.</b> El sistema lee la publicación y toma la fecha, la hora y el lugar.</div>
<div class="card"><b>3.</b> La actividad aparece en el día correcto, con enlace a la publicación original.</div>
</div>
</section>
<aside>
<div class="card">
<h2>Red cultural de Chile</h2>
<p>No reemplazamos estas plataformas: las complementamos con las actividades que los centros publican solo en Instagram y no alcanzan a cargar a mano.</p>
<a class="lnk" href="https://www.chilecultura.gob.cl" target="_blank" rel="noopener">Chile Cultura<span>Cartelera nacional del Ministerio</span></a>
<a class="lnk" href="https://www.cultura.gob.cl" target="_blank" rel="noopener">Ministerio de las Culturas<span>Fondos, políticas y patrimonio</span></a>
<a class="lnk" href="https://www.biblioredes.gob.cl" target="_blank" rel="noopener">Biblioredes<span>Bibliotecas públicas y contenidos</span></a>
<a class="lnk" href="https://www.mapacultural.cl" target="_blank" rel="noopener">Mapa Cultural<span>Directorio de espacios culturales</span></a>
</div>
</aside>
</main>
<footer>Proyecto 2 · Prototipo con datos ficticios · Centros marcados “(ejemplo)” no son reales</footer>
<script>
var E=[["2026-11-03","Centro Cultural El Espacio","Taller de cerámica infantil","16:00"],["2026-11-05","Centro Cultural El Espacio","Ciclo de cine nacional","19:00"],["2026-11-05","Biblioteca Municipal (ejemplo)","Cuentacuentos","11:00"],["2026-11-07","Teatro Regional (ejemplo)","Obra “La casa vacía”","20:00"],["2026-11-07","Centro Cultural El Espacio","Feria de artesanos","10:00"],["2026-11-07","Casa de la Cultura (ejemplo)","Clase abierta de folclor","17:00"],["2026-11-10","Biblioteca Municipal (ejemplo)","Lanzamiento de libro local","18:30"],["2026-11-12","Centro Cultural El Espacio","Muestra de fotografía","19:00"],["2026-11-14","Teatro Regional (ejemplo)","Concierto de música de cámara","20:00"],["2026-11-14","Centro Cultural El Espacio","Taller de ajedrez","15:00"],["2026-11-19","Casa de la Cultura (ejemplo)","Taller de telar","16:00"],["2026-11-21","Centro Cultural El Espacio","Encuentro de narradores","18:00"],["2026-11-21","Teatro Regional (ejemplo)","Función familiar","12:00"],["2026-11-26","Biblioteca Municipal (ejemplo)","Club de lectura","18:00"],["2026-11-28","Centro Cultural El Espacio","Torneo amistoso de ajedrez","15:00"],["2026-12-02","Centro Cultural El Espacio","Muestra de fin de talleres","18:00"],["2026-12-05","Teatro Regional (ejemplo)","Ballet de fin de año","20:00"],["2026-12-05","Casa de la Cultura (ejemplo)","Feria navideña","11:00"],["2026-12-12","Centro Cultural El Espacio","Concierto de cierre","19:30"],["2026-12-12","Biblioteca Municipal (ejemplo)","Cuentacuentos navideño","11:00"],["2026-12-19","Centro Cultural El Espacio","Taller de ilustración","16:00"]];
var M={},y=2026,m=10,sel="2026-11-07";
function norm(s){return s.normalize("NFD").replace(/[\u0300-\u036f]/g,"").toLowerCase()}
var R=[["Taller",/taller|clase/],["Ajedrez",/ajedrez/],["Cine",/cine/],["Literatura",/cuentacuentos|lectura|libro|narrador/],["Teatro",/obra|funcion|teatro/],["Música y danza",/concierto|ballet|folclor/],["Feria",/feria/],["Exposición",/fotografia|muestra/]];
E.forEach(function(e){var n=norm(e[2]);e[4]=R.filter(function(r){return r[1].test(n)}).map(function(r){return r[0]})});
function fill(id,v,l){document.getElementById(id).innerHTML='<option value="">'+l+'</option>'+v.map(function(x){return '<option>'+x+'</option>'}).join("")}
fill("tipo",R.map(function(r){return r[0]}),"Todos los tipos");
fill("centro",E.map(function(e){return e[1]}).filter(function(v,i,a){return a.indexOf(v)===i}),"Todos los centros");
function match(e){var q=norm(document.getElementById("q").value.trim()),t=document.getElementById("tipo").value,c=document.getElementById("centro").value;return(!q||norm(e[1]+" "+e[2]+" "+e[4].join(" ")).indexOf(q)>-1)&&(!t||e[4].indexOf(t)>-1)&&(!c||e[1]===c)}
function build(){M={};E.filter(match).forEach(function(e){(M[e[0]]=M[e[0]]||[]).push(e)})}
function res(){var X=document.getElementById("res"),on=document.getElementById("q").value.trim()||document.getElementById("tipo").value||document.getElementById("centro").value;if(!on){X.style.display="none";return}
var f=E.filter(match).sort(function(a,b){return a[0]<b[0]?-1:1}),h='<h3>'+f.length+(f.length===1?' resultado':' resultados')+'</h3>';
if(!f.length)h+='<p class="empty">No encontramos actividades con esa búsqueda.</p>';
f.forEach(function(e){var p=e[0].split("-");h+='<button class="r" data-k="'+e[0]+'"><b>'+e[2]+'</b><small>'+Number(p[2])+' de '+MES[Number(p[1])-1]+' · '+e[3]+' · '+e[1]+'</small></button>'});
X.innerHTML=h;X.style.display="block"}
function upd(){build();res();draw()}
build();
["q","tipo","centro"].forEach(function(id){document.getElementById(id).addEventListener("input",upd)});
document.getElementById("res").addEventListener("click",function(e){var b=e.target.closest(".r");if(!b)return;var p=b.dataset.k.split("-");y=+p[0];m=+p[1]-1;sel=b.dataset.k;draw();document.getElementById("cal").scrollIntoView({behavior:"smooth",block:"center"})});
var MES=["enero","febrero","marzo","abril","mayo","junio","julio","agosto","septiembre","octubre","noviembre","diciembre"];
function k(d){return y+"-"+String(m+1).padStart(2,"0")+"-"+String(d).padStart(2,"0")}
function draw(){
var c=document.getElementById("cal"),h="";
["L","M","M","J","V","S","D"].forEach(function(x){h+='<div class="dow">'+x+'</div>'});
var off=(new Date(y,m,1).getDay()+6)%7,n=new Date(y,m+1,0).getDate(),t=new Date();
for(var i=0;i<off;i++)h+='<div class="day off"></div>';
for(var d=1;d<=n;d++){
var key=k(d),c2=(M[key]||[]).length,cl="day"+(c2?" has":"")+(key===sel?" sel":"")+(t.getFullYear()===y&&t.getMonth()===m&&t.getDate()===d?" today":"");
h+='<button class="'+cl+'" data-k="'+key+'"'+(c2?' data-tip="Número de actividades: '+c2+'"':'')+(c2?'':' tabindex="-1"')+'><span class="n">'+d+'</span>'+(c2?'<span class="badge">'+c2+'</span>':'')+'</button>';
}
c.innerHTML=h;
document.getElementById("mes").textContent=MES[m]+" "+y;
list();
}
function list(){
var L=document.getElementById("list"),ev=M[sel]||[];
if(!ev.length){L.innerHTML='<p class="empty">Haz clic en un día marcado para ver sus actividades.</p>';return}
var p=sel.split("-"),h='<h3>Actividades del '+Number(p[2])+" de "+MES[Number(p[1])-1]+"</h3>";
ev.sort(function(a,b){return a[3]<b[3]?-1:1}).forEach(function(e){
h+='<div class="ev"><div class="t">'+e[3]+'</div><div><b>'+e[2]+'</b><small>'+e[1]+'</small><br><a href="https://www.instagram.com/" target="_blank" rel="noopener">Ver publicación original ↗</a></div></div>'});
L.innerHTML=h;
}
document.getElementById("cal").addEventListener("click",function(e){
var b=e.target.closest(".day");if(!b||!b.dataset.k||!M[b.dataset.k])return;sel=b.dataset.k;draw()});
function go(s){m+=s;if(m<10&&y===2026){m=10}if(m>11){m=11}draw()}
document.getElementById("prev").onclick=function(){go(-1)};
document.getElementById("next").onclick=function(){go(1)};
draw();
</script>
</body>
</html>
