[financas (1).html](https://github.com/user-attachments/files/32813405/financas.1.html)
# fina-as-<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Minhas finanças</title>
<style>
:root{--bg:#f3f6f5;--card:#fff;--tx:#17232d;--mut:#66757f;--bd:#d9e1e0;--pri:#0f4c5c;--pri2:#0a3540;--on:#fff;--ok:#1a7f5a;--bad:#c8433a;--warn:#b7791f;--soft:#e8f0ef}
@media(prefers-color-scheme:dark){:root{--bg:#0f1a1e;--card:#172429;--tx:#e5eeee;--mut:#93a6ab;--bd:#2a3c42;--pri:#4fb3c8;--pri2:#7cc7d8;--on:#0b1c21;--ok:#4cc38a;--bad:#ef7b72;--warn:#e0b04f;--soft:#1e3138}}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--tx);font:15px/1.45 system-ui,-apple-system,"Segoe UI",sans-serif;padding:env(safe-area-inset-top,0) 0 calc(90px + env(safe-area-inset-bottom,0))}
.app{max-width:920px;margin:0 auto;padding:16px}
.topo{display:flex;justify-content:space-between;align-items:center;gap:12px;flex-wrap:wrap}
h1{margin:0;font-size:22px;color:var(--pri)}
h2{font-size:16px;margin:24px 0 10px}
.mes{display:flex;align-items:center;gap:8px}
.mes strong{min-width:140px;text-align:center;text-transform:capitalize}
button,input,select{font:inherit;color:inherit}
button{cursor:pointer;border:1px solid var(--bd);background:var(--card);border-radius:8px;padding:8px 12px}
button:hover{background:var(--soft)}
button:focus-visible,input:focus-visible,select:focus-visible{outline:2px solid var(--pri);outline-offset:1px}
.pri{background:var(--pri);color:var(--on);border-color:transparent;font-weight:600}
.pri:hover{background:var(--pri2)}
nav{display:flex;gap:6px;overflow-x:auto;margin:16px 0 0;padding-bottom:4px}
nav button{white-space:nowrap;border-radius:20px}
nav button.on{background:var(--pri);color:var(--on);border-color:transparent}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:12px}
.card{background:var(--card);border:1px solid var(--bd);border-radius:12px;padding:14px}
.card small,.lin small{color:var(--mut);display:block}
.big{font-size:24px;font-weight:700;font-variant-numeric:tabular-nums}
.ok{color:var(--ok)}.bad{color:var(--bad)}
ul{list-style:none;margin:0;padding:0}
.lin{display:flex;align-items:center;gap:8px;padding:10px 12px;border-bottom:1px solid var(--bd)}
.lin:last-child{border:0}
.lin>div:first-child{flex:1;min-width:0}
.lin b{overflow-wrap:anywhere}
.v{font-weight:600;font-variant-numeric:tabular-nums;white-space:nowrap}
.tag{font-size:12px;padding:2px 8px;border-radius:10px;background:var(--soft);white-space:nowrap}
.tag.atrasado{background:var(--bad);color:#fff}
.tag.pago{color:var(--ok)}
.ic{padding:4px 8px}
.barra{height:8px;background:var(--soft);border-radius:4px;overflow:hidden;margin-top:6px}
.barra i{display:block;height:100%;background:var(--pri);border-radius:4px}
.barra i.bad{background:var(--bad)}.barra i.warn{background:var(--warn)}
.filtros{display:flex;gap:8px;flex-wrap:wrap;margin:16px 0 10px}
input,select{padding:9px;border:1px solid var(--bd);border-radius:8px;background:var(--card);width:100%}
.filtros input,.filtros select{width:auto;flex:1;min-width:120px}
.fab{position:fixed;right:16px;bottom:calc(16px + env(safe-area-inset-bottom,0px));box-shadow:0 6px 20px #0004;padding:14px 18px;border-radius:30px}
dialog{border:0;border-radius:14px;padding:20px;width:min(440px,92vw);background:var(--card);color:var(--tx)}
dialog::backdrop{background:#0008}
.f{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.f label{display:flex;flex-direction:column;gap:4px;font-size:13px;color:var(--mut)}
.f .w{grid-column:1/-1}
.f .chk{flex-direction:row;align-items:center;gap:8px}
.f .chk input{width:auto}
.acoes{display:flex;gap:8px;justify-content:flex-end;flex-wrap:wrap;margin-top:12px}
.aviso{margin-top:12px;background:var(--soft);border-left:4px solid var(--warn);padding:10px 12px;border-radius:8px;cursor:pointer}
.vazio{color:var(--mut);padding:16px;text-align:center;margin:0}
.cols{display:flex;gap:10px}
.cols>div{flex:1;text-align:center;font-size:12px;color:var(--mut)}
.cols .p{display:flex;align-items:flex-end;justify-content:center;gap:3px;height:110px}
.cols .p i{width:40%;border-radius:3px 3px 0 0;min-height:2px}
.cols .r{background:var(--ok)}.cols .d{background:var(--bad)}
table{width:100%;border-collapse:collapse}
td,th{padding:8px;text-align:right;border-bottom:1px solid var(--bd)}
td:first-child,th:first-child{text-align:left}
@media print{nav,.fab,.topo button,#aviso,.noprint,.acoes,.ic{display:none!important}body{background:#fff}}
</style>
</head>
<body>
<div class="app">
  <div class="topo">
    <h1>Minhas finanças</h1>
    <div class="mes"><button id="ant" aria-label="Mês anterior">‹</button><strong id="mesTxt"></strong><button id="prox" aria-label="Próximo mês">›</button></div>
  </div>
  <div id="aviso"></div>
  <nav id="abas"></nav>
  <main id="tela"></main>
</div>
<button class="fab pri" id="novo">+ Nova movimentação</button>
<dialog id="dlg"></dialog>
<input type="file" id="arq" accept=".json" hidden>

<script>
const K = "financas.v1", $ = s => document.querySelector(s);
const esc = s => String(s ?? "").replace(/[&<>"']/g, c => ({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
const brl = n => (+n || 0).toLocaleString("pt-BR", {style: "currency", currency: "BRL"});
const uid = () => Math.random().toString(36).slice(2, 9);
const iso = d => new Date(d - d.getTimezoneOffset() * 6e4).toISOString().slice(0, 10);
const hoje = () => iso(new Date());
const somaDia = n => iso(new Date(Date.now() + n * 864e5));
const CD = ["Moradia","Alimentação","Transporte","Saúde","Lazer","Educação","Outros"];
const CR = ["Salário","Freelance","Investimentos","Outros"];
const FP = ["Pix","Débito","Crédito","Dinheiro","Boleto","Transferência"];
const padrao = () => ({contas: [{id: uid(), nome: "Carteira", tipo: "dinheiro", saldo: 0, limite: 0}], tx: [], orc: {}, metas: []});
let S = carregar(), V = "resumo", M = hoje().slice(0, 7), F = {tipo: "", cat: "", st: "", q: ""};

function carregar() {
  try { const s = JSON.parse(localStorage.getItem(K)); if (s && Array.isArray(s.tx) && Array.isArray(s.contas)) return s; } catch {}
  return padrao();
}
function salvar() { try { localStorage.setItem(K, JSON.stringify(S)); } catch {} }

// ---------- datas ----------
const somaMes = (d, n) => {
  const [y, m, dia] = d.split("-").map(Number), r = new Date(y, m - 1 + n, 1);
  r.setDate(Math.min(dia, new Date(y, m + n, 0).getDate()));
  return iso(r);
};
const mesMais = (m, n) => somaMes(m + "-01", n).slice(0, 7);
const mesTxt = m => new Date(+m.slice(0, 4), +m.slice(5) - 1, 1).toLocaleDateString("pt-BR", {month: "long", year: "numeric"});
const dd = d => d.slice(8) + "/" + d.slice(5, 7);

// ---------- cálculos ----------
const conta = id => S.contas.find(c => c.id === id);
const st = t => t.pago ? "pago" : t.data < hoje() ? "atrasado" : "pendente";
const ROT = t => ({pago: t.tipo == "receita" ? "Recebido" : "Pago", pendente: t.tipo == "receita" ? "A receber" : "A pagar", atrasado: "Atrasada"})[st(t)];
const soma = l => l.reduce((a, t) => a + t.valor, 0);
const doMes = m => S.tx.filter(t => t.data.startsWith(m));
// saldo = saldo inicial + só o que já foi recebido/pago
const saldoConta = c => c.saldo + S.tx.filter(t => t.conta === c.id && t.pago).reduce((a, t) => a + (t.tipo == "receita" ? t.valor : -t.valor), 0);
const fatura = c => soma(S.tx.filter(t => t.conta === c.id && t.tipo == "despesa" && !t.pago));
const opts = (a, s) => a.map(x => `<option ${x == s ? "selected" : ""}>${esc(x)}</option>`).join("");

// ---------- componentes ----------
const linha = t => `<li class="lin"><div><b>${esc(t.desc)}</b><small>${dd(t.data)} · ${esc(t.cat)} · ${esc(conta(t.conta)?.nome || "—")} · ${esc(t.forma)}</small></div>
<span class="tag ${st(t)}">${ROT(t)}</span>
<span class="v ${t.tipo == "receita" ? "ok" : "bad"}">${t.tipo == "receita" ? "+" : "−"}${brl(t.valor)}</span>
<button class="ic" data-a="baixa" data-i="${t.id}" title="${t.pago ? "Voltar para pendente" : "Marcar como pago/recebido"}">${t.pago ? "↺" : "✓"}</button>
<button class="ic" data-a="edita" data-i="${t.id}" title="Editar">✎</button>
<button class="ic" data-a="exclui" data-i="${t.id}" title="Excluir">✕</button></li>`;
const lista = l => l.length ? `<ul class="card" style="padding:0">${l.map(linha).join("")}</ul>` : `<p class="vazio">Nada por aqui ainda.</p>`;
const filtradas = () => doMes(M).filter(t => (!F.tipo || t.tipo == F.tipo) && (!F.cat || t.cat == F.cat) && (!F.st || st(t) == F.st) && (!F.q || t.desc.toLowerCase().includes(F.q.toLowerCase()))).sort((a, b) => a.data < b.data ? 1 : -1);

// ---------- telas ----------
const V_ = {
  resumo() {
    const l = doMes(M), pg = l.filter(t => t.pago);
    const rec = soma(pg.filter(t => t.tipo == "receita")), des = soma(pg.filter(t => t.tipo == "despesa"));
    const aPagar = soma(l.filter(t => t.tipo == "despesa" && !t.pago));
    const total = S.contas.filter(c => c.tipo != "cartao").reduce((a, c) => a + saldoConta(c), 0);
    const prox = S.tx.filter(t => !t.pago && t.data <= somaDia(7)).sort((a, b) => a.data < b.data ? -1 : 1).slice(0, 6);
    const cat = {}; l.filter(t => t.tipo == "despesa").forEach(t => cat[t.cat] = (cat[t.cat] || 0) + t.valor);
    const cs = Object.entries(cat).sort((a, b) => b[1] - a[1]), mx = cs[0]?.[1] || 1;
    return `<div class="grid" style="margin-top:16px">
<div class="card"><small>Saldo disponível</small><div class="big ${total < 0 ? "bad" : ""}">${brl(total)}</div><small>só movimentações realizadas</small></div>
<div class="card"><small>Receitas do mês</small><div class="big ok">${brl(rec)}</div><small>já recebidas</small></div>
<div class="card"><small>Despesas do mês</small><div class="big bad">${brl(des)}</div><small>ainda a pagar: ${brl(aPagar)}</small></div>
<div class="card"><small>Saldo do mês</small><div class="big ${rec - des < 0 ? "bad" : "ok"}">${brl(rec - des)}</div><small>${rec - des < 0 ? "saldo negativo" : "saldo positivo"}</small></div></div>
<h2>Vencidas e próximos 7 dias</h2>${prox.length ? lista(prox) : `<p class="vazio card">Nenhuma conta vencendo por enquanto.</p>`}
<h2>Despesas por categoria</h2><div class="card">${cs.length ? cs.map(([c, v]) => `<div style="margin-bottom:12px"><div style="display:flex;justify-content:space-between"><span>${esc(c)}</span><b>${brl(v)}</b></div><div class="barra"><i style="width:${v / mx * 100}%"></i></div></div>`).join("") : `<p class="vazio">Sem despesas neste mês.</p>`}</div>`;
  },
  movs() {
    const sel = (t, ph, arr) => `<select data-f="${t}"><option value="">${ph}</option>${arr.map(([v, n]) => `<option value="${v}" ${F[t] == v ? "selected" : ""}>${n}</option>`).join("")}</select>`;
    return `<div class="filtros">${sel("tipo", "Receitas e despesas", [["receita", "Receitas"], ["despesa", "Despesas"]])}${sel("cat", "Categoria", [...new Set([...CD, ...CR])].map(c => [c, c]))}${sel("st", "Situação", [["pendente", "Pendentes"], ["atrasado", "Atrasadas"], ["pago", "Pagas/recebidas"]])}<input data-f="q" type="search" placeholder="Buscar descrição" value="${esc(F.q)}"></div><div id="lista">${lista(filtradas())}</div>`;
  },
  pagar() {
    const ab = S.tx.filter(t => !t.pago).sort((a, b) => a.data < b.data ? -1 : 1);
    const at = ab.filter(t => st(t) == "atrasado"), ok = ab.filter(t => st(t) != "atrasado");
    return `<div class="grid" style="margin-top:16px"><div class="card"><small>Total a pagar</small><div class="big bad">${brl(soma(ab.filter(t => t.tipo == "despesa")))}</div></div><div class="card"><small>Total a receber</small><div class="big ok">${brl(soma(ab.filter(t => t.tipo == "receita")))}</div></div></div>
<h2>Atrasadas (${at.length})</h2>${lista(at)}<h2>A vencer (${ok.length})</h2>${lista(ok)}`;
  },
  contas() {
    return `<div class="grid" style="margin-top:16px">${S.contas.map(c => {
      const cartao = c.tipo == "cartao", fa = fatura(c), sd = saldoConta(c);
      return `<div class="card"><small>${{banco: "Conta bancária", dinheiro: "Dinheiro", cartao: "Cartão de crédito"}[c.tipo]}</small><b>${esc(c.nome)}</b>
${cartao ? `<div class="big bad">${brl(fa)}</div><small>fatura em aberto · disponível ${brl(c.limite - fa)} de ${brl(c.limite)}</small><div class="barra"><i class="${fa > c.limite * .8 ? "warn" : ""}" style="width:${Math.min(100, c.limite ? fa / c.limite * 100 : 0)}%"></i></div>` : `<div class="big ${sd < 0 ? "bad" : ""}">${brl(sd)}</div><small>saldo atual</small>`}
<div class="acoes"><button class="ic" data-a="editaC" data-i="${c.id}">Editar</button><button class="ic" data-a="excluiC" data-i="${c.id}">Excluir</button></div></div>`;
    }).join("")}</div><div class="acoes" style="justify-content:flex-start"><button class="pri" data-a="novaC">+ Nova conta ou cartão</button></div>`;
  },
  orc() {
    const l = doMes(M).filter(t => t.tipo == "despesa");
    const bud = CD.map(c => {
      const g = soma(l.filter(t => t.cat == c)), lim = +S.orc[c] || 0, p = lim ? g / lim * 100 : 0;
      return `<div class="card"><div style="display:flex;justify-content:space-between;gap:10px;align-items:center"><b>${c}</b><input type="number" min="0" step="10" placeholder="Limite" value="${lim || ""}" data-o="${c}" style="width:120px" aria-label="Limite de ${c}"></div>
<small>${brl(g)}${lim ? ` de ${brl(lim)} · ${p > 100 ? `estourou ${brl(g - lim)}` : `restam ${brl(lim - g)}`}` : " gasto · sem limite"}</small><div class="barra"><i class="${p > 100 ? "bad" : p > 80 ? "warn" : ""}" style="width:${Math.min(100, p)}%"></i></div></div>`;
    }).join("");
    const metas = S.metas.map(m => {
      const p = Math.min(100, m.alvo ? m.atual / m.alvo * 100 : 0);
      return `<div class="card"><div style="display:flex;justify-content:space-between"><b>${esc(m.nome)}</b><span>${p.toFixed(0)}%</span></div><small>${brl(m.atual)} de ${brl(m.alvo)} · faltam ${brl(Math.max(0, m.alvo - m.atual))}</small><div class="barra"><i style="width:${p}%"></i></div>
<div class="acoes"><button class="ic" data-a="guarda" data-i="${m.id}">+ Guardar</button><button class="ic" data-a="excluiM" data-i="${m.id}">Excluir</button></div></div>`;
    }).join("");
    return `<h2>Limite de gastos por categoria — ${mesTxt(M)}</h2><div class="grid">${bud}</div>
<h2>Metas de economia</h2><div class="grid">${metas}</div><div class="acoes" style="justify-content:flex-start"><button class="pri" data-a="novaM">+ Nova meta</button></div>`;
  },
  relat() {
    const meses = [5, 4, 3, 2, 1, 0].map(i => mesMais(M, -i));
    const dados = meses.map(m => { const l = doMes(m); return {m, r: soma(l.filter(t => t.tipo == "receita")), d: soma(l.filter(t => t.tipo == "despesa"))}; });
    const mx = Math.max(1, ...dados.flatMap(x => [x.r, x.d]));
    const a = mesMais(M, -1), cur = doMes(M), prev = doMes(a), tot = (l, tp) => soma(l.filter(t => t.tipo == tp));
    const cats = [...new Set([...cur, ...prev].filter(t => t.tipo == "despesa").map(t => t.cat))];
    const lin = (n, x, y, sobeBom) => `<tr><td>${esc(n)}</td><td>${brl(x)}</td><td>${brl(y)}</td><td class="${(y - x) * (sobeBom ? 1 : -1) >= 0 ? "ok" : "bad"}">${y - x > 0 ? "+" : ""}${brl(y - x)}</td></tr>`;
    const ult = iso(new Date(+M.slice(0, 4), +M.slice(5), 0));
    return `<h2>Últimos 6 meses</h2><div class="card"><div class="cols">${dados.map(x => `<div><div class="p"><i class="r" style="height:${x.r / mx * 100}%" title="Receitas ${brl(x.r)}"></i><i class="d" style="height:${x.d / mx * 100}%" title="Despesas ${brl(x.d)}"></i></div>${mesTxt(x.m).slice(0, 3)}</div>`).join("")}</div>
<small style="color:var(--mut);margin-top:8px"><span class="ok">■</span> receitas &nbsp;<span class="bad">■</span> despesas (tudo que foi lançado no mês)</small></div>
<h2>${mesTxt(a)} × ${mesTxt(M)}</h2><div class="card"><table><tr><th></th><th>Anterior</th><th>Atual</th><th>Diferença</th></tr>
${lin("Receitas", tot(prev, "receita"), tot(cur, "receita"), 1)}${lin("Despesas", tot(prev, "despesa"), tot(cur, "despesa"), 0)}${lin("Saldo", tot(prev, "receita") - tot(prev, "despesa"), tot(cur, "receita") - tot(cur, "despesa"), 1)}
${cats.map(c => lin(c, soma(prev.filter(t => t.tipo == "despesa" && t.cat == c)), soma(cur.filter(t => t.tipo == "despesa" && t.cat == c)), 0)).join("")}</table></div>
<h2 class="noprint">Exportar e backup</h2><div class="card noprint"><div class="f"><label>De<input type="date" id="de" value="${M}-01"></label><label>Até<input type="date" id="ate" value="${ult}"></label></div>
<div class="acoes" style="justify-content:flex-start"><button class="pri" data-a="csv">Exportar para Excel (CSV)</button><button data-a="pdf">Imprimir / salvar em PDF</button></div>
<div class="acoes" style="justify-content:flex-start"><button data-a="bkp">Baixar backup</button><button data-a="rest">Restaurar backup</button><button data-a="limpa">Apagar tudo</button></div></div>`;
  }
};
const ABAS = {resumo: "Resumo", movs: "Movimentações", pagar: "A pagar / receber", contas: "Contas e cartões", orc: "Orçamento e metas", relat: "Relatórios"};

function render() {
  $("#mesTxt").textContent = mesTxt(M);
  $("#abas").innerHTML = Object.entries(ABAS).map(([k, n]) => `<button data-v="${k}" class="${k == V ? "on" : ""}">${n}</button>`).join("");
  const at = S.tx.filter(t => !t.pago && st(t) == "atrasado").length;
  const vc = S.tx.filter(t => !t.pago && t.data >= hoje() && t.data <= somaDia(3)).length;
  $("#aviso").innerHTML = at || vc ? `<div class="aviso" data-v="pagar">⚠ ${at ? `${at} atrasada${at > 1 ? "s" : ""}` : ""}${at && vc ? " · " : ""}${vc ? `${vc} vence${vc > 1 ? "m" : ""} em até 3 dias` : ""}</div>` : "";
  $("#tela").innerHTML = V_[V]();
}

// ---------- formulários ----------
function abrir(html, ok) {
  const d = $("#dlg");
  d.innerHTML = `<form class="f">${html}<div class="acoes w"><button type="button" data-a="fecha">Cancelar</button><button class="pri">Salvar</button></div></form>`;
  d.querySelector("form").onsubmit = e => { e.preventDefault(); ok(Object.fromEntries(new FormData(e.target))); d.close(); salvar(); render(); };
  d.showModal();
}
function formTx(id) {
  const ex = S.tx.find(x => x.id == id), novo = !ex;
  const t = ex || {tipo: "despesa", desc: "", valor: "", cat: "", data: hoje(), forma: "Pix", conta: S.contas[0]?.id, pago: false};
  abrir(`<label class="w">Tipo<select name="tipo" id="tp"><option value="despesa">Despesa</option><option value="receita" ${t.tipo == "receita" ? "selected" : ""}>Receita</option></select></label>
<label class="w">Descrição<input name="desc" required value="${esc(t.desc)}"></label>
<label>Valor (R$)<input name="valor" type="number" step="0.01" min="0.01" required value="${t.valor}"></label>
<label>Data (vencimento)<input name="data" type="date" required value="${t.data}"></label>
<label>Categoria<select name="cat" id="ct"></select></label>
<label>Forma de pagamento<select name="forma">${opts(FP, t.forma)}</select></label>
<label class="w">Conta ou cartão<select name="conta">${S.contas.map(c => `<option value="${c.id}" ${c.id == t.conta ? "selected" : ""}>${esc(c.nome)}</option>`).join("")}</select></label>
${novo ? `<label>Repetição<select name="rep"><option value="1">Única</option><option value="mensal">Mensal (recorrente)</option><option value="parc">Parcelada (divide o valor)</option></select></label><label>Vezes<input name="n" type="number" min="2" max="60" value="12"></label>` : ""}
<label class="w chk"><input type="checkbox" name="pago" ${t.pago ? "checked" : ""}> Já foi pago / recebido</label>`, f => {
    const b = {tipo: f.tipo, desc: f.desc.trim(), cat: f.cat, forma: f.forma, conta: f.conta}, v = +f.valor;
    if (!novo) { Object.assign(t, b, {valor: v, data: f.data, pago: !!f.pago}); return; }
    const n = f.rep == "1" ? 1 : Math.max(2, +f.n || 2), g = uid();
    for (let i = 0; i < n; i++) S.tx.push({...b, id: uid(), grupo: g, valor: f.rep == "parc" ? Math.round(v / n * 100) / 100 : v, data: somaMes(f.data, i), pago: i == 0 && !!f.pago, desc: n > 1 ? `${b.desc} (${i + 1}/${n})` : b.desc});
  });
  const cat = () => { $("#ct").innerHTML = opts($("#tp").value == "receita" ? CR : CD, t.cat); };
  $("#tp").onchange = cat; cat();
}
function formC(id) {
  const c = conta(id) || {nome: "", tipo: "banco", saldo: 0, limite: 0};
  abrir(`<label class="w">Nome<input name="nome" required value="${esc(c.nome)}"></label>
<label>Tipo<select name="tipo"><option value="banco">Conta bancária</option><option value="dinheiro" ${c.tipo == "dinheiro" ? "selected" : ""}>Dinheiro</option><option value="cartao" ${c.tipo == "cartao" ? "selected" : ""}>Cartão de crédito</option></select></label>
<label>Saldo inicial<input name="saldo" type="number" step="0.01" value="${c.saldo}"></label>
<label class="w">Limite do cartão (R$)<input name="limite" type="number" step="0.01" min="0" value="${c.limite || 0}"></label>`, f => {
    const d = {nome: f.nome.trim(), tipo: f.tipo, saldo: +f.saldo || 0, limite: +f.limite || 0};
    id ? Object.assign(c, d) : S.contas.push({id: uid(), ...d});
  });
}
function formM() {
  abrir(`<label class="w">Nome da meta<input name="nome" required></label><label>Valor alvo (R$)<input name="alvo" type="number" min="1" step="0.01" required></label><label>Já guardado (R$)<input name="atual" type="number" min="0" step="0.01" value="0"></label>`,
    f => S.metas.push({id: uid(), nome: f.nome.trim(), alvo: +f.alvo, atual: +f.atual || 0}));
}

// ---------- exportar / backup ----------
function baixar(n, txt, tipo) {
  const a = document.createElement("a");
  a.href = URL.createObjectURL(new Blob([txt], {type: tipo})); a.download = n; a.click();
  setTimeout(() => URL.revokeObjectURL(a.href), 1e3);
}
function exportarCSV() {
  const de = $("#de").value, ate = $("#ate").value, q = x => `"${String(x).replace(/"/g, '""')}"`;
  const l = S.tx.filter(t => t.data >= de && t.data <= ate).sort((a, b) => a.data < b.data ? -1 : 1);
  const csv = ["Data;Tipo;Descrição;Categoria;Conta;Forma;Situação;Valor",
    ...l.map(t => [t.data.split("-").reverse().join("/"), t.tipo, q(t.desc), t.cat, q(conta(t.conta)?.nome || ""), t.forma, ROT(t), t.valor.toFixed(2).replace(".", ",")].join(";"))].join("\r\n");
  baixar(`movimentacoes-${de}_${ate}.csv`, "\ufeff" + csv, "text/csv;charset=utf-8");
}
$("#arq").onchange = async e => {
  const f = e.target.files[0]; if (!f) return;
  try {
    const d = JSON.parse(await f.text());
    if (!Array.isArray(d.tx) || !Array.isArray(d.contas)) throw 0;
    if (!confirm("Substituir os dados atuais pelo backup?")) return;
    S = {contas: d.contas, tx: d.tx, orc: d.orc || {}, metas: d.metas || []}; salvar(); render();
  } catch { alert("Arquivo de backup inválido."); }
  e.target.value = "";
};

// ---------- eventos ----------
document.addEventListener("click", e => {
  const n = e.target.closest("[data-v]");
  if (n) { V = n.dataset.v; return render(); }
  const b = e.target.closest("[data-a]"); if (!b) return;
  const a = b.dataset.a, i = b.dataset.i, t = S.tx.find(x => x.id == i);
  if (a == "baixa") t.pago = !t.pago;
  else if (a == "edita") return formTx(i);
  else if (a == "exclui") { if (!confirm("Excluir esta movimentação?")) return; S.tx = S.tx.filter(x => x.id != i); }
  else if (a == "editaC") return formC(i);
  else if (a == "excluiC") { if (!confirm("Excluir esta conta e todas as movimentações dela?")) return; S.contas = S.contas.filter(c => c.id != i); S.tx = S.tx.filter(x => x.conta != i); }
  else if (a == "novaC") return formC();
  else if (a == "novaM") return formM();
  else if (a == "guarda") { const v = parseFloat((prompt("Quanto guardar agora? (R$)") || "").replace(",", ".")); if (!(v > 0)) return; S.metas.find(m => m.id == i).atual += v; }
  else if (a == "excluiM") { if (!confirm("Excluir esta meta?")) return; S.metas = S.metas.filter(m => m.id != i); }
  else if (a == "fecha") return $("#dlg").close();
  else if (a == "csv") return exportarCSV();
  else if (a == "pdf") return print();
  else if (a == "bkp") return baixar(`financas-${hoje()}.json`, JSON.stringify(S, null, 1), "application/json");
  else if (a == "rest") return $("#arq").click();
  else if (a == "limpa") { if (!confirm("Apagar TODOS os dados deste navegador? Baixe um backup antes.")) return; S = padrao(); }
  salvar(); render();
});
document.addEventListener("input", e => {
  const f = e.target.dataset.f; if (!f) return;
  F[f] = e.target.value; $("#lista").innerHTML = lista(filtradas());
});
document.addEventListener("change", e => {
  const c = e.target.dataset.o; if (!c) return;
  S.orc[c] = +e.target.value || 0; salvar(); render();
});
$("#ant").onclick = () => { M = mesMais(M, -1); render(); };
$("#prox").onclick = () => { M = mesMais(M, 1); render(); };
$("#novo").onclick = () => formTx();
render();
</script>
</body>
</html>

finaças 
