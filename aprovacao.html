<!doctype html>
<html lang="pt-BR">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Títulos • Aprovação (Admin)</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/xlsx@0.18.5/dist/xlsx.full.min.js"></script>
<style>
  :root{
    --bg:#0f0f10; --card:#151515; --line:#2a2a2a; --text:#f6f6f6; --muted:#cfcfcf;
    --brand:#2563eb; --ok:#16a34a; --danger:#ef4444; --warn:#f59e0b;
  }
  *{box-sizing:border-box}
  body{margin:0;background:var(--bg);color:var(--text);font-family:Inter,system-ui,Arial,sans-serif}
  header{padding:16px 20px;border-bottom:1px solid var(--line);display:flex;gap:16px;align-items:center;justify-content:space-between}
  h1{margin:0;font-size:18px;font-weight:800;letter-spacing:.2px}
  .actions{display:flex;gap:8px;flex-wrap:wrap}
  button.btn{display:inline-flex;gap:8px;align-items:center;justify-content:center;padding:10px 14px;border-radius:10px;border:1px solid var(--line);background:#1a1a1a;color:var(--text);cursor:pointer;font-weight:600}
  .btn.primary{background:var(--brand);border-color:#1f4fd1}
  .btn.ghost{background:#111;border-color:#232323}
  .btn.ok{background:var(--ok);border-color:#0d6a28}
  .btn.danger{background:var(--danger);border-color:#b71c1c}
  .btn.warn{background:var(--warn);border-color:#a16207}
  main{padding:16px}
  .row{display:grid;gap:12px}
  @media(min-width:1100px){ .row{grid-template-columns: .9fr 1.1fr} }
  .card{background:var(--card);border:1px solid var(--line);border-radius:14px;margin-bottom:12px}
  .card h2{margin:0;padding:12px 14px;border-bottom:1px solid var(--line);font-size:14px;font-weight:700}
  .card .content{padding:12px 14px}
  select,input[type="text"],input[type="password"],input[type="date"]{width:100%;background:#121212;border:1px solid var(--line);border-radius:10px;color:var(--text);padding:10px}
  table{width:100%;border-collapse:collapse}
  th,td{border-bottom:1px solid var(--line);padding:10px 8px;font-size:13px}
  th{color:var(--muted);text-align:left}
  .right{text-align:right}
  .muted{color:var(--muted)}
  .inline{display:flex;flex-wrap:wrap;gap:10px;align-items:center}
  .status{padding:2px 8px;border-radius:999px;font-size:12px;border:1px solid #2d2d2d;display:inline-block}
  .PENDENTE{background:#111}
  .APROVADO{background:#0f2; color:#041}
  .NEGADO{background:#f203; color:#fbb}
  .CONTESTADO{background:#fd03; color:#320}
</style>
</head>
<body>
<header>
  <h1>Títulos • <span class="muted">Aprovação (Admin)</span></h1>
  <div class="actions">
    <button id="btnExportCSV" class="btn">Exportar CSV</button>
    <button id="btnExportXLSX" class="btn">Exportar XLSX</button>
  </div>
</header>

<main>
  <section class="card" id="authCard">
    <h2>Autenticação</h2>
    <div class="content inline">
      <input id="adminUser" type="text" placeholder="Usuário">
      <input id="adminPass" type="password" placeholder="Senha (padrão: adm123)">
      <button id="btnLogin" class="btn primary">Entrar</button>
      <span class="muted">* Proteção de interface (não substitui controle de acesso no servidor).</span>
    </div>
  </section>

  <section class="card" id="panel" style="display:none">
    <h2>Filtros</h2>
    <div class="content">
      <div class="row">
        <div>
          <label class="muted">Empresa</label>
          <input id="fEmpresa" list="empresas">
          <datalist id="empresas"></datalist>
        </div>
        <div>
          <label class="muted">Status</label>
          <select id="fStatus">
            <option value="">(Todos)</option>
            <option>PENDENTE</option>
            <option>APROVADO</option>
            <option>NEGADO</option>
            <option>CONTESTADO</option>
          </select>
        </div>
      </div>

      <div class="inline" style="margin-top:8px">
        <button id="btnFiltrar" class="btn">Aplicar Filtros</button>
        <button id="btnReset" class="btn ghost">Limpar</button>
      </div>
    </div>
  </section>

  <section class="card" id="listCard" style="display:none">
    <h2>Lista de Títulos</h2>
    <div class="content">
      <div class="inline" style="justify-content:space-between;margin-bottom:8px">
        <div class="muted" id="infoCount">0 registros</div>
        <div class="actions">
          <button id="btnSelAll" class="btn ghost">Selecionar todos</button>
          <button id="btnAprovarSel" class="btn ok">Aprovar selecionados</button>
          <button id="btnNegarSel" class="btn danger">Negar selecionados</button>
          <button id="btnContestarSel" class="btn warn">Contestar selecionados</button>
        </div>
      </div>
      <div style="max-height:60vh;overflow:auto;border:1px solid var(--line);border-radius:10px">
        <table id="tbl">
          <thead>
            <tr>
              <th><input type="checkbox" id="chkAll"></th>
              <th>Empresa</th>
              <th>Fornecedor</th>
              <th>Vencimento</th>
              <th>Meio de Pagamento</th>
              <th>Histórico</th>
              <th>Status</th>
              <th>Ações</th>
            </tr>
          </thead>
          <tbody></tbody>
        </table>
      </div>
    </div>
  </section>
</main>

<script>
const KEY='titulos_pendentes_v1';
const ADMIN_PASSWORD='adm123'; // troque aqui se quiser

let USER=null;
let LIST=[];     // lista completa do storage
let VIEW=[];     // após filtros

document.getElementById('btnLogin').addEventListener('click', ()=>{
  const u=document.getElementById('adminUser').value.trim();
  const p=document.getElementById('adminPass').value.trim();
  if(!u||!p){ alert('Informe usuário e senha.'); return; }
  if(p!==ADMIN_PASSWORD){ alert('Senha incorreta.'); return; }
  USER=u;
  document.getElementById('authCard').style.display='none';
  document.getElementById('panel').style.display='';
  document.getElementById('listCard').style.display='';
  load();
});

function load(){
  LIST = JSON.parse(localStorage.getItem(KEY)||'[]');
  fillEmpresaDatalist(LIST);
  VIEW=[...LIST];
  render();
}

function fillEmpresaDatalist(arr){
  const d=document.getElementById('empresas'); d.innerHTML='';
  const set=new Set(arr.map(x=>x.empresa).filter(Boolean));
  [...set].sort().forEach(e=>{
    const opt=document.createElement('option'); opt.value=e; d.appendChild(opt);
  });
}

document.getElementById('btnFiltrar').addEventListener('click', ()=>{
  const emp=document.getElementById('fEmpresa').value.trim();
  const st =document.getElementById('fStatus').value;
  VIEW = LIST.filter(x=>{
    if(emp && x.empresa!==emp) return false;
    if(st && x.status!==st) return false;
    return true;
  });
  render();
});

document.getElementById('btnReset').addEventListener('click', ()=>{
  document.getElementById('fEmpresa').value='';
  document.getElementById('fStatus').value='';
  VIEW=[...LIST];
  render();
});

function render(){
  const tbody=document.querySelector('#tbl tbody'); tbody.innerHTML='';
  document.getElementById('infoCount').textContent = `${VIEW.length} registros`;
  VIEW.forEach(x=>{
    const tr=document.createElement('tr');
    tr.innerHTML = `
      <td><input type="checkbox" class="rowchk" data-id="${x.id}"></td>
      <td>${esc(x.empresa)}</td>
      <td>${esc(x.fornecedor)}</td>
      <td>${fmtBR(x.vencimento)}</td>
      <td>${esc(x.meioPagamento)}</td>
      <td>${esc(x.historico)}</td>
      <td><span class="status ${x.status}">${x.status}</span></td>
      <td class="actions">
        <button class="btn ok" data-act="ap" data-id="${x.id}">Aprovar</button>
        <button class="btn danger" data-act="ng" data-id="${x.id}">Negar</button>
        <button class="btn warn" data-act="ct" data-id="${x.id}">Contestar</button>
      </td>
    `;
    tbody.appendChild(tr);
  });
  hookRowButtons();
  document.getElementById('chkAll').checked=false;
}

function hookRowButtons(){
  document.querySelectorAll('#tbl .actions .btn').forEach(b=>{
    b.addEventListener('click', ()=>{
      const id=b.dataset.id;
      if(b.dataset.act==='ap') updateStatus(id,'APROVADO','');
      if(b.dataset.act==='ng') updateStatus(id,'NEGADO', prompt('Motivo (opcional):')||'');
      if(b.dataset.act==='ct'){
        const d=prompt('Descreva a contestação:');
        if(d==null) return;
        updateStatus(id,'CONTESTADO', d.trim());
      }
    });
  });
  const chkAll=document.getElementById('chkAll');
  chkAll.addEventListener('change', ()=>{
    document.querySelectorAll('.rowchk').forEach(c=>c.checked=chkAll.checked);
  });
  document.getElementById('btnSelAll').onclick=()=>{ chkAll.checked=true; chkAll.dispatchEvent(new Event('change')); };

  document.getElementById('btnAprovarSel').onclick=()=>bulkUpdate('APROVADO','');
  document.getElementById('btnNegarSel').onclick=()=>bulkUpdate('NEGADO', prompt('Motivo para negar (opcional):')||'');
  document.getElementById('btnContestarSel').onclick=()=>{
    const d=prompt('Descrição da contestação:');
    if(d==null) return;
    bulkUpdate('CONTESTADO', d.trim());
  };
}

function bulkUpdate(status, desc){
  const ids=[...document.querySelectorAll('.rowchk:checked')].map(c=>c.dataset.id);
  if(!ids.length){ alert('Selecione ao menos um título.'); return; }
  ids.forEach(id=>updateStatus(id,status,desc,true));
  persist();
  render();
}

function updateStatus(id,status,desc, silent){
  const i = LIST.findIndex(x=>x.id===id);
  if(i<0) return;
  LIST[i].status = status;
  LIST[i].statusDesc = desc||'';
  LIST[i].statusWhen = new Date().toISOString();
  LIST[i].statusUser = USER;
  if(!silent){ persist(); render(); }
}

function persist(){
  localStorage.setItem(KEY, JSON.stringify(LIST));
}

/* EXPORTS */
document.getElementById('btnExportCSV').addEventListener('click', ()=>{
  const arr = LIST;
  const out = [['Empresa','Fornecedor','Vencimento','Meio de Pagamento','Histórico','Status','Descrição Status','Data Status','Usuário']];
  arr.forEach(x=>out.push([x.empresa,x.fornecedor,x.vencimento,x.meioPagamento,x.historico,x.status,x.statusDesc||'',x.statusWhen||'',x.statusUser||'']));
  const csv = out.map(r=>r.map(s=>{
    s=String(s??'');
    return /[",;\n]/.test(s)?`"${s.replace(/"/g,'""')}"`:s;
  }).join(';')).join('\n');
  download(csv, 'titulos_aprovacao.csv', 'text/csv');
});

document.getElementById('btnExportXLSX').addEventListener('click', ()=>{
  const arr = LIST;
  const aoa = [['Empresa','Fornecedor','Vencimento','Meio de Pagamento','Histórico','Status','Descrição Status','Data Status','Usuário']];
  arr.forEach(x=>aoa.push([x.empresa,x.fornecedor,x.vencimento,x.meioPagamento,x.historico,x.status,x.statusDesc||'',x.statusWhen||'',x.statusUser||'']));
  const ws = XLSX.utils.aoa_to_sheet(aoa);
  const wb = XLSX.utils.book_new(); XLSX.utils.book_append_sheet(wb, ws, 'Aprovação');
  XLSX.writeFile(wb, 'titulos_aprovacao.xlsx');
});

/* UTILS */
function esc(s){ return String(s||'').replace(/[&<>"']/g, m=>({ '&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#039;' }[m])); }
function fmtBR(s){ if(!s) return ''; const [y,m,d]=s.split('-'); return `${d}/${m}/${y}`; }
function download(text, name, mime){ const blob=new Blob([text],{type:mime}); const a=document.createElement('a'); a.href=URL.createObjectURL(blob); a.download=name; a.click(); URL.revokeObjectURL(a.href); }
</script>
</body>
</html>
