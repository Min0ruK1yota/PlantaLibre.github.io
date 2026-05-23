# Min0ruK1yota.github.io
Catálogo de Planta Libre
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="Planta Libre">
<meta name="mobile-web-app-capable" content="yes">
<meta name="theme-color" content="#f5f4f1">
<title>Catálogo — Planta Libre</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;0,9..40,700;1,9..40,400;1,9..40,500&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg:#fff;--bg2:#f5f4f1;--bg3:#eeece8;
  --ink:#141210;--ink-mid:#5a5650;--ink-light:#9a9590;
  --rule:#dedad4;--rule-dark:#ccc9c2;
  --green-bg:#EAF3DE;--green-tx:#27500A;
  --amber-bg:#FAEEDA;--amber-tx:#633806;
  --gray-bg:#F1EFE8;--gray-tx:#5F5E5A;
  --blue-bg:#E6F1FB;--blue-tx:#0C447C;
  --r-sm:6px;--r-md:10px;--r-lg:14px;
}
body{font-family:'DM Sans',sans-serif;background:var(--bg2);color:var(--ink);
  min-height:100vh;min-height:-webkit-fill-available;font-size:14px;font-weight:400;
  -webkit-text-size-adjust:100%;-webkit-font-smoothing:antialiased}
.shell{max-width:900px;margin:0 auto;padding:0 1rem calc(5rem + env(safe-area-inset-bottom));
  padding-left:max(1rem,env(safe-area-inset-left));padding-right:max(1rem,env(safe-area-inset-right))}
@media(min-width:600px){.shell{padding:0 1.5rem 3rem}}

/* HEADER */
.header{padding:1.5rem 0 1.25rem;border-bottom:1px solid var(--ink);text-align:center}
.g-nombre{font-size:17px;font-weight:700;letter-spacing:.22em;text-transform:uppercase;margin-bottom:5px}
.g-info{font-size:11px;color:var(--ink-mid);line-height:1.8}
.header-bottom{display:flex;justify-content:space-between;align-items:center;padding-top:.6rem;text-align:left}
.header-titulo{font-size:22px;font-weight:600;letter-spacing:.08em;text-transform:uppercase}

/* STATS */
.stats-row{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;padding:1rem 0;border-bottom:.5px solid var(--rule)}
.stat{background:var(--bg);border-radius:var(--r-md);padding:10px 12px;border:.5px solid var(--rule)}
.stat-label{font-size:9px;font-weight:500;letter-spacing:.15em;text-transform:uppercase;color:var(--ink-light);margin-bottom:6px}
.stat-val{font-size:24px;font-weight:600;color:var(--ink)}
@media(max-width:640px){.stats-row{grid-template-columns:1fr 1fr;gap:6px}.stat-val{font-size:20px}}

/* TABS */
.tabs-nav{display:flex;border-bottom:.5px solid var(--rule-dark);margin-top:1rem;overflow-x:auto;-webkit-overflow-scrolling:touch;scrollbar-width:none}
.tabs-nav::-webkit-scrollbar{display:none}
.tab-btn{font-family:inherit;font-size:10px;font-weight:400;letter-spacing:.12em;text-transform:uppercase;
  padding:10px 16px;border:none;background:transparent;cursor:pointer;color:var(--ink-light);
  border-bottom:2px solid transparent;margin-bottom:-1px;flex-shrink:0;display:flex;
  align-items:center;gap:6px;min-height:44px;white-space:nowrap;-webkit-tap-highlight-color:transparent}
.tab-btn.activo{color:var(--ink);border-bottom-color:var(--ink);font-weight:600}
.tab-count{font-size:10px;background:var(--bg3);border-radius:20px;padding:1px 7px;color:var(--ink-light)}
.tab-btn.activo .tab-count{background:var(--ink);color:var(--bg)}
.tab-count.rojo{background:#c0392b;color:#fff}

/* FILTROS */
.filtros{display:flex;gap:8px;padding:.75rem 0;flex-wrap:wrap;border-bottom:.5px solid var(--rule);align-items:center}
.filtro-label{font-size:10px;letter-spacing:.12em;text-transform:uppercase;color:var(--ink-light)}
.chip{font-family:inherit;font-size:10px;font-weight:500;letter-spacing:.1em;text-transform:uppercase;
  padding:5px 13px;border-radius:20px;border:.5px solid var(--rule-dark);background:transparent;
  color:var(--ink-mid);cursor:pointer;min-height:40px;-webkit-tap-highlight-color:transparent}
.chip.activo{background:var(--ink);color:var(--bg);border-color:var(--ink)}
.busq{font-family:inherit;font-size:16px;padding:6px 12px;border-radius:var(--r-sm);border:.5px solid var(--rule-dark);background:var(--bg);color:var(--ink);-webkit-appearance:none;width:180px}
@media(max-width:640px){.filtro-label{display:none}.busq{width:100%;margin-top:4px}}

/* OBRAS GRID */
.obras-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1rem;padding-top:1rem}
@media(max-width:700px){.obras-grid{grid-template-columns:1fr 1fr;gap:8px}}
.grupo-header{grid-column:1/-1;display:flex;align-items:center;gap:10px;padding:10px 0 5px;border-top:.5px solid var(--rule);margin-top:4px}
.grupo-header:first-child{border-top:none;margin-top:0}
.grupo-nombre{font-size:11px;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:var(--ink-mid)}
.grupo-badge{font-size:10px;color:var(--ink-light);background:var(--bg3);border-radius:20px;padding:1px 8px}

/* OBRA CARD */
.obra-card{background:var(--bg);border:.5px solid var(--rule);border-radius:var(--r-lg);overflow:hidden;cursor:pointer;-webkit-tap-highlight-color:transparent}
.obra-img{aspect-ratio:4/3;background:var(--bg3);display:flex;align-items:center;justify-content:center;position:relative;overflow:hidden}
.obra-img img{width:100%;height:100%;object-fit:cover;display:block}
.obra-img-ph{display:flex;flex-direction:column;align-items:center;gap:6px;color:var(--ink-light)}
.obra-img-ph svg{opacity:.35}
.obra-img-ph span{font-size:9px;letter-spacing:.1em;text-transform:uppercase}
.pill{font-size:9px;font-weight:500;letter-spacing:.06em;text-transform:uppercase;padding:3px 8px;border-radius:20px;display:inline-block}
.pill-disp{background:var(--green-bg);color:var(--green-tx)}
.pill-res{background:var(--amber-bg);color:var(--amber-tx)}
.pill-vend{background:var(--gray-bg);color:var(--gray-tx)}
.card-pill{position:absolute;top:7px;right:7px}
.btn-cart{position:absolute;bottom:8px;right:8px;width:28px;height:28px;border-radius:50%;
  background:rgba(255,255,255,.92);border:none;cursor:pointer;display:flex;align-items:center;
  justify-content:center;color:var(--ink);font-size:15px;font-weight:700;
  box-shadow:0 1px 4px rgba(0,0,0,.18);-webkit-tap-highlight-color:transparent}
