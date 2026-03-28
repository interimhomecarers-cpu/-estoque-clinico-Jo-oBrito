# -estoque-clinico-Jo-oBrito[index.html.html](https://github.com/user-attachments/files/26326778/index.html.html)
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Controle de Estoque Clínico</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;1,9..40,300&family=DM+Mono:wght@400;500&display=swap');

:root {
  --bg:        #f4f5f7;
  --surface:   #ffffff;
  --surface2:  #f8f9fb;
  --border:    #e4e7ed;
  --border2:   #d1d5df;
  --text:      #1a1d26;
  --text2:     #6b7385;
  --text3:     #a8afc4;
  --green:     #1a9e6e;
  --green-bg:  #edf7f3;
  --green-mid: #b6e8d5;
  --amber:     #d4860a;
  --amber-bg:  #fef6e7;
  --amber-mid: #fad79c;
  --red:       #c83535;
  --red-bg:    #fdf0f0;
  --red-mid:   #f5bcbc;
  --blue:      #2563c4;
  --blue-bg:   #eef3fd;
  --blue-mid:  #b8ccf6;
  --purple:    #7c3fbf;
  --purple-bg: #f3eeff;
  --sans: 'DM Sans', sans-serif;
  --mono: 'DM Mono', monospace;
  --r: 10px;
  --r-sm: 6px;
  --shadow: 0 1px 3px rgba(0,0,0,0.06), 0 1px 2px rgba(0,0,0,0.04);
  --shadow-md: 0 4px 16px rgba(0,0,0,0.10);
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: var(--sans);
  background: var(--bg);
  color: var(--text);
  font-size: 14px;
  line-height: 1.5;
  min-height: 100vh;
}

/* ── LAYOUT ── */
.shell { display: flex; min-height: 100vh; }

.rail {
  width: 230px;
  background: var(--surface);
  border-right: 1px solid var(--border);
  display: flex;
  flex-direction: column;
  position: fixed;
  height: 100vh;
  overflow-y: auto;
  z-index: 200;
}

.rail-brand {
  padding: 22px 20px 16px;
  border-bottom: 1px solid var(--border);
}

.brand-mark {
  display: flex;
  align-items: center;
  gap: 10px;
}

.brand-icon {
  width: 34px; height: 34px;
  background: var(--green);
  border-radius: 8px;
  display: flex; align-items: center; justify-content: center;
  font-size: 16px;
  flex-shrink: 0;
}

.brand-name {
  font-size: 13px;
  font-weight: 600;
  color: var(--text);
  line-height: 1.2;
}

.brand-sub {
  font-size: 11px;
  color: var(--text3);
  margin-top: 1px;
}

.rail-nav { padding: 10px 10px; flex: 1; }

.nav-section-label {
  font-size: 10px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--text3);
  padding: 12px 10px 6px;
}

.nav-btn {
  display: flex;
  align-items: center;
  gap: 10px;
  width: 100%;
  padding: 9px 10px;
  border: none;
  background: none;
  cursor: pointer;
  border-radius: var(--r-sm);
  font-family: var(--sans);
  font-size: 13.5px;
  color: var(--text2);
  text-align: left;
  transition: all 0.12s;
  position: relative;
}

.nav-btn:hover { background: var(--surface2); color: var(--text); }

.nav-btn.active {
  background: var(--green-bg);
  color: var(--green);
  font-weight: 500;
}

.nav-btn .ni { font-size: 15px; width: 20px; text-align: center; flex-shrink: 0; }

.nav-badge {
  margin-left: auto;
  background: var(--red);
  color: white;
  font-size: 10px;
  font-weight: 600;
  padding: 1px 6px;
  border-radius: 20px;
  font-family: var(--mono);
}

.rail-footer {
  padding: 14px 20px;
  border-top: 1px solid var(--border);
  font-size: 11px;
  color: var(--text3);
}

.rail-footer .week-label {
  font-weight: 500;
  color: var(--text2);
  margin-bottom: 2px;
}

/* ── MAIN ── */
.main-wrap { margin-left: 230px; flex: 1; display: flex; flex-direction: column; }

.topbar {
  background: var(--surface);
  border-bottom: 1px solid var(--border);
  padding: 0 28px;
  height: 58px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  position: sticky;
  top: 0;
  z-index: 100;
  gap: 16px;
}

.topbar-left { display: flex; align-items: center; gap: 14px; min-width: 0; }
.topbar-title { font-size: 16px; font-weight: 600; white-space: nowrap; }
.topbar-pill {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 3px 10px;
  background: var(--blue-bg);
  color: var(--blue);
  border-radius: 20px;
  font-size: 11px;
  font-weight: 500;
  font-family: var(--mono);
  white-space: nowrap;
}

.topbar-actions { display: flex; align-items: center; gap: 8px; flex-shrink: 0; }

/* ── BUTTONS ── */
.btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 8px 16px;
  border-radius: var(--r-sm);
  font-family: var(--sans);
  font-size: 13px;
  font-weight: 500;
  cursor: pointer;
  border: 1px solid transparent;
  transition: all 0.12s;
  white-space: nowrap;
}

.btn-green  { background: var(--green);  color: #fff; border-color: var(--green); }
.btn-green:hover  { filter: brightness(1.08); }
.btn-ghost  { background: transparent; color: var(--text2); border-color: var(--border2); }
.btn-ghost:hover  { border-color: var(--text2); color: var(--text); background: var(--surface2); }
.btn-amber  { background: var(--amber);  color: #fff; border-color: var(--amber); }
.btn-amber:hover  { filter: brightness(1.08); }
.btn-red    { background: transparent; color: var(--red); border-color: var(--red-mid); }
.btn-red:hover    { background: var(--red-bg); }
.btn-sm     { padding: 6px 12px; font-size: 12px; }
.btn-xs     { padding: 4px 9px; font-size: 11px; }

/* ── CONTENT ── */
.page { padding: 24px 28px; display: none; }
.page.active { display: block; }

/* ── STATS ROW ── */
.stats-row {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
  gap: 12px;
  margin-bottom: 20px;
}

.stat {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--r);
  padding: 14px 16px;
  box-shadow: var(--shadow);
}

.stat-label {
  font-size: 11px;
  color: var(--text3);
  text-transform: uppercase;
  letter-spacing: 0.08em;
  font-weight: 500;
  margin-bottom: 6px;
}

.stat-val {
  font-family: var(--mono);
  font-size: 26px;
  font-weight: 500;
  line-height: 1;
}

.stat-val.green  { color: var(--green); }
.stat-val.amber  { color: var(--amber); }
.stat-val.red    { color: var(--red); }
.stat-val.blue   { color: var(--blue); }

/* ── CARD ── */
.card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--r);
  box-shadow: var(--shadow);
}

.card-head {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 14px 18px;
  border-bottom: 1px solid var(--border);
  gap: 12px;
  flex-wrap: wrap;
}

.card-title {
  font-size: 13px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: var(--text2);
}

.card-body { padding: 18px; }

/* ── ALERT BANNER ── */
.alert-banner {
  display: flex;
  align-items: flex-start;
  gap: 10px;
  padding: 12px 16px;
  border-radius: var(--r-sm);
  font-size: 13px;
  margin-bottom: 14px;
  border: 1px solid;
}

.ab-green  { background: var(--green-bg);  border-color: var(--green-mid);  color: var(--green); }
.ab-amber  { background: var(--amber-bg);  border-color: var(--amber-mid);  color: var(--amber); }
.ab-red    { background: var(--red-bg);    border-color: var(--red-mid);    color: var(--red); }
.ab-blue   { background: var(--blue-bg);   border-color: var(--blue-mid);   color: var(--blue); }

/* ── FILTER BAR ── */
.filter-bar {
  display: flex;
  gap: 10px;
  padding: 12px 18px;
  border-bottom: 1px solid var(--border);
  flex-wrap: wrap;
  background: var(--surface2);
  border-radius: 0;
}

