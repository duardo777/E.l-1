<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>E. L. Instalações Elétricas Prediais — Orçamentos e OS</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Barlow:wght@400;500;600;700&family=Barlow+Semi+Condensed:wght@500;600;700&display=swap" rel="stylesheet">
<script src="https://cdn.tailwindcss.com"></script>
<script>
  tailwind.config = {
    theme: { extend: {
      colors: {
        navy: { 50:'#eef3f9',100:'#d9e4f1',200:'#b5c9e2',300:'#86a5cc',400:'#5a80b0',500:'#3d6597',600:'#2c4f7c',700:'#213f66',800:'#182f4e',900:'#0f2039' },
        volt: { 400:'#fcc934', 500:'#f5b301' }
      },
      fontFamily: {
        sans: ['Barlow','system-ui','Segoe UI','Arial','sans-serif'],
        display: ['"Barlow Semi Condensed"','Barlow','system-ui','Arial','sans-serif']
      }
    } }
  };
</script>
<style>
  :root { color-scheme: light; box-sizing: border-box; padding-top: env(safe-area-inset-top, 0px); padding-bottom: env(safe-area-inset-bottom, 0px); }
  html { scroll-padding-top: env(safe-area-inset-top, 0px); }
  body { margin: 0; background: #eef1f5; font-family: Barlow, system-ui, "Segoe UI", Arial, sans-serif; -webkit-font-smoothing: antialiased; color: #0f172a; }
  body.preview-open { overflow: hidden; }
  .num { font-variant-numeric: tabular-nums; }
  input[type=number]::-webkit-inner-spin-button { display: none; }

  /* ---------- Documento (tela + impressão A4) ---------- */
  #print-root { display: none; }
  #print-root:not(:empty) { display: block; }
  .print-overlay { position: fixed; inset: 0; z-index: 100; background: #475569; display: flex; flex-direction: column; }
  .print-toolbar { display: flex; gap: 8px; align-items: center; flex-wrap: wrap; padding: 10px 14px; padding-top: calc(10px + env(safe-area-inset-top, 0px)); background: #0f2039; color: #fff; }
  .tb-btn { border: 1px solid rgba(255,255,255,.35); background: transparent; color: #fff; border-radius: 6px; padding: 7px 14px; font: 600 14px Barlow, Arial, sans-serif; cursor: pointer; }
  .tb-btn:hover { background: rgba(255,255,255,.12); }
  .tb-btn.main { background: #f5b301; color: #0f2039; border-color: #f5b301; }
  .tb-btn.main:hover { background: #fcc934; }
  .print-scroll { flex: 1; overflow: auto; padding: 20px 12px; padding-bottom: calc(20px + env(safe-area-inset-bottom, 0px)); }
  .sheet { box-sizing: border-box; width: 210mm; min-height: 297mm; margin: 0 auto; background: #fff; color: #0f172a; padding: 12mm; box-shadow: 0 6px 28px rgba(0,0,0,.35); font-size: 10pt; line-height: 1.4; }
  @media screen and (max-width: 860px) { .sheet { zoom: .75; } }
  @media screen and (max-width: 640px) { .sheet { zoom: .5; } }
  @media screen and (max-width: 430px) { .sheet { zoom: .44; } }

  .doc-head { display: flex; justify-content: space-between; gap: 16px; border-bottom: 3px solid #0f2039; padding-bottom: 10px; margin-bottom: 12px; }
  .doc-brand { display: flex; gap: 10px; align-items: flex-start; }
  .doc-logo { width: 42px; height: 42px; background: #0f2039; color: #fcc934; display: flex; align-items: center; justify-content: center; border-radius: 6px; flex: none; }
  .doc-name { font: 700 16pt "Barlow Semi Condensed", Barlow, Arial, sans-serif; color: #0f2039; line-height: 1.1; }
  .doc-sub { font-size: 8.5pt; color: #475569; }
  .doc-meta { text-align: right; font-size: 9pt; color: #334155; min-width: 52mm; }
  .doc-meta-title { font-size: 8.5pt; color: #64748b; font-weight: 600; }
  .doc-meta-num { font: 700 18pt "Barlow Semi Condensed", Barlow, Arial, sans-serif; color: #0f2039; line-height: 1.1; }
  .doc-box { border: 1px solid #cbd5e1; border-radius: 4px; padding: 8px 10px; margin-bottom: 12px; }
  .doc-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 3px 16px; font-size: 9.5pt; }
  .doc h3 { font: 700 11pt "Barlow Semi Condensed", Barlow, Arial, sans-serif; color: #0f2039; margin: 12px 0 5px; break-after: avoid; page-break-after: avoid; }
  .doc-table { width: 100%; border-collapse: collapse; font-size: 9pt; page-break-inside: auto; }
  .doc-table th { background: #0f2039; color: #fff; text-align: left; padding: 4px 6px; font-weight: 600; }
  .doc-table td { padding: 4px 6px; border-bottom: 1px solid #e2e8f0; vertical-align: top; }
  .doc-table .r { text-align: right; font-variant-numeric: tabular-nums; }
  .doc-table thead { display: table-header-group; }
  .doc-subtotal { text-align: right; font-weight: 700; padding: 5px 6px; background: #eef3f9; font-size: 9.5pt; }
  .doc-fin { display: grid; grid-template-columns: 1fr auto; gap: 3px 24px; font-size: 10pt; }
  .doc-fin .strong { font-weight: 700; font-size: 11pt; }
  .doc-sign { display: grid; grid-template-columns: 1fr 1fr; gap: 28px; margin-top: 34px; text-align: center; font-size: 9pt; color: #475569; }
  .doc-sign div { border-top: 1px solid #0f172a; padding-top: 4px; }
  .doc-foot { margin-top: 14px; font-size: 8pt; color: #64748b; text-align: center; }
  .avoid, .doc-table tr, .doc-box { break-inside: avoid; page-break-inside: avoid; page-break-after: auto; }

  @page { size: A4; margin: 12mm 12mm 16mm 12mm; @bottom-right { content: "Página " counter(page) " de " counter(pages); font: 8pt Barlow, Arial, sans-serif; color: #64748b; } }
  @media print {
    * { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
    html, body { background: #fff !important; overflow: visible !important; }
    :root { padding: 0 !important; }
    #root { display: none !important; }
    #print-root { display: block !important; }
    .print-overlay { position: static; display: block; background: #fff; }
    .print-scroll { overflow: visible; padding: 0; }
    .no-print { display: none !important; }
    .sheet { width: auto; min-height: 0; margin: 0; padding: 0; box-shadow: none; zoom: 1 !important; }
  }
</style>
</head>
<body>
<div id="root"></div>
<div id="print-root"></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/react/18.3.1/umd/react.production.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/react-dom/18.3.1/umd/react-dom.production.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/babel-standalone/7.24.7/babel.min.js"></script>

<script type="text/plain" id="app-src">
const { useState, useEffect, useMemo, useRef } = React;

/* =====================================================================
   TIPOS
   ===================================================================== */
type Situacao = 'Em Orçamento' | 'Aprovada' | 'Em Execução' | 'Concluída' | 'Cancelada';
const SITUACOES: Situacao[] = ['Em Orçamento', 'Aprovada', 'Em Execução', 'Concluída', 'Cancelada'];
const UNIDADES = ['UND', 'Metros', 'Barra', 'KG', 'Kit', 'Rolo', 'Caixa'];

interface Material { id: string; codigo: string; descricao: string; categoria: string; unidade: string; precoUnit: number; precoCobrar: number; estoque: number; }
interface ItemOS { id: string; materialId?: string; codigo: string; descricao: string; categoria: string; unidade: string; qtd: number; preco: number; }
interface Servico { id: string; descricao: string; preco: number; }
interface Cliente { nome: string; email: string; telefone: string; rua: string; numero: string; bairro: string; cidade: string; }
interface Pagamento { aVista: number | null; parcelas: number; juros: number; valorParcela: number | null; pagoMateriais: number; pagoMaoObra: number; }
interface OS { id: string; numero: string; data: string; emissor: string; situacao: Situacao; cliente: Cliente; itens: ItemOS[]; servicos: Servico[]; pagamento: Pagamento; observacoes: string; }
interface Settings { email: string; telefone: string; cidade: string; cnpj: string; usuario: string; }

const DEFAULT_SETTINGS: Settings = {
  email: 'contato@elinstalacoes.com.br',
  telefone: '(69) 99999-0000',
  cidade: 'Ji-Paraná/RO',
  cnpj: '',
  usuario: 'Eduardo F. Vargas',
};

/* =====================================================================
   UTILITÁRIOS
   ===================================================================== */
const uid = () => Math.random().toString(36).slice(2, 10) + Date.now().toString(36).slice(-4);
const brl = new Intl.NumberFormat('pt-BR', { style: 'currency', currency: 'BRL' });
const qtdFmt = new Intl.NumberFormat('pt-BR', { maximumFractionDigits: 3 });
const money = (n: number) => brl.format(n || 0);
const round2 = (n: number) => Math.round((n + Number.EPSILON) * 100) / 100;
const pad = (n: number) => String(n).padStart(2, '0');
const isoDe = (d: Date) => d.getFullYear() + '-' + pad(d.getMonth() + 1) + '-' + pad(d.getDate());
const hoje = () => isoDe(new Date());
const addDias = (n: number) => { const d = new Date(); d.setDate(d.getDate() + n); return isoDe(d); };
const fmtData = (iso: string) => { if (!iso) return '—'; const [y, m, d] = iso.split('-'); return d + '/' + m + '/' + y; };

function useLocalStorage<T>(key: string, initial: () => T): [T, (v: T | ((p: T) => T)) => void] {
  const [val, setVal] = useState<T>(() => {
    try { const raw = localStorage.getItem(key); if (raw) return JSON.parse(raw); } catch (e) {}
    return initial();
  });
  useEffect(() => { try { localStorage.setItem(key, JSON.stringify(val)); } catch (e) {} }, [key, val]);
  return [val, setVal];
}

/* =====================================================================
   REGRAS DE NEGÓCIO
   ===================================================================== */
function calc(os: OS) {
  const p = os.pagamento;
  const totMat = round2(os.itens.reduce((s, i) => s + (i.qtd || 0) * (i.preco || 0), 0));
  const totMO = round2(os.servicos.reduce((s, i) => s + (i.preco || 0), 0));
  const totalGeral = round2(totMat + totMO);
  const valorTotal = p.aVista == null ? totalGeral : round2(p.aVista);
  const pagoTotal = round2((p.pagoMateriais || 0) + (p.pagoMaoObra || 0));
  const saldo = round2(Math.max(0, valorTotal - pagoTotal));
  const n = Math.max(1, p.parcelas || 1);
  const saldoJuros = n > 1 ? round2(saldo * (1 + (p.juros || 0) / 100)) : saldo;
  const sugerida = round2(saldoJuros / n);
  const parcela = p.valorParcela == null ? sugerida : round2(p.valorParcela);
  const totalParcelado = round2(parcela * n);
  return { totMat, totMO, totalGeral, valorTotal, pagoTotal, saldo, n, saldoJuros, sugerida, parcela, totalParcelado };
}

function proximoNumero(ordens: OS[]) {
  const max = ordens.reduce((m, o) => { const n = parseInt(o.numero.replace(/\D/g, ''), 10); return isNaN(n) ? m : Math.max(m, n); }, 0);
  return 'OS-' + String(max + 1).padStart(4, '0');
}

function novaOS(ordens: OS[], s: Settings): OS {
  return {
    id: uid(), numero: proximoNumero(ordens), data: hoje(), emissor: s.usuario, situacao: 'Em Orçamento',
    cliente: { nome: '', email: '', telefone: '', rua: '', numero: '', bairro: '', cidade: s.cidade },
    itens: [], servicos: [],
    pagamento: { aVista: null, parcelas: 1, juros: 0, valorParcela: null, pagoMateriais: 0, pagoMaoObra: 0 },
    observacoes: '',
  };
}

/* =====================================================================
   DADOS DE EXEMPLO (catálogo e OS iniciais para teste — edite à vontade)
   ===================================================================== */
function gerarMateriais(): Material[] {
  const out: Material[] = [];
  const cnt: Record<string, number> = {};
  const add = (pre: string, cat: string, un: string, desc: string, custo: number) => {
    cnt[pre] = (cnt[pre] || 0) + 1;
    const i = out.length;
    out.push({
      id: 'm' + (i + 1), codigo: pre + '-' + String(cnt[pre]).padStart(3, '0'), descricao: desc, categoria: cat, unidade: un,
      precoUnit: round2(custo), precoCobrar: round2(custo * 1.45), estoque: ((i * 37) % 45) + (un === 'Metros' ? 60 : 2),
    });
  };
  const vir = (n: number) => String(n).replace('.', ',');

  // Fios e cabos
  ([[1.5, 1.9], [2.5, 3.1], [4, 4.9], [6, 7.2], [10, 12], [16, 19], [25, 30]] as [number, number][]).forEach(([b, c]) =>
    ['Preto', 'Azul', 'Vermelho', 'Verde'].forEach(cor => add('CAB', 'Fios e Cabos', 'Metros', 'Cabo flexível 750 V ' + vir(b) + ' mm² ' + cor, c)));

  // Disjuntores
  [10, 16, 20, 25, 32, 40, 50, 63].forEach(a =>
    ([['Monopolar', 1], ['Bipolar', 2.2], ['Tripolar', 3.3]] as [string, number][]).forEach(([n, f]) =>
      add('DJM', 'Disjuntores', 'UND', 'Disjuntor ' + n + ' ' + a + ' A curva C', (8 + a * 0.28) * f)));

  // Eletrodutos e conexões
  ([[20, 11], [25, 15], [32, 24], [40, 33], [50, 46]] as [number, number][]).forEach(([d, c]) =>
    add('ELE', 'Eletroduto', 'Barra', 'Eletroduto PVC rígido roscável ' + d + ' mm (3 m)', c));
  ([[20, 52], [25, 74], [32, 108]] as [number, number][]).forEach(([d, c]) =>
    add('ELE', 'Eletroduto', 'Rolo', 'Eletroduto corrugado flexível ' + d + ' mm (50 m)', c));
  [20, 25, 32].forEach(d => {
    add('CON', 'Eletroduto', 'UND', 'Luva para eletroduto ' + d + ' mm', d * 0.06);
    add('CON', 'Eletroduto', 'UND', 'Curva 90° para eletroduto ' + d + ' mm', d * 0.12);
    add('CON', 'Eletroduto', 'UND', 'Abraçadeira tipo D ' + d + ' mm', d * 0.05);
    add('CON', 'Eletroduto', 'UND', 'Bucha e arruela ' + d + ' mm', d * 0.07);
  });

  // Tomadas e interruptores
  ([
    ['Tomada 2P+T 10 A 4x2', 8.5], ['Tomada 2P+T 20 A 4x2', 9.5], ['Tomada dupla 2P+T 10 A 4x2', 16], ['Tomada USB 2 portas 4x2', 38],
    ['Interruptor simples 1 tecla 4x2', 7.5], ['Interruptor simples 2 teclas 4x2', 12], ['Interruptor simples 3 teclas 4x2', 17],
    ['Interruptor paralelo 1 tecla 4x2', 10], ['Interruptor bipolar 1 tecla 4x2', 13], ['Dimmer rotativo 4x2', 34],
    ['Sensor de presença de parede', 42], ['Campainha cigarra 127/220 V', 22], ['Placa 4x2 cega', 4], ['Placa 4x2 1 posto', 4.5],
    ['Placa 4x2 2 postos', 5], ['Placa 4x2 3 postos', 6], ['Caixa de embutir 4x2 PVC', 2.8], ['Caixa de embutir 4x4 PVC', 4.6],
  ] as [string, number][]).forEach(([d, c]) => add('TOM', 'Tomadas e Interruptores', 'UND', d, c));

  // Iluminação
  [9, 12, 15, 18].forEach(w => ['6500 K', '3000 K'].forEach(k =>
    add('ILU', 'Iluminação', 'UND', 'Lâmpada LED bulbo ' + w + ' W ' + k, 5 + w * 0.6)));
  ([[12, 22], [18, 31], [24, 42]] as [number, number][]).forEach(([w, c]) => add('ILU', 'Iluminação', 'UND', 'Painel LED embutir ' + w + ' W', c));
  ([[30, 36], [50, 58], [100, 96]] as [number, number][]).forEach(([w, c]) => add('ILU', 'Iluminação', 'UND', 'Refletor LED ' + w + ' W IP65', c));
  add('ILU', 'Iluminação', 'UND', 'Plafon LED sobrepor 18 W', 34);
  add('ILU', 'Iluminação', 'UND', 'Plafon LED sobrepor 24 W', 46);
  add('ILU', 'Iluminação', 'Kit', 'Fita LED 5 m com fonte', 62);
  add('ILU', 'Iluminação', 'UND', 'Luminária tartaruga IP54', 14);
  add('ILU', 'Iluminação', 'UND', 'Spot LED direcionável', 19);
  add('ILU', 'Iluminação', 'UND', 'Fonte 12 V 5 A', 27);

  // Quadros
  [3, 6, 8, 12, 18, 24, 34].forEach(q => add('QDR', 'Quadros', 'UND', 'Quadro de distribuição embutir ' + q + ' disjuntores', 28 + q * 6.5));

  // Proteção
  ([['25 A', 'Bipolar', 96], ['40 A', 'Bipolar', 104], ['63 A', 'Bipolar', 142], ['25 A', 'Tetrapolar', 178], ['40 A', 'Tetrapolar', 192], ['63 A', 'Tetrapolar', 238]] as [string, string, number][])
    .forEach(([a, p, c]) => add('PRO', 'Proteção', 'UND', 'Interruptor DR ' + p + ' ' + a + ' 30 mA', c));
  add('PRO', 'Proteção', 'UND', 'DPS Classe II 275 V 20 kA', 38);
  add('PRO', 'Proteção', 'UND', 'DPS Classe II 275 V 40 kA', 52);
  add('PRO', 'Proteção', 'UND', 'DPS Classe II 275 V 45 kA', 64);

  // Outros
  add('OUT', 'Outros', 'Rolo', 'Fita isolante 20 m', 7.5);
  add('OUT', 'Outros', 'Rolo', 'Fita isolante autofusão', 18);
  add('OUT', 'Outros', 'Kit', 'Terminal pré-isolado ilhós 2,5 mm² (100 un)', 24);
  add('OUT', 'Outros', 'Kit', 'Conector de emenda (10 un)', 16);
  add('OUT', 'Outros', 'UND', 'Haste de aterramento 2,4 m', 42);
  add('OUT', 'Outros', 'Metros', 'Cabo de cobre nu 16 mm²', 19);
  add('OUT', 'Outros', 'Kit', 'Abraçadeira de nylon 200 mm (100 un)', 21);
  add('OUT', 'Outros', 'Rolo', 'Fita veda rosca', 4.5);
  add('OUT', 'Outros', 'UND', 'Caixa de passagem 30x30 cm', 48);
  add('OUT', 'Outros', 'Barra', 'Eletrocalha perfurada 50x50 mm (3 m)', 56);
  add('OUT', 'Outros', 'Kit', 'Parafuso e bucha nº 6 (50 un)', 14);
  add('OUT', 'Outros', 'Rolo', 'Solda de estanho 1 mm', 32);
  return out;
}

function gerarOrdensExemplo(mats: Material[]): OS[] {
  const byCod = (c: string) => mats.find(m => m.codigo === c);
  const mk = (n: number, dias: number, sit: Situacao, cli: Partial<Cliente>, itens: [string, number][], serv: [string, number][], frac: number, parcelas = 1, juros = 0): OS => {
    const its: ItemOS[] = itens.flatMap(([cod, qtd]) => {
      const m = byCod(cod);
      return m ? [{ id: uid(), materialId: m.id, codigo: m.codigo, descricao: m.descricao, categoria: m.categoria, unidade: m.unidade, qtd, preco: m.precoCobrar }] : [];
    });
    const svs: Servico[] = serv.map(([descricao, preco]) => ({ id: uid(), descricao, preco }));
    const totMat = round2(its.reduce((s, i) => s + i.qtd * i.preco, 0));
    const totMO = round2(svs.reduce((s, i) => s + i.preco, 0));
    return {
      id: uid(), numero: 'OS-' + String(n).padStart(4, '0'), data: addDias(dias), emissor: DEFAULT_SETTINGS.usuario, situacao: sit,
      cliente: { nome: '', email: '', telefone: '', rua: '', numero: '', bairro: '', cidade: 'Ji-Paraná/RO', ...cli },
      itens: its, servicos: svs,
      pagamento: { aVista: null, parcelas, juros, valorParcela: null, pagoMateriais: round2(totMat * frac), pagoMaoObra: round2(totMO * frac) },
      observacoes: '',
    };
  };
  return [
    mk(1, -80, 'Concluída', { nome: 'Condomínio Residencial Ipê', telefone: '(69) 3421-0000', rua: 'Rua das Acácias', numero: '210', bairro: 'Centro' },
      [['CAB-002', 150], ['DJM-003', 6], ['ELE-001', 20], ['TOM-003', 12]], [['Instalação elétrica das áreas comuns', 3800]], 1),
    mk(2, -58, 'Concluída', { nome: 'Marcos A. Ribeiro', telefone: '(69) 99999-1111', rua: 'Av. Brasil', numero: '1520', bairro: 'Nova Brasília' },
      [['CAB-005', 80], ['DJM-002', 4], ['QDR-002', 1]], [['Troca de quadro e recomposição de circuitos', 1450]], 1),
    mk(3, -30, 'Em Execução', { nome: 'Padaria Pão Dourado', telefone: '(69) 99999-2222', rua: 'Rua Rio Branco', numero: '88', bairro: 'Dom Bosco' },
      [['CAB-009', 200], ['DJM-011', 8], ['ILU-002', 20], ['TOM-002', 14]], [['Adequação da instalação elétrica', 4200], ['Instalação de iluminação', 900]], 0.5),
    mk(4, -14, 'Aprovada', { nome: 'Clínica Vida Plena', telefone: '(69) 99999-3333', rua: 'Av. Marechal Rondon', numero: '2340', bairro: 'Centro' },
      [['CAB-013', 300], ['QDR-004', 2], ['PRO-001', 2], ['ILU-011', 30]], [['Projeto e instalação elétrica — 2º andar', 6800]], 0.3),
    mk(5, -6, 'Em Orçamento', { nome: 'Edifício Solar das Palmeiras', telefone: '(69) 99999-4444', rua: 'Rua Tiradentes', numero: '455', bairro: 'Centro' },
      [['CAB-017', 400], ['DJM-020', 10], ['ELE-002', 40], ['OUT-005', 4]], [['Reforma do sistema de aterramento e SPDA', 5200]], 0),
    mk(6, -4, 'Cancelada', { nome: 'Loja Casa & Cia', telefone: '(69) 99999-5555', rua: 'Rua Duque de Caxias', numero: '12', bairro: 'Urupá' },
      [['ILU-010', 12], ['TOM-001', 10]], [['Instalação de iluminação da vitrine', 780]], 0),
    mk(7, -1, 'Em Execução', { nome: 'Ana Paula Souza', email: 'ana.souza@exemplo.com', telefone: '(69) 99999-6666', rua: 'Rua Ipê Amarelo', numero: '73', bairro: 'Jardim Presidencial' },
      [['CAB-006', 120], ['DJM-005', 5], ['TOM-005', 9], ['ELE-003', 15]], [['Instalação elétrica residencial completa', 3200]], 0.4, 6, 2),
  ];
}

/* =====================================================================
   ÍCONES E ESTILOS BASE
   ===================================================================== */
const ICONS: Record<string, string[]> = {
  bolt: ['M13 2 3 14h9l-1 8 10-12h-9l1-8z'],
  dash: ['M3 3h7v9H3z', 'M14 3h7v5h-7z', 'M14 12h7v9h-7z', 'M3 16h7v5H3z'],
  box: ['M21 8 12 3 3 8v8l9 5 9-5z', 'M3 8l9 5 9-5', 'M12 13v8'],
  file: ['M14 3H7a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V8z', 'M14 3v5h5', 'M9 13h6', 'M9 17h6'],
  list: ['M8 6h13', 'M8 12h13', 'M8 18h13', 'M3 6h.01', 'M3 12h.01', 'M3 18h.01'],
  plus: ['M12 5v14', 'M5 12h14'],
  trash: ['M3 6h18', 'M8 6V4h8v2', 'M6 6l1 14h10l1-14', 'M10 11v6', 'M14 11v6'],
  edit: ['M12 20h9', 'M16.5 3.5a2.1 2.1 0 0 1 3 3L7 19l-4 1 1-4z'],
  print: ['M6 9V3h12v6', 'M6 18H4a1 1 0 0 1-1-1v-6a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2v6a1 1 0 0 1-1 1h-2', 'M6 14h12v7H6z'],
  eye: ['M2 12s3.5-7 10-7 10 7 10 7-3.5 7-10 7S2 12 2 12z', 'M12 9a3 3 0 1 0 0 6 3 3 0 0 0 0-6z'],
  search: ['M11 4a7 7 0 1 0 0 14 7 7 0 0 0 0-14z', 'M21 21l-4.3-4.3'],
  save: ['M5 3h11l3 3v15H5z', 'M8 3v6h8V3', 'M8 21v-7h8v7'],
  x: ['M18 6 6 18', 'M6 6l12 12'],
  sliders: ['M4 21v-7', 'M4 10V3', 'M12 21v-9', 'M12 8V3', 'M20 21v-5', 'M20 12V3', 'M1 14h6', 'M9 8h6', 'M17 16h6'],
  wallet: ['M3 7a2 2 0 0 1 2-2h13v4', 'M3 7v11a2 2 0 0 0 2 2h15a1 1 0 0 0 1-1V9a1 1 0 0 0-1-1H5a2 2 0 0 1-2-2', 'M16 14h.01'],
  coins: ['M12 3a8 4 0 1 0 0 8 8 4 0 0 0 0-8z', 'M4 7v5c0 2.2 3.6 4 8 4s8-1.8 8-4V7', 'M4 12v5c0 2.2 3.6 4 8 4s8-1.8 8-4v-5'],
};
function Icon({ n, size = 18, className = '' }: { n: string; size?: number; className?: string }) {
  return (
    <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className} aria-hidden="true">
      {ICONS[n].map((d, i) => <path key={i} d={d} />)}
    </svg>
  );
}

const STATUS: Record<Situacao, { badge: string; bar: string; text: string; soft: string }> = {
  'Em Orçamento': { badge: 'bg-amber-100 text-amber-900 border-amber-300', bar: 'bg-amber-400', text: 'text-amber-700', soft: 'bg-amber-50' },
  'Aprovada': { badge: 'bg-sky-100 text-sky-900 border-sky-300', bar: 'bg-sky-500', text: 'text-sky-700', soft: 'bg-sky-50' },
  'Em Execução': { badge: 'bg-indigo-100 text-indigo-900 border-indigo-300', bar: 'bg-indigo-500', text: 'text-indigo-700', soft: 'bg-indigo-50' },
  'Concluída': { badge: 'bg-emerald-100 text-emerald-900 border-emerald-300', bar: 'bg-emerald-500', text: 'text-emerald-700', soft: 'bg-emerald-50' },
  'Cancelada': { badge: 'bg-red-100 text-red-900 border-red-300', bar: 'bg-red-500', text: 'text-red-700', soft: 'bg-red-50' },
};

const inputCls = 'w-full rounded-md border border-slate-300 bg-white px-3 py-2 text-sm text-slate-900 placeholder:text-slate-400 focus:border-navy-600 focus:outline-none focus:ring-2 focus:ring-navy-600/30 disabled:bg-slate-100 disabled:text-slate-500';
const BTN: Record<string, string> = {
  primary: 'bg-navy-800 text-white hover:bg-navy-700',
  secondary: 'border border-slate-300 bg-white text-navy-800 hover:bg-slate-50',
  danger: 'bg-red-600 text-white hover:bg-red-700',
  volt: 'bg-volt-500 text-navy-900 hover:bg-volt-400',
  ghost: 'text-navy-700 hover:bg-navy-50',
};
const B = (k: string) => 'inline-flex items-center justify-center gap-2 rounded-md px-4 py-2 text-sm font-semibold transition-colors focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-navy-600 disabled:opacity-50 ' + BTN[k];
const iconBtn = 'inline-flex items-center gap-1.5 rounded-md p-1.5 text-xs font-semibold text-navy-700 hover:bg-navy-50 focus-visible:outline focus-visible:outline-2 focus-visible:outline-navy-600';

/* =====================================================================
   COMPONENTES BASE
   ===================================================================== */
function Field({ label, error, children, className = '' }: any) {
  return (
    <label className={'block ' + className}>
      <span className="mb-1 block text-xs font-semibold text-slate-600">{label}</span>
      {children}
      {error && <span className="mt-1 block text-xs font-medium text-red-600">{error}</span>}
    </label>
  );
}

function NumInput({ value, onChange, placeholder, allowNull = false, disabled = false, className = '', ariaLabel }: any) {
  const parse = (t: string): number | null => {
    if (t.trim() === '') return allowNull ? null : 0;
    const n = Number(t.replace(',', '.'));
    return Number.isNaN(n) ? 0 : n;
  };
  const fmt = (v: number | null) => (v == null ? '' : String(v));
  const [txt, setTxt] = useState<string>(fmt(value));
  useEffect(() => { if (parse(txt) !== value) setTxt(fmt(value)); }, [value]);
  return (
    <input
      type="text" inputMode="decimal" value={txt} placeholder={placeholder} disabled={disabled} aria-label={ariaLabel}
      className={inputCls + ' num text-right ' + className}
      onFocus={e => e.target.select()}
      onChange={e => {
        const t = e.target.value;
        if (!/^\d*[.,]?\d*$/.test(t)) return;
        setTxt(t);
        const p = parse(t);
        if (p !== value) onChange(p);
      }}
    />
  );
}

function Modal({ title, onClose, children, footer, wide }: any) {
  useEffect(() => {
    const k = (e: KeyboardEvent) => { if (e.key === 'Escape') onClose(); };
    window.addEventListener('keydown', k);
    return () => window.removeEventListener('keydown', k);
  }, []);
  return (
    <div className="fixed inset-0 z-50 flex items-end justify-center bg-navy-900/60 p-0 sm:items-center sm:p-4" role="dialog" aria-modal="true" aria-label={title}
      onMouseDown={e => { if (e.target === e.currentTarget) onClose(); }}>
      <div className={'flex max-h-[92vh] w-full flex-col rounded-t-xl bg-white shadow-2xl sm:rounded-xl ' + (wide ? 'sm:max-w-2xl' : 'sm:max-w-md')}>
        <div className="flex items-center justify-between border-b border-slate-200 px-5 py-3">
          <h2 className="font-display text-xl font-bold text-navy-900">{title}</h2>
          <button onClick={onClose} aria-label="Fechar" className="rounded p-1 text-slate-500 hover:bg-slate-100"><Icon n="x" /></button>
        </div>
        <div className="overflow-y-auto px-5 py-4">{children}</div>
        {footer && <div className="flex flex-wrap justify-end gap-2 border-t border-slate-200 px-5 py-3">{footer}</div>}
      </div>
    </div>
  );
}

function ConfirmDialog({ dados, onClose }: any) {
  return (
    <Modal title={dados.titulo} onClose={onClose}
      footer={<>
        <button className={B('secondary')} onClick={onClose}>Cancelar</button>
        <button className={B('danger')} onClick={() => { dados.onOk(); onClose(); }}>{dados.label}</button>
      </>}>
      <p className="text-sm text-slate-700">{dados.msg}</p>
    </Modal>
  );
}

function Card({ title, action, children, className = '' }: any) {
  return (
    <section className={'rounded-xl border border-slate-200 bg-white shadow-sm ' + className}>
      {(title || action) && (
        <div className="flex flex-wrap items-center justify-between gap-2 border-b border-slate-100 px-4 py-3 sm:px-5">
          <h2 className="font-display text-lg font-bold text-navy-900">{title}</h2>
          {action}
        </div>
      )}
      <div className="p-4 sm:p-5">{children}</div>
    </section>
  );
}

function Badge({ s }: { s: Situacao }) {
  return <span className={'inline-block whitespace-nowrap rounded-full border px-2.5 py-0.5 text-xs font-semibold ' + STATUS[s].badge}>{s}</span>;
}

function StatusSelect({ value, onChange }: { value: Situacao; onChange: (s: Situacao) => void }) {
  return (
    <select value={value} onChange={e => onChange(e.target.value as Situacao)} aria-label="Alterar situação"
      className={'cursor-pointer rounded-full border px-2.5 py-1 text-xs font-semibold focus:outline-none focus:ring-2 focus:ring-navy-600/40 ' + STATUS[value].badge}>
      {SITUACOES.map(s => <option key={s} value={s}>{s}</option>)}
    </select>
  );
}

/* =====================================================================
   ABA 1 — DASHBOARD
   ===================================================================== */
function Metric({ label, value, icon, tone = 'neutral' }: any) {
  const tones: Record<string, string> = {
    neutral: 'border-slate-200 bg-white',
    green: 'border-emerald-300 bg-emerald-50',
    red: 'border-red-300 bg-red-50',
  };
  const valueTone: Record<string, string> = { neutral: 'text-navy-900', green: 'text-emerald-700', red: 'text-red-700' };
  const iconTone: Record<string, string> = { neutral: 'bg-navy-50 text-navy-700', green: 'bg-emerald-100 text-emerald-700', red: 'bg-red-100 text-red-700' };
  return (
    <div className={'flex items-start justify-between gap-3 rounded-xl border p-4 shadow-sm ' + tones[tone]}>
      <div className="min-w-0">
        <div className="text-sm font-medium text-slate-600">{label}</div>
        <div className={'num mt-1 truncate font-display text-2xl font-bold sm:text-3xl ' + valueTone[tone]}>{value}</div>
      </div>
      <div className={'flex h-10 w-10 flex-none items-center justify-center rounded-lg ' + iconTone[tone]}><Icon n={icon} size={20} /></div>
    </div>
  );
}

function Dashboard({ materiais, ordens, go, onEdit }: any) {
  const stat = useMemo(() => {
    const valorEstoque = round2(materiais.reduce((s: number, m: Material) => s + m.precoUnit * m.estoque, 0));
    let fat = 0, rec = 0, sal = 0;
    ordens.forEach((o: OS) => {
      if (o.situacao === 'Cancelada') return;
      const c = calc(o);
      fat += c.valorTotal; rec += Math.min(c.pagoTotal, c.valorTotal); sal += c.saldo;
    });
    const por: Record<string, number> = {};
    SITUACOES.forEach(s => { por[s] = ordens.filter((o: OS) => o.situacao === s).length; });
    return { valorEstoque, fat: round2(fat), rec: round2(rec), sal: round2(sal), por };
  }, [materiais, ordens]);

  const recentes = useMemo(() => [...ordens].sort((a: OS, b: OS) => b.data.localeCompare(a.data) || b.numero.localeCompare(a.numero)).slice(0, 6), [ordens]);

  return (
    <div className="space-y-6">
      <div className="grid grid-cols-1 gap-3 sm:grid-cols-2 lg:grid-cols-3">
        <Metric label="Materiais Cadastrados" value={materiais.length} icon="box" />
        <Metric label="Valor em Estoque" value={money(stat.valorEstoque)} icon="coins" />
        <Metric label="Total de OS" value={ordens.length} icon="file" />
        <Metric label="Faturamento Total" value={money(stat.fat)} icon="wallet" />
        <Metric label="Total Recebido" value={money(stat.rec)} icon="wallet" tone="green" />
        <Metric label="Saldo a Receber" value={money(stat.sal)} icon="wallet" tone="red" />
      </div>
      <p className="-mt-3 text-xs text-slate-500">Faturamento, recebido e saldo não incluem OS canceladas.</p>

      <div>
        <h2 className="mb-2 font-display text-lg font-bold text-navy-900">Ordens de serviço por situação</h2>
        <div className="grid grid-cols-2 gap-3 md:grid-cols-3 lg:grid-cols-5">
          {SITUACOES.map(s => (
            <button key={s} onClick={() => go('lista', s)}
              className={'overflow-hidden rounded-xl border border-slate-200 text-left shadow-sm transition hover:shadow-md focus-visible:outline focus-visible:outline-2 focus-visible:outline-navy-600 ' + STATUS[s].soft}>
              <div className={'h-1.5 ' + STATUS[s].bar} />
              <div className="p-3">
                <div className={'text-sm font-semibold ' + STATUS[s].text}>{s}</div>
                <div className="num font-display text-3xl font-bold text-navy-900">{stat.por[s]}</div>
              </div>
            </button>
          ))}
        </div>
      </div>

      <Card title="Ordens de serviço recentes" action={<button className={B('secondary')} onClick={() => go('lista', 'Todas')}>Ver todas</button>}>
        <div className="-mx-4 overflow-x-auto sm:-mx-5">
          <table className="w-full min-w-[640px] text-sm">
            <thead>
              <tr className="border-b border-slate-200 text-left text-xs font-semibold text-slate-500">
                <th className="px-4 py-2 sm:px-5">Nº da OS</th><th className="px-2 py-2">Cliente</th><th className="px-2 py-2">Data</th>
                <th className="px-2 py-2 text-right">Valor total</th><th className="px-2 py-2 text-right">Saldo</th><th className="px-4 py-2 sm:px-5">Status</th>
              </tr>
            </thead>
            <tbody>
              {recentes.length === 0 && <tr><td colSpan={6} className="px-5 py-8 text-center text-slate-500">Nenhuma OS criada ainda. Use a aba “Orçamento / OS” para criar a primeira.</td></tr>}
              {recentes.map((o: OS) => { const c = calc(o); return (
                <tr key={o.id} className="border-b border-slate-100 last:border-0 hover:bg-slate-50">
                  <td className="px-4 py-2.5 font-semibold sm:px-5"><button className="text-navy-700 underline-offset-2 hover:underline" onClick={() => onEdit(o)}>{o.numero}</button></td>
                  <td className="px-2 py-2.5">{o.cliente.nome || '—'}</td>
                  <td className="num px-2 py-2.5">{fmtData(o.data)}</td>
                  <td className="num px-2 py-2.5 text-right">{money(c.valorTotal)}</td>
                  <td className={'num px-2 py-2.5 text-right font-semibold ' + (c.saldo > 0 && o.situacao !== 'Cancelada' ? 'text-red-600' : 'text-emerald-600')}>{money(o.situacao === 'Cancelada' ? 0 : c.saldo)}</td>
                  <td className="px-4 py-2.5 sm:px-5"><Badge s={o.situacao} /></td>
                </tr>
              ); })}
            </tbody>
          </table>
        </div>
      </Card>
    </div>
  );
}

/* =====================================================================
   ABA 2 — CATÁLOGO DE MATERIAIS
   ===================================================================== */
function MaterialModal({ material, materiais, categorias, onSave, onClose }: any) {
  const [f, setF] = useState<Material>(material || { id: uid(), codigo: '', descricao: '', categoria: '', unidade: 'UND', precoUnit: 0, precoCobrar: 0, estoque: 0 });
  const [err, setErr] = useState<Record<string, string>>({});
  const set = (p: Partial<Material>) => setF(x => ({ ...x, ...p }));
  const submit = () => {
    const e: Record<string, string> = {};
    if (!f.codigo.trim()) e.codigo = 'Informe o código';
    else if (materiais.some((m: Material) => m.id !== f.id && m.codigo.toLowerCase() === f.codigo.trim().toLowerCase())) e.codigo = 'Já existe um material com este código';
    if (!f.descricao.trim()) e.descricao = 'Informe a descrição';
    if (!f.categoria.trim()) e.categoria = 'Informe a categoria';
    setErr(e);
    if (Object.keys(e).length) return;
    onSave({ ...f, codigo: f.codigo.trim(), descricao: f.descricao.trim(), categoria: f.categoria.trim() });
  };
  const margem = f.precoUnit > 0 ? Math.round((f.precoCobrar / f.precoUnit - 1) * 100) : null;
  return (
    <Modal title={material ? 'Editar material' : 'Novo material'} onClose={onClose} wide
      footer={<><button className={B('secondary')} onClick={onClose}>Cancelar</button><button className={B('primary')} onClick={submit}><Icon n="save" size={16} />Salvar material</button></>}>
      <div className="grid grid-cols-1 gap-3 sm:grid-cols-2">
        <Field label="Código do material *" error={err.codigo}><input autoFocus className={inputCls} value={f.codigo} onChange={e => set({ codigo: e.target.value })} placeholder="Ex.: CAB-030" /></Field>
        <Field label="Categoria *" error={err.categoria}>
          <input className={inputCls} list="lista-categorias" value={f.categoria} onChange={e => set({ categoria: e.target.value })} placeholder="Ex.: Iluminação" />
          <datalist id="lista-categorias">{categorias.map((c: string) => <option key={c} value={c} />)}</datalist>
        </Field>
        <Field label="Descrição *" error={err.descricao} className="sm:col-span-2"><input className={inputCls} value={f.descricao} onChange={e => set({ descricao: e.target.value })} placeholder="Ex.: Cabo flexível 750 V 2,5 mm² Azul" /></Field>
        <Field label="Unidade de medida">
          <select className={inputCls} value={f.unidade} onChange={e => set({ unidade: e.target.value })}>{UNIDADES.map(u => <option key={u}>{u}</option>)}</select>
        </Field>
        <Field label="Quantidade em estoque"><NumInput value={f.estoque} onChange={(v: number) => set({ estoque: v })} /></Field>
        <Field label="Preço unitário (custo) — R$"><NumInput value={f.precoUnit} onChange={(v: number) => set({ precoUnit: v })} /></Field>
        <Field label="Preço a cobrar (venda) — R$"><NumInput value={f.precoCobrar} onChange={(v: number) => set({ precoCobrar: v })} /></Field>
      </div>
      {margem !== null && <p className="mt-3 text-xs text-slate-500">Margem sobre o custo: <b className="num">{margem}%</b></p>}
    </Modal>
  );
}

function Materiais({ materiais, setMateriais, notify }: any) {
  const [busca, setBusca] = useState('');
  const [cat, setCat] = useState('Todas');
  const [page, setPage] = useState(0);
  const [modal, setModal] = useState<null | { mat: Material | null }>(null);
  const [confirm, setConfirm] = useState<any>(null);
  const PER = 20;

  const categorias = useMemo(() => Array.from(new Set(materiais.map((m: Material) => m.categoria))).sort((a: any, b: any) => a.localeCompare(b)) as string[], [materiais]);
  const filtrados = useMemo(() => {
    const q = busca.trim().toLowerCase();
    return materiais
      .filter((m: Material) => (cat === 'Todas' || m.categoria === cat) && (!q || m.codigo.toLowerCase().includes(q) || m.descricao.toLowerCase().includes(q)))
      .sort((a: Material, b: Material) => a.codigo.localeCompare(b.codigo, 'pt-BR', { numeric: true }));
  }, [materiais, busca, cat]);
  const pages = Math.max(1, Math.ceil(filtrados.length / PER));
  const p = Math.min(page, pages - 1);
  const fatia = filtrados.slice(p * PER, p * PER + PER);

  const salvar = (m: Material) => {
    const existe = materiais.some((x: Material) => x.id === m.id);
    setMateriais((list: Material[]) => existe ? list.map(x => x.id === m.id ? m : x) : [...list, m]);
    setModal(null);
    notify(existe ? 'Material atualizado.' : 'Material cadastrado.');
  };
  const excluir = (m: Material) => setConfirm({
    titulo: 'Excluir material?', msg: 'O material ' + m.codigo + ' — ' + m.descricao + ' será removido do catálogo. OS já criadas não são alteradas.', label: 'Excluir',
    onOk: () => { setMateriais((list: Material[]) => list.filter(x => x.id !== m.id)); notify('Material excluído.'); },
  });

  return (
    <div className="space-y-4">
      <div className="flex flex-col gap-3 rounded-xl border border-slate-200 bg-white p-3 shadow-sm sm:flex-row sm:items-center">
        <div className="relative flex-1">
          <Icon n="search" size={16} className="pointer-events-none absolute left-3 top-1/2 -translate-y-1/2 text-slate-400" />
          <input className={inputCls + ' pl-9'} placeholder="Buscar por código ou descrição" value={busca} onChange={e => { setBusca(e.target.value); setPage(0); }} aria-label="Buscar material" />
        </div>
        <select className={inputCls + ' sm:w-56'} value={cat} onChange={e => { setCat(e.target.value); setPage(0); }} aria-label="Filtrar por categoria">
          <option>Todas</option>{categorias.map(c => <option key={c}>{c}</option>)}
        </select>
        <button className={B('volt')} onClick={() => setModal({ mat: null })}><Icon n="plus" size={16} />Novo Material</button>
      </div>

      <div className="overflow-hidden rounded-xl border border-slate-200 bg-white shadow-sm">
        <div className="overflow-x-auto">
          <table className="w-full min-w-[820px] text-sm">
            <thead>
              <tr className="bg-navy-900 text-left text-xs font-semibold text-white">
                <th className="px-4 py-2.5">Código</th><th className="px-2 py-2.5">Descrição</th><th className="px-2 py-2.5">Categoria</th><th className="px-2 py-2.5">Unidade</th>
                <th className="px-2 py-2.5 text-right">Preço unit.</th><th className="px-2 py-2.5 text-right">Preço cobrar</th><th className="px-2 py-2.5 text-right">Estoque</th><th className="px-4 py-2.5 text-right">Ações</th>
              </tr>
            </thead>
            <tbody>
              {fatia.length === 0 && <tr><td colSpan={8} className="px-5 py-10 text-center text-slate-500">Nenhum material encontrado. Ajuste a busca ou cadastre um novo material.</td></tr>}
              {fatia.map((m: Material) => (
                <tr key={m.id} className="border-b border-slate-100 last:border-0 hover:bg-slate-50">
                  <td className="px-4 py-2 font-semibold text-navy-800">{m.codigo}</td>
                  <td className="px-2 py-2">{m.descricao}</td>
                  <td className="px-2 py-2 text-slate-600">{m.categoria}</td>
                  <td className="px-2 py-2">{m.unidade}</td>
                  <td className="num px-2 py-2 text-right">{money(m.precoUnit)}</td>
                  <td className="num px-2 py-2 text-right font-semibold">{money(m.precoCobrar)}</td>
                  <td className={'num px-2 py-2 text-right font-semibold ' + (m.estoque <= 0 ? 'text-red-600' : m.estoque <= 5 ? 'text-amber-600' : 'text-slate-800')}>{qtdFmt.format(m.estoque)}</td>
                  <td className="px-4 py-2 text-right whitespace-nowrap">
                    <button className={iconBtn} onClick={() => setModal({ mat: m })} title="Editar" aria-label={'Editar ' + m.codigo}><Icon n="edit" size={16} /></button>
                    <button className={iconBtn + ' text-red-600 hover:bg-red-50'} onClick={() => excluir(m)} title="Excluir" aria-label={'Excluir ' + m.codigo}><Icon n="trash" size={16} /></button>
                  </td>
                </tr>
              ))}
            </tbody>
          </table>
        </div>
        <div className="flex flex-wrap items-center justify-between gap-2 border-t border-slate-200 px-4 py-2.5 text-sm text-slate-600">
          <span className="num">{filtrados.length === 0 ? '0 itens' : (p * PER + 1) + '–' + Math.min(filtrados.length, p * PER + PER) + ' de ' + filtrados.length + ' itens'}</span>
          <div className="flex items-center gap-2">
            <button className={B('secondary') + ' !px-3 !py-1'} disabled={p === 0} onClick={() => setPage(p - 1)}>Anterior</button>
            <span className="num">Página {p + 1} de {pages}</span>
            <button className={B('secondary') + ' !px-3 !py-1'} disabled={p >= pages - 1} onClick={() => setPage(p + 1)}>Próxima</button>
          </div>
        </div>
      </div>

      {modal && <MaterialModal material={modal.mat} materiais={materiais} categorias={categorias} onSave={salvar} onClose={() => setModal(null)} />}
      {confirm && <ConfirmDialog dados={confirm} onClose={() => setConfirm(null)} />}
    </div>
  );
}

/* =====================================================================
   ABA 3 — PLANILHA DE ORÇAMENTO / CRIAÇÃO DE OS
   ===================================================================== */
function CodigoField({ item, materiais, onPick, onType }: any) {
  const [open, setOpen] = useState(false);
  const q = item.codigo.trim().toLowerCase();
  const exato = materiais.find((m: Material) => m.codigo.toLowerCase() === q);
  const resultados = useMemo(() => {
    if (!open) return [];
    return materiais.filter((m: Material) => !q || m.codigo.toLowerCase().includes(q) || m.descricao.toLowerCase().includes(q)).slice(0, 8);
  }, [open, q, materiais]);
  return (
    <div className="relative">
      <input className={inputCls} value={item.codigo} placeholder="Código ou busca" aria-label="Código do material" autoComplete="off"
        onFocus={() => setOpen(true)}
        onChange={e => { onType(e.target.value); setOpen(true); }}
        onBlur={() => { setTimeout(() => setOpen(false), 120); if (exato && item.materialId !== exato.id) onPick(exato); }}
        onKeyDown={e => {
          if (e.key === 'Enter') { e.preventDefault(); const m = exato || resultados[0]; if (m) { onPick(m); setOpen(false); } }
          if (e.key === 'Escape') setOpen(false);
        }} />
      {open && resultados.length > 0 && (
        <ul className="absolute z-30 mt-1 max-h-64 w-[min(30rem,88vw)] overflow-auto rounded-md border border-slate-200 bg-white shadow-xl">
          {resultados.map((m: Material) => (
            <li key={m.id}>
              <button type="button" className="flex w-full items-baseline gap-3 px-3 py-2 text-left text-sm hover:bg-navy-50"
                onMouseDown={e => { e.preventDefault(); onPick(m); setOpen(false); }}>
                <span className="w-20 flex-none font-semibold text-navy-800">{m.codigo}</span>
                <span className="flex-1">{m.descricao}</span>
                <span className="num flex-none text-xs text-slate-500">{money(m.precoCobrar)}</span>
              </button>
            </li>
          ))}
        </ul>
      )}
    </div>
  );
}

function Cell({ label, children, className = '' }: any) {
  return <div className={className}><span className="mb-1 block text-xs font-semibold text-slate-500 md:hidden">{label}</span>{children}</div>;
}

const ITEM_GRID = 'grid grid-cols-2 gap-2 md:grid-cols-[170px_1fr_84px_84px_112px_118px_36px] md:items-start';

function Box({ label, value, tone = 'neutral', children }: any) {
  const t: Record<string, string> = {
    neutral: 'border-slate-200 bg-white text-navy-900',
    navy: 'border-navy-800 bg-navy-900 text-white',
    green: 'border-emerald-300 bg-emerald-50 text-emerald-800',
    red: 'border-red-300 bg-red-50 text-red-700',
    amber: 'border-amber-300 bg-amber-50 text-amber-900',
  };
  return (
    <div className={'rounded-xl border p-3.5 ' + t[tone]}>
      <div className={'text-xs font-semibold ' + (tone === 'navy' ? 'text-navy-200' : 'opacity-75')}>{label}</div>
      {value !== undefined && <div className="num mt-0.5 font-display text-2xl font-bold">{value}</div>}
      {children}
    </div>
  );
}

function EditorOS({ draft, setDraft, materiais, dirty, existe, tentou, onSave, onPreview, onNova }: any) {
  const c = calc(draft);
  const p: Pagamento = draft.pagamento;
  const upd = (patch: Partial<OS>) => setDraft((d: OS) => ({ ...d, ...patch }));
  const updCli = (patch: Partial<Cliente>) => setDraft((d: OS) => ({ ...d, cliente: { ...d.cliente, ...patch } }));
  const updPag = (patch: Partial<Pagamento>) => setDraft((d: OS) => ({ ...d, pagamento: { ...d.pagamento, ...patch } }));
  const addItem = () => setDraft((d: OS) => ({ ...d, itens: [...d.itens, { id: uid(), codigo: '', descricao: '', categoria: '', unidade: 'UND', qtd: 1, preco: 0 }] }));
  const updItem = (id: string, patch: Partial<ItemOS>) => setDraft((d: OS) => ({ ...d, itens: d.itens.map(i => i.id === id ? { ...i, ...patch } : i) }));
  const delItem = (id: string) => setDraft((d: OS) => ({ ...d, itens: d.itens.filter(i => i.id !== id) }));
  const addServ = () => setDraft((d: OS) => ({ ...d, servicos: [...d.servicos, { id: uid(), descricao: '', preco: 0 }] }));
  const updServ = (id: string, patch: Partial<Servico>) => setDraft((d: OS) => ({ ...d, servicos: d.servicos.map(s => s.id === id ? { ...s, ...patch } : s) }));
  const delServ = (id: string) => setDraft((d: OS) => ({ ...d, servicos: d.servicos.filter(s => s.id !== id) }));
  const pick = (id: string, m: Material) => updItem(id, { materialId: m.id, codigo: m.codigo, descricao: m.descricao, categoria: m.categoria, unidade: m.unidade, preco: m.precoCobrar });
  const erroNome = tentou && !draft.cliente.nome.trim();

  return (
    <div className="space-y-5 pb-4">
      {/* Cabeçalho da empresa + dados da OS */}
      <section className="overflow-hidden rounded-xl border border-slate-200 bg-white shadow-sm">
        <div className="flex flex-wrap items-center justify-between gap-3 bg-navy-900 px-4 py-4 text-white sm:px-5">
          <div className="flex items-center gap-3">
            <div className="flex h-11 w-11 items-center justify-center rounded-lg bg-volt-500 text-navy-900"><Icon n="bolt" size={26} /></div>
            <div>
              <div className="font-display text-xl font-bold leading-tight">E. L. Instalações Elétricas Prediais</div>
              <div className="text-xs text-navy-200">{window.__cfg.telefone} • {window.__cfg.email} • {window.__cfg.cidade}</div>
            </div>
          </div>
          <span className={'rounded-full px-3 py-1 text-xs font-semibold ' + (existe ? 'bg-white/15 text-white' : 'bg-volt-500 text-navy-900')}>
            {existe ? 'Editando ' + draft.numero : 'Nova OS — ainda não salva'}
          </span>
        </div>
        <div className="grid grid-cols-1 gap-3 p-4 sm:grid-cols-2 sm:p-5 lg:grid-cols-4">
          <Field label="Número da OS"><input className={inputCls + ' font-semibold'} value={draft.numero} onChange={e => upd({ numero: e.target.value })} /></Field>
          <Field label="Data de emissão"><input type="date" className={inputCls} value={draft.data} onChange={e => upd({ data: e.target.value })} /></Field>
          <Field label="Emissor"><input className={inputCls} value={draft.emissor} onChange={e => upd({ emissor: e.target.value })} /></Field>
          <Field label="Situação">
            <select className={inputCls + ' font-semibold'} value={draft.situacao} onChange={e => upd({ situacao: e.target.value as Situacao })}>
              {SITUACOES.map(s => <option key={s}>{s}</option>)}
            </select>
          </Field>
        </div>
      </section>

      {/* Cliente */}
      <Card title="Dados do cliente">
        <div className="grid grid-cols-1 gap-3 sm:grid-cols-2 lg:grid-cols-6">
          <Field label="Nome do cliente *" error={erroNome ? 'Informe o nome do cliente' : ''} className="lg:col-span-3"><input className={inputCls + (erroNome ? ' !border-red-500' : '')} value={draft.cliente.nome} onChange={e => updCli({ nome: e.target.value })} /></Field>
          <Field label="E-mail" className="lg:col-span-2"><input type="email" className={inputCls} value={draft.cliente.email} onChange={e => updCli({ email: e.target.value })} /></Field>
          <Field label="Telefone"><input className={inputCls} value={draft.cliente.telefone} onChange={e => updCli({ telefone: e.target.value })} /></Field>
          <Field label="Rua" className="lg:col-span-3"><input className={inputCls} value={draft.cliente.rua} onChange={e => updCli({ rua: e.target.value })} /></Field>
          <Field label="Nº"><input className={inputCls} value={draft.cliente.numero} onChange={e => updCli({ numero: e.target.value })} /></Field>
          <Field label="Bairro"><input className={inputCls} value={draft.cliente.bairro} onChange={e => updCli({ bairro: e.target.value })} /></Field>
          <Field label="Cidade"><input className={inputCls} value={draft.cliente.cidade} onChange={e => updCli({ cidade: e.target.value })} /></Field>
        </div>
      </Card>

      {/* Materiais */}
      <Card title="Materiais" action={<button className={B('primary')} onClick={addItem}><Icon n="plus" size={16} />Adicionar Item</button>}>
        {draft.itens.length === 0 ? (
          <p className="py-4 text-center text-sm text-slate-500">Nenhum material na OS. Clique em “Adicionar Item” e digite o código ou parte da descrição.</p>
        ) : (
          <div className="space-y-3 md:space-y-2">
            <div className={'hidden text-xs font-semibold text-slate-500 md:grid md:grid-cols-[170px_1fr_84px_84px_112px_118px_36px] md:gap-2'}>
              <span>Código</span><span>Descrição</span><span>Unid.</span><span className="text-right">Qtd</span><span className="text-right">Preço unit.</span><span className="text-right">Total</span><span />
            </div>
            {draft.itens.map((it: ItemOS) => (
              <div key={it.id} className={ITEM_GRID + ' rounded-lg border border-slate-200 p-3 md:border-0 md:p-0'}>
                <Cell label="Código" className="col-span-2 md:col-span-1"><CodigoField item={it} materiais={materiais} onPick={(m: Material) => pick(it.id, m)} onType={(v: string) => updItem(it.id, { codigo: v, materialId: undefined })} /></Cell>
                <Cell label="Descrição" className="col-span-2 md:col-span-1">
                  <input className={inputCls} value={it.descricao} placeholder="Descrição do material" onChange={e => updItem(it.id, { descricao: e.target.value })} aria-label="Descrição" />
                  {it.categoria && <span className="mt-0.5 block text-xs text-slate-500">{it.categoria}</span>}
                </Cell>
                <Cell label="Unid."><input className={inputCls} value={it.unidade} onChange={e => updItem(it.id, { unidade: e.target.value })} aria-label="Unidade" /></Cell>
                <Cell label="Qtd"><NumInput value={it.qtd} onChange={(v: number) => updItem(it.id, { qtd: v })} ariaLabel="Quantidade" /></Cell>
                <Cell label="Preço unit. (R$)"><NumInput value={it.preco} onChange={(v: number) => updItem(it.id, { preco: v })} ariaLabel="Preço unitário" /></Cell>
                <Cell label="Total"><div className="num flex h-[38px] items-center justify-end rounded-md bg-slate-50 px-2 text-sm font-semibold text-navy-900">{money((it.qtd || 0) * (it.preco || 0))}</div></Cell>
                <div className="col-span-2 flex justify-end md:col-span-1">
                  <button className={iconBtn + ' h-[38px] text-red-600 hover:bg-red-50'} onClick={() => delItem(it.id)} title="Remover item" aria-label="Remover item"><Icon n="trash" size={16} /></button>
                </div>
              </div>
            ))}
          </div>
        )}
        <div className="mt-3 flex justify-end border-t border-slate-100 pt-3 text-sm">
          <span className="text-slate-600">Total de materiais:&nbsp;</span><span className="num font-bold text-navy-900">{money(c.totMat)}</span>
        </div>
      </Card>

      {/* Mão de obra */}
      <Card title="Mão de obra" action={<button className={B('primary')} onClick={addServ}><Icon n="plus" size={16} />Adicionar Serviço</button>}>
        {draft.servicos.length === 0 ? (
          <p className="py-4 text-center text-sm text-slate-500">Nenhum serviço informado. Clique em “Adicionar Serviço” para descrever a mão de obra.</p>
        ) : (
          <div className="space-y-2">
            {draft.servicos.map((s: Servico) => (
              <div key={s.id} className="grid grid-cols-[1fr_auto] items-start gap-2 sm:grid-cols-[1fr_150px_36px]">
                <input className={inputCls + ' col-span-2 sm:col-span-1'} value={s.descricao} placeholder="Descrição do serviço prestado" aria-label="Descrição do serviço" onChange={e => updServ(s.id, { descricao: e.target.value })} />
                <NumInput value={s.preco} onChange={(v: number) => updServ(s.id, { preco: v })} ariaLabel="Preço do serviço" />
                <button className={iconBtn + ' h-[38px] text-red-600 hover:bg-red-50'} onClick={() => delServ(s.id)} title="Remover serviço" aria-label="Remover serviço"><Icon n="trash" size={16} /></button>
              </div>
            ))}
          </div>
        )}
        <div className="mt-3 flex justify-end border-t border-slate-100 pt-3 text-sm">
          <span className="text-slate-600">Total de mão de obra:&nbsp;</span><span className="num font-bold text-navy-900">{money(c.totMO)}</span>
        </div>
      </Card>

      {/* Resumo financeiro */}
      <Card title="Resumo financeiro e condições de pagamento">
        <div className="grid grid-cols-1 gap-3 sm:grid-cols-2 lg:grid-cols-4">
          <Box label="Total de materiais" value={money(c.totMat)} />
          <Box label="Total de mão de obra" value={money(c.totMO)} />
          <Box label="Total à vista" tone="navy">
            <NumInput value={p.aVista} allowNull placeholder={String(c.totalGeral)} onChange={(v: number | null) => updPag({ aVista: v })} className="mt-1 !border-navy-600 !bg-navy-800 !text-lg !font-bold !text-white placeholder:!text-navy-300" ariaLabel="Total à vista" />
            <div className="mt-1 flex items-center justify-between text-xs text-navy-200">
              <span className="num">{p.aVista == null ? 'Soma automática' : 'Soma dos itens: ' + money(c.totalGeral)}</span>
              {p.aVista != null && <button className="font-semibold text-volt-400 underline" onClick={() => updPag({ aVista: null })}>Restaurar</button>}
            </div>
          </Box>
          <Box label="Saldo restante" value={money(c.saldo)} tone={c.saldo > 0 ? 'red' : 'green'} />
        </div>

        <div className="mt-4 grid grid-cols-1 gap-3 sm:grid-cols-2 lg:grid-cols-5">
          <Field label="Parcelas">
            <select className={inputCls} value={p.parcelas} onChange={e => updPag({ parcelas: Number(e.target.value), valorParcela: null })}>
              {Array.from({ length: 12 }, (_, i) => i + 1).map(n => <option key={n} value={n}>{n === 1 ? '1x (à vista)' : n + 'x'}</option>)}
            </select>
          </Field>
          <Field label="Juros sobre o saldo (%)">
            <NumInput value={p.juros} disabled={p.parcelas === 1} onChange={(v: number) => updPag({ juros: v, valorParcela: null })} ariaLabel="Juros sobre o saldo" />
          </Field>
          <Field label="Valor de cada parcela (R$)">
            <NumInput value={p.valorParcela} allowNull placeholder={String(c.sugerida)} onChange={(v: number | null) => updPag({ valorParcela: v })} ariaLabel="Valor de cada parcela" />
            <span className="mt-1 flex items-center justify-between text-xs text-slate-500">
              <span className="num">{p.valorParcela == null ? 'Sugestão: ' + money(c.sugerida) : 'Editado (sug. ' + money(c.sugerida) + ')'}</span>
              {p.valorParcela != null && <button type="button" className="font-semibold text-navy-700 underline" onClick={() => updPag({ valorParcela: null })}>Usar sugestão</button>}
            </span>
          </Field>
          <Field label="Já pago — materiais (R$)"><NumInput value={p.pagoMateriais} onChange={(v: number) => updPag({ pagoMateriais: v, valorParcela: null })} /></Field>
          <Field label="Já pago — mão de obra (R$)"><NumInput value={p.pagoMaoObra} onChange={(v: number) => updPag({ pagoMaoObra: v, valorParcela: null })} /></Field>
        </div>

        <div className="mt-4 grid grid-cols-1 gap-3 sm:grid-cols-3">
          <Box label="Valor pago total" value={money(c.pagoTotal)} tone="green" />
          <Box label="Saldo com juros" value={money(c.saldoJuros)} tone={c.saldoJuros > 0 ? 'amber' : 'neutral'} />
          <Box label={'Valor total parcelado (' + c.n + 'x)'} value={money(c.totalParcelado)} />
        </div>
        {c.pagoTotal > c.valorTotal && <p className="mt-3 rounded-md bg-amber-50 px-3 py-2 text-sm font-medium text-amber-900">Atenção: os valores pagos superam o total à vista desta OS.</p>}

        <Field label="Observações (aparecem na impressão)" className="mt-4">
          <textarea rows={3} className={inputCls} value={draft.observacoes} onChange={e => upd({ observacoes: e.target.value })} placeholder="Prazo de execução, garantia, forma de pagamento, etc." />
        </Field>
      </Card>

      {/* Barra de ações */}
      <div className="sticky z-30 -mx-4 border-t border-slate-200 bg-white/95 px-4 py-3 shadow-[0_-4px_14px_rgba(15,32,57,.08)] backdrop-blur sm:-mx-6 sm:px-6" style={{ bottom: 'env(safe-area-inset-bottom, 0px)' }}>
        <div className="mx-auto flex max-w-7xl flex-wrap items-center gap-2">
          <button className={B('primary')} onClick={onSave}><Icon n="save" size={16} />Salvar OS</button>
          <button className={B('secondary')} onClick={onPreview}><Icon n="print" size={16} />Pré-visualizar / Imprimir</button>
          <button className={B('ghost')} onClick={onNova}><Icon n="plus" size={16} />Nova OS</button>
          {dirty && <span className="ml-auto rounded-full bg-amber-100 px-3 py-1 text-xs font-semibold text-amber-900">Alterações não salvas</span>}
        </div>
      </div>
    </div>
  );
}

/* =====================================================================
   ABA 4 — GESTÃO E LISTAGEM DE OS
   ===================================================================== */
function ListaOS({ ordens, filtro, setFiltro, onEdit, onView, onPrint, onDelete, onStatus }: any) {
  const [busca, setBusca] = useState('');
  const lista = useMemo(() => {
    const q = busca.trim().toLowerCase();
    return ordens
      .filter((o: OS) => (filtro === 'Todas' || o.situacao === filtro) && (!q || o.numero.toLowerCase().includes(q) || o.cliente.nome.toLowerCase().includes(q)))
      .sort((a: OS, b: OS) => b.data.localeCompare(a.data) || b.numero.localeCompare(a.numero));
  }, [ordens, busca, filtro]);

  return (
    <div className="space-y-4">
      <div className="flex flex-col gap-3 rounded-xl border border-slate-200 bg-white p-3 shadow-sm sm:flex-row sm:items-center">
        <div className="relative flex-1">
          <Icon n="search" size={16} className="pointer-events-none absolute left-3 top-1/2 -translate-y-1/2 text-slate-400" />
          <input className={inputCls + ' pl-9'} placeholder="Buscar por número da OS ou nome do cliente" value={busca} onChange={e => setBusca(e.target.value)} aria-label="Buscar OS" />
        </div>
        <select className={inputCls + ' sm:w-56'} value={filtro} onChange={e => setFiltro(e.target.value)} aria-label="Filtrar por situação">
          <option>Todas</option>{SITUACOES.map(s => <option key={s}>{s}</option>)}
        </select>
      </div>

      <div className="overflow-hidden rounded-xl border border-slate-200 bg-white shadow-sm">
        <div className="overflow-x-auto">
          <table className="w-full min-w-[980px] text-sm">
            <thead>
              <tr className="bg-navy-900 text-left text-xs font-semibold text-white">
                <th className="px-4 py-2.5">Nº da OS</th><th className="px-2 py-2.5">Cliente</th><th className="px-2 py-2.5">Data</th>
                <th className="px-2 py-2.5 text-right">Valor total</th><th className="px-2 py-2.5 text-right">Valor pago</th><th className="px-2 py-2.5 text-right">Saldo</th>
                <th className="px-3 py-2.5">Situação</th><th className="px-4 py-2.5 text-right">Ações</th>
              </tr>
            </thead>
            <tbody>
              {lista.length === 0 && <tr><td colSpan={8} className="px-5 py-10 text-center text-slate-500">Nenhuma ordem de serviço encontrada.</td></tr>}
              {lista.map((o: OS) => { const c = calc(o); const cancel = o.situacao === 'Cancelada'; return (
                <tr key={o.id} className="border-b border-slate-100 last:border-0 hover:bg-slate-50">
                  <td className="px-4 py-2.5 font-semibold text-navy-800">{o.numero}</td>
                  <td className="px-2 py-2.5">{o.cliente.nome || <span className="text-slate-400">Sem cliente</span>}</td>
                  <td className="num px-2 py-2.5">{fmtData(o.data)}</td>
                  <td className="num px-2 py-2.5 text-right">{money(c.valorTotal)}</td>
                  <td className="num px-2 py-2.5 text-right text-emerald-700">{money(c.pagoTotal)}</td>
                  <td className={'num px-2 py-2.5 text-right font-semibold ' + (cancel ? 'text-slate-400' : c.saldo > 0 ? 'text-red-600' : 'text-emerald-600')}>{money(cancel ? 0 : c.saldo)}</td>
                  <td className="px-3 py-2.5"><StatusSelect value={o.situacao} onChange={s => onStatus(o.id, s)} /></td>
                  <td className="whitespace-nowrap px-3 py-2.5 text-right">
                    <button className={iconBtn} onClick={() => onView(o)} title="Visualizar" aria-label={'Visualizar ' + o.numero}><Icon n="eye" size={16} /></button>
                    <button className={iconBtn} onClick={() => onEdit(o)} title="Editar OS" aria-label={'Editar ' + o.numero}><Icon n="edit" size={16} /></button>
                    <button className={iconBtn} onClick={() => onPrint(o)} title="Imprimir orçamento" aria-label={'Imprimir orçamento ' + o.numero}><Icon n="print" size={16} /><span className="hidden xl:inline">Imprimir</span></button>
                    <button className={iconBtn + ' text-red-600 hover:bg-red-50'} onClick={() => onDelete(o)} title="Excluir" aria-label={'Excluir ' + o.numero}><Icon n="trash" size={16} /></button>
                  </td>
                </tr>
              ); })}
            </tbody>
          </table>
        </div>
        <div className="border-t border-slate-200 px-4 py-2.5 text-sm text-slate-600 num">{lista.length} {lista.length === 1 ? 'ordem' : 'ordens'} exibida{lista.length === 1 ? '' : 's'}</div>
      </div>
    </div>
  );
}

/* =====================================================================
   DOCUMENTO A4 (visualização e impressão)
   ===================================================================== */
function Documento({ os, settings }: { os: OS; settings: Settings }) {
  const c = calc(os);
  const cl = os.cliente;
  const p = os.pagamento;
  const endereco = [cl.rua && (cl.numero ? cl.rua + ', ' + cl.numero : cl.rua), cl.bairro, cl.cidade].filter(Boolean).join(' — ');
  return (
    <article className="sheet doc">
      <header className="doc-head">
        <div className="doc-brand">
          <div className="doc-logo"><Icon n="bolt" size={26} /></div>
          <div>
            <div className="doc-name">E. L. Instalações Elétricas Prediais</div>
            <div className="doc-sub">{[settings.cidade, settings.cnpj && 'CNPJ ' + settings.cnpj].filter(Boolean).join(' • ')}</div>
            <div className="doc-sub">{[settings.telefone, settings.email].filter(Boolean).join(' • ')}</div>
          </div>
        </div>
        <div className="doc-meta">
          <div className="doc-meta-title">{os.situacao === 'Em Orçamento' ? 'ORÇAMENTO' : 'ORDEM DE SERVIÇO'}</div>
          <div className="doc-meta-num">{os.numero}</div>
          <div>Emissão: <b>{fmtData(os.data)}</b></div>
          <div>Emissor: <b>{os.emissor || '—'}</b></div>
          <div>Situação: <b>{os.situacao}</b></div>
        </div>
      </header>

      <section className="doc-box">
        <div className="doc-grid">
          <div><b>Cliente:</b> {cl.nome || '—'}</div>
          <div><b>Telefone:</b> {cl.telefone || '—'}</div>
          <div><b>E-mail:</b> {cl.email || '—'}</div>
          <div><b>Endereço:</b> {endereco || '—'}</div>
        </div>
      </section>

      <h3>Materiais</h3>
      {os.itens.length === 0 ? <div className="doc-box">Nenhum material informado.</div> : (
        <table className="doc-table">
          <thead><tr><th style={{ width: '16%' }}>Código</th><th>Descrição</th><th style={{ width: '7%' }}>Un.</th><th className="r" style={{ width: '9%' }}>Qtd</th><th className="r" style={{ width: '14%' }}>Preço unit.</th><th className="r" style={{ width: '14%' }}>Total</th></tr></thead>
          <tbody>
            {os.itens.map(i => (
              <tr key={i.id}>
                <td>{i.codigo || '—'}</td><td>{i.descricao}</td><td>{i.unidade}</td>
                <td className="r">{qtdFmt.format(i.qtd || 0)}</td><td className="r">{money(i.preco)}</td><td className="r">{money((i.qtd || 0) * (i.preco || 0))}</td>
              </tr>
            ))}
          </tbody>
        </table>
      )}
      <div className="doc-subtotal avoid">Total de materiais: {money(c.totMat)}</div>

      <h3>Mão de obra</h3>
      {os.servicos.length === 0 ? <div className="doc-box">Nenhum serviço informado.</div> : (
        <table className="doc-table">
          <thead><tr><th>Descrição do serviço</th><th className="r" style={{ width: '18%' }}>Valor</th></tr></thead>
          <tbody>{os.servicos.map(s => <tr key={s.id}><td>{s.descricao}</td><td className="r">{money(s.preco)}</td></tr>)}</tbody>
        </table>
      )}
      <div className="doc-subtotal avoid">Total de mão de obra: {money(c.totMO)}</div>

      <section className="doc-box avoid" style={{ marginTop: 14 }}>
        <h3 style={{ marginTop: 0 }}>Resumo financeiro</h3>
        <div className="doc-fin">
          <span>Materiais</span><span style={{ textAlign: 'right' }}>{money(c.totMat)}</span>
          <span>Mão de obra</span><span style={{ textAlign: 'right' }}>{money(c.totMO)}</span>
          <span className="strong">Total à vista</span><span className="strong" style={{ textAlign: 'right' }}>{money(c.valorTotal)}</span>
          <span>Valor já pago (materiais {money(p.pagoMateriais)} + mão de obra {money(p.pagoMaoObra)})</span><span style={{ textAlign: 'right' }}>{money(c.pagoTotal)}</span>
          <span className="strong">Saldo restante</span><span className="strong" style={{ textAlign: 'right' }}>{money(c.saldo)}</span>
          {c.n > 1 && c.saldo > 0 && <>
            <span>Parcelamento do saldo</span><span style={{ textAlign: 'right' }}>{c.n}x de {money(c.parcela)}</span>
            <span>Juros sobre o saldo</span><span style={{ textAlign: 'right' }}>{qtdFmt.format(p.juros || 0)}%</span>
            <span>Saldo com juros</span><span style={{ textAlign: 'right' }}>{money(c.saldoJuros)}</span>
            <span className="strong">Valor total parcelado</span><span className="strong" style={{ textAlign: 'right' }}>{money(c.totalParcelado)}</span>
          </>}
        </div>
      </section>

      {os.observacoes.trim() && (
        <section className="doc-box avoid"><b>Observações:</b><div style={{ whiteSpace: 'pre-wrap' }}>{os.observacoes}</div></section>
      )}

      <div className="doc-sign avoid"><div>Cliente</div><div>{os.emissor || 'Emissor'} — E. L. Instalações Elétricas Prediais</div></div>
      <div className="doc-foot">Documento gerado em {fmtData(hoje())} — {os.numero}</div>
    </article>
  );
}

function Preview({ os, settings, autoPrint, onClose }: any) {
  const [aviso, setAviso] = useState('');
  const imprimir = () => {
    try { window.print(); } catch (e) { setAviso('Não foi possível abrir a impressão aqui. Abra o aplicativo em uma nova aba e tente novamente.'); }
  };
  useEffect(() => {
    const t = document.title;
    document.title = os.numero + ' - ' + (os.cliente.nome || 'Orçamento');
    document.body.classList.add('preview-open');
    const k = (e: KeyboardEvent) => { if (e.key === 'Escape') onClose(); };
    window.addEventListener('keydown', k);
    let timer: any;
    if (autoPrint) timer = setTimeout(imprimir, 450);
    return () => { document.title = t; document.body.classList.remove('preview-open'); window.removeEventListener('keydown', k); clearTimeout(timer); };
  }, []);
  return ReactDOM.createPortal(
    <div className="print-overlay">
      <div className="print-toolbar no-print">
        <button className="tb-btn" onClick={onClose}>← Voltar</button>
        <button className="tb-btn main" onClick={imprimir}>Imprimir / Salvar PDF</button>
        <span style={{ fontSize: 12, opacity: .8 }}>Formato A4 • no destino da impressão escolha “Salvar como PDF” para gerar o arquivo.</span>
        {aviso && <span style={{ fontSize: 12, color: '#fcc934', fontWeight: 600 }}>{aviso}</span>}
      </div>
      <div className="print-scroll"><Documento os={os} settings={settings} /></div>
    </div>,
    document.getElementById('print-root')
  );
}

/* =====================================================================
   CONFIGURAÇÕES DA EMPRESA
   ===================================================================== */
function SettingsModal({ settings, onSave, onClose }: any) {
  const [f, setF] = useState<Settings>(settings);
  const set = (p: Partial<Settings>) => setF(x => ({ ...x, ...p }));
  return (
    <Modal title="Dados da empresa e do usuário" onClose={onClose}
      footer={<><button className={B('secondary')} onClick={onClose}>Cancelar</button><button className={B('primary')} onClick={() => onSave(f)}>Salvar dados</button></>}>
      <div className="space-y-3">
        <p className="text-xs text-slate-500">Estes dados aparecem no cabeçalho da OS e na impressão. Substitua os valores de exemplo pelos dados reais da empresa.</p>
        <Field label="Telefone de contato"><input className={inputCls} value={f.telefone} onChange={e => set({ telefone: e.target.value })} /></Field>
        <Field label="E-mail de contato"><input className={inputCls} value={f.email} onChange={e => set({ email: e.target.value })} /></Field>
        <Field label="Cidade padrão"><input className={inputCls} value={f.cidade} onChange={e => set({ cidade: e.target.value })} /></Field>
        <Field label="CNPJ (opcional)"><input className={inputCls} value={f.cnpj} onChange={e => set({ cnpj: e.target.value })} /></Field>
        <Field label="Usuário atual (emissor padrão das OS)"><input className={inputCls} value={f.usuario} onChange={e => set({ usuario: e.target.value })} /></Field>
      </div>
    </Modal>
  );
}

/* =====================================================================
   APP
   ===================================================================== */
const TABS = [
  { id: 'dashboard', label: 'Dashboard', icon: 'dash' },
  { id: 'materiais', label: 'Materiais', icon: 'box' },
  { id: 'os', label: 'Orçamento / OS', icon: 'file' },
  { id: 'lista', label: 'Ordens de Serviço', icon: 'list' },
];

function App() {
  const [tab, setTab] = useState<string>('dashboard');
  const [materiais, setMateriais] = useLocalStorage<Material[]>('el-materiais-v1', gerarMateriais);
  const [ordens, setOrdens] = useLocalStorage<OS[]>('el-ordens-v1', () => gerarOrdensExemplo(gerarMateriais()));
  const [settings, setSettings] = useLocalStorage<Settings>('el-config-v1', () => DEFAULT_SETTINGS);
  const [draft, setDraft] = useState<OS>(() => novaOS(ordens, settings));
  const baseline = useRef<string>(JSON.stringify(draft));
  const [tentou, setTentou] = useState(false);
  const [filtro, setFiltro] = useState<string>('Todas');
  const [preview, setPreview] = useState<null | { os: OS; auto: boolean }>(null);
  const [confirm, setConfirm] = useState<any>(null);
  const [showCfg, setShowCfg] = useState(false);
  const [toast, setToast] = useState<null | { msg: string; tone: string }>(null);

  window.__cfg = settings; // usado no cabeçalho do editor

  const dirty = JSON.stringify(draft) !== baseline.current;
  const existe = ordens.some(o => o.id === draft.id);
  const notify = (msg: string, tone = 'ok') => { setToast({ msg, tone }); setTimeout(() => setToast(null), 3200); };
  const go = (t: string, f?: string) => { if (f) setFiltro(f); setTab(t); window.scrollTo(0, 0); };

  const carregar = (os: OS) => {
    const copia: OS = JSON.parse(JSON.stringify(os));
    setDraft(copia); baseline.current = JSON.stringify(copia); setTentou(false); go('os');
  };
  const resetDraft = () => {
    const n = novaOS(ordens, settings);
    setDraft(n); baseline.current = JSON.stringify(n); setTentou(false); go('os');
  };
  const acaoNova = () => {
    if (dirty) setConfirm({ titulo: 'Descartar alterações?', msg: 'A OS em edição tem alterações não salvas. Deseja começar uma nova OS mesmo assim?', label: 'Descartar e criar nova', onOk: resetDraft });
    else resetDraft();
  };
  const editar = (os: OS) => {
    if (dirty && draft.id !== os.id) setConfirm({ titulo: 'Descartar alterações?', msg: 'A OS em edição tem alterações não salvas. Abrir ' + os.numero + ' descartará essas alterações.', label: 'Descartar e abrir', onOk: () => carregar(os) });
    else if (draft.id === os.id && dirty) go('os');
    else carregar(os);
  };
  const salvar = () => {
    if (!draft.cliente.nome.trim()) { setTentou(true); notify('Informe o nome do cliente para salvar a OS.', 'err'); return; }
    let os = { ...draft };
    if (!existe && ordens.some(o => o.numero === os.numero)) os.numero = proximoNumero(ordens);
    setOrdens(list => list.some(o => o.id === os.id) ? list.map(o => o.id === os.id ? os : o) : [...list, os]);
    setDraft(os); baseline.current = JSON.stringify(os); setTentou(false);
    notify(os.numero + ' salva com sucesso.');
  };
  const excluir = (os: OS) => setConfirm({
    titulo: 'Excluir ' + os.numero + '?', msg: 'A ordem de serviço de ' + (os.cliente.nome || 'cliente não informado') + ' será removida definitivamente.', label: 'Excluir OS',
    onOk: () => {
      setOrdens(list => list.filter(o => o.id !== os.id));
      if (draft.id === os.id) { const rest = ordens.filter(o => o.id !== os.id); const n = novaOS(rest, settings); setDraft(n); baseline.current = JSON.stringify(n); }
      notify(os.numero + ' excluída.');
    },
  });
  const mudarStatus = (id: string, s: Situacao) => {
    setOrdens(list => list.map(o => o.id === id ? { ...o, situacao: s } : o));
    if (draft.id === id) {
      setDraft(d => ({ ...d, situacao: s }));
      try { const b = JSON.parse(baseline.current); b.situacao = s; baseline.current = JSON.stringify(b); } catch (e) {}
    }
    notify('Situação atualizada para “' + s + '”.');
  };

  return (
    <div className="min-h-screen">
      <header className="sticky z-40 bg-navy-900 text-white shadow-md" style={{ top: 'env(safe-area-inset-top, 0px)' }}>
        <div className="mx-auto flex max-w-7xl items-center justify-between gap-3 px-4 pt-3 sm:px-6">
          <div className="flex min-w-0 items-center gap-3">
            <div className="flex h-10 w-10 flex-none items-center justify-center rounded-lg bg-volt-500 text-navy-900"><Icon n="bolt" size={24} /></div>
            <div className="min-w-0">
              <div className="truncate font-display text-lg font-bold leading-tight sm:text-xl">E. L. Instalações Elétricas Prediais</div>
              <div className="truncate text-xs text-navy-200">Orçamentos e Ordens de Serviço • {settings.cidade}</div>
            </div>
          </div>
          <div className="flex flex-none items-center gap-2 text-sm">
            <span className="hidden text-navy-200 sm:inline">{settings.usuario}</span>
            <button onClick={() => setShowCfg(true)} className="rounded-md p-2 text-navy-100 hover:bg-white/10" title="Dados da empresa" aria-label="Dados da empresa"><Icon n="sliders" size={18} /></button>
          </div>
        </div>
        <nav className="mx-auto mt-2 flex max-w-7xl gap-1 overflow-x-auto px-3 sm:px-5" role="tablist" aria-label="Navegação principal">
          {TABS.map(t => (
            <button key={t.id} role="tab" aria-selected={tab === t.id} onClick={() => go(t.id)}
              className={'relative flex flex-none items-center gap-2 whitespace-nowrap px-3.5 py-2.5 text-sm font-semibold transition-colors focus-visible:outline focus-visible:outline-2 focus-visible:outline-volt-400 ' + (tab === t.id ? 'text-white' : 'text-navy-200 hover:text-white')}>
              <Icon n={t.icon} size={16} />{t.label}
              {t.id === 'os' && dirty && <span className="h-2 w-2 rounded-full bg-volt-500" title="Alterações não salvas" />}
              {tab === t.id && <span className="absolute inset-x-2 bottom-0 h-[3px] rounded-t bg-volt-500" />}
            </button>
          ))}
        </nav>
      </header>

      <main className="mx-auto max-w-7xl px-4 py-6 sm:px-6">
        {tab === 'dashboard' && <Dashboard materiais={materiais} ordens={ordens} go={go} onEdit={editar} />}
        {tab === 'materiais' && <Materiais materiais={materiais} setMateriais={setMateriais} notify={notify} />}
        {tab === 'os' && <EditorOS draft={draft} setDraft={setDraft} materiais={materiais} dirty={dirty} existe={existe} tentou={tentou} onSave={salvar} onPreview={() => setPreview({ os: draft, auto: false })} onNova={acaoNova} />}
        {tab === 'lista' && <ListaOS ordens={ordens} filtro={filtro} setFiltro={setFiltro} onEdit={editar} onView={(o: OS) => setPreview({ os: o, auto: false })} onPrint={(o: OS) => setPreview({ os: o, auto: true })} onDelete={excluir} onStatus={mudarStatus} />}
      </main>

      {preview && <Preview os={preview.os} settings={settings} autoPrint={preview.auto} onClose={() => setPreview(null)} />}
      {confirm && <ConfirmDialog dados={confirm} onClose={() => setConfirm(null)} />}
      {showCfg && <SettingsModal settings={settings} onClose={() => setShowCfg(false)} onSave={(s: Settings) => { setSettings(s); setShowCfg(false); notify('Dados atualizados.'); }} />}
      {toast && (
        <div role="status" className={'fixed left-1/2 z-[60] -translate-x-1/2 rounded-lg px-4 py-2.5 text-sm font-semibold shadow-lg ' + (toast.tone === 'err' ? 'bg-red-600 text-white' : 'bg-navy-900 text-white')} style={{ bottom: 'calc(84px + env(safe-area-inset-bottom, 0px))' }}>
          {toast.msg}
        </div>
      )}
    </div>
  );
}

ReactDOM.createRoot(document.getElementById('root')).render(<App />);
</script>

<script>
  (function () {
    var root = document.getElementById('root');
    try {
      var src = document.getElementById('app-src').textContent;
      var out = Babel.transform(src, {
        filename: 'app.tsx',
        presets: [['typescript', { isTSX: true, allExtensions: true }], 'react']
      }).code;
      var s = document.createElement('script');
      s.textContent = out;
      document.body.appendChild(s);
    } catch (e) {
      root.innerHTML = '<pre style="padding:16px;color:#b91c1c;white-space:pre-wrap;font:14px monospace">Erro ao iniciar o aplicativo: ' + (e && e.message ? e.message : e) + '</pre>';
    }
  })();
</script>
</body>
</html>
