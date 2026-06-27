<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no"/>
<meta name="theme-color" content="#060a12"/>
<meta name="mobile-web-app-capable" content="yes"/>
<meta name="apple-mobile-web-app-capable" content="yes"/>
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent"/>
<meta name="apple-mobile-web-app-title" content="LocaFácil"/>
<title>LocaFácil</title>
<style>
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
body{background:#060a12;color:#eef0ff;font-family:'Inter',system-ui,sans-serif;min-height:100vh;padding-bottom:80px}
button{cursor:pointer;font-family:inherit;border:none;transition:all .18s}
button:active{opacity:.72;transform:scale(.96)}
input,select,textarea{font-family:inherit;outline:none;transition:border-color .2s}
::-webkit-scrollbar{width:3px}
::-webkit-scrollbar-thumb{background:#1e2845;border-radius:3px}

/* ── HEADER ── */
#header{background:#090e1cee;backdrop-filter:blur(18px);border-bottom:1px solid #141e38;padding:13px 16px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:30}
.h-logo{width:38px;height:38px;background:linear-gradient(135deg,#0d5c32,#18a558);border-radius:11px;display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0}
.h-titles{margin-left:10px}
.h-name{font-weight:800;font-size:16px;letter-spacing:-.4px}
.h-sub{font-size:10px;color:#4a5880;margin-top:1px}
.h-clock{text-align:right}
.h-time{font-size:15px;font-weight:800;color:#18a558}
.h-date{font-size:10px;color:#4a5880;margin-top:1px}

/* ── NAV ── */
#nav{position:fixed;bottom:0;left:0;right:0;background:#090e1cee;backdrop-filter:blur(18px);border-top:1px solid #141e38;display:flex;justify-content:space-around;padding:7px 0 13px;z-index:30}
.nb{background:none;border:none;display:flex;flex-direction:column;align-items:center;gap:3px;padding:3px 8px;color:#2e3a58;font-size:9px;font-weight:700;letter-spacing:.4px;min-width:52px}
.nb .ni{font-size:21px;transition:transform .2s}
.nb.active{color:#18a558}
.nb.active .ni{transform:scale(1.12)}

/* ── CONTENT ── */
#app{padding:14px 14px 0;max-width:520px;margin:0 auto}

/* ── CARDS ── */
.card{background:#0c1222;border:1px solid #141e38;border-radius:16px}
.card-p{padding:14px}

/* ── STAT GRID ── */
.sg{display:grid;grid-template-columns:1fr 1fr;gap:9px;margin-bottom:16px}
.sc{background:#0c1222;border:1px solid #141e38;border-radius:15px;padding:13px}
.sc-ic{width:34px;height:34px;border-radius:9px;display:flex;align-items:center;justify-content:center;font-size:15px;margin-bottom:9px}
.sc-lb{font-size:10px;color:#4a5880;font-weight:600;margin-bottom:3px;letter-spacing:.2px}
.sc-vl{font-size:19px;font-weight:900;letter-spacing:-.5px}

/* ── LIST ITEM ── */
.li{background:#0c1222;border:1px solid #141e38;border-radius:14px;padding:13px;margin-bottom:8px;cursor:pointer;transition:border-color .2s,transform .15s}
.li:active{border-color:#18a558;transform:scale(.99)}
.li.red{border-color:#f8717155}
.li.yellow{border-color:#fbbf2455}
.li-row{display:flex;align-items:center;gap:11px}
.li-ic{width:44px;height:44px;border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0}
.li-info{flex:1;min-width:0}
.li-name{font-weight:700;font-size:14px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.li-sub{font-size:11px;color:#4a5880;margin-top:2px}
.li-right{text-align:right;flex-shrink:0}
.li-val{font-weight:800;font-size:14px}
.li-meta{font-size:10px;color:#4a5880;margin-top:2px}

/* ── PROGRESS ── */
.pb{background:#141e38;border-radius:4px;height:4px;overflow:hidden;margin-top:9px}
.pf{height:100%;border-radius:4px;transition:width .5s}
.pl{display:flex;justify-content:space-between;font-size:9px;color:#4a5880;margin-top:3px}

/* ── BADGE ── */
.bdg{border-radius:20px;padding:3px 9px;font-size:10px;font-weight:700;display:inline-block}
.bg{background:#18a55820;color:#18a558;border:1px solid #18a55840}
.br{background:#f8717120;color:#f87171;border:1px solid #f8717140}
.by{background:#fbbf2420;color:#fbbf24;border:1px solid #fbbf2440}
.bb{background:#4f8ef720;color:#4f8ef7;border:1px solid #4f8ef740}
.bgr{background:#3a456020;color:#8890b0;border:1px solid #3a456040}

/* ── SEC HEADER ── */
.sh{display:flex;align-items:center;justify-content:space-between;margin-bottom:12px}
.sh h2{font-size:18px;font-weight:800;letter-spacing:-.3px}
.st{font-size:10px;font-weight:700;color:#4a5880;letter-spacing:.8px;margin:14px 0 8px}

/* ── MODAL ── */
#ov{display:none;position:fixed;inset:0;background:#00000099;z-index:50;align-items:flex-end;justify-content:center}
#ov.open{display:flex}
#mb{background:#090e1c;border:1px solid #141e38;border-radius:22px 22px 0 0;width:100%;max-width:520px;max-height:94vh;overflow-y:auto;padding:18px 16px 40px}
.mh{width:38px;height:4px;background:#1a2440;border-radius:2px;margin:0 auto 16px}
.mt{font-size:18px;font-weight:800;margin-bottom:16px;letter-spacing:-.3px}

/* ── FORM ── */
.f{margin-bottom:13px}
.f label{display:block;font-size:10px;color:#4a5880;font-weight:700;letter-spacing:.5px;margin-bottom:5px}
.f input,.f select,.f textarea{width:100%;background:#060a12;border:1.5px solid #141e38;border-radius:11px;padding:11px 12px;color:#eef0ff;font-size:14px}
.f input:focus,.f select:focus,.f textarea:focus{border-color:#18a558}
.f select option{background:#060a12}
.f textarea{resize:none;height:76px;line-height:1.5}
.fr{display:grid;grid-template-columns:1fr 1fr;gap:10px}

/* ── BUTTONS ── */
.bp{background:linear-gradient(135deg,#0d5c32,#18a558);color:#fff;border-radius:12px;padding:13px;width:100%;font-size:15px;font-weight:700;box-shadow:0 4px 18px #18a55830}
.by2{background:linear-gradient(135deg,#92400e,#d97706);color:#fff;border-radius:12px;padding:13px;width:100%;font-size:15px;font-weight:700;margin-top:8px}
.bg2{background:#141e38;color:#eef0ff;border-radius:11px;padding:10px 14px;font-size:13px;font-weight:600}
.bd{background:#f8717115;color:#f87171;border:1px solid #f8717140;border-radius:12px;padding:12px;width:100%;font-size:13px;font-weight:600;margin-top:9px}
.br2{background:#4f8ef715;color:#4f8ef7;border:1px solid #4f8ef740;border-radius:12px;padding:12px;width:100%;font-size:13px;font-weight:600;margin-top:8px}

/* ── DETAIL ── */
.dc{background:#0c1222;border:1px solid #141e38;border-radius:13px;padding:13px;margin-bottom:11px}
.dr{display:flex;justify-content:space-between;align-items:flex-start;padding:6px 0;border-bottom:1px solid #141e3833}
.dr:last-child{border-bottom:none}
.dl{font-size:12px;color:#4a5880}
.dv{font-size:12px;font-weight:600;color:#eef0ff;text-align:right;max-width:58%}

/* ── SUMMARY ── */
.sb{background:#071410;border:1px solid #0d3022;border-radius:13px;padding:13px;margin-bottom:11px}
.sbt{font-size:10px;color:#18a558;font-weight:700;letter-spacing:.5px;margin-bottom:9px}

/* ── PHOTO ── */
.pg{display:grid;grid-template-columns:repeat(3,1fr);gap:7px;margin-top:7px}
.pt{width:100%;aspect-ratio:1;border-radius:9px;object-fit:cover;border:1px solid #141e38}
.pa{width:100%;aspect-ratio:1;border-radius:9px;background:#141e38;border:1.5px dashed #253060;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:3px;cursor:pointer;font-size:20px;color:#4a5880}
.pa span{font-size:9px}

/* ── TIMELINE ── */
.tl-item{display:flex;gap:12px;margin-bottom:14px}
.tl-dot{display:flex;flex-direction:column;align-items:center;gap:0}
.tl-circle{width:12px;height:12px;border-radius:50%;flex-shrink:0;margin-top:3px}
.tl-line{width:2px;flex:1;background:#141e38;margin:4px 0}
.tl-content{flex:1;background:#0c1222;border:1px solid #141e38;border-radius:12px;padding:11px;margin-bottom:2px}
.tl-name{font-weight:700;font-size:13px}
.tl-period{font-size:11px;color:#4a5880;margin-top:2px}
.tl-val{font-size:13px;font-weight:800;color:#18a558;margin-top:4px}

/* ── CHART ── */
.chart-bars{display:flex;align-items:flex-end;gap:5px;height:80px}
.chart-bar{flex:1;border-radius:4px 4px 0 0;transition:height .5s;min-height:4px}
.chart-label{font-size:9px;color:#4a5880;text-align:center;margin-top:4px}

/* ── OCUPACAO ── */
.ocp-bar{height:8px;border-radius:4px;background:#141e38;overflow:hidden;margin-top:6px}
.ocp-fill{height:100%;border-radius:4px;background:linear-gradient(90deg,#0d5c32,#18a558)}

/* ── TIPO TAG ── */
.tt{font-size:9px;font-weight:700;color:#18a558;background:#18a55815;border:1px solid #18a55830;border-radius:5px;padding:2px 6px;display:inline-block;margin-bottom:5px}

/* ── AVISO ── */
.aviso{background:#3a1a0a;border:1px solid #f8717140;border-radius:10px;padding:10px 12px;font-size:12px;color:#f87171;margin-bottom:11px}

/* ── EMPTY ── */
.empty{text-align:center;padding:44px 20px;color:#2e3a58}
.empty-ic{font-size:44px;margin-bottom:10px;opacity:.4}
.empty-tx{font-size:13px}

/* ── TOAST ── */
#toast{position:fixed;bottom:92px;left:50%;transform:translateX(-50%);background:#0d5c32;color:#fff;padding:9px 20px;border-radius:20px;font-weight:700;font-size:12px;opacity:0;pointer-events:none;transition:opacity .3s;z-index:100;white-space:nowrap;box-shadow:0 4px 18px #18a55840}
#toast.show{opacity:1}

/* ── VIEW TABS ── */
.vt{display:flex;background:#0c1222;border:1px solid #141e38;border-radius:12px;padding:3px;margin-bottom:14px;gap:3px}
.vt-btn{flex:1;padding:8px;border-radius:9px;font-size:11px;font-weight:700;color:#4a5880;background:none;border:none}
.vt-btn.active{background:#0d3022;color:#18a558}

/* ── ESTOQUE BADGE ── */
.est-badge{display:inline-flex;align-items:center;gap:4px;background:#141e38;border-radius:8px;padding:3px 8px;font-size:11px;font-weight:700;color:#eef0ff}
</style>
</head>
<body>

<div id="header">
  <div style="display:flex;align-items:center">
    <div class="h-logo">🏠</div>
    <div class="h-titles">
      <div class="h-name">LocaFácil</div>
      <div class="h-sub">Gestão de aluguéis e locações</div>
    </div>
  </div>
  <div class="h-clock">
    <div class="h-time" id="htime"></div>
    <div class="h-date" id="hdate"></div>
  </div>
</div>

<div id="app"></div>

<nav id="nav">
  <button class="nb active" onclick="go('dash')" id="t-dash"><span class="ni">🏠</span>Início</button>
  <button class="nb" onclick="go('imoveis')" id="t-imoveis"><span class="ni">🏘️</span>Imóveis</button>
  <button class="nb" onclick="go('itens')" id="t-itens"><span class="ni">📦</span>Itens</button>
  <button class="nb" onclick="go('clientes')" id="t-clientes"><span class="ni">👥</span>Clientes</button>
  <button class="nb" onclick="go('fin')" id="t-fin"><span class="ni">📊</span>Financeiro</button>
</nav>

<div id="ov" onclick="closeModal()">
  <div id="mb" onclick="event.stopPropagation()">
    <div class="mh"></div>
    <div id="mc"></div>
  </div>
</div>
<div id="toast"></div>

<script>
// ══════════════════════════════════════════════════════
//  STATE
// ══════════════════════════════════════════════════════
let S = JSON.parse(localStorage.getItem('lf2') || 'null') || {
  clientes:[],   // {id,nome,telefone,cpf,email,obs,foto}
  imoveis:[],    // {id,endereco,tipo,descricao,fotos[],status:'disponivel'|'ocupado'|'manutencao'}
  itens:[],      // {id,nome,categoria,descricao,qtdTotal,fotos[],status}
  contratos:[],  // {id,tipo:'imovel'|'item',refId,clienteId,dataInicio,dataFim,valor,tipoCob,periodo,obs,fotosEntrada[],fotosSaida[],status:'ativo'|'encerrado',pagamentos[{data,valor,obs}],despesas[{data,valor,desc}]}
  nextId:1
};
let view='dash', calOff=0, _fotos=[], _fotos2=[];

function sv(){localStorage.setItem('lf2',JSON.stringify(S));}
function nid(){return S.nextId++;}

// ══════════════════════════════════════════════════════
//  HELPERS
// ══════════════════════════════════════════════════════
const R=v=>Number(v||0).toLocaleString('pt-BR',{style:'currency',currency:'BRL'});
const FD=s=>{if(!s)return'—';const[y,m,d]=s.split('-');return`${d}/${m}/${y}`;};
const TD=()=>new Date().toISOString().split('T')[0];
const MO=s=>s?s.slice(0,7):'';
const CM=()=>new Date().toISOString().slice(0,7);

const gc=id=>S.clientes.find(x=>x.id===Number(id));
const gi=id=>S.imoveis.find(x=>x.id===Number(id));
const git=id=>S.itens.find(x=>x.id===Number(id));
const gct=id=>S.contratos.find(x=>x.id===Number(id));

function diffDias(a,b){return Math.round((new Date(b)-new Date(a))/(86400000));}

function totalPagoC(c){return(c.pagamentos||[]).reduce((s,p)=>s+Number(p.valor),0);}
function totalDespC(c){return(c.despesas||[]).reduce((s,d)=>s+Number(d.valor),0);}
function lucroC(c){return totalPagoC(c)-totalDespC(c);}

function contratosAtivos(refId,tipo){return S.contratos.filter(c=>c.refId===Number(refId)&&c.tipo===tipo&&c.status==='ativo');}
function contratoAtivoImovel(refId){const a=contratosAtivos(refId,'imovel');return a.length>0?a[0]:null;}

function pagoMesAtual(contratoId){
  const c=gct(contratoId); if(!c) return false;
  return (c.pagamentos||[]).some(p=>MO(p.data)===CM());
}

function isVencidoHoje(c){
  if(c.tipo!=='imovel'||c.status!=='ativo') return false;
  const dia=new Date().getDate();
  return c.periodo===dia&&!pagoMesAtual(c.id);
}

function ocupacaoPct(refId,tipo){
  const cts=S.contratos.filter(c=>c.refId===Number(refId)&&c.tipo===tipo);
  if(cts.length===0) return 0;
  const inicio=cts.reduce((mn,c)=>c.dataInicio<mn?c.dataInicio:mn,cts[0].dataInicio);
  const totalDias=diffDias(inicio,TD());
  if(totalDias<=0) return 0;
  const ocupDias=cts.reduce((s,c)=>{
    const fim=c.dataFim&&c.dataFim<TD()?c.dataFim:TD();
    return s+Math.max(0,diffDias(c.dataInicio,fim));
  },0);
  return Math.min(100,Math.round(ocupDias/totalDias*100));
}

function avt(c,sz=40){
  if(c?.foto) return `<img src="${c.foto}" style="width:${sz}px;height:${sz}px;border-radius:50%;object-fit:cover;border:2px solid #141e38;flex-shrink:0"/>`;
  const l=c?.nome?.[0]?.toUpperCase()||'?';
  return `<div style="width:${sz}px;height:${sz}px;border-radius:50%;background:#0d3022;color:#18a558;display:flex;align-items:center;justify-content:center;font-weight:800;font-size:${Math.round(sz*.38)}px;flex-shrink:0">${l}</div>`;
}

function bdg(st){
  const m={ativo:'bg Ativo',encerrado:'bgr Encerrado',disponivel:'bb Disponível',ocupado:'by Em uso',manutencao:'br Manutenção',atrasado:'br Atrasado',pago:'bg Pago'};
  const[cls,lb]=(m[st]||'bgr '+st).split(' ');
  return `<span class="bdg ${cls}">${lb}</span>`;
}

// ══════════════════════════════════════════════════════
//  CLOCK
// ══════════════════════════════════════════════════════
function tick(){
  const d=new Date();
  const dias=['Dom','Seg','Ter','Qua','Qui','Sex','Sáb'];
  const meses=['Jan','Fev','Mar','Abr','Mai','Jun','Jul','Ago','Set','Out','Nov','Dez'];
  document.getElementById('htime').textContent=`${String(d.getHours()).padStart(2,'0')}:${String(d.getMinutes()).padStart(2,'0')}`;
  document.getElementById('hdate').textContent=`${dias[d.getDay()]}, ${d.getDate()} ${meses[d.getMonth()]}`;
}

// ══════════════════════════════════════════════════════
//  NAVIGATION
// ══════════════════════════════════════════════════════
function go(v){
  view=v;
  document.querySelectorAll('.nb').forEach(b=>b.classList.remove('active'));
  document.getElementById('t-'+v)?.classList.add('active');
  render();
}
function render(){
  const el=document.getElementById('app');
  if(view==='dash') el.innerHTML=renderDash();
  else if(view==='imoveis') el.innerHTML=renderImoveis();
  else if(view==='itens') el.innerHTML=renderItens();
  else if(view==='clientes') el.innerHTML=renderClientes();
  else if(view==='fin') el.innerHTML=renderFin();
}

// ══════════════════════════════════════════════════════
//  DASHBOARD
// ══════════════════════════════════════════════════════
function renderDash(){
  const m=CM();
  const ctAtivos=S.contratos.filter(c=>c.status==='ativo');
  const imOcup=S.imoveis.filter(im=>im.status==='ocupado').length;
  const itOcup=S.itens.filter(it=>it.status==='ocupado').length;
  const recMes=S.contratos.reduce((s,c)=>{return s+(c.pagamentos||[]).filter(p=>MO(p.data)===m).reduce((a,p)=>a+Number(p.valor),0);},0);
  const despMes=S.contratos.reduce((s,c)=>{return s+(c.despesas||[]).filter(d=>MO(d.data)===m).reduce((a,d)=>a+Number(d.valor),0);},0);
  const aRecMes=ctAtivos.filter(c=>c.tipo==='imovel').reduce((s,c)=>s+(pagoMesAtual(c.id)?0:Number(c.valor)),0);
  const atrasados=ctAtivos.filter(c=>isVencidoHoje(c));
  const valorAt=atrasados.reduce((s,c)=>s+Number(c.valor),0);

  // calendário
  const calD=new Date(); calD.setDate(calD.getDate()+calOff);
  const calStr=calD.toISOString().split('T')[0];
  const calDayNum=calD.getDate();
  const dias2=['Dom','Seg','Ter','Qua','Qui','Sex','Sáb'];
  const meses2=['Janeiro','Fevereiro','Março','Abril','Maio','Junho','Julho','Agosto','Setembro','Outubro','Novembro','Dezembro'];
  const calLabel=`${dias2[calD.getDay()]}, ${calD.getDate()} de ${meses2[calD.getMonth()]}`;
  const calNome=calOff===0?'Hoje':calOff===1?'Amanhã':calOff===-1?'Ontem':calLabel;
  const vencCal=S.contratos.filter(c=>c.status==='ativo'&&c.tipo==='imovel'&&c.periodo===calDayNum);
  const devCal=S.contratos.filter(c=>c.status==='ativo'&&c.tipo==='item'&&c.dataFim===calStr);

  const stats=[
    {ic:'💰',lb:'Recebido no Mês',vl:R(recMes),cl:'#18a558',bg:'#071410'},
    {ic:'📅',lb:'A Receber no Mês',vl:R(aRecMes),cl:'#4f8ef7',bg:'#070e20'},
    {ic:'🏘️',lb:'Imóveis Ocupados',vl:imOcup+'/'+S.imoveis.length,cl:'#a78bfa',bg:'#0e0720'},
    {ic:'📦',lb:'Itens em Uso',vl:itOcup+'/'+S.itens.length,cl:'#fbbf24',bg:'#1a0f02'},
    {ic:'📈',lb:'Lucro do Mês',vl:R(recMes-despMes),cl:recMes-despMes>=0?'#18a558':'#f87171',bg:'#071410'},
    {ic:'⚠️',lb:'Em Atraso',vl:R(valorAt),cl:'#f87171',bg:'#1a0505'},
  ];

  const recent=[...S.contratos.filter(c=>c.status==='ativo')].slice(-4).reverse();

  return `
  <div class="sg">
    ${stats.map(s=>`<div class="sc"><div class="sc-ic" style="background:${s.bg}">${s.ic}</div><div class="sc-lb">${s.lb}</div><div class="sc-vl" style="color:${s.cl}">${s.vl}</div></div>`).join('')}
  </div>

  <div class="card card-p" style="margin-bottom:14px">
    <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:10px">
      <button class="bg2" style="width:30px;height:30px;padding:0;font-size:16px" onclick="calOff--;render()">‹</button>
      <div style="text-align:center">
        <div style="font-weight:800;font-size:14px;color:#18a558">${calNome}</div>
        <div style="font-size:10px;color:#4a5880">${calLabel}</div>
      </div>
      <button class="bg2" style="width:30px;height:30px;padding:0;font-size:16px" onclick="calOff++;render()">›</button>
    </div>
    ${vencCal.length===0&&devCal.length===0?'<div style="text-align:center;color:#2e3a58;padding:14px;font-size:12px">Nenhum vencimento neste dia</div>':
    [...vencCal.map(c=>{const cl=gc(c.clienteId);const im=gi(c.refId);return`
      <div style="display:flex;align-items:center;gap:9px;padding:8px 0;border-bottom:1px solid #141e3833">
        <div style="width:8px;height:8px;border-radius:50%;background:#18a558;flex-shrink:0"></div>
        <div style="flex:1"><div style="font-size:13px;font-weight:600">${cl?.nome||'?'}</div><div style="font-size:10px;color:#4a5880">Aluguel · ${im?.endereco||'?'}</div></div>
        <div style="font-weight:800;font-size:13px;color:#18a558">${R(c.valor)}</div>
      </div>`;}),
    ...devCal.map(c=>{const cl=gc(c.clienteId);const it=git(c.refId);return`
      <div style="display:flex;align-items:center;gap:9px;padding:8px 0;border-bottom:1px solid #141e3833">
        <div style="width:8px;height:8px;border-radius:50%;background:#fbbf24;flex-shrink:0"></div>
        <div style="flex:1"><div style="font-size:13px;font-weight:600">${cl?.nome||'?'}</div><div style="font-size:10px;color:#4a5880">Devolução · ${it?.nome||'?'}</div></div>
        <div style="font-weight:800;font-size:13px;color:#fbbf24">${R(c.valor)}</div>
      </div>`})].join('