.filter-bar input,
.filter-bar select {
  background: var(--surface);
  border: 1px solid var(--border2);
  border-radius: var(--r-sm);
  padding: 7px 10px;
  font-family: var(--sans);
  font-size: 13px;
  color: var(--text);
  outline: none;
  transition: border-color 0.12s;
}

.filter-bar input:focus,
.filter-bar select:focus { border-color: var(--green); }

.filter-bar input { min-width: 200px; }

/* ── TABLE ── */
.tbl-wrap { overflow-x: auto; }

table { width: 100%; border-collapse: collapse; }

thead th {
  font-size: 11px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--text3);
  padding: 10px 14px;
  text-align: left;
  background: var(--surface2);
  border-bottom: 1px solid var(--border);
  white-space: nowrap;
}

tbody td {
  padding: 11px 14px;
  border-bottom: 1px solid var(--border);
  vertical-align: middle;
  font-size: 13.5px;
}

tbody tr:last-child td { border-bottom: none; }
tbody tr:hover td { background: #fafbfc; }

.cat-sep td {
  background: var(--bg) !important;
  padding: 7px 14px !important;
  font-size: 11px !important;
  font-weight: 600 !important;
  text-transform: uppercase !important;
  letter-spacing: 0.09em !important;
  color: var(--text2) !important;
  border-top: 2px solid var(--border) !important;
}

/* ── BADGES ── */
.badge {
  display: inline-flex;
  align-items: center;
  padding: 3px 9px;
  border-radius: 20px;
  font-size: 11px;
  font-weight: 500;
  white-space: nowrap;
}

.b-green  { background: var(--green-bg);  color: var(--green); }
.b-amber  { background: var(--amber-bg);  color: var(--amber); }
.b-red    { background: var(--red-bg);    color: var(--red); }
.b-blue   { background: var(--blue-bg);   color: var(--blue); }
.b-purple { background: var(--purple-bg); color: var(--purple); }
.b-gray   { background: var(--surface2);  color: var(--text2); border: 1px solid var(--border); }

/* ── QTY STEPPER ── */
.stepper {
  display: inline-flex;
  align-items: center;
  gap: 0;
  border: 1px solid var(--border2);
  border-radius: var(--r-sm);
  overflow: hidden;
}

.stepper-btn {
  width: 28px; height: 30px;
  background: var(--surface2);
  border: none;
  cursor: pointer;
  font-size: 15px;
  color: var(--text2);
  display: flex; align-items: center; justify-content: center;
  transition: all 0.1s;
  flex-shrink: 0;
}

.stepper-btn:hover { background: var(--border); color: var(--text); }

.stepper-val {
  width: 52px;
  border: none;
  border-left: 1px solid var(--border2);
  border-right: 1px solid var(--border2);
  text-align: center;
  font-family: var(--mono);
  font-size: 13px;
  font-weight: 500;
  padding: 0 4px;
  height: 30px;
  outline: none;
  color: var(--text);
  background: var(--surface);
}

/* ── ACTION BTNS IN TABLE ── */
.tbl-actions { display: flex; gap: 5px; }

/* ── FORM ── */
.form-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 14px;
}

.field { display: flex; flex-direction: column; gap: 5px; }

.field label {
  font-size: 11px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  color: var(--text2);
}

.field input,
.field select,
.field textarea {
  background: var(--surface);
  border: 1px solid var(--border2);
  border-radius: var(--r-sm);
  padding: 9px 11px;
  font-family: var(--sans);
  font-size: 13px;
  color: var(--text);
  outline: none;
  transition: border-color 0.12s;
  width: 100%;
}

.field input:focus,
.field select:focus,
.field textarea:focus { border-color: var(--green); box-shadow: 0 0 0 3px var(--green-bg); }

.field.span2 { grid-column: span 2; }
.field.span3 { grid-column: 1 / -1; }

/* ── LOG ── */
.log-list { display: flex; flex-direction: column; }

.log-item {
  display: flex;
  gap: 14px;
  padding: 12px 18px;
  border-bottom: 1px solid var(--border);
  align-items: flex-start;
}

.log-item:last-child { border-bottom: none; }
.log-item:hover { background: var(--surface2); }

.log-dot {
  width: 8px; height: 8px;
  border-radius: 50%;
  margin-top: 5px;
  flex-shrink: 0;
}

.ld-entrada { background: var(--green); }
.ld-saida   { background: var(--red); }
.ld-ajuste  { background: var(--amber); }

.log-body { flex: 1; min-width: 0; }

.log-main {
  font-size: 13.5px;
  color: var(--text);
  font-weight: 500;
  margin-bottom: 2px;
}

.log-meta {
  font-size: 11.5px;
  color: var(--text3);
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
}

.log-meta span { display: flex; align-items: center; gap: 3px; }

.log-right {
  text-align: right;
  flex-shrink: 0;
}

.log-qty {
  font-family: var(--mono);
  font-size: 14px;
  font-weight: 500;
}

.log-qty.pos { color: var(--green); }
.log-qty.neg { color: var(--red); }
.log-qty.neu { color: var(--amber); }

.log-time {
  font-size: 11px;
  color: var(--text3);
  font-family: var(--mono);
}

/* ── MODAL ── */
.overlay {
  position: fixed; inset: 0;
  background: rgba(10,12,20,0.45);
  backdrop-filter: blur(2px);
  z-index: 1000;
  display: none;
  align-items: center;
  justify-content: center;
  padding: 16px;
}

.overlay.open { display: flex; }

.modal {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--r);
  box-shadow: var(--shadow-md);
  width: 100%;
  max-width: 480px;
  max-height: 90vh;
  overflow-y: auto;
}

.modal-head {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 20px;
  border-bottom: 1px solid var(--border);
}

.modal-title { font-size: 15px; font-weight: 600; }

.modal-close {
  background: none;
  border: none;
  cursor: pointer;
  font-size: 20px;
  color: var(--text3);
  line-height: 1;
  padding: 0;
  transition: color 0.1s;
}

.modal-close:hover { color: var(--text); }

.modal-body { padding: 20px; }

.modal-foot {
  display: flex;
  justify-content: flex-end;
  gap: 8px;
  padding: 14px 20px;
  border-top: 1px solid var(--border);
}

/* ── REPORT ── */
.report-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--r);
  box-shadow: var(--shadow);
  margin-bottom: 14px;
  cursor: pointer;
  transition: all 0.12s;
}

.report-card:hover { border-color: var(--green-mid); box-shadow: var(--shadow-md); }
.report-card.selected { border-color: var(--green); }

.report-card-body { padding: 14px 18px; }

.report-wk { font-size: 14px; font-weight: 600; color: var(--green); }
.report-meta { font-size: 12px; color: var(--text2); margin-top: 3px; }

.report-pills { display: flex; gap: 6px; margin-top: 8px; flex-wrap: wrap; }

/* ── REPORT VIEW ── */
.rpt-section { margin-bottom: 28px; }
.rpt-section-title {
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.09em;
  color: var(--green);
  border-bottom: 2px solid var(--green-mid);
  padding-bottom: 6px;
  margin-bottom: 12px;
}

/* ── SPLIT LAYOUT ── */
.split { display: grid; grid-template-columns: 280px 1fr; gap: 16px; }

/* ── EMPTY ── */
.empty {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 48px;
  color: var(--text3);
  gap: 8px;
  text-align: center;
}

.empty-icon { font-size: 36px; }
.empty-text { font-size: 14px; }