.btn-cart.activo{background:var(--ink);color:#fff}
.obra-body{padding:10px 12px}
.obra-num{font-size:9px;color:var(--ink-light);letter-spacing:.1em;text-transform:uppercase;margin-bottom:4px}
.obra-titulo-card{font-size:14px;font-style:italic;font-weight:500;color:var(--ink);margin-bottom:2px;
  white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.obra-artista-card{font-size:10px;font-weight:500;letter-spacing:.06em;text-transform:uppercase;color:var(--ink-mid);margin-bottom:8px}
.obra-meta{display:flex;justify-content:space-between;align-items:flex-end}
.obra-anio{font-size:10px;color:var(--ink-light)}
.obra-precio{font-size:15px;font-weight:600;color:var(--ink)}
.obra-precio.vendida{color:var(--ink-light);text-decoration:line-through;font-size:13px}

/* ACCORDION */
.panel-section{padding:.75rem 0}
.acc-card{background:var(--bg);border:.5px solid var(--rule);border-radius:var(--r-lg);margin-bottom:.75rem;overflow:hidden}
.acc-header{display:flex;align-items:center;justify-content:space-between;padding:14px 18px;cursor:pointer;-webkit-tap-highlight-color:transparent}
.acc-header:active{background:var(--bg2)}
.avatar{width:38px;height:38px;border-radius:50%;background:var(--blue-bg);display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:600;color:var(--blue-tx);flex-shrink:0}
.tipo-icon{width:38px;height:38px;border-radius:var(--r-sm);background:var(--bg3);display:flex;align-items:center;justify-content:center;flex-shrink:0;color:var(--ink-mid)}
.acc-nombre{font-size:14px;font-weight:600;letter-spacing:.06em;text-transform:uppercase}
.acc-sub{font-size:10px;color:var(--ink-light);text-transform:uppercase;letter-spacing:.05em;margin-top:2px}
.acc-stat-val{font-size:16px;font-weight:600;text-align:right}
.acc-stat-label{font-size:9px;color:var(--ink-light);letter-spacing:.1em;text-transform:uppercase;text-align:right}
.acc-body{border-top:.5px solid var(--rule);display:none}
.acc-body.open{display:block}
.col-header{display:grid;gap:8px;padding:6px 18px;background:var(--bg2);border-bottom:.5px solid var(--rule)}
.col-head{font-size:9px;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:var(--ink-light)}
.obra-row{display:grid;gap:8px;padding:9px 18px;border-bottom:.5px solid var(--rule);align-items:center;cursor:pointer;-webkit-tap-highlight-color:transparent}
.obra-row:last-child{border-bottom:none}
.obra-row:active{background:var(--bg2)}
.obra-row-titulo{font-size:14px;font-style:italic;font-weight:500}
.obra-row-meta{font-size:11px;color:var(--ink-mid)}
.obra-row-precio{font-size:14px;font-weight:600;text-align:right}

/* CARRITO */
.carrito-panel{padding:.75rem 0;max-width:600px;margin:0 auto}
.paso-indicator{display:flex;align-items:center;margin-bottom:1.25rem}
.paso-circle{width:28px;height:28px;border-radius:50%;background:var(--bg3);color:var(--ink-light);display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;flex-shrink:0;border:.5px solid var(--rule-dark)}
.paso-circle.on{background:var(--ink);color:#fff;border-color:var(--ink)}
.paso-label{font-size:11px;color:var(--ink-light);letter-spacing:.06em;text-transform:uppercase}
.paso-label.on{color:var(--ink);font-weight:600}
.paso-line{flex:1;height:1px;background:var(--rule-dark);margin:0 12px}
.paso-line.on{background:var(--ink)}
.cart-card{background:var(--bg);border:.5px solid var(--rule);border-radius:var(--r-lg);overflow:hidden;margin-bottom:1rem}
.cart-header{padding:11px 16px;border-bottom:.5px solid var(--rule);background:var(--bg2);display:flex;justify-content:space-between;align-items:center}
.cart-row{display:grid;grid-template-columns:48px 1fr auto auto;gap:10px;padding:12px 16px;align-items:center}
.cart-row+.cart-row{border-top:.5px solid var(--rule)}
.cart-thumb{width:48px;height:48px;border-radius:var(--r-sm);background:var(--bg3);overflow:hidden;flex-shrink:0}
.cart-thumb img{width:100%;height:100%;object-fit:cover}
.cart-total{padding:14px 16px;border-top:2px solid var(--ink);display:flex;justify-content:space-between;align-items:center}
.checkout-sec{background:var(--bg);border:.5px solid var(--rule);border-radius:var(--r-lg);overflow:hidden;margin-bottom:1rem}
.checkout-sec-hdr{padding:11px 16px;border-bottom:.5px solid var(--rule);background:var(--bg2)}
.checkout-sec-hdr span{font-size:11px;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:var(--ink-mid)}
.checkout-body{padding:16px}
.form-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.form-full{grid-column:1/-1}
@media(max-width:640px){.form-grid{grid-template-columns:1fr}}
.f-label{font-size:10px;font-weight:500;letter-spacing:.1em;text-transform:uppercase;color:var(--ink-mid);display:block;margin-bottom:5px}
.f-inp{font-family:inherit;font-size:16px;color:var(--ink);background:var(--bg);border:.5px solid var(--rule-dark);border-radius:var(--r-sm);padding:10px;width:100%;-webkit-appearance:none;appearance:none}
.f-sel{font-family:inherit;font-size:16px;color:var(--ink);background:var(--bg);border:.5px solid var(--rule-dark);border-radius:var(--r-sm);padding:10px;width:100%;-webkit-appearance:none;appearance:none;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 24 24' fill='none' stroke='%239a9590' stroke-width='2'%3E%3Cpolyline points='6 9 12 15 18 9'/%3E%3C/svg%3E");
  background-repeat:no-repeat;background-position:right 10px center;padding-right:32px}
.f-inp:focus,.f-sel:focus{outline:none;border-color:var(--ink-mid)}
.res-row{display:flex;justify-content:space-between;align-items:center;padding:9px 16px;font-size:13px}
.res-row+.res-row{border-top:.5px solid var(--rule)}
.res-sub{color:var(--ink-mid)}
.res-desc{color:#c0392b;border-top:.5px solid var(--rule)}
.res-total{padding:12px 16px;border-top:2px solid var(--ink);display:flex;justify-content:space-between;font-size:20px;font-weight:700}
.btns-accion{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:10px}
@media(max-width:480px){.btns-accion{grid-template-columns:1fr}}

/* BTNS */
.btn{font-family:inherit;font-size:10px;font-weight:500;letter-spacing:.15em;text-transform:uppercase;
  padding:9px 16px;border-radius:var(--r-sm);cursor:pointer;border:.5px solid var(--rule-dark);
  background:transparent;color:var(--ink-mid);display:inline-flex;align-items:center;gap:6px;-webkit-tap-highlight-color:transparent}
.btn:active{background:var(--bg3)}
.btn-primary{background:var(--ink);color:var(--bg);border-color:var(--ink)}
.btn-primary:active{opacity:.85}
.btn-danger{border-color:#c0392b;color:#c0392b}
.btn-danger:active{background:#fdf0ef}
.btn-lg{font-size:12px;font-weight:700;padding:14px 22px;border-radius:var(--r-md);box-shadow:0 4px 14px rgba(0,0,0,.14)}
.btn-checkout{width:100%;justify-content:center;font-size:13px;font-weight:700;padding:15px 24px;border-radius:var(--r-md);background:var(--ink);color:var(--bg);border:none;box-shadow:0 4px 14px rgba(0,0,0,.16);margin-top:4px;letter-spacing:.1em}
.btn-back{width:100%;justify-content:center;font-size:11px;padding:11px;border-radius:var(--r-sm);background:transparent;border:.5px solid var(--rule-dark);color:var(--ink-light);margin-top:10px}
.btn-outline{background:transparent;border:1.5px solid var(--ink);color:var(--ink)}

/* EMPTY */
.empty{padding:3rem 0;text-align:center;color:var(--ink-light)}
.empty svg{opacity:.3;margin-bottom:12px}
.empty p{font-size:10px;letter-spacing:.15em;text-transform:uppercase}
.empty p.sub{font-size:12px;text-transform:none;letter-spacing:0;margin-top:4px}

/* FAB */
.fab{position:fixed;bottom:max(1.5rem,calc(env(safe-area-inset-bottom)+1rem));
  right:max(1.25rem,env(safe-area-inset-right));width:56px;height:56px;border-radius:50%;
  background:var(--ink);color:var(--bg);border:none;cursor:pointer;display:none;
  align-items:center;justify-content:center;z-index:50;box-shadow:0 4px 16px rgba(0,0,0,.22);
  -webkit-tap-highlight-color:transparent}
.fab:active{transform:scale(.93)}
@media(max-width:640px){.fab{display:flex}}

/* TOAST */
.toast{position:fixed;bottom:2rem;left:50%;transform:translateX(-50%) translateY(8px);
  background:var(--ink);color:var(--bg);font-size:10px;font-weight:500;letter-spacing:.12em;
  text-transform:uppercase;padding:10px 20px;border-radius:20px;opacity:0;
  transition:opacity .3s,transform .3s;z-index:300;pointer-events:none;white-space:nowrap}
.toast.show{opacity:1;transform:translateX(-50%) translateY(0)}

/* ── MODALES ── */
/* Todos los modales usan la misma estructura base */
.overlay{position:fixed;inset:0;background:rgba(10,9,8,.45);display:none;align-items:flex-end;justify-content:center;z-index:100}
.overlay.open{display:flex}
.overlay-center{align-items:center;padding:1rem}
.modal-box{background:var(--bg);border-radius:var(--r-lg) var(--r-lg) 0 0;width:100%;
  max-width:660px;max-height:93vh;max-height:93svh;overflow-y:auto;
  -webkit-overflow-scrolling:touch;overscroll-behavior:contain}
.modal-box.center-box{border-radius:var(--r-lg);max-width:400px;max-height:none;overflow:visible}
.modal-handle{width:36px;height:4px;background:var(--rule-dark);border-radius:2px;margin:0 auto 10px}
.modal-hdr{position:sticky;top:0;background:var(--bg);border-bottom:.5px solid var(--rule);padding:14px 18px 12px;z-index:2;display:flex;justify-content:space-between;align-items:center}
.modal-title{font-size:15px;font-weight:600;letter-spacing:.06em;text-transform:uppercase}
.modal-close{background:none;border:none;font-size:22px;cursor:pointer;color:var(--ink-light);line-height:1;padding:2px 6px;-webkit-tap-highlight-color:transparent}
.modal-body{padding:18px}
.modal-ftr{position:sticky;bottom:0;background:var(--bg);border-top:.5px solid var(--rule);padding:12px 18px;padding-bottom:max(12px,env(safe-area-inset-bottom));display:flex;justify-content:flex-end;gap:10px;z-index:2}
@media(max-width:640px){.modal-body{padding:14px}.form-grid{grid-template-columns:1fr}}

/* DETALLE */
.detail-top{display:grid;grid-template-columns:1fr 1fr}
@media(max-width:600px){.detail-top{grid-template-columns:1fr}}
.detail-img-area{background:var(--bg3);display:flex;flex-direction:column}
.detail-img-main{aspect-ratio:1;overflow:hidden;display:flex;align-items:center;justify-content:center}
.detail-img-main img{width:100%;height:100%;object-fit:cover}
.detail-thumbs{display:flex;gap:6px;padding:8px 14px;overflow-x:auto}
.detail-thumb{width:46px;height:46px;object-fit:cover;border-radius:var(--r-sm);cursor:pointer;flex-shrink:0;-webkit-tap-highlight-color:transparent}
.detail-info{padding:18px;display:flex;flex-direction:column;justify-content:space-between}
.ficha{width:100%;border-collapse:collapse}
.ficha tr{border-bottom:.5px solid var(--rule)}
.ficha tr:last-child{border-bottom:none}
.ficha td{padding:5px 0;font-size:12px;vertical-align:top;line-height:1.5}
.ficha td:first-child{font-size:9px;font-weight:500;letter-spacing:.1em;text-transform:uppercase;color:var(--ink-light);width:42%}
.precio-bloque{border-top:.5px solid var(--ink-mid);padding-top:14px;margin-top:14px}
.detail-ftr{display:flex;justify-content:space-between;align-items:center;padding:12px 18px;border-top:.5px solid var(--rule);padding-bottom:max(12px,env(safe-area-inset-bottom));flex-wrap:wrap;gap:8px}

/* FOTOS UPLOADER */
.fotos-grid{display:grid;grid-template-columns:repeat(5,1fr);gap:8px;margin-bottom:10px}
@media(max-width:640px){.fotos-grid{grid-template-columns:repeat(3,1fr)}}
.foto-thumb{position:relative;aspect-ratio:1;border-radius:var(--r-sm);overflow:hidden;background:var(--bg3);border:.5px solid var(--rule)}
.foto-thumb img{width:100%;height:100%;object-fit:cover;display:block}
.foto-principal{position:absolute;bottom:4px;left:4px;font-size:8px;font-weight:600;text-transform:uppercase;background:var(--ink);color:#fff;padding:2px 6px;border-radius:3px}
.foto-quitar{position:absolute;top:4px;right:4px;width:22px;height:22px;border-radius:50%;background:rgba(0,0,0,.55);border:none;cursor:pointer;color:#fff;font-size:14px;display:flex;align-items:center;justify-content:center;-webkit-tap-highlight-color:transparent}
.upload-btns{display:flex;gap:8px;flex-wrap:wrap}
.upload-btn{flex:1;min-width:110px;border:.5px solid var(--rule-dark);border-radius:var(--r-md);padding:12px 10px;cursor:pointer;display:flex;flex-direction:column;align-items:center;gap:6px;background:var(--bg2);text-align:center;-webkit-tap-highlight-color:transparent}
.upload-drop{flex:2;min-width:140px;border:1px dashed var(--rule-dark);border-radius:var(--r-md);padding:12px 16px;cursor:pointer;display:flex;align-items:center;gap:10px;background:var(--bg2)}
@media(max-width:640px){.upload-drop{display:none}}

/* CERTIFICADO OVERLAY */
.cert-overlay{position:fixed;inset:0;z-index:500;background:#374151;display:none;flex-direction:column}
.cert-overlay.open{display:flex}
.cert-bar{display:flex;align-items:center;justify-content:space-between;background:var(--ink);color:#fff;padding:12px 20px;flex-shrink:0;gap:12px;flex-wrap:wrap}
.cert-bar-title{font-size:12px;font-weight:600;letter-spacing:.1em;text-transform:uppercase;white-space:nowrap}
.cert-bar-btns{display:flex;gap:10px;flex-wrap:wrap}
.cert-scroll{flex:1;overflow:auto;display:flex;justify-content:center;padding:24px}
.cert-doc{background:#fff;width:210mm;min-height:297mm;box-shadow:0 8px 40px rgba(0,0,0,.4);flex-shrink:0;font-family:'DM Sans',sans-serif;color:#141210;display:flex;flex-direction:column}
@media print{
  body>*:not(.cert-overlay){display:none!important}
  .cert-overlay{position:static!important;background:#fff!important;display:block!important}
  .cert-bar{display:none!important}
  .cert-scroll{padding:0!important;overflow:visible!important;display:block!important}
  .cert-doc{box-shadow:none!important;width:100%!important}
}
</style>
</head>
<body>

<div class="shell">
  <!-- HEADER -->
  <div class="header">
    <div style="margin-bottom:.75rem">
      <div class="g-nombre">Planta Libre Espacio Experimental</div>
      <div class="g-info">Zuazua 457 Zona Centro · Mexicali, Baja California, México · C.P. 21100<br>plantalibre.mxl@gmail.com</div>
    </div>
    <div class="header-bottom">
      <span class="header-titulo">Catálogo de obra</span>
      <button class="btn btn-primary" id="btn-agregar-header">
        <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>
        Agregar obra
      </button>
    </div>
  </div>

  <!-- STATS -->
  <div class="stats-row" id="stats-row"></div>

  <!-- TABS -->
  <div class="tabs-nav" id="tabs-nav">
    <button class="tab-btn activo" data-tab="catalogo">
      <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="3" y="3" width="7" height="7" rx="1"/><rect x="14" y="3" width="7" height="7" rx="1"/><rect x="3" y="14" width="7" height="7" rx="1"/><rect x="14" y="14" width="7" height="7" rx="1"/></svg>
      Catálogo <span class="tab-count" id="tc-catalogo">0</span>
    </button>
    <button class="tab-btn" data-tab="artista">
      <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="12" cy="8" r="4"/><path d="M4 20c0-4 3.6-7 8-7s8 3 8 7"/></svg>
      Por artista <span class="tab-count" id="tc-artista">0</span>
    </button>
    <button class="tab-btn" data-tab="tipo">
      <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M4 6h16M4 12h10M4 18h6"/></svg>
      Por tipo <span class="tab-count" id="tc-tipo">0</span>
    </button>
    <button class="tab-btn" data-tab="ubicacion">
      <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7z"/><circle cx="12" cy="9" r="2.5"/></svg>
      Por ubicación <span class="tab-count" id="tc-ubicacion">0</span>
    </button>
    <button class="tab-btn" data-tab="carrito">
      <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="9" cy="21" r="1"/><circle cx="20" cy="21" r="1"/><path d="M1 1h4l2.68 13.39a2 2 0 002 1.61h9.72a2 2 0 002-1.61L23 6H6"/></svg>
      Venta <span class="tab-count" id="tc-carrito">0</span>
    </button>
    <div style="margin-left:auto;display:flex;align-items:center;gap:6px;padding-right:2px">
      <button class="btn" id="btn-exportar" style="font-size:9px;padding:5px 10px">
        <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>Exportar
      </button>
      <label class="btn" style="font-size:9px;padding:5px 10px;cursor:pointer">
        <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4"/><polyline points="17 8 12 3 7 8"/><line x1="12" y1="3" x2="12" y2="15"/></svg>Importar
        <input type="file" id="inp-importar" accept=".json" style="display:none">
      </label>
    </div>
  </div>

  <!-- FILTROS -->
  <div class="filtros" id="filtros-bar">
    <span class="filtro-label">Estado</span>
    <button class="chip activo" data-filtro="todos">Todas</button>
    <button class="chip" data-filtro="Disponible">Disponibles</button>
    <button class="chip" data-filtro="Reservada">Reservadas</button>
    <button class="chip" data-filtro="Vendida">Vendidas</button>
    <div style="margin-left:auto"><input class="busq" id="buscador" type="text" placeholder="Buscar..."></div>
  </div>

  <!-- PANELS -->
  <div id="panel-catalogo"><div class="obras-grid" id="obras-grid"></div></div>
  <div id="panel-artista"   style="display:none"><div class="panel-section" id="artista-panel"></div></div>
  <div id="panel-tipo"      style="display:none"><div class="panel-section" id="tipo-panel"></div></div>
  <div id="panel-ubicacion" style="display:none"><div class="panel-section" id="ubicacion-panel"></div></div>
  <div id="panel-carrito"   style="display:none"><div class="carrito-panel" id="carrito-panel"></div></div>
</div>

<!-- FAB -->
<button class="fab" id="fab-agregar">
  <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>
</button>

<!-- MODAL FORMULARIO -->
<div class="overlay" id="modal-form">
  <div class="modal-box" style="max-width:640px">
    <div class="modal-hdr">
      <div><div class="modal-handle"></div><span class="modal-title" id="form-titulo">Nueva obra</span></div>
      <button class="modal-close" id="btn-cerrar-form">×</button>
    </div>
    <div class="modal-body">
      <div class="form-grid">
        <div><label class="f-label">Título</label><input class="f-inp" id="f-titulo" placeholder="Sin título (campo rojo)"></div>
        <div><label class="f-label">Artista</label><input class="f-inp" id="f-artista" placeholder="Nombre completo"></div>
        <div><label class="f-label">Disciplina</label>
          <select class="f-sel" id="f-tipo">
            <option>Pintura</option><option>Escultura</option><option>Fotografía</option>
            <option>Arte digital / instalación</option><option>Obra gráfica / grabado</option><option>Mixta</option>
          </select>
        </div>
        <div><label class="f-label">Estado</label>
          <select class="f-sel" id="f-estado"><option>Disponible</option><option>Reservada</option><option>Vendida</option></select>
        </div>
        <div><label class="f-label">Técnica</label><input class="f-inp" id="f-tecnica" placeholder="Óleo sobre lino"></div>
        <div><label class="f-label">Dimensiones</label><input class="f-inp" id="f-dimensiones" placeholder="120 × 90 cm"></div>
        <div><label class="f-label">Año</label><input class="f-inp" id="f-anio" placeholder="2024"></div>
        <div><label class="f-label">Edición / tiraje</label><input class="f-inp" id="f-edicion" placeholder="Pieza única · 3/5+2PA"></div>
        <div><label class="f-label">Ubicación</label><input class="f-inp" id="f-ubicacion" placeholder="Sala principal · Bodega"></div>
        <div><label class="f-label">Precio (MXN)</label><input class="f-inp" type="number" id="f-precio" placeholder="38000" min="0"></div>
        <div><label class="f-label">Registro</label><input class="f-inp" id="f-registro" placeholder="PL-001"></div>
        <div class="form-full">
          <label class="f-label">Fotografías <span style="font-weight:400;color:var(--ink-light)">(máx. 5)</span></label>
          <div class="fotos-grid" id="fotos-grid"></div>
          <div class="upload-btns">
            <label class="upload-btn">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="var(--ink-mid)" stroke-width="1.5"><path d="M23 19a2 2 0 01-2 2H3a2 2 0 01-2-2V8a2 2 0 012-2h4l2-3h6l2 3h4a2 2 0 012 2z"/><circle cx="12" cy="13" r="4"/></svg>
              <span style="font-size:11px;font-weight:600;color:var(--ink)">Tomar foto</span>
              <span style="font-size:10px;color:var(--ink-light)">Cámara</span>
              <input type="file" accept="image/*" capture="environment" multiple style="display:none" id="inp-camara">
            </label>
            <label class="upload-btn">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="var(--ink-mid)" stroke-width="1.5"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21,15 16,10 5,21"/></svg>
              <span style="font-size:11px;font-weight:600;color:var(--ink)">Subir archivos</span>
              <span style="font-size:10px;color:var(--ink-light)">Galería / escritorio</span>
              <input type="file" id="inp-fotos" accept="image/jpeg,image/png,image/webp" multiple style="display:none">
            </label>
            <div class="upload-drop" id="drop-zone">
              <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="var(--ink-light)" stroke-width="1.5" style="flex-shrink:0"><path d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4"/><polyline points="17 8 12 3 7 8"/><line x1="12" y1="3" x2="12" y2="15"/></svg>
              <div>
                <div id="drop-label" style="font-size:12px;font-weight:600;color:var(--ink)">Arrastra aquí</div>
                <div style="font-size:10px;color:var(--ink-light);margin-top:2px">Suelta imágenes</div>
              </div>
            </div>
          </div>
          <input type="hidden" id="f-imagen">
        </div>
        <div class="form-full">
          <label class="f-label">Nota curatorial</label>
          <textarea class="f-inp" id="f-nota" placeholder="Descripción, contexto o comentario..." style="min-height:70px;resize:vertical"></textarea>
        </div>
      </div>
    </div>
    <div class="modal-ftr">
      <button class="btn" id="btn-cancelar-form">Cancelar</button>
      <button class="btn btn-primary" id="btn-guardar-obra">Guardar obra</button>
    </div>
  </div>
</div>

<!-- MODAL DETALLE -->
<div class="overlay" id="modal-detalle">
  <div class="modal-box" style="max-width:660px" id="modal-detalle-box"></div>
</div>

<!-- MODAL CONFIRMAR ELIMINAR -->
<div class="overlay overlay-center" id="modal-confirmar">
  <div class="modal-box center-box" style="padding:24px">
    <div style="font-size:16px;font-weight:600;margin-bottom:10px">¿Eliminar esta obra?</div>
    <div style="font-size:13px;color:var(--ink-mid);line-height:1.6;margin-bottom:20px">Esta acción no se puede deshacer.</div>
    <div style="display:flex;justify-content:flex-end;gap:10px">
      <button class="btn" id="btn-cancelar-borrar">Cancelar</button>
      <button class="btn btn-danger" id="btn-confirmar-borrar" style="background:#c0392b;color:#fff;border-color:#c0392b">Eliminar</button>
    </div>
  </div>
</div>

<!-- CERTIFICADO OVERLAY -->
<div class="cert-overlay" id="cert-overlay">
  <div class="cert-bar">
    <span class="cert-bar-title">Certificado de Autenticidad</span>
    <div class="cert-bar-btns">
      <button class="btn btn-primary btn-lg" id="btn-cert-print">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polyline points="6 9 6 2 18 2 18 9"/><path d="M6 18H4a2 2 0 01-2-2v-5a2 2 0 012-2h16a2 2 0 012 2v5a2 2 0 01-2 2h-2"/><rect x="6" y="14" width="12" height="8"/></svg>
        Imprimir / Guardar PDF
      </button>
      <button class="btn" id="btn-cert-cerrar" style="border-color:rgba(255,255,255,.4);color:#fff;background:transparent">✕ Cerrar</button>
    </div>
  </div>
  <div class="cert-scroll">
    <div class="cert-doc" id="cert-doc"></div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<script>
'use strict';
/* ═══════════════════════════════════════════════════════
   PLANTA LIBRE — CATÁLOGO DE OBRA
   Todos los listeners son addEventListener puros.
   Sin onclick en innerHTML. Sin dependencias externas
   excepto jsPDF para el PDF de ventas.
════════════════════════════════════════════════════════ */

const GALERIA = {
  nombre:    'Planta Libre Espacio Experimental',
  direccion: 'Zuazua 457 Zona Centro, Mexicali, Baja California, México, C.P. 21100',
  email:     'plantalibre.mxl@gmail.com'
};

/* ── ESTADO GLOBAL ── */
let obras = [], nextId = 1, carrito = [], fotosActuales = [];
let filtroActivo = 'todos', tabActivo = 'catalogo';
let editandoId = null, obraDetalle = null, obraABorrar = null;
let artistasAb = {}, tiposAb = {}, ubicAb = {};
let pasoCarrito = 1;
let db = null;

/* ── INDEXEDDB ── */
function abrirDB() {
  return new Promise(r => {
    if (!window.indexedDB) { r(null); return; }
    const req = indexedDB.open('plantalibre', 1);
    req.onupgradeneeded = e => e.target.result.createObjectStore('catalogo', { keyPath: 'key' });
    req.onsuccess = e => { db = e.target.result; r(db); };
    req.onerror = () => r(null);
  });
}
const dbGet = k => new Promise(r => {
  if (!db) { r(null); return; }
  const q = db.transaction('catalogo','readonly').objectStore('catalogo').get(k);
  q.onsuccess = () => r(q.result?.value ?? null);
  q.onerror = () => r(null);
});
const dbSet = (k,v) => new Promise(r => {
  if (!db) { r(false); return; }
  const tx = db.transaction('catalogo','readwrite');
  tx.objectStore('catalogo').put({ key: k, value: v });
  tx.oncomplete = () => r(true);
  tx.onerror = () => r(false);
});

/* ── PERSISTENCIA ── */
async function cargar() {
  await abrirDB();
  let d = db ? await dbGet('planta-libre-catalogo-v1') : null;
  if (!d) { try { const r = localStorage.getItem('planta-libre-catalogo-v1'); if (r) d = JSON.parse(r); } catch {} }
  if (d?.obras) { obras = d.obras; nextId = d.nextId || Math.max(0,...obras.map(o=>o.id)) + 1; }
  else { obras = datosEjemplo(); nextId = obras.length + 1; }
}
async function guardar() {
  const d = { obras, nextId };
  if (db) await dbSet('planta-libre-catalogo-v1', d);
  try { localStorage.setItem('planta-libre-catalogo-v1', JSON.stringify({ ...d, obras: d.obras.map(o=>({...o,imagen:''})) })); } catch {}
}
function datosEjemplo() {
  return [
    {id:1,titulo:'Sin título (campo rojo)',artista:'Ana Reyes',tipo:'Pintura',tecnica:'Óleo sobre lino',dimensiones:'120 × 90 cm',anio:'2024',edicion:'Pieza única',ubicacion:'Sala principal',precio:38000,estado:'Disponible',nota:'Capas superpuestas con preparación pigmentada.',imagen:'[]',registro:'PL-001'},
    {id:2,titulo:'Umbral, núm. 3',artista:'Carlos Ibáñez',tipo:'Fotografía',tecnica:'Inkjet sobre papel de algodón',dimensiones:'60 × 80 cm',anio:'2023',edicion:'3/5 + 2 PA',ubicacion:'En préstamo',precio:14500,estado:'Reservada',nota:'Serie sobre umbrales de luz.',imagen:'[]',registro:'PL-002'},
    {id:3,titulo:'Fractura lenta',artista:'Valeria Muro',tipo:'Obra gráfica / grabado',tecnica:'Aguafuerte y aguatinta',dimensiones:'Huella 40×30 / Papel 56×38 cm',anio:'2024',edicion:'7/20',ubicacion:'Bodega',precio:6800,estado:'Disponible',nota:'',imagen:'[]',registro:'PL-003'},
    {id:4,titulo:'Forma blanda II',artista:'Jorge Peralta',tipo:'Escultura',tecnica:'Bronce patinado',dimensiones:'45 × 22 × 18 cm',anio:'2023',edicion:'2/3 + 1 PA',ubicacion:'—',precio:72000,estado:'Vendida',nota:'Base no incluida.',imagen:'[]',registro:'PL-004'},
    {id:5,titulo:'Loop 44',artista:'Ana Reyes',tipo:'Arte digital / instalación',tecnica:'Videoarte, loop generativo',dimensiones:'4K · 3840×2160 px',anio:'2024',edicion:'1/3',ubicacion:'Sala experimental',precio:24000,estado:'Disponible',nota:'',imagen:'[]',registro:'PL-005'},
    {id:6,titulo:'Sedimento I',artista:'Valeria Muro',tipo:'Pintura',tecnica:'Técnica mixta sobre tela',dimensiones:'90 × 70 cm',anio:'2023',edicion:'Pieza única',ubicacion:'Sala principal',precio:28000,estado:'Disponible',nota:'',imagen:'[]',registro:'PL-006'},
  ];
}

/* ── UTILS ── */
const fmt = n => n ? Number(n).toLocaleString('es-MX',{style:'currency',currency:'MXN',minimumFractionDigits:0}) : '—';
const ini = n => n.split(' ').map(p=>p[0]).slice(0,2).join('').toUpperCase();
const pillCls = e => e==='Disponible'?'pill-disp':e==='Reservada'?'pill-res':'pill-vend';
const fechaHoy = () => new Date().toLocaleDateString('es-MX',{year:'numeric',month:'long',day:'numeric'});
const folioNuevo = () => 'PL-'+Date.now().toString().slice(-6);
function getFotos(o) {
  try { const p=JSON.parse(o.imagen||'[]'); return Array.isArray(p)?p:(o.imagen?.startsWith('data:')?[o.imagen]:[]); } catch { return o.imagen?[o.imagen]:[]; }
}
function toast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg; t.classList.add('show');
  clearTimeout(t._t); t._t = setTimeout(() => t.classList.remove('show'), 2500);
}

/* ── EXPORTAR / IMPORTAR ── */
function exportarJSON() {
  const a = document.createElement('a');
  a.href = URL.createObjectURL(new Blob([JSON.stringify({obras,nextId},null,2)],{type:'application/json'}));
  a.download = 'catalogo-planta-libre-'+new Date().toISOString().slice(0,10)+'.json';
  a.click(); toast('Catálogo exportado');
}
function importarJSON(e) {
  const f = e.target.files[0]; if (!f) return;
  const r = new FileReader();
  r.onload = ev => {
    try {
      const d = JSON.parse(ev.target.result);
      if (d.obras && Array.isArray(d.obras)) {
        obras = d.obras; nextId = d.nextId || Math.max(0,...d.obras.map(o=>o.id)) + 1;
        guardar(); renderStats(); renderTab(); toast('Importado · '+d.obras.length+' obras');
      } else toast('Archivo no válido');
    } catch { toast('Error al leer'); }
  };
  r.readAsText(f); e.target.value = '';
}

/* ── STATS ── */
function renderStats() {
  const t=obras.length, d=obras.filter(o=>o.estado==='Disponible').length, v=obras.filter(o=>o.estado==='Vendida').length;
  const val=obras.filter(o=>o.estado==='Disponible').reduce((a,b)=>a+(Number(b.precio)||0),0);
  document.getElementById('stats-row').innerHTML=`
    <div class="stat"><div class="stat-label">Total</div><div class="stat-val">${t}</div></div>
    <div class="stat"><div class="stat-label">Disponibles</div><div class="stat-val">${d}</div></div>
    <div class="stat"><div class="stat-label">Vendidas</div><div class="stat-val">${v}</div></div>
    <div class="stat"><div class="stat-label">Valor disp.</div><div class="stat-val">${val?'$'+Math.round(val/1000)+'k':'—'}</div></div>`;
  document.getElementById('tc-catalogo').textContent = obras.length;
  document.getElementById('tc-artista').textContent = [...new Set(obras.map(o=>o.artista))].length;
  document.getElementById('tc-tipo').textContent = [...new Set(obras.map(o=>o.tipo))].length;
  document.getElementById('tc-ubicacion').textContent = [...new Set(obras.map(o=>(o.ubicacion||'—').trim()).filter(u=>u&&u!=='—'))].length;
  const tc = document.getElementById('tc-carrito');
  tc.textContent = carrito.length;
  tc.className = 'tab-count' + (carrito.length > 0 ? ' rojo' : '');
}

/* ── TABS ── */
function setTab(tab) {
  tabActivo = tab;
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.toggle('activo', b.dataset.tab === tab));
  ['catalogo','artista','tipo','ubicacion','carrito'].forEach(t =>
    document.getElementById('panel-'+t).style.display = t === tab ? 'block' : 'none'
  );
  const esCarrito = tab === 'carrito';
  document.getElementById('filtros-bar').style.display = esCarrito ? 'none' : 'flex';
  document.getElementById('fab-agregar').style.display = esCarrito ? 'none' : 'flex';
  renderTab();
}
function renderTab() {
  if (tabActivo==='catalogo') renderCatalogo();
  else if (tabActivo==='artista') renderArtistas();
  else if (tabActivo==='tipo') renderTipos();
  else if (tabActivo==='ubicacion') renderUbicaciones();
  else renderCarrito();
}

/* ── FILTRADO ── */
function filtradas() {
  const q = document.getElementById('buscador').value.toLowerCase();
  return obras.filter(o =>
    (filtroActivo==='todos' || o.estado===filtroActivo) &&
    (!q || o.titulo.toLowerCase().includes(q) || o.artista.toLowerCase().includes(q))
  );
}

/* ── CATÁLOGO ── */
function renderCatalogo() {
  const lista = filtradas();
  const grid = document.getElementById('obras-grid');
  if (!lista.length) { grid.innerHTML = emptyHTML('Sin obras que coincidan'); return; }
  const tipos = [...new Set(lista.map(o=>o.tipo))];
  grid.innerHTML = tipos.map(tipo => {
    const g = lista.filter(o=>o.tipo===tipo);
    return `<div class="grupo-header"><span class="grupo-nombre">${tipo}</span><span class="grupo-badge">${g.length}</span></div>`
      + g.map(o => obraCardHTML(o)).join('');
  }).join('');
  // Listeners en las cards
  grid.querySelectorAll('.obra-card').forEach(card => {
    card.addEventListener('click', () => verDetalle(parseInt(card.dataset.id)));
  });
  grid.querySelectorAll('.btn-cart').forEach(btn => {
    btn.addEventListener('click', e => { e.stopPropagation(); toggleCarrito(parseInt(btn.dataset.id)); });
  });
}

function obraCardHTML(o) {
  const fotos = getFotos(o), src = fotos[0]||'';
  const enC = carrito.includes(o.id), esD = o.estado==='Disponible';
  return `<div class="obra-card" data-id="${o.id}">
    <div class="obra-img">
      ${src ? `<img src="${src}" alt="${o.titulo}" loading="lazy">` : ''}
      <div class="obra-img-ph" ${src?'style="display:none"':''}>
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1"><rect x="3" y="3" width="18" height="18" rx="1"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21,15 16,10 5,21"/></svg>
        <span>Imagen</span>
      </div>
      <span class="pill ${pillCls(o.estado)} card-pill">${o.estado}</span>
      ${esD ? `<button class="btn-cart ${enC?'activo':''}" data-id="${o.id}" title="${enC?'Quitar':'Agregar a venta'}">${enC?'✓':'＋'}</button>` : ''}
    </div>
    <div class="obra-body">
      <div class="obra-num">${o.registro||'—'}</div>
      <div class="obra-titulo-card">${o.titulo}</div>
      <div class="obra-artista-card">${o.artista}</div>
      <div class="obra-meta">
        <span class="obra-anio">${o.anio||''}</span>
        <span class="obra-precio ${o.estado==='Vendida'?'vendida':''}">${fmt(o.precio)}</span>
      </div>
    </div>
  </div>`;
}

/* ── ACCORDION HELPER ── */
function accBody(cols, cabeceras, filas, id, onRowClick) {
  return `<div class="acc-body ${id?'open':''}" id="${id||''}">
    <div class="col-header" style="grid-template-columns:${cols}">
      ${cabeceras.map((h,i)=>`<span class="col-head" style="${i===cabeceras.length-1?'text-align:right':''}">${h}</span>`).join('')}
    </div>
    ${filas}
  </div>`;
}

/* ── POR ARTISTA ── */
function renderArtistas() {
  const lista = filtradas(), panel = document.getElementById('artista-panel');
  const arts = [...new Set(lista.map(o=>o.artista))].sort();
  if (!arts.length) { panel.innerHTML = emptyHTML('Sin artistas que coincidan'); return; }
  const cols = '2fr 1fr 1fr 1fr';
  panel.innerHTML = arts.map(a => {
    const od = lista.filter(o=>o.artista===a);
    const val = od.filter(o=>o.estado==='Disponible').reduce((s,o)=>s+(Number(o.precio)||0),0);
    const ab = artistasAb[a];
    const filas = od.map(o=>`<div class="obra-row" style="grid-template-columns:${cols}" data-id="${o.id}">
      <div><div class="obra-row-titulo">${o.titulo}</div><div style="display:flex;gap:5px;margin-top:3px"><span class="pill ${pillCls(o.estado)}" style="font-size:8px;padding:2px 7px">${o.estado}</span><span style="font-size:9px;color:var(--ink-light)">${o.registro||''}</span></div></div>
      <div class="obra-row-meta">${o.tipo}</div>
      <div class="obra-row-meta">${o.ubicacion||'—'}</div>
      <div class="obra-row-precio ${o.estado==='Vendida'?'vendida':''}">${fmt(o.precio)}</div>
    </div>`).join('');
    return `<div class="acc-card">
      <div class="acc-header" data-artista="${a}">
        <div style="display:flex;align-items:center;gap:12px">
          <div class="avatar">${ini(a)}</div>
          <div><div class="acc-nombre">${a}</div><div class="acc-sub">${od.length} obra${od.length!==1?'s':''}</div></div>
        </div>
        <div style="display:flex;align-items:center;gap:14px">
          <div><div class="acc-stat-val">${val?fmt(val):'—'}</div><div class="acc-stat-label">valor disp.</div></div>
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" style="color:var(--ink-light);transform:${ab?'rotate(180deg)':'none'}"><polyline points="6 9 12 15 18 9"/></svg>
        </div>
      </div>
      <div class="acc-body ${ab?'open':''}">
        <div class="col-header" style="grid-template-columns:${cols}">${['Título','Tipo','Ubicación','Precio'].map((h,i)=>`<span class="col-head" style="${i===3?'text-align:right':''}">${h}</span>`).join('')}</div>
        ${filas}
      </div>
    </div>`;
  }).join('');
  panel.querySelectorAll('.acc-header[data-artista]').forEach(h => {
    h.addEventListener('click', () => { const a=h.dataset.artista; artistasAb[a]=!artistasAb[a]; renderArtistas(); });
  });
  panel.querySelectorAll('.obra-row[data-id]').forEach(row => {
    row.addEventListener('click', () => verDetalle(parseInt(row.dataset.id)));
  });
}

/* ── POR TIPO ── */
function renderTipos() {
  const lista = filtradas(), panel = document.getElementById('tipo-panel');
  const tipos = [...new Set(lista.map(o=>o.tipo))].sort();
  if (!tipos.length) { panel.innerHTML = emptyHTML('Sin tipos que coincidan'); return; }
  const cols = '2fr 1.5fr 1fr 1fr';
  panel.innerHTML = tipos.map(t => {
    const od = lista.filter(o=>o.tipo===t);
    const disp=od.filter(o=>o.estado==='Disponible').length, vend=od.filter(o=>o.estado==='Vendida').length;
    const ab = tiposAb[t];
    const avs = [...new Set(od.map(o=>o.artista))].slice(0,3).map(a=>`<div class="avatar" style="width:26px;height:26px;font-size:9px">${ini(a)}</div>`).join('');
    const filas = od.map(o=>`<div class="obra-row" style="grid-template-columns:${cols}" data-id="${o.id}">
      <div><div class="obra-row-titulo">${o.titulo}</div><div style="display:flex;gap:5px;margin-top:3px"><span class="pill ${pillCls(o.estado)}" style="font-size:8px;padding:2px 7px">${o.estado}</span><span style="font-size:9px;color:var(--ink-light)">${o.registro||''}</span></div></div>
      <div class="obra-row-meta">${o.artista}</div>
      <div class="obra-row-meta">${o.ubicacion||'—'}</div>
      <div class="obra-row-precio ${o.estado==='Vendida'?'vendida':''}">${fmt(o.precio)}</div>
    </div>`).join('');
    return `<div class="acc-card">
      <div class="acc-header" data-tipo="${t}">
        <div style="display:flex;align-items:center;gap:12px">
          <div class="tipo-icon"><svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M4 6h16M4 12h10M4 18h6"/></svg></div>
          <div><div class="acc-nombre">${t}</div><div class="acc-sub">${od.length} obras · ${disp} disp. · ${vend} vend.</div></div>
        </div>
        <div style="display:flex;align-items:center;gap:8px">
          <div style="display:flex;gap:3px">${avs}</div>
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" style="color:var(--ink-light);transform:${ab?'rotate(180deg)':'none'}"><polyline points="6 9 12 15 18 9"/></svg>
        </div>
      </div>
      <div class="acc-body ${ab?'open':''}">
        <div class="col-header" style="grid-template-columns:${cols}">${['Título','Artista','Ubicación','Precio'].map((h,i)=>`<span class="col-head" style="${i===3?'text-align:right':''}">${h}</span>`).join('')}</div>
        ${filas}
      </div>
    </div>`;
  }).join('');
  panel.querySelectorAll('.acc-header[data-tipo]').forEach(h => {
    h.addEventListener('click', () => { const t=h.dataset.tipo; tiposAb[t]=!tiposAb[t]; renderTipos(); });
  });
  panel.querySelectorAll('.obra-row[data-id]').forEach(row => {
    row.addEventListener('click', () => verDetalle(parseInt(row.dataset.id)));
  });
}

/* ── POR UBICACIÓN ── */
function renderUbicaciones() {
  const lista = filtradas(), panel = document.getElementById('ubicacion-panel');
  const SIN = 'Sin ubicación asignada';
  const getU = o => (o.ubicacion&&o.ubicacion.trim()&&o.ubicacion.trim()!=='—') ? o.ubicacion.trim() : SIN;
  const ubics = [...new Set(lista.map(getU))].sort((a,b)=>a===SIN?1:b===SIN?-1:a.localeCompare(b,'es'));
  if (!ubics.length) { panel.innerHTML = emptyHTML('Sin ubicaciones'); return; }
  const cols = '2fr 1.2fr 1fr 1fr';
  panel.innerHTML = ubics.map(u => {
    const od = lista.filter(o=>getU(o)===u);
    const disp=od.filter(o=>o.estado==='Disponible').length, res=od.filter(o=>o.estado==='Reservada').length, vend=od.filter(o=>o.estado==='Vendida').length;
    const val=od.filter(o=>o.estado==='Disponible').reduce((s,o)=>s+(Number(o.precio)||0),0);
    const ab=ubicAb[u], esSin=u===SIN;
    const pills=[disp?`<span class="pill pill-disp" style="font-size:8px;padding:2px 7px">${disp} disp.</span>`:'',res?`<span class="pill pill-res" style="font-size:8px;padding:2px 7px">${res} res.</span>`:'',vend?`<span class="pill pill-vend" style="font-size:8px;padding:2px 7px">${vend} vend.</span>`:''].filter(Boolean).join('');
    const filas=od.map(o=>`<div class="obra-row" style="grid-template-columns:${cols}" data-id="${o.id}">
      <div><div class="obra-row-titulo">${o.titulo}</div><div style="font-size:10px;color:var(--ink-light);text-transform:uppercase;margin-top:2px">${o.artista} · ${o.registro||''}</div></div>
      <div class="obra-row-meta">${o.tipo}</div>
      <div><span class="pill ${pillCls(o.estado)}" style="font-size:8px;padding:2px 7px">${o.estado}</span></div>
      <div class="obra-row-precio ${o.estado==='Vendida'?'vendida':''}">${fmt(o.precio)}</div>
    </div>`).join('');
    return `<div class="acc-card">
      <div class="acc-header" data-ubic="${u}">
        <div style="display:flex;align-items:center;gap:12px">
          <div class="tipo-icon" style="color:${esSin?'var(--ink-light)':'var(--ink-mid)'}"><svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7z"/><circle cx="12" cy="9" r="2.5"/></svg></div>
          <div><div class="acc-nombre" style="color:${esSin?'var(--ink-light)':'var(--ink)'}">${u}</div><div style="display:flex;gap:4px;margin-top:4px;flex-wrap:wrap">${pills}</div></div>
        </div>
        <div style="display:flex;align-items:center;gap:14px">
          <div><div class="acc-stat-val">${val?fmt(val):'—'}</div><div class="acc-stat-label">valor disp.</div></div>
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" style="color:var(--ink-light);transform:${ab?'rotate(180deg)':'none'}"><polyline points="6 9 12 15 18 9"/></svg>
        </div>
      </div>
      <div class="acc-body ${ab?'open':''}">
        <div class="col-header" style="grid-template-columns:${cols}">${['Título / Artista','Tipo','Estado','Precio'].map((h,i)=>`<span class="col-head" style="${i===3?'text-align:right':''}">${h}</span>`).join('')}</div>
        ${filas}
      </div>
    </div>`;
  }).join('');
  panel.querySelectorAll('.acc-header[data-ubic]').forEach(h => {
    h.addEventListener('click', () => { const u=h.dataset.ubic; ubicAb[u]=!ubicAb[u]; renderUbicaciones(); });
  });
  panel.querySelectorAll('.obra-row[data-id]').forEach(row => {
    row.addEventListener('click', () => verDetalle(parseInt(row.dataset.id)));
  });
}

/* ── CARRITO ── */
function toggleCarrito(id) {
  const o = obras.find(x=>x.id===id);
  if (carrito.includes(id)) { carrito = carrito.filter(x=>x!==id); }
  else {
    if (o?.estado !== 'Disponible') { toast('Solo obras disponibles'); return; }
    carrito.push(id); toast('Agregada a la venta');
  }
  renderStats();
  if (tabActivo==='catalogo') renderCatalogo();
  if (tabActivo==='carrito') renderCarrito();
}

function renderCarrito() {
  const panel = document.getElementById('carrito-panel');
  const obrasC = carrito.map(id=>obras.find(o=>o.id===id)).filter(Boolean);
  if (!obrasC.length) { pasoCarrito=1; panel.innerHTML=`<div class="empty"><svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1"><circle cx="9" cy="21" r="1"/><circle cx="20" cy="21" r="1"/><path d="M1 1h4l2.68 13.39a2 2 0 002 1.61h9.72a2 2 0 002-1.61L23 6H6"/></svg><p>Sin obras seleccionadas</p><p class="sub">Agrega obras desde el catálogo con el botón ＋</p></div>`; return; }
  if (pasoCarrito===1) renderPaso1(panel, obrasC);
  else renderPaso2(panel, obrasC);
}

function pasoHTML(paso) {
  return `<div class="paso-indicator">
    <div style="display:flex;align-items:center;gap:8px"><div class="paso-circle ${paso>=1?'on':''}">${paso>1?'✓':'1'}</div><span class="paso-label ${paso>=1?'on':''}">Selección</span></div>
    <div class="paso-line ${paso>1?'on':''}"></div>
    <div style="display:flex;align-items:center;gap:8px"><div class="paso-circle ${paso>=2?'on':''}">2</div><span class="paso-label ${paso>=2?'on':''}">Checkout</span></div>
  </div>`;
}

function renderPaso1(panel, obrasC) {
  const sub = obrasC.reduce((a,o)=>a+(Number(o.precio)||0),0);
  panel.innerHTML = pasoHTML(1) + `
    <div class="cart-card">
      <div class="cart-header">
        <span style="font-size:11px;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:var(--ink-mid)">${obrasC.length} obra${obrasC.length!==1?'s':''} en la venta</span>
        <button class="btn" id="btn-limpiar-carrito" style="font-size:10px;padding:5px 10px">Limpiar todo</button>
      </div>
      ${obrasC.map(o=>{
        const fotos=getFotos(o),src=fotos[0]||'';
        return `<div class="cart-row">
          <div class="cart-thumb">${src?`<img src="${src}" alt="">`:'<div style="width:100%;height:100%;display:flex;align-items:center;justify-content:center;color:var(--ink-light);opacity:.3"><svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1"><rect x="3" y="3" width="18" height="18" rx="1"/></svg></div>'}</div>
          <div>
            <div style="font-size:14px;font-style:italic;font-weight:500">${o.titulo}</div>
            <div style="font-size:10px;font-weight:500;text-transform:uppercase;letter-spacing:.06em;color:var(--ink-mid);margin-top:2px">${o.artista}</div>
            <div style="font-size:9px;color:var(--ink-light)">${o.registro||''}</div>
          </div>
          <div style="font-size:15px;font-weight:700;white-space:nowrap">${fmt(o.precio)}</div>
          <button class="btn" style="padding:4px 8px;font-size:18px;border:none;color:var(--ink-light)" data-quitar="${o.id}">×</button>
        </div>`;
      }).join('')}
      <div class="cart-total">
        <span style="font-size:12px;font-weight:600;letter-spacing:.1em;text-transform:uppercase">Subtotal</span>
        <span style="font-size:22px;font-weight:700">${fmt(sub)}</span>
      </div>
    </div>
    <button class="btn btn-checkout" id="btn-ir-checkout">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M5 12h14"/><path d="M12 5l7 7-7 7"/></svg>
      Proceder al checkout
    </button>`;

  document.getElementById('btn-limpiar-carrito').addEventListener('click', () => { carrito=[]; renderStats(); renderCarrito(); });
  document.getElementById('btn-ir-checkout').addEventListener('click', () => { pasoCarrito=2; renderCarrito(); });
  panel.querySelectorAll('[data-quitar]').forEach(btn => {
    btn.addEventListener('click', () => { toggleCarrito(parseInt(btn.dataset.quitar)); });
  });
}

function renderPaso2(panel, obrasC) {
  const sub = obrasC.reduce((a,o)=>a+(Number(o.precio)||0),0);
  panel.innerHTML = pasoHTML(2) + `
    <div class="checkout-sec">
      <div class="checkout-sec-hdr"><span>Datos del cliente</span></div>
      <div class="checkout-body">
        <div class="form-grid">
          <div class="form-full"><label class="f-label">Nombre completo</label><input class="f-inp" id="ch-nombre" placeholder="Nombre del comprador"></div>
          <div><label class="f-label">Teléfono</label><input class="f-inp" type="tel" id="ch-telefono" placeholder="+52 686 000 0000"></div>
          <div><label class="f-label">Correo electrónico</label><input class="f-inp" type="email" id="ch-email" placeholder="correo@ejemplo.com"></div>
        </div>
      </div>
    </div>
    <div class="checkout-sec">
      <div class="checkout-sec-hdr"><span>Descuento (opcional)</span></div>
      <div class="checkout-body">
        <div class="form-grid">
          <div><label class="f-label">Tipo</label>
            <select class="f-sel" id="ch-desc-tipo">
              <option value="ninguno">Sin descuento</option>
              <option value="pct">Porcentaje (%)</option>
              <option value="fijo">Monto fijo (MXN)</option>
            </select>
          </div>
          <div><label class="f-label" id="ch-desc-label">Valor</label>
            <input class="f-inp" type="number" id="ch-desc-val" min="0" placeholder="0" disabled style="opacity:.45">
          </div>
        </div>
      </div>
    </div>
    <div class="checkout-sec">
      <div class="checkout-sec-hdr"><span>Resumen — ${obrasC.length} obra${obrasC.length!==1?'s':''}</span></div>
      ${obrasC.map(o=>`<div class="res-row"><div><span style="font-size:13px;font-style:italic;font-weight:500">${o.titulo}</span> <span style="font-size:10px;color:var(--ink-light)">${o.artista}</span></div><span style="font-size:14px;font-weight:600">${fmt(o.precio)}</span></div>`).join('')}
      <div class="res-row res-sub"><span>Subtotal</span><span>${fmt(sub)}</span></div>
      <div class="res-row res-desc" id="res-desc-row" style="display:none"></div>
      <div class="res-total"><span>Total</span><span id="res-total-val">${fmt(sub)}</span></div>
    </div>
    <div class="btns-accion">
      <button class="btn btn-primary btn-lg" id="btn-generar-pdf">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8z"/><polyline points="14 2 14 8 20 8"/></svg>
        Descargar PDF
      </button>
      <button class="btn btn-outline btn-lg" id="btn-enviar-correo">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
        Enviar por correo
      </button>
    </div>
    <button class="btn btn-back" id="btn-volver-paso1">
      <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M19 12H5"/><path d="M12 5l-7 7 7 7"/></svg>
      Volver a la selección
    </button>`;

  // Listeners
  document.getElementById('btn-volver-paso1').addEventListener('click', () => { pasoCarrito=1; renderCarrito(); });

  const descTipo = document.getElementById('ch-desc-tipo');
  const descVal  = document.getElementById('ch-desc-val');
  const descLbl  = document.getElementById('ch-desc-label');
  function calcDesc() {
    const t=descTipo.value, v=parseFloat(descVal.value)||0;
    const monto = t==='pct'?Math.min(sub,sub*v/100):t==='fijo'?Math.min(sub,v):0;
    const total = sub-monto;
    document.getElementById('res-total-val').textContent = fmt(total);
    const dr = document.getElementById('res-desc-row');
    if (monto>0) { dr.style.display='flex'; dr.innerHTML=`<span>Descuento${t==='pct'?' ('+v+'%)':''}</span><span>−${fmt(monto)}</span>`; }
    else dr.style.display='none';
    return { monto, total };
  }
  descTipo.addEventListener('change', () => {
    const none=descTipo.value==='ninguno';
    descVal.disabled=none; descVal.style.opacity=none?'.45':'1'; if(none)descVal.value='';
    descLbl.textContent=descTipo.value==='pct'?'Porcentaje (%)':descTipo.value==='fijo'?'Monto (MXN)':'Valor';
    calcDesc();
  });
  descVal.addEventListener('input', calcDesc);

  document.getElementById('btn-generar-pdf').addEventListener('click', () => {
    const { monto, total } = calcDesc();
    generarPDF(obrasC, sub, monto, total, descTipo.value, parseFloat(descVal.value)||0);
  });
  document.getElementById('btn-enviar-correo').addEventListener('click', () => {
    const { monto, total } = calcDesc();
    enviarCorreo(obrasC, sub, monto, total, descTipo.value, parseFloat(descVal.value)||0);
  });
}

/* ── GENERAR PDF ── */
function generarPDF(obrasC, sub, descMonto, total, descTipo, descVal) {
  if (!window.jspdf) { toast('Cargando PDF, intenta de nuevo...'); return; }
  const nombre = document.getElementById('ch-nombre')?.value||'';
  const tel    = document.getElementById('ch-telefono')?.value||'';
  const email  = document.getElementById('ch-email')?.value||'';
  const folio  = folioNuevo();
  const fecha  = fechaHoy();
  const { jsPDF } = window.jspdf;
  const doc = new jsPDF({ unit:'mm', format:'a4' });
  const W=210, L=20, R=190;
  const negro=[20,18,16], gris=[90,86,80], claro=[154,149,144], gris1=[245,244,241], rojo=[192,57,43];

  // Cabecera
  doc.setFillColor(...negro); doc.rect(0,0,W,36,'F');
  doc.setTextColor(255,255,255);
  doc.setFont('helvetica','bold'); doc.setFontSize(14);
  doc.text(GALERIA.nombre.toUpperCase(), W/2, 13, {align:'center'});
  doc.setFont('helvetica','normal'); doc.setFontSize(8.5);
  doc.text(GALERIA.direccion, W/2, 20, {align:'center'});
  doc.text(GALERIA.email, W/2, 26, {align:'center'});

  // Título
  doc.setTextColor(...negro);
  doc.setFont('helvetica','bold'); doc.setFontSize(18);
  doc.text('RECIBO DE VENTA', L, 48);
  doc.setFont('helvetica','normal'); doc.setFontSize(9); doc.setTextColor(...claro);
  doc.text('Folio '+folio, L, 55);
  doc.setTextColor(...gris); doc.text(fecha, R, 55, {align:'right'});

  // Cliente
  let y=66;
  doc.setFillColor(...gris1); doc.roundedRect(L, y-4, 170, 26, 2,2,'F');
  doc.setFont('helvetica','bold'); doc.setFontSize(8); doc.setTextColor(...claro); doc.setCharSpace(.8);
  doc.text('DATOS DEL CLIENTE', L+4, y+2);
  doc.setCharSpace(0); doc.setFont('helvetica','normal'); doc.setFontSize(10); doc.setTextColor(...negro);
  const cW=56;
  [['Nombre',nombre||'—'],['Teléfono',tel||'—'],['Correo',email||'—']].forEach(([lbl,val],i)=>{
    const x=L+4+i*cW;
    doc.setFont('helvetica','bold'); doc.setFontSize(7.5); doc.setTextColor(...claro);
    doc.text(lbl.toUpperCase(), x, y+10);
    doc.setFont('helvetica','normal'); doc.setFontSize(10); doc.setTextColor(...negro);
    doc.text(String(val), x, y+17);
  });

  // Obras
  y=102;
  doc.setFont('helvetica','bold'); doc.setFontSize(8); doc.setTextColor(...claro); doc.setCharSpace(.8);
  doc.text('OBRAS ADQUIRIDAS', L, y);
  doc.setCharSpace(0); y+=5;
  doc.setFillColor(...gris1); doc.rect(L,y,170,8,'F');
  doc.setFont('helvetica','bold'); doc.setFontSize(8); doc.setTextColor(...claro);
  doc.text('OBRA / ARTISTA', L+3, y+5.5);
  doc.text('REGISTRO', L+100, y+5.5);
  doc.text('AÑO', L+128, y+5.5);
  doc.text('PRECIO', R-3, y+5.5, {align:'right'});
  y+=8;
  obrasC.forEach((o,i)=>{
    if(i%2===1){doc.setFillColor(250,249,247);doc.rect(L,y,170,14,'F');}
    doc.setFont('helvetica','bolditalic'); doc.setFontSize(10); doc.setTextColor(...negro);
    doc.text(o.titulo.length>42?o.titulo.slice(0,41)+'…':o.titulo, L+3, y+6);
    doc.setFont('helvetica','normal'); doc.setFontSize(8.5); doc.setTextColor(...gris);
    doc.text(o.artista, L+3, y+11.5);
    doc.text(o.registro||'—', L+100, y+8);
    doc.text(o.anio||'—', L+128, y+8);
    doc.setFont('helvetica','bold'); doc.setFontSize(10); doc.setTextColor(...negro);
    doc.text(fmt(o.precio), R-3, y+8, {align:'right'});
    y+=14;
  });
  doc.setLineWidth(.5); doc.setDrawColor(...negro); doc.line(L,y,R,y); y+=2;

  // Totales
  doc.setFont('helvetica','normal'); doc.setFontSize(10.5); doc.setTextColor(...gris);
  doc.text('Subtotal', L+3, y+6); doc.text(fmt(sub), R-3, y+6, {align:'right'}); y+=9;
  if(descMonto>0){
    doc.setTextColor(...rojo);
    doc.text('Descuento'+(descTipo==='pct'?' ('+descVal+'%)':''), L+3, y+6);
    doc.text('−'+fmt(descMonto), R-3, y+6, {align:'right'}); y+=9;
  }
  y+=2;
  doc.setFillColor(...negro); doc.rect(L,y-2,170,14,'F');
  doc.setFont('helvetica','bold'); doc.setFontSize(13); doc.setTextColor(255,255,255);
  doc.text('TOTAL', L+4, y+8); doc.text(fmt(total), R-4, y+8, {align:'right'});
  y+=20;

  // Pie
  doc.setFont('helvetica','normal'); doc.setFontSize(8.5); doc.setTextColor(...claro);
  doc.setLineWidth(.3); doc.setDrawColor(...claro); doc.line(L,y,R,y); y+=6;
  doc.text('Las obras incluyen certificado de autenticidad. Para más información: '+GALERIA.email, W/2, y, {align:'center'});

  doc.save('recibo-'+folio+'.pdf');
  toast('PDF descargado');
}

/* ── ENVIAR CORREO ── */
function enviarCorreo(obrasC, sub, descMonto, total, descTipo, descVal) {
  const email = document.getElementById('ch-email')?.value||'';
  if (!email) { toast('Ingresa el correo del cliente'); return; }
  const nombre = document.getElementById('ch-nombre')?.value||'—';
  const tel    = document.getElementById('ch-telefono')?.value||'—';
  const lineas = obrasC.map(o=>`  • ${o.titulo} — ${o.artista} (${o.registro||'—'}) ... ${fmt(o.precio)}`).join('\n');
  const body = `${GALERIA.nombre}\n${GALERIA.direccion}\n${GALERIA.email}\n\nRECIBO DE VENTA — ${fechaHoy()}\n\nCLIENTE\nNombre: ${nombre}\nTeléfono: ${tel}\n\nOBRAS\n${lineas}\n\nSubtotal: ${fmt(sub)}${descMonto>0?'\nDescuento'+(descTipo==='pct'?' ('+descVal+'%)':'')+ ': −'+fmt(descMonto):''}\nTOTAL: ${fmt(total)}\n\nLas obras incluyen certificado de autenticidad.\nGracias por su adquisición.`;
  window.location.href=`mailto:${email}?subject=${encodeURIComponent('Recibo de venta — '+GALERIA.nombre)}&body=${encodeURIComponent(body)}`;
  toast('Abriendo correo...');
}

/* ── DETALLE ── */
function verDetalle(id) {
  const o = obras.find(x=>x.id===id); if (!o) return;
  obraDetalle = o;
  const fotos = getFotos(o), src = fotos[0]||'';
  const box = document.getElementById('modal-detalle-box');
  box.innerHTML = `
    <div class="modal-hdr">
      <div><div class="modal-handle"></div><span class="modal-title">Ficha de obra</span></div>
      <button class="modal-close" id="btn-cerrar-detalle">×</button>
    </div>
    <div style="display:grid;grid-template-columns:1fr 1fr">
      <div class="detail-img-area">
        <div class="detail-img-main">
          ${src
            ? `<img id="det-main" src="${src}" style="width:100%;height:100%;object-fit:cover">`
            : `<div style="display:flex;flex-direction:column;align-items:center;gap:8px;color:var(--ink-light)"><svg width="30" height="30" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1" style="opacity:.3"><rect x="3" y="3" width="18" height="18" rx="1"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21,15 16,10 5,21"/></svg><span style="font-size:10px;letter-spacing:.1em;text-transform:uppercase">Sin imagen</span></div>`}
        </div>
        ${fotos.length>1?`<div class="detail-thumbs">${fotos.map((s,i)=>`<img class="detail-thumb" src="${s}" data-src="${s}" style="outline:${i===0?'2px solid var(--ink)':'0.5px solid var(--rule)'}">`).join('')}</div>`:''}
      </div>
      <div class="detail-info">
        <div>
          <div style="font-size:10px;color:var(--ink-light);letter-spacing:.1em;text-transform:uppercase;margin-bottom:6px">${o.registro||'—'} · ${o.tipo}</div>
          <div style="font-size:22px;font-style:italic;font-weight:500;line-height:1.2;margin-bottom:4px">${o.titulo}</div>
          <div style="font-size:11px;font-weight:500;letter-spacing:.1em;text-transform:uppercase;color:var(--ink-mid);margin-bottom:16px">${o.artista} · ${o.anio||'—'}</div>
          <table class="ficha">
            ${[['Técnica',o.tecnica],['Dimensiones',o.dimensiones],['Edición',o.edicion],['Ubicación',o.ubicacion],['Certificado','Incluido']].map(([k,v])=>`<tr><td>${k}</td><td>${v||'—'}</td></tr>`).join('')}
          </table>
        </div>
        <div class="precio-bloque">
          <div style="font-size:9px;letter-spacing:.15em;text-transform:uppercase;color:var(--ink-light);margin-bottom:4px">Precio de venta</div>
          <div style="font-size:28px;font-weight:600;${o.estado==='Vendida'?'text-decoration:line-through;color:var(--ink-light)':''}">${fmt(o.precio)}</div>
          <span class="pill ${pillCls(o.estado)}" style="margin-top:8px">${o.estado}</span>
        </div>
      </div>
    </div>
    ${o.nota?`<div style="padding:14px 18px;border-top:.5px solid var(--rule);font-size:13px;font-style:italic;color:var(--ink-mid);line-height:1.7">${o.nota}</div>`:''}
    <div class="detail-ftr">
      <div style="display:flex;gap:8px;flex-wrap:wrap">
        <button class="btn" id="btn-editar-obra">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M11 4H4a2 2 0 00-2 2v14a2 2 0 002 2h14a2 2 0 002-2v-7"/><path d="M18.5 2.5a2.1 2.1 0 013 3L12 15l-4 1 1-4 9.5-9.5z"/></svg>Editar
        </button>
        <button class="btn btn-danger" id="btn-borrar-obra">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="3 6 5 6 21 6"/><path d="M19 6l-1 14a2 2 0 01-2 2H8a2 2 0 01-2-2L5 6"/></svg>Eliminar
        </button>
        <button class="btn btn-primary" id="btn-certificado-obra" style="gap:6px">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="8" r="6"/><path d="M15.477 12.89L17 22l-5-3-5 3 1.523-9.11"/></svg>Certificado
        </button>
      </div>
      <span style="font-size:11px;font-weight:500;letter-spacing:.15em;text-transform:uppercase;color:var(--ink-light)">Planta Libre</span>
    </div>`;

  // Listeners del detalle — asignados directamente a elementos reales, no strings
  document.getElementById('btn-cerrar-detalle').addEventListener('click', cerrarDetalle);
  document.getElementById('btn-editar-obra').addEventListener('click', () => { cerrarDetalle(); abrirFormulario(id); });
  document.getElementById('btn-borrar-obra').addEventListener('click', () => abrirConfirmar(id));
  document.getElementById('btn-certificado-obra').addEventListener('click', () => emitirCertificado(id));

  // Thumbnails
  box.querySelectorAll('.detail-thumb').forEach(thumb => {
    thumb.addEventListener('click', () => {
      const main = document.getElementById('det-main');
      if (main) main.src = thumb.dataset.src;
      box.querySelectorAll('.detail-thumb').forEach(t => t.style.outline = '0.5px solid var(--rule)');
      thumb.style.outline = '2px solid var(--ink)';
    });
  });

  document.getElementById('modal-detalle').classList.add('open');
}
function cerrarDetalle() { document.getElementById('modal-detalle').classList.remove('open'); obraDetalle=null; }

/* ── FORMULARIO ── */
function abrirFormulario(id) {
  editandoId = id||null;
  const o = id ? obras.find(x=>x.id===id) : null;
  document.getElementById('form-titulo').textContent = id ? 'Editar obra' : 'Nueva obra';
  ['titulo','artista','tecnica','dimensiones','anio','edicion','ubicacion','precio','registro','nota'].forEach(k => {
    document.getElementById('f-'+k).value = o ? (o[k]||'') : '';
  });
  document.getElementById('f-tipo').value   = o ? o.tipo   : 'Pintura';
  document.getElementById('f-estado').value = o ? o.estado : 'Disponible';
  if (!id) document.getElementById('f-registro').value = 'PL-'+String(nextId).padStart(3,'0');
  try {
    const img = o?.imagen||'[]';
    fotosActuales = Array.isArray(JSON.parse(img)) ? JSON.parse(img) : (img.startsWith('data:') ? [img] : []);
  } catch { fotosActuales = o?.imagen ? [o.imagen] : []; }
  renderFotosGrid();
  document.getElementById('modal-form').classList.add('open');
}
function cerrarFormulario() { document.getElementById('modal-form').classList.remove('open'); }

function guardarObra() {
  const campos=['titulo','artista','tipo','tecnica','dimensiones','anio','edicion','ubicacion','precio','estado','imagen','registro','nota'];
  const datos = {};
  campos.forEach(k => datos[k] = document.getElementById('f-'+k).value);
  datos.titulo  = datos.titulo  || 'Sin título';
  datos.artista = datos.artista || '—';
  if (editandoId) {
    const i = obras.findIndex(o=>o.id===editandoId);
    obras[i] = {...obras[i], ...datos};
    toast('Obra actualizada');
  } else {
    obras.push({id:nextId++, ...datos});
    toast('Obra agregada');
  }
  guardar(); cerrarFormulario(); cerrarDetalle(); renderStats(); renderTab();
}

/* ── FOTOS ── */
function renderFotosGrid() {
  const grid = document.getElementById('fotos-grid');
  const drop  = document.getElementById('drop-zone');
  const MAX = 5, lleno = fotosActuales.length >= MAX;
  grid.innerHTML = fotosActuales.map((src,i) => `
    <div class="foto-thumb">
      <img src="${src}">
      ${i===0?'<span class="foto-principal">Principal</span>':''}
      <button class="foto-quitar" data-idx="${i}">×</button>
    </div>`).join('');
  grid.querySelectorAll('.foto-quitar').forEach(btn => {
    btn.addEventListener('click', () => { fotosActuales.splice(parseInt(btn.dataset.idx),1); renderFotosGrid(); });
  });
  document.querySelectorAll('.upload-btn').forEach(b => b.style.display = lleno ? 'none' : 'flex');
  if (drop) drop.style.display = lleno ? 'none' : 'flex';
  const lbl = document.getElementById('drop-label');
  if (lbl) lbl.textContent = 'Arrastra aquí ('+( MAX-fotosActuales.length)+' más)';
  document.getElementById('f-imagen').value = JSON.stringify(fotosActuales);
}

async function cargarFotos(files) {
  const MAX=5, esp=MAX-fotosActuales.length;
  if(esp<=0){toast('Máximo 5 fotografías');return;}
  const lote=Array.from(files).filter(f=>f.type.startsWith('image/')).slice(0,esp);
  if(files.length>esp) toast('Solo se agregaron '+esp+' foto'+(esp>1?'s':''));
  for(const f of lote){
    await new Promise(r=>{
      const rd=new FileReader();
      rd.onload=async ev=>{
        const img=new Image();
        img.onload=()=>{
          let w=img.width,h=img.height;
          if(w>1200){h=Math.round(h*1200/w);w=1200;}
          if(h>1200){w=Math.round(w*1200/h);h=1200;}
          const c=document.createElement('canvas');c.width=w;c.height=h;
          c.getContext('2d').drawImage(img,0,0,w,h);
          fotosActuales.push(c.toDataURL('image/jpeg',.75));r();
        };
        img.onerror=()=>{fotosActuales.push(ev.target.result);r();};
        img.src=ev.target.result;
      };
      rd.readAsDataURL(f);
    });
  }
  renderFotosGrid();
}

/* ── CONFIRMAR BORRAR ── */
function abrirConfirmar(id) { obraABorrar=id; document.getElementById('modal-confirmar').classList.add('open'); }
function cerrarConfirmar() { obraABorrar=null; document.getElementById('modal-confirmar').classList.remove('open'); }
function confirmarBorrar() {
  obras=obras.filter(o=>o.id!==obraABorrar); obraABorrar=null;
  guardar(); cerrarConfirmar(); cerrarDetalle(); renderStats(); renderTab(); toast('Obra eliminada');
}

/* ── CERTIFICADO ── */
function emitirCertificado(id) {
  const o = obras.find(x=>x.id===id); if(!o) return;
  const fotos=getFotos(o), imgSrc=fotos[0]||'';
  const fecha=fechaHoy();
  const folio='CERT-'+(o.registro||id)+'-'+new Date().getFullYear();

  const doc = document.getElementById('cert-doc');
  doc.style.cssText = 'font-family:DM Sans,sans-serif;color:#141210;display:flex;flex-direction:column;background:#fff;width:210mm;min-height:297mm';

  doc.innerHTML = `
    <!-- Cabecera negra -->
    <div style="background:#141210;color:#fff;padding:24px 32px 20px;display:flex;justify-content:space-between;align-items:flex-end">
      <div>
        <div style="font-size:15px;font-weight:700;letter-spacing:.22em;text-transform:uppercase;margin-bottom:4px">Planta Libre Espacio Experimental</div>
        <div style="font-size:9px;color:#9a9590;line-height:1.7">Zuazua 457 Zona Centro · Mexicali, Baja California, México · C.P. 21100<br>plantalibre.mxl@gmail.com</div>
      </div>
      <div style="text-align:right;font-size:9px;color:#9a9590;line-height:1.7">
        <div style="font-size:8px;letter-spacing:.15em;text-transform:uppercase;margin-bottom:2px">Folio</div>
        <div style="font-size:11px;font-weight:600;color:#fff">${folio}</div>
        <div>${fecha}</div>
      </div>
    </div>
    <!-- Título -->
    <div style="padding:20px 32px 12px;border-bottom:1px solid #141210;display:flex;justify-content:space-between;align-items:flex-end">
      <h1 style="font-size:24px;font-weight:700;letter-spacing:.14em;text-transform:uppercase">Certificado de Autenticidad</h1>
      <span style="font-size:10px;color:#9a9590">Documento oficial de la galería</span>
    </div>
    <!-- Cuerpo -->
    <div style="padding:24px 32px;flex:1">
      <!-- Imagen + ficha -->
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:24px;margin-bottom:24px">
        <div>
          <div style="aspect-ratio:4/3;background:#eeece8;overflow:hidden;display:flex;align-items:center;justify-content:center;border:.5px solid #dedad4">
            ${imgSrc
              ? `<img src="${imgSrc}" style="width:100%;height:100%;object-fit:cover;display:block">`
              : `<div style="display:flex;flex-direction:column;align-items:center;gap:8px;color:#9a9590"><svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1" style="opacity:.3"><rect x="3" y="3" width="18" height="18" rx="1"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21,15 16,10 5,21"/></svg><span style="font-size:9px;letter-spacing:.1em;text-transform:uppercase">Sin imagen</span></div>`}
          </div>
          ${fotos.length>1?`<div style="display:flex;gap:4px;margin-top:6px;flex-wrap:wrap">${fotos.slice(1,4).map(s=>`<img src="${s}" style="width:58px;height:58px;object-fit:cover;border:.5px solid #dedad4;border-radius:4px">`).join('')}</div>`:''}
        </div>
        <div>
          <div style="font-size:20px;font-style:italic;font-weight:500;line-height:1.2;margin-bottom:4px">${o.titulo}</div>
          <div style="font-size:11px;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:#5a5650;margin-bottom:16px">${o.artista}</div>
          <table style="width:100%;border-collapse:collapse">
            ${[['Registro',o.registro||'—'],['Disciplina',o.tipo||'—'],['Técnica',o.tecnica||'—'],['Dimensiones',o.dimensiones||'—'],['Año',o.anio||'—'],['Edición',o.edicion||'—'],o.nota?['Nota curatorial',o.nota]:null].filter(Boolean).map(([k,v])=>`<tr style="border-bottom:.5px solid #dedad4"><td style="padding:6px 0;font-size:9px;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:#9a9590;width:40%;vertical-align:top">${k}</td><td style="padding:6px 0;font-size:11px;line-height:1.5;vertical-align:top${k==='Nota curatorial'?';font-style:italic;color:#5a5650':''}">${v}</td></tr>`).join('')}
          </table>
        </div>
      </div>
      <!-- Declaración -->
      <div style="background:#f5f4f1;border-left:3px solid #141210;padding:14px 18px;margin-bottom:24px;font-size:11px;line-height:1.75;color:#5a5650">
        <strong style="color:#141210">Planta Libre Espacio Experimental</strong> certifica que la obra titulada
        <strong style="color:#141210">"${o.titulo}"</strong>, de autoría de <strong style="color:#141210">${o.artista}</strong>,
        es una pieza original${o.edicion?' ('+o.edicion+')':''} creada en ${o.anio||'fecha registrada'}.
        Este documento acredita su autenticidad y procedencia a través de la galería.
        La presente certificación es intransferible y acompaña permanentemente a la obra.
      </div>
      <!-- Sello -->
      <div style="width:72px;height:72px;border-radius:50%;border:2px solid #141210;display:flex;flex-direction:column;align-items:center;justify-content:center;margin:0 auto 20px;gap:2px">
        <span style="font-size:6px;font-weight:700;letter-spacing:.2em;text-transform:uppercase">Planta</span>
        <span style="font-size:16px">✦</span>
        <span style="font-size:5.5px;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:#5a5650">Libre</span>
      </div>
      <!-- Firmas -->
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:32px;margin-bottom:20px">
        <div style="display:flex;flex-direction:column;align-items:center">
          <div style="width:100%;border-bottom:1px solid #141210;margin-bottom:8px;height:52px"></div>
          <div style="font-size:10px;font-weight:600;letter-spacing:.08em;text-transform:uppercase;text-align:center">${o.artista}</div>
          <div style="font-size:9px;color:#9a9590;text-align:center;margin-top:2px">Artista · Autor/a de la obra</div>
        </div>
        <div style="display:flex;flex-direction:column;align-items:center">
          <div style="width:100%;border-bottom:1px solid #141210;margin-bottom:8px;height:52px"></div>
          <div style="font-size:10px;font-weight:600;letter-spacing:.08em;text-transform:uppercase;text-align:center">Minoru Kiyota García</div>
          <div style="font-size:9px;color:#9a9590;text-align:center;margin-top:2px">Director · Planta Libre Espacio Experimental</div>
        </div>
      </div>
    </div>
    <!-- Pie -->
    <div style="border-top:.5px solid #dedad4;padding:12px 32px;display:flex;justify-content:space-between;align-items:center;background:#f5f4f1">
      <div style="font-size:9px;font-weight:600;letter-spacing:.18em;text-transform:uppercase;color:#141210">Planta Libre ✦ Espacio Experimental</div>
      <div style="font-size:9px;color:#9a9590;text-align:right;line-height:1.7">Zuazua 457 Zona Centro · Mexicali, B.C., México<br>plantalibre.mxl@gmail.com · ${fecha}</div>
    </div>`;

  document.getElementById('cert-overlay').classList.add('open');
  toast('Certificado listo · toca "Imprimir" para guardar como PDF');
}

/* ── EMPTY STATE ── */
function emptyHTML(msg) {
  return `<div class="empty" style="grid-column:1/-1"><svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1"><rect x="3" y="3" width="18" height="18" rx="1"/><line x1="3" y1="3" x2="21" y2="21"/></svg><p>${msg}</p></div>`;
}

/* ════════════════════════════════════════════════════════
   LISTENERS — todos asignados aquí, una sola vez, sin
   onclick en HTML ni en innerHTML
════════════════════════════════════════════════════════ */
document.getElementById('btn-agregar-header').addEventListener('click', () => abrirFormulario());
document.getElementById('fab-agregar').addEventListener('click', () => abrirFormulario());
document.getElementById('btn-cerrar-form').addEventListener('click', cerrarFormulario);
document.getElementById('btn-cancelar-form').addEventListener('click', cerrarFormulario);
document.getElementById('btn-guardar-obra').addEventListener('click', guardarObra);
document.getElementById('btn-cancelar-borrar').addEventListener('click', cerrarConfirmar);
document.getElementById('btn-confirmar-borrar').addEventListener('click', confirmarBorrar);
document.getElementById('btn-exportar').addEventListener('click', exportarJSON);
document.getElementById('inp-importar').addEventListener('change', importarJSON);
document.getElementById('btn-cert-print').addEventListener('click', () => window.print());
document.getElementById('btn-cert-cerrar').addEventListener('click', () => document.getElementById('cert-overlay').classList.remove('open'));
document.getElementById('buscador').addEventListener('input', renderTab);

// Tabs
document.getElementById('tabs-nav').addEventListener('click', e => {
  const btn = e.target.closest('[data-tab]'); if (!btn) return; setTab(btn.dataset.tab);
});

// Chips de filtro
document.getElementById('filtros-bar').addEventListener('click', e => {
  const chip = e.target.closest('[data-filtro]'); if (!chip) return;
  filtroActivo = chip.dataset.filtro;
  document.querySelectorAll('[data-filtro]').forEach(c => c.classList.toggle('activo', c===chip));
  renderTab();
});

// Cerrar modales al hacer clic en el fondo
document.getElementById('modal-form').addEventListener('click', e => { if(e.target===e.currentTarget) cerrarFormulario(); });
document.getElementById('modal-detalle').addEventListener('click', e => { if(e.target===e.currentTarget) cerrarDetalle(); });
document.getElementById('modal-confirmar').addEventListener('click', e => { if(e.target===e.currentTarget) cerrarConfirmar(); });

// Fotos
document.getElementById('inp-fotos').addEventListener('change', e => { cargarFotos(e.target.files); e.target.value=''; });
document.getElementById('inp-camara').addEventListener('change', e => { cargarFotos(e.target.files); e.target.value=''; });
document.getElementById('drop-zone').addEventListener('click', () => document.getElementById('inp-fotos').click());
document.getElementById('drop-zone').addEventListener('dragover', e => { e.preventDefault(); e.currentTarget.style.borderColor='var(--ink)'; });
document.getElementById('drop-zone').addEventListener('dragleave', e => { e.currentTarget.style.borderColor='var(--rule-dark)'; });
document.getElementById('drop-zone').addEventListener('drop', e => {
  e.preventDefault(); e.currentTarget.style.borderColor='var(--rule-dark)';
  cargarFotos(e.dataTransfer.files);
});

/* ── INIT ── */
async function init() {
  await cargar();
  renderStats();
  renderTab();
}
init();
</script>
</body>
</html>