/* ── SCROLLBAR ── */
::-webkit-scrollbar { width: 5px; height: 5px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb { background: var(--border2); border-radius: 3px; }

/* ── TOAST ── */
.toast-wrap {
  position: fixed;
  bottom: 24px;
  right: 24px;
  z-index: 9999;
  display: flex;
  flex-direction: column;
  gap: 8px;
  pointer-events: none;
}

.toast {
  background: var(--text);
  color: var(--surface);
  padding: 11px 16px;
  border-radius: var(--r-sm);
  font-size: 13px;
  box-shadow: var(--shadow-md);
  animation: toastIn 0.2s ease;
  max-width: 320px;
}

@keyframes toastIn {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}

/* ── RESPONSIVE ── */
@media (max-width: 800px) {
  .rail { width: 100%; height: auto; position: relative; flex-direction: row; }
  .rail-brand { display: none; }
  .rail-nav { display: flex; flex-direction: row; padding: 4px; overflow-x: auto; }
  .nav-section-label { display: none; }
  .nav-btn { padding: 8px 12px; white-space: nowrap; font-size: 12px; }
  .rail-footer { display: none; }
  .main-wrap { margin-left: 0; }
  .shell { flex-direction: column; }
  .split { grid-template-columns: 1fr; }
  .page { padding: 16px; }
  .topbar { padding: 0 16px; height: 50px; }
}

@media print {
  .rail, .topbar, .filter-bar, .btn, .stepper, .tbl-actions, .topbar-actions { display: none !important; }
  .main-wrap { margin-left: 0; }
  body { background: white; }
  .card, .stat { border: 1px solid #ddd; box-shadow: none; }
}
</style>
</head>
<body>

<div class="shell">

<!-- ══ RAIL ══ -->
<aside class="rail" id="rail">
  <div class="rail-brand">
    <div class="brand-mark">
      <div class="brand-icon">🏥</div>
      <div>
        <div class="brand-name">Estoque Clínico</div>
        <div class="brand-sub">Controle semanal</div>
      </div>
    </div>
  </div>

  <nav class="rail-nav">
    <div class="nav-section-label">Principal</div>
    <button class="nav-btn active" id="nb-estoque" onclick="nav('estoque')">
      <span class="ni">📦</span> Estoque
    </button>
    <button class="nav-btn" id="nb-mover" onclick="nav('mover')">
      <span class="ni">🔄</span> Movimentação
    </button>
    <button class="nav-btn" id="nb-historico" onclick="nav('historico')">
      <span class="ni">📋</span> Histórico
    </button>

    <div class="nav-section-label">Alertas e Relatórios</div>
    <button class="nav-btn" id="nb-alertas" onclick="nav('alertas')">
      <span class="ni">⚠️</span> Alertas
      <span class="nav-badge" id="alert-badge" style="display:none">0</span>
    </button>
    <button class="nav-btn" id="nb-fechamento" onclick="nav('fechamento')">
      <span class="ni">✅</span> Fechamento
    </button>
    <button class="nav-btn" id="nb-relatorios" onclick="nav('relatorios')">
      <span class="ni">📊</span> Relatórios
    </button>

    <div class="nav-section-label">Configuração</div>
    <button class="nav-btn" id="nb-cadastro" onclick="nav('cadastro')">
      <span class="ni">➕</span> Cadastrar Item
    </button>
  </nav>

  <div class="rail-footer">
    <div class="week-label" id="rf-week">—</div>
    <div id="rf-date">—</div>
  </div>
</aside>

<!-- ══ MAIN ══ -->
<div class="main-wrap">

  <header class="topbar">
    <div class="topbar-left">
      <span class="topbar-title" id="tb-title">Estoque</span>
      <span class="topbar-pill" id="tb-week">—</span>
    </div>
    <div class="topbar-actions">
      <button class="btn btn-ghost btn-sm" onclick="exportCSV()">⬇ Exportar CSV</button>
      <button class="btn btn-green btn-sm" onclick="openMoveModal(null,'entrada')">+ Registrar Entrada</button>
    </div>
  </header>

  <!-- ══ PAGE: ESTOQUE ══ -->
  <div class="page active" id="page-estoque">
    <div class="stats-row" id="stats-row"></div>
    <div id="low-banner"></div>
    <div class="card">
      <div class="card-head">
        <span class="card-title">Materiais em Estoque</span>
        <button class="btn btn-ghost btn-sm" onclick="nav('cadastro')">+ Novo Item</button>
      </div>
      <div class="filter-bar">
        <input type="text" id="srch" placeholder="🔍  Buscar material..." oninput="renderEstoque()">
        <select id="fcat" onchange="renderEstoque()">
          <option value="">Todas as categorias</option>
        </select>
        <select id="fstatus" onchange="renderEstoque()">
          <option value="">Todos os status</option>
          <option value="ok">OK</option>
          <option value="baixo">Estoque baixo</option>
          <option value="critico">Crítico / Zerado</option>
        </select>
      </div>
      <div class="tbl-wrap">
        <table>
          <thead>
            <tr>
              <th>Status</th>
              <th>Material</th>
              <th>Categoria</th>
              <th>Quantidade</th>
              <th>Mín.</th>
              <th>Ações</th>
            </tr>
          </thead>
          <tbody id="estoque-tbody"></tbody>
        </table>
      </div>
    </div>
  </div>

  <!-- ══ PAGE: MOVIMENTAÇÃO ══ -->
  <div class="page" id="page-mover">
    <div class="card" style="max-width:560px">
      <div class="card-head"><span class="card-title">Registrar Movimentação</span></div>
      <div class="card-body">
        <div class="form-grid">
          <div class="field">
            <label>Tipo *</label>
            <select id="mv-tipo">
              <option value="entrada">Entrada</option>
              <option value="saida">Saída</option>
              <option value="ajuste">Ajuste manual (definir valor)</option>
            </select>
          </div>
          <div class="field">
            <label>Material *</label>
            <select id="mv-item"></select>
          </div>
          <div class="field">
            <label>Quantidade *</label>
            <input type="number" id="mv-qty" value="1" min="1">
          </div>
          <div class="field">
            <label>Responsável</label>
            <input type="text" id="mv-resp" placeholder="Seu nome">
          </div>
          <div class="field span2">
            <label>Observação / Motivo</label>
            <input type="text" id="mv-obs" placeholder="Ex: reposição semanal, uso rotineiro...">
          </div>
        </div>
        <div style="margin-top:18px;display:flex;gap:10px">
          <button class="btn btn-green" onclick="submitMove()">Confirmar Movimentação</button>
          <button class="btn btn-ghost" onclick="nav('estoque')">Cancelar</button>
        </div>
      </div>
    </div>
  </div>

  <!-- ══ PAGE: HISTÓRICO ══ -->
  <div class="page" id="page-historico">
    <div class="card">
      <div class="card-head">
        <span class="card-title">Histórico de Movimentações</span>
        <div style="display:flex;gap:8px;flex-wrap:wrap">
          <select id="hf-tipo" onchange="renderHistorico()">
            <option value="">Todos os tipos</option>
            <option value="entrada">Entrada</option>
            <option value="saida">Saída</option>
            <option value="ajuste">Ajuste</option>
          </select>
          <select id="hf-cat" onchange="renderHistorico()">
            <option value="">Todas as categorias</option>
          </select>
          <select id="hf-week" onchange="renderHistorico()">
            <option value="">Todas as semanas</option>
          </select>
        </div>
      </div>
      <div id="historico-list"></div>
    </div>
  </div>

  <!-- ══ PAGE: ALERTAS ══ -->
  <div class="page" id="page-alertas">
    <div class="card">
      <div class="card-head"><span class="card-title">Itens com Estoque Baixo ou Zerado</span></div>
      <div class="tbl-wrap">
        <table>
          <thead>
            <tr><th>Status</th><th>Material</th><th>Categoria</th><th>Qtd. Atual</th><th>Mínimo</th><th>Ação</th></tr>
          </thead>
          <tbody id="alertas-tbody"></tbody>
        </table>
      </div>
    </div>
  </div>

  <!-- ══ PAGE: FECHAMENTO ══ -->
  <div class="page" id="page-fechamento">
    <div style="max-width:600px">
      <div class="card">
        <div class="card-head"><span class="card-title">Fechamento Semanal</span></div>
        <div class="card-body">
          <div class="alert-banner ab-blue" style="margin-bottom:18px">
            <span>ℹ️</span>
            <div>O fechamento consolida todas as movimentações da semana e gera um <strong>relatório imutável</strong>. Após gerado, os dados históricos não são afetados por alterações futuras. Realize sempre <strong>domingo à noite</strong>.</div>
          </div>
          <div id="fech-status" style="margin-bottom:18px"></div>
          <div class="form-grid">
            <div class="field">
              <label>Responsável pelo Fechamento</label>
              <input type="text" id="fech-resp" placeholder="Nome do responsável">
            </div>
            <div class="field">
              <label>Observações Gerais</label>
              <input type="text" id="fech-obs" placeholder="Observações opcionais">
            </div>
          </div>
          <div style="margin-top:20px">
            <button class="btn btn-amber" onclick="realizarFechamento()">📋 Realizar Fechamento Semanal</button>
          </div>
        </div>
      </div>

      <div id="fech-preview" style="margin-top:16px"></div>
    </div>
  </div>

  <!-- ══ PAGE: RELATÓRIOS ══ -->
  <div class="page" id="page-relatorios">
    <div class="split">
      <div>
        <div style="font-size:12px;font-weight:600;text-transform:uppercase;letter-spacing:0.08em;color:var(--text2);margin-bottom:10px">Fechamentos Salvos</div>
        <div id="report-list"></div>
      </div>
      <div id="report-view">
        <div class="empty">
          <div class="empty-icon">📊</div>
          <div class="empty-text">Selecione um relatório à esquerda para visualizá-lo.</div>
        </div>
      </div>
    </div>
  </div>

  <!-- ══ PAGE: CADASTRO ══ -->
  <div class="page" id="page-cadastro">
    <div class="card" style="max-width:600px">
      <div class="card-head"><span class="card-title">Cadastrar Novo Item</span></div>
      <div class="card-body">
        <div class="form-grid">
          <div class="field span2">
            <label>Nome do Material *</label>
            <input type="text" id="cad-nome" placeholder="Ex: Álcool gel 500 ml">
          </div>
          <div class="field">
            <label>Categoria *</label>
            <select id="cad-cat">
              <option value="">Selecione</option>
              <option>Nutrição</option>
              <option>Higiene</option>
              <option>Monitoramento (HGT)</option>
              <option>Procedimentos</option>
              <option>Medicamentos Tópicos</option>
              <option>Medicamentos Orais</option>
              <option>Outro</option>
            </select>
          </div>
          <div class="field">
            <label>Unidade</label>
            <input type="text" id="cad-unit" placeholder="Ex: un, cx, fr, pct">
          </div>
          <div class="field">
            <label>Quantidade Inicial</label>
            <input type="number" id="cad-qty" value="0" min="0">
          </div>
          <div class="field">
            <label>Estoque Mínimo (alerta)</label>
            <input type="number" id="cad-min" value="5" min="0">
          </div>
        </div>
        <div style="margin-top:20px;display:flex;gap:10px">
          <button class="btn btn-green" onclick="cadastrar()">Cadastrar Item</button>
          <button class="btn btn-ghost" onclick="nav('estoque')">Cancelar</button>
        </div>
      </div>
    </div>
  </div>

</div><!-- /main-wrap -->
</div><!-- /shell -->

<!-- ══ MODAL: MOVIMENTAÇÃO RÁPIDA ══ -->
<div class="overlay" id="modal-move">
  <div class="modal">
    <div class="modal-head">
      <span class="modal-title" id="mm-title">Registrar Movimentação</span>
      <button class="modal-close" onclick="closeModal('modal-move')">×</button>
    </div>
    <div class="modal-body">
      <div class="form-grid">
        <div class="field">
          <label>Tipo *</label>
          <select id="mm-tipo">
            <option value="entrada">↑ Entrada</option>
            <option value="saida">↓ Saída</option>
            <option value="ajuste">✎ Ajuste manual</option>
          </select>
        </div>
        <div class="field">
          <label>Material *</label>
          <select id="mm-item"></select>
        </div>
        <div class="field">
          <label>Quantidade *</label>
          <input type="number" id="mm-qty" value="1" min="1">
        </div>
        <div class="field">
          <label>Responsável</label>
          <input type="text" id="mm-resp" placeholder="Nome">
        </div>
        <div class="field span2">
          <label>Observação</label>
          <input type="text" id="mm-obs" placeholder="Motivo, lote, etc.">
        </div>
      </div>
    </div>
    <div class="modal-foot">
      <button class="btn btn-ghost" onclick="closeModal('modal-move')">Cancelar</button>
      <button class="btn btn-green" onclick="submitModalMove()">Confirmar</button>
    </div>
  </div>
</div>

<!-- ══ TOAST ══ -->
<div class="toast-wrap" id="toasts"></div>

<script>
/* ═══════════════════════════════
   DADOS INICIAIS
═══════════════════════════════ */
const SEED = [
  { cat:'Nutrição',               name:'Peptamen 1.5 Kcal Sistema Fechado',                qty:31,  min:5,  unit:'un' },
  { cat:'Higiene',                name:'Pano Sontara Clean Care 30x30 cm',                 qty:20,  min:3,  unit:'pct' },
  { cat:'Higiene',                name:'Sabonete líquido glicerinado',                     qty:4,   min:2,  unit:'fr' },
  { cat:'Higiene',                name:'Discos de algodão (100 unidades)',                 qty:1,   min:1,  unit:'pct' },
  { cat:'Higiene',                name:'Álcool gel 500 ml',                                qty:2,   min:1,  unit:'fr' },
  { cat:'Higiene',                name:'Álcool 70% líquido 1 litro',                       qty:2,   min:1,  unit:'fr' },
  { cat:'Higiene',                name:'Fraldas geriátricas',                              qty:250, min:56, unit:'un' },
  { cat:'Monitoramento (HGT)',    name:'Fitas para HGT ON CALL PLUS',                     qty:50,  min:10, unit:'ft' },
  { cat:'Monitoramento (HGT)',    name:'Lancetas para HGT',                                qty:50,  min:10, unit:'un' },
  { cat:'Procedimentos',          name:'Compressa de gaze estéril não aderente',           qty:5,   min:2,  unit:'pct' },
  { cat:'Procedimentos',          name:'Luva nitrílica sem pó (tam. M e G)',               qty:10,  min:2,  unit:'cx' },
  { cat:'Procedimentos',          name:'Seringa sem agulha 20 ml',                         qty:30,  min:5,  unit:'un' },
  { cat:'Procedimentos',          name:'Seringa sem agulha 10 ml',                         qty:30,  min:5,  unit:'un' },
  { cat:'Procedimentos',          name:'Frasco de dieta simples para água',                qty:30,  min:5,  unit:'un' },
  { cat:'Procedimentos',          name:'Equipo de dieta simples para infusão de água',     qty:30,  min:5,  unit:'un' },
  { cat:'Procedimentos',          name:'Equipo ponta cruz compatível com bomba AMIKA',     qty:30,  min:5,  unit:'un' },
  { cat:'Procedimentos',          name:'Extensor de gastrostomia Boton Mickey',            qty:2,   min:1,  unit:'un' },
  { cat:'Medicamentos Tópicos',   name:'Creme barreira',                                   qty:4,   min:1,  unit:'un' },
  { cat:'Medicamentos Tópicos',   name:'Dersani 200 ml',                                   qty:2,   min:1,  unit:'fr' },
  { cat:'Medicamentos Tópicos',   name:'Dexametasona pomada 20 mg',                        qty:2,   min:1,  unit:'un' },
  { cat:'Medicamentos Tópicos',   name:'Nebacetin 5 mg',                                   qty:2,   min:1,  unit:'un' },
  { cat:'Medicamentos Tópicos',   name:'Bella Dex 60 g',                                   qty:2,   min:1,  unit:'un' },
  { cat:'Medicamentos Tópicos',   name:'Belglós 45 g',                                     qty:2,   min:1,  unit:'un' },
  { cat:'Medicamentos Tópicos',   name:'Óxido de zinco',                                   qty:14,  min:2,  unit:'un' },
  { cat:'Medicamentos Tópicos',   name:'Aciclovir 50 mg',                                  qty:4,   min:1,  unit:'un' },
  { cat:'Medicamentos Tópicos',   name:'Cetoconazol 30 g',                                 qty:4,   min:1,  unit:'un' },
  { cat:'Medicamentos Tópicos',   name:'Hirudoid',                                         qty:2,   min:1,  unit:'un' },
  { cat:'Medicamentos Tópicos',   name:'Bactroban 20 mg',                                  qty:4,   min:1,  unit:'un' },
  { cat:'Medicamentos Orais',     name:'Omeprazol 20 mg',                                  qty:0,   min:10, unit:'cp' },
  { cat:'Medicamentos Orais',     name:'Levetiracetam 100 mg/ml',                          qty:0,   min:3,  unit:'fr' },
  { cat:'Medicamentos Orais',     name:'Clopidogrel 75 mg',                                qty:0,   min:10, unit:'cp' },
  { cat:'Medicamentos Orais',     name:'Prednisolona 5 mg',                                qty:0,   min:10, unit:'cp' },
  { cat:'Medicamentos Orais',     name:'Anlodipino 5 mg',                                  qty:0,   min:10, unit:'cp' },
];

/* ═══════════════════════════════
   ESTADO
═══════════════════════════════ */
let items      = [];
let movements  = [];
let reports    = [];

function ls_load() {
  const i = localStorage.getItem('ec_items');
  const m = localStorage.getItem('ec_movs');
  const r = localStorage.getItem('ec_reports');
  if (i) { items     = JSON.parse(i); }
  else   { items     = SEED.map((x, idx) => ({ ...x, id: 'i' + idx })); ls_save(); }
  if (m) { movements = JSON.parse(m); }
  if (r) { reports   = JSON.parse(r); }
}

function ls_save() {
  localStorage.setItem('ec_items',   JSON.stringify(items));
  localStorage.setItem('ec_movs',    JSON.stringify(movements));
  localStorage.setItem('ec_reports', JSON.stringify(reports));
}

/* ═══════════════════════════════
   WEEK UTILS
═══════════════════════════════ */
function weekStart(d) {
  const dt = d ? new Date(d) : new Date();
  const day = dt.getDay(); // 0=dom
  const diff = dt.getDate() - day + (day === 0 ? -6 : 1);
  const mon = new Date(dt); mon.setDate(diff);
  mon.setHours(0,0,0,0);
  return mon.toISOString().split('T')[0];
}

function weekLabel(wk) {
  const mon = new Date(wk + 'T00:00:00');
  const sun = new Date(mon); sun.setDate(sun.getDate() + 6);
  const f = d => d.toLocaleDateString('pt-BR', { day: '2-digit', month: '2-digit' });
  return `Semana ${f(mon)} – ${f(sun)}`;
}

function currentWeek() { return weekStart(); }

function fmtDT(iso) {
  if (!iso) return '—';
  const d = new Date(iso);
  return d.toLocaleDateString('pt-BR',{day:'2-digit',month:'2-digit',year:'numeric'}) + ' ' +
         d.toLocaleTimeString('pt-BR',{hour:'2-digit',minute:'2-digit'});
}

function fmtDate(iso) {
  if (!iso) return '—';
  return new Date(iso).toLocaleDateString('pt-BR',{day:'2-digit',month:'2-digit',year:'numeric'});
}

/* ═══════════════════════════════
   STATUS
═══════════════════════════════ */
function itemStatus(item) {
  if (item.qty <= 0)       return 'critico';
  if (item.qty <= item.min) return 'baixo';
  return 'ok';
}

function statusBadge(item) {
  const s = itemStatus(item);
  if (s === 'ok')      return '<span class="badge b-green">OK</span>';
  if (s === 'baixo')   return '<span class="badge b-amber">Baixo</span>';
  return '<span class="badge b-red">Zerado</span>';
}

/* ═══════════════════════════════
   NAV
═══════════════════════════════ */
const PAGE_TITLES = {
  estoque:    'Estoque',
  mover:      'Registrar Movimentação',
  historico:  'Histórico',
  alertas:    'Alertas',
  fechamento: 'Fechamento Semanal',
  relatorios: 'Relatórios',
  cadastro:   'Cadastrar Item',
};

function nav(page) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
  document.getElementById('page-' + page).classList.add('active');
  document.getElementById('nb-' + page).classList.add('active');
  document.getElementById('tb-title').textContent = PAGE_TITLES[page] || page;

  if (page === 'historico')  { populateHistFilters(); renderHistorico(); }
  if (page === 'alertas')    renderAlertas();
  if (page === 'fechamento') renderFechamento();
  if (page === 'relatorios') renderReportList();
  if (page === 'mover')      populateItemSelect('mv-item');
}

/* ═══════════════════════════════
   CATEGORIAS
═══════════════════════════════ */
function cats() {
  return [...new Set(items.map(i => i.cat))].sort();
}

function populateCatSelects() {
  const cs = cats();
  ['fcat','hf-cat'].forEach(id => {
    const el = document.getElementById(id);
    if (!el) return;
    const prev = el.value;
    el.innerHTML = '<option value="">Todas as categorias</option>';
    cs.forEach(c => el.innerHTML += `<option value="${c}">${c}</option>`);
    el.value = prev;
  });
}

function populateItemSelect(id, selectedId) {
  const el = document.getElementById(id);
  el.innerHTML = '';
  items.forEach(i => {
    const o = document.createElement('option');
    o.value = i.id;
    o.textContent = `${i.name}  (${i.qty} ${i.unit||'un'})`;
    if (i.id === selectedId) o.selected = true;
    el.appendChild(o);
  });
}

function populateWeekFilter() {
  const weeks = [...new Set(movements.map(m => m.week))].sort().reverse();
  const el = document.getElementById('hf-week');
  const prev = el.value;
  el.innerHTML = '<option value="">Todas as semanas</option>';
  weeks.forEach(w => {
    el.innerHTML += `<option value="${w}">${weekLabel(w)}</option>`;
  });
  el.value = weeks.includes(prev) ? prev : '';
}

function populateHistFilters() {
  populateCatSelects();
  populateWeekFilter();
}

/* ═══════════════════════════════
   RENDER: ESTOQUE
═══════════════════════════════ */
function renderEstoque() {
  const srch   = document.getElementById('srch').value.toLowerCase();
  const catF   = document.getElementById('fcat').value;
  const stF    = document.getElementById('fstatus').value;
  const allCats = cats();

  let html = '';
  let shown = 0;

  allCats.forEach(cat => {
    if (catF && catF !== cat) return;
    const ci = items.filter(i => {
      if (i.cat !== cat) return false;
      if (srch && !i.name.toLowerCase().includes(srch)) return false;
      if (stF && itemStatus(i) !== stF) return false;
      return true;
    });
    if (!ci.length) return;

    html += `<tr class="cat-sep"><td colspan="6">📁  ${cat}</td></tr>`;
    ci.forEach(item => {
      html += `<tr>
        <td>${statusBadge(item)}</td>
        <td style="font-weight:500">${item.name}</td>
        <td><span class="badge b-gray">${item.cat}</span></td>
        <td>
          <div class="stepper">
            <button class="stepper-btn" onclick="stepQty('${item.id}',-1)">−</button>
            <input class="stepper-val" type="number" value="${item.qty}" min="0"
              onchange="setQty('${item.id}',+this.value)" onblur="setQty('${item.id}',+this.value)">
            <button class="stepper-btn" onclick="stepQty('${item.id}',+1)">+</button>
          </div>
        </td>
        <td style="font-family:var(--mono);color:var(--text3)">${item.min}</td>
        <td>
          <div class="tbl-actions">
            <button class="btn btn-ghost btn-xs" onclick="openMoveModal('${item.id}','entrada')">↑ In</button>
            <button class="btn btn-ghost btn-xs" onclick="openMoveModal('${item.id}','saida')">↓ Out</button>
            <button class="btn btn-ghost btn-xs" onclick="openMoveModal('${item.id}','ajuste')">✎</button>
          </div>
        </td>
      </tr>`;
      shown++;
    });
  });

  document.getElementById('estoque-tbody').innerHTML =
    html || '<tr><td colspan="6"><div class="empty"><div class="empty-icon">🔍</div><div class="empty-text">Nenhum item encontrado.</div></div></td></tr>';

  renderStats();
  renderLowBanner();
  updateAlertBadge();
}

function stepQty(id, delta) {
  const item = items.find(i => i.id === id);
  if (!item) return;
  const prev = item.qty;
  item.qty = Math.max(0, item.qty + delta);
  addMov(id, delta > 0 ? 'entrada' : 'saida', Math.abs(delta), 'Ajuste rápido (stepper)', 'Sistema', prev);
  ls_save();
  renderEstoque();
}

function setQty(id, val) {
  const item = items.find(i => i.id === id);
  if (!item || isNaN(val) || val < 0) return;
  const prev = item.qty;
  if (val === prev) return;
  item.qty = val;
  addMov(id, 'ajuste', Math.abs(val - prev), `Edição direta (${prev}→${val})`, 'Sistema', prev);
  ls_save();
  renderEstoque();
}

/* ═══════════════════════════════
   RENDER: STATS
═══════════════════════════════ */
function renderStats() {
  const total    = items.length;
  const baixo    = items.filter(i => itemStatus(i) === 'baixo').length;
  const critico  = items.filter(i => itemStatus(i) === 'critico').length;
  const wk       = currentWeek();
  const movSem   = movements.filter(m => m.week === wk).length;

  document.getElementById('stats-row').innerHTML = `
    <div class="stat"><div class="stat-label">Total de Itens</div><div class="stat-val green">${total}</div></div>
    <div class="stat"><div class="stat-label">Estoque Baixo</div><div class="stat-val amber">${baixo}</div></div>
    <div class="stat"><div class="stat-label">Zerados / Críticos</div><div class="stat-val red">${critico}</div></div>
    <div class="stat"><div class="stat-label">Movim. esta semana</div><div class="stat-val blue">${movSem}</div></div>
  `;
}

function renderLowBanner() {
  const lows = items.filter(i => itemStatus(i) !== 'ok');
  const el = document.getElementById('low-banner');
  if (!lows.length) { el.innerHTML = ''; return; }
  const hasCrit = lows.some(i => itemStatus(i) === 'critico');
  const names = lows.slice(0, 3).map(i => `<strong>${i.name}</strong>`).join(', ');
  el.innerHTML = `
    <div class="alert-banner ${hasCrit ? 'ab-red' : 'ab-amber'}" style="margin-bottom:14px">
      <span>${hasCrit ? '🔴' : '🟡'}</span>
      <div>${lows.length} item(s) com estoque ${hasCrit ? 'zerado ou ' : ''}baixo: ${names}${lows.length > 3 ? ` e mais ${lows.length - 3}` : ''}.
        <a href="#" onclick="nav('alertas');return false" style="color:inherit;margin-left:8px;text-decoration:underline">Ver todos →</a>
      </div>
    </div>`;
}

function updateAlertBadge() {
  const lows = items.filter(i => itemStatus(i) !== 'ok').length;
  const badge = document.getElementById('alert-badge');
  if (lows > 0) { badge.textContent = lows; badge.style.display = ''; }
  else { badge.style.display = 'none'; }
}

/* ═══════════════════════════════
   MOVIMENTAÇÕES
═══════════════════════════════ */
function addMov(itemId, tipo, qty, obs, resp, prevQty) {
  const item = items.find(i => i.id === itemId);
  movements.push({
    id:       'mv' + Date.now() + Math.random().toString(36).slice(2, 6),
    itemId,
    itemName: item ? item.name : '—',
    cat:      item ? item.cat  : '—',
    tipo,
    qty,
    obs:      obs  || '',
    resp:     resp || '',
    date:     new Date().toISOString(),
    week:     currentWeek(),
    prevQty,
    newQty:   item ? item.qty : 0,
  });
}

function submitMove() {
  const tipo    = document.getElementById('mv-tipo').value;
  const itemId  = document.getElementById('mv-item').value;
  const qty     = +document.getElementById('mv-qty').value;
  const resp    = document.getElementById('mv-resp').value.trim();
  const obs     = document.getElementById('mv-obs').value.trim();

  if (!itemId || isNaN(qty) || qty <= 0) { toast('Preencha todos os campos obrigatórios.', 'red'); return; }

  applyMove(tipo, itemId, qty, obs, resp);
  document.getElementById('mv-qty').value = 1;
  document.getElementById('mv-obs').value = '';
  nav('estoque');
}

function applyMove(tipo, itemId, qty, obs, resp) {
  const item = items.find(i => i.id === itemId);
  if (!item) return;
  const prev = item.qty;
  if (tipo === 'entrada') item.qty += qty;
  else if (tipo === 'saida') item.qty = Math.max(0, item.qty - qty);
  else item.qty = qty;
  addMov(itemId, tipo, qty, obs, resp, prev);
  ls_save();
  renderEstoque();
  toast(`Movimentação registrada: ${tipo} de ${qty} ${item.unit || 'un'} — ${item.name}`);
}

function openMoveModal(itemId, tipo) {
  populateItemSelect('mm-item', itemId);
  document.getElementById('mm-tipo').value  = tipo || 'entrada';
  document.getElementById('mm-qty').value   = 1;
  document.getElementById('mm-resp').value  = '';
  document.getElementById('mm-obs').value   = '';
  const labels = { entrada: '↑ Registrar Entrada', saida: '↓ Registrar Saída', ajuste: '✎ Ajuste Manual' };
  document.getElementById('mm-title').textContent = labels[tipo] || 'Movimentação';
  document.getElementById('modal-move').classList.add('open');
}

function submitModalMove() {
  const tipo   = document.getElementById('mm-tipo').value;
  const itemId = document.getElementById('mm-item').value;
  const qty    = +document.getElementById('mm-qty').value;
  const resp   = document.getElementById('mm-resp').value.trim();
  const obs    = document.getElementById('mm-obs').value.trim();
  if (!itemId || isNaN(qty) || qty <= 0) { toast('Preencha todos os campos.', 'red'); return; }
  applyMove(tipo, itemId, qty, obs, resp);
  closeModal('modal-move');
}

/* ═══════════════════════════════
   RENDER: HISTÓRICO
═══════════════════════════════ */
function renderHistorico() {
  const tipoF = document.getElementById('hf-tipo').value;
  const catF  = document.getElementById('hf-cat').value;
  const wkF   = document.getElementById('hf-week').value;

  const list = [...movements]
    .filter(m =>
      (!tipoF || m.tipo === tipoF) &&
      (!catF  || m.cat  === catF)  &&
      (!wkF   || m.week === wkF)
    )
    .sort((a, b) => new Date(b.date) - new Date(a.date));

  if (!list.length) {
    document.getElementById('historico-list').innerHTML =
      '<div class="empty"><div class="empty-icon">📭</div><div class="empty-text">Nenhuma movimentação encontrada.</div></div>';
    return;
  }

  const typeInfo = {
    entrada: { dot: 'ld-entrada', label: '↑ Entrada',      cls: 'pos' },
    saida:   { dot: 'ld-saida',   label: '↓ Saída',        cls: 'neg' },
    ajuste:  { dot: 'ld-ajuste',  label: '✎ Ajuste',       cls: 'neu' },
  };

  let html = '<div class="log-list">';
  list.forEach(m => {
    const ti = typeInfo[m.tipo] || { dot: '', label: m.tipo, cls: '' };
    html += `<div class="log-item">
      <div class="log-dot ${ti.dot}"></div>
      <div class="log-body">
        <div class="log-main">${m.itemName}</div>
        <div class="log-meta">
          <span>📁 ${m.cat}</span>
          ${m.resp ? `<span>👤 ${m.resp}</span>` : ''}
          ${m.obs  ? `<span>💬 ${m.obs}</span>`  : ''}
          <span>📅 ${weekLabel(m.week)}</span>
          <span>${m.prevQty} → ${m.newQty}</span>
        </div>
      </div>
      <div class="log-right">
        <div class="log-qty ${ti.cls}">${ti.label} ${m.qty}</div>
        <div class="log-time">${fmtDT(m.date)}</div>
      </div>
    </div>`;
  });
  html += '</div>';
  document.getElementById('historico-list').innerHTML = html;
}

/* ═══════════════════════════════
   RENDER: ALERTAS
═══════════════════════════════ */
function renderAlertas() {
  const lows = items.filter(i => itemStatus(i) !== 'ok').sort((a, b) => a.qty - b.qty);
  if (!lows.length) {
    document.getElementById('alertas-tbody').innerHTML =
      '<tr><td colspan="6"><div class="alert-banner ab-green" style="margin:16px"><span>✅</span><div>Todos os itens estão com estoque adequado.</div></div></td></tr>';
    return;
  }
  let html = '';
  lows.forEach(i => {
    html += `<tr>
      <td>${statusBadge(i)}</td>
      <td style="font-weight:500">${i.name}</td>
      <td><span class="badge b-gray">${i.cat}</span></td>
      <td style="font-family:var(--mono);font-weight:600;color:${itemStatus(i)==='critico'?'var(--red)':'var(--amber)'}">${i.qty}</td>
      <td style="font-family:var(--mono);color:var(--text3)">${i.min}</td>
      <td><button class="btn btn-ghost btn-xs" onclick="openMoveModal('${i.id}','entrada')">↑ Entrada</button></td>
    </tr>`;
  });
  document.getElementById('alertas-tbody').innerHTML = html;
}

/* ═══════════════════════════════
   FECHAMENTO SEMANAL
═══════════════════════════════ */
function renderFechamento() {
  const wk  = currentWeek();
  const prev = reports.find(r => r.week === wk);
  const el  = document.getElementById('fech-status');

  if (prev) {
    el.innerHTML = `<div class="alert-banner ab-green"><span>✅</span><div>
      Esta semana já possui um fechamento registrado em <strong>${fmtDT(prev.date)}</strong>
      ${prev.responsavel ? ` por <strong>${prev.responsavel}</strong>` : ''}.
      Você pode gerar um segundo registro se necessário.
    </div></div>`;
  } else {
    el.innerHTML = `<div class="alert-banner ab-blue"><span>📅</span><div>
      <strong>${weekLabel(wk)}</strong> — Nenhum fechamento realizado ainda esta semana.
    </div></div>`;
  }

  // Preview resumo semana
  const wkMovs = movements.filter(m => m.week === wk);
  const ent    = wkMovs.filter(m => m.tipo === 'entrada').reduce((s,m) => s + m.qty, 0);
  const sai    = wkMovs.filter(m => m.tipo === 'saida').reduce((s,m) => s + m.qty, 0);
  const adj    = wkMovs.filter(m => m.tipo === 'ajuste').length;
  const lows   = items.filter(i => itemStatus(i) !== 'ok');

  document.getElementById('fech-preview').innerHTML = `
    <div class="card">
      <div class="card-head"><span class="card-title">Prévia do Fechamento</span></div>
      <div class="card-body">
        <div class="stats-row">
          <div class="stat"><div class="stat-label">Movimentações</div><div class="stat-val blue">${wkMovs.length}</div></div>
          <div class="stat"><div class="stat-label">Entradas (total)</div><div class="stat-val green">${ent}</div></div>
          <div class="stat"><div class="stat-label">Saídas (total)</div><div class="stat-val red">${sai}</div></div>
          <div class="stat"><div class="stat-label">Ajustes manuais</div><div class="stat-val amber">${adj}</div></div>
          <div class="stat"><div class="stat-label">Itens c/ alerta</div><div class="stat-val ${lows.length?'red':'green'}">${lows.length}</div></div>
        </div>
      </div>
    </div>`;
}

function realizarFechamento() {
  const resp = document.getElementById('fech-resp').value.trim();
  const obs  = document.getElementById('fech-obs').value.trim();
  const wk   = currentWeek();

  if (!confirm(`Confirma o fechamento semanal de "${weekLabel(wk)}"?\n\nEsta ação gera um relatório permanente.`)) return;

  const wkMovs = movements.filter(m => m.week === wk);
  const ent    = wkMovs.filter(m => m.tipo === 'entrada').reduce((s,m) => s + m.qty, 0);
  const sai    = wkMovs.filter(m => m.tipo === 'saida').reduce((s,m) => s + m.qty, 0);
  const adj    = wkMovs.filter(m => m.tipo === 'ajuste').length;
  const lows   = items.filter(i => itemStatus(i) !== 'ok');

  const report = {
    id:          'r' + Date.now(),
    week:        wk,
    weekLabel:   weekLabel(wk),
    date:        new Date().toISOString(),
    responsavel: resp,
    obs,
    snapshot:    JSON.parse(JSON.stringify(items)),
    movements:   JSON.parse(JSON.stringify(wkMovs)),
    summary: {
      totalMovs: wkMovs.length,
      entradas:  ent,
      saidas:    sai,
      ajustes:   adj,
      lowItems:  lows.map(i => ({ name: i.name, cat: i.cat, qty: i.qty, min: i.min })),
    },
  };

  reports.unshift(report);
  ls_save();
  toast('✅ Fechamento realizado com sucesso!');
  nav('relatorios');
  renderReportList();
  viewReport(report.id);
}

/* ═══════════════════════════════
   RELATÓRIOS
═══════════════════════════════ */
function renderReportList() {
  const el = document.getElementById('report-list');
  if (!reports.length) {
    el.innerHTML = '<div class="empty"><div class="empty-icon">📂</div><div class="empty-text">Nenhum fechamento gerado ainda.</div></div>';
    return;
  }
  el.innerHTML = reports.map(r => `
    <div class="report-card" onclick="viewReport('${r.id}')" id="rc-${r.id}">
      <div class="report-card-body">
        <div class="report-wk">📊 ${r.weekLabel}</div>
        <div class="report-meta">${fmtDT(r.date)}${r.responsavel ? ' · ' + r.responsavel : ''}</div>
        <div class="report-pills">
          <span class="badge b-blue">${r.summary.totalMovs} movim.</span>
          <span class="badge b-green">↑${r.summary.entradas}</span>
          <span class="badge b-red">↓${r.summary.saidas}</span>
          ${r.summary.lowItems.length ? `<span class="badge b-amber">⚠ ${r.summary.lowItems.length}</span>` : ''}
        </div>
      </div>
    </div>`).join('');
}

function viewReport(id) {
  const r = reports.find(x => x.id === id);
  if (!r) return;

  document.querySelectorAll('.report-card').forEach(c => c.classList.remove('selected'));
  const rc = document.getElementById('rc-' + id);
  if (rc) rc.classList.add('selected');

  const allCats = [...new Set(r.snapshot.map(i => i.cat))].sort();

  // Tabela de estoque no fechamento
  let stockHtml = '';
  allCats.forEach(cat => {
    stockHtml += `<tr class="cat-sep"><td colspan="4">📁  ${cat}</td></tr>`;
    r.snapshot.filter(i => i.cat === cat).forEach(i => {
      const s = i.qty <= 0 ? 'red' : i.qty <= i.min ? 'amber' : 'green';
      stockHtml += `<tr>
        <td style="font-weight:500">${i.name}</td>
        <td style="font-family:var(--mono);font-weight:600;color:var(--${s})">${i.qty}</td>
        <td style="font-family:var(--mono);color:var(--text3)">${i.min}</td>
        <td>${i.qty<=0?'<span class="badge b-red">Zerado</span>':i.qty<=i.min?'<span class="badge b-amber">Baixo</span>':'<span class="badge b-green">OK</span>'}</td>
      </tr>`;
    });
  });

  // Tabela movimentações
  const tmap = {
    entrada: '<span style="color:var(--green);font-weight:600">↑ Entrada</span>',
    saida:   '<span style="color:var(--red);font-weight:600">↓ Saída</span>',
    ajuste:  '<span style="color:var(--amber);font-weight:600">✎ Ajuste</span>',
  };

  let movHtml = '';
  if (r.movements.length) {
    [...r.movements].reverse().forEach(m => {
      movHtml += `<tr>
        <td style="font-size:12px;font-family:var(--mono);color:var(--text3)">${fmtDT(m.date)}</td>
        <td style="font-weight:500">${m.itemName}</td>
        <td>${tmap[m.tipo]||m.tipo}</td>
        <td style="font-family:var(--mono)">${m.qty}</td>
        <td style="color:var(--text2)">${m.resp||'—'}</td>
        <td style="color:var(--text2);font-size:12px">${m.obs||'—'}</td>
      </tr>`;
    });
  } else {
    movHtml = '<tr><td colspan="6"><div class="empty" style="padding:20px"><div class="empty-text">Nenhuma movimentação nesta semana.</div></div></td></tr>';
  }

  // Itens baixos
  let lowHtml = '';
  if (r.summary.lowItems.length) {
    r.summary.lowItems.forEach(i => {
      lowHtml += `<tr>
        <td style="font-weight:500">${i.name}</td>
        <td><span class="badge b-gray">${i.cat}</span></td>
        <td style="font-family:var(--mono);font-weight:600;color:${i.qty<=0?'var(--red)':'var(--amber)'}">${i.qty}</td>
        <td style="font-family:var(--mono);color:var(--text3)">${i.min}</td>
      </tr>`;
    });
  } else {
    lowHtml = '<tr><td colspan="4"><div class="alert-banner ab-green" style="margin:12px"><span>✅</span><div>Nenhum item com estoque baixo no fechamento.</div></div></td></tr>';
  }

  document.getElementById('report-view').innerHTML = `
    <div class="card">
      <div class="card-head">
        <div>
          <div style="font-size:18px;font-weight:700;color:var(--green)">${r.weekLabel}</div>
          <div style="font-size:12px;color:var(--text2);margin-top:3px">
            Fechado em ${fmtDT(r.date)}${r.responsavel ? '  ·  👤 ' + r.responsavel : ''}
          </div>
          ${r.obs ? `<div style="font-size:12px;color:var(--text2);margin-top:2px">📝 ${r.obs}</div>` : ''}
        </div>
        <button class="btn btn-ghost btn-sm" onclick="window.print()">🖨 Imprimir</button>
      </div>

      <div class="card-body">

        <div class="rpt-section">
          <div class="rpt-section-title">Resumo da Semana</div>
          <div class="stats-row">
            <div class="stat"><div class="stat-label">Movimentações</div><div class="stat-val blue">${r.summary.totalMovs}</div></div>
            <div class="stat"><div class="stat-label">Total Entradas</div><div class="stat-val green">${r.summary.entradas}</div></div>
            <div class="stat"><div class="stat-label">Total Saídas</div><div class="stat-val red">${r.summary.saidas}</div></div>
            <div class="stat"><div class="stat-label">Ajustes manuais</div><div class="stat-val amber">${r.summary.ajustes}</div></div>
            <div class="stat"><div class="stat-label">Itens c/ alerta</div><div class="stat-val ${r.summary.lowItems.length?'red':'green'}">${r.summary.lowItems.length}</div></div>
          </div>
        </div>

        <div class="rpt-section">
          <div class="rpt-section-title">Estoque no Fechamento</div>
          <div class="tbl-wrap">
            <table>
              <thead><tr><th>Material</th><th>Qtd.</th><th>Mín.</th><th>Status</th></tr></thead>
              <tbody>${stockHtml}</tbody>
            </table>
          </div>
        </div>

        <div class="rpt-section">
          <div class="rpt-section-title">Movimentações da Semana</div>
          <div class="tbl-wrap">
            <table>
              <thead><tr><th>Data/Hora</th><th>Material</th><th>Tipo</th><th>Qtd.</th><th>Responsável</th><th>Obs.</th></tr></thead>
              <tbody>${movHtml}</tbody>
            </table>
          </div>
        </div>

        <div class="rpt-section">
          <div class="rpt-section-title">Itens com Estoque Baixo ou Zerado</div>
          <div class="tbl-wrap">
            <table>
              <thead><tr><th>Material</th><th>Categoria</th><th>Qtd.</th><th>Mínimo</th></tr></thead>
              <tbody>${lowHtml}</tbody>
            </table>
          </div>
        </div>

      </div>
    </div>`;
}

/* ═══════════════════════════════
   CADASTRO
═══════════════════════════════ */
function cadastrar() {
  const nome = document.getElementById('cad-nome').value.trim();
  const cat  = document.getElementById('cad-cat').value;
  const unit = document.getElementById('cad-unit').value.trim() || 'un';
  const qty  = +document.getElementById('cad-qty').value || 0;
  const min  = +document.getElementById('cad-min').value || 5;

  if (!nome || !cat) { toast('Nome e categoria são obrigatórios.', 'red'); return; }

  const item = { id: 'i' + Date.now(), name: nome, cat, unit, qty, min };
  items.push(item);
  if (qty > 0) addMov(item.id, 'entrada', qty, 'Estoque inicial no cadastro', 'Cadastro', 0);
  ls_save();
  populateCatSelects();

  // reset
  ['cad-nome','cad-unit'].forEach(id => document.getElementById(id).value = '');
  document.getElementById('cad-cat').value = '';
  document.getElementById('cad-qty').value = '0';
  document.getElementById('cad-min').value = '5';

  toast(`"${nome}" cadastrado com sucesso.`);
  nav('estoque');
}

/* ═══════════════════════════════
   EXPORT CSV
═══════════════════════════════ */
function exportCSV() {
  const rows = [['Material','Categoria','Quantidade','Unidade','Estoque Mínimo','Status']];
  items.forEach(i => rows.push([`"${i.name}"`, i.cat, i.qty, i.unit||'un', i.min, itemStatus(i)]));
  const csv = rows.map(r => r.join(',')).join('\n');
  const blob = new Blob(['\uFEFF' + csv], { type: 'text/csv;charset=utf-8;' });
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = `estoque_${new Date().toISOString().split('T')[0]}.csv`;
  a.click();
}

/* ═══════════════════════════════
   MODAL
═══════════════════════════════ */
function closeModal(id) {
  document.getElementById(id).classList.remove('open');
}

document.querySelectorAll('.overlay').forEach(o => {
  o.addEventListener('click', e => { if (e.target === o) o.classList.remove('open'); });
});

/* ═══════════════════════════════
   TOAST
═══════════════════════════════ */
function toast(msg, type) {
  const t = document.createElement('div');
  t.className = 'toast';
  t.textContent = msg;
  if (type === 'red') t.style.background = 'var(--red)';
  document.getElementById('toasts').appendChild(t);
  setTimeout(() => t.remove(), 3500);
}

/* ═══════════════════════════════
   TOPBAR WEEK LABEL
═══════════════════════════════ */
function setWeekUI() {
  const wl = weekLabel(currentWeek());
  document.getElementById('tb-week').textContent    = wl;
  document.getElementById('rf-week').textContent    = wl;
  document.getElementById('rf-date').textContent    = new Date().toLocaleDateString('pt-BR', { weekday:'long', day:'2-digit', month:'long' });
}

/* ═══════════════════════════════
   INIT
═══════════════════════════════ */
function init() {
  ls_load();
  setWeekUI();
  populateCatSelects();
  populateItemSelect('mv-item');
  renderEstoque();
}

init();
</script>
</body>
</html>
