# Exemplo Completo — Plann Design System

Este arquivo é um HTML completo e funcional com:
- Tokens CSS completos (`:root`)
- Sidebar com ícones e tooltips
- Topbar com breadcrumb e user pill
- Filter Panel com dropdowns e chips
- Tabela hierárquica com expand e checkboxes
- Toolbar acima da tabela

Use como base para qualquer nova tela.

---

## HTML COMPLETO FUNCIONAL

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Plannera — [Nome da Tela]</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Epilogue:wght@400;500;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
  <style>
    /* ── Tokens CSS Plann Design System ─────────────────────────── */
    :root {
      --blue-lighter: #e3eaf6; --blue-light: #495583; --blue-default: #2d3558; --blue-dark: #1f2747;
      --purple-dark: #8d9aec; --purple-default: #bcc8f5; --purple-light: #e3eafc; --purple-lighter: #f1f5ff;
      --grey-lighter: #f4f5f9; --grey-light: #dadeea; --grey-default: #9ca2b8; --grey-dark: #8f93a3;
      --green-lighter: #ebfcf0; --green-light: #b4e6c4; --green-default: #47b274; --green-dark: #17653e;
      --red-lighter: #fff0f0; --red-light: #ebb6b6; --red-default: #cb5158; --red-dark: #832e3b;
      --yellow-lighter: #fef8ee; --yellow-light: #ffdcae; --yellow-default: #f8b967; --yellow-dark: #f7941e;
      --white: #ffffff; --black: #000000;

      --primary: var(--blue-default); --primary-light: var(--blue-light);
      --primary-lighter: var(--blue-lighter); --primary-dark: var(--blue-dark);
      --secondary: var(--purple-default); --secondary-dark: var(--purple-dark);
      --secondary-light: var(--purple-light); --secondary-lighter: var(--purple-lighter);
      --neutral: var(--grey-default); --neutral-light: var(--grey-light);
      --neutral-lighter: var(--grey-lighter); --neutral-dark: var(--grey-dark);
      --success: var(--green-default); --success-light: var(--green-light);
      --success-lighter: var(--green-lighter); --success-dark: var(--green-dark);
      --danger: var(--red-default); --danger-light: var(--red-light);
      --danger-lighter: var(--red-lighter); --danger-dark: var(--red-dark);
      --warning: var(--yellow-default); --warning-light: var(--yellow-light);
      --warning-lighter: var(--yellow-lighter); --warning-dark: var(--yellow-dark);

      --bg-page: var(--neutral-lighter);
      --text-heading: var(--primary); --text-body: var(--primary);
      --text-muted: #626f86; --text-disabled: var(--neutral);

      --font-sans: 'Epilogue', system-ui, sans-serif;
      --font-mono: ui-monospace, 'JetBrains Mono', monospace;
      --fw-regular: 400; --fw-medium: 500; --fw-semibold: 600; --fw-bold: 700;
      --lh-tight: 1.2; --lh-normal: 1.5;
      --fs-12: 12px; --fs-14: 14px; --fs-16: 16px; --fs-18: 18px;
      --fs-22: 22px; --fs-25: 25px; --fs-28: 28px; --fs-32: 32px;

      --shadow-card: 0 1px 2px rgba(31,39,71,0.06), 0 1px 3px rgba(31,39,71,0.05);
      --shadow-popover: 0 4px 12px rgba(31,39,71,0.12);
      --ease-standard: cubic-bezier(.2,.6,.2,1);
      --ease-out: cubic-bezier(.16,1,.3,1);
      --dur-fast: 120ms; --dur-base: 200ms; --dur-slow: 320ms;

      --radius-sm: 4px; --radius-md: 8px; --radius-pill: 9999px;
    }

    /* ── Reset ───────────────────────────────────────────────────── */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html, body, #root { height: 100%; background: var(--bg-page); font-family: var(--font-sans); color: var(--text-body); -webkit-font-smoothing: antialiased; }
    button { font-family: inherit; cursor: pointer; }

    /* ── App Shell ───────────────────────────────────────────────── */
    .app-shell { display: grid; grid-template-columns: 64px 1fr; height: 100vh; overflow: hidden; }
    .main-col { display: flex; flex-direction: column; min-width: 0; height: 100vh; overflow: hidden; }

    /* ── Sidebar ─────────────────────────────────────────────────── */
    .sidebar { background: var(--primary); display: flex; flex-direction: column; align-items: center; padding: 12px 0; gap: 8px; overflow: visible; width: 64px; height: 100vh; }
    .sidebar-logo { width: 40px; height: 40px; display: grid; place-items: center; margin-bottom: 8px; }
    .sidebar-icon { width: 100%; height: 44px; display: grid; place-items: center; color: rgba(255,255,255,0.55); cursor: pointer; transition: all var(--dur-fast) var(--ease-standard); position: relative; font-size: 16px; border: 0; border-radius: 0; background: transparent; }
    .sidebar-icon:hover { background: rgba(255,255,255,0.08); color: var(--white); }
    .sidebar-icon[data-active="true"] { background: rgba(255,255,255,0.10); color: var(--white); }
    .sidebar-tooltip { position: absolute; left: calc(100% + 12px); top: 50%; transform: translateY(-50%); background: var(--neutral); color: var(--white); padding: 6px 10px; border-radius: 6px; font-size: 12px; font-weight: 500; white-space: nowrap; opacity: 0; pointer-events: none; transition: opacity var(--dur-fast); z-index: 100; }
    .sidebar-icon:hover .sidebar-tooltip { opacity: 1; }
    .sidebar-divider { width: 32px; height: 1px; background: rgba(255,255,255,0.10); margin: 6px 0; }
    .sidebar-spacer { flex: 1; }

    /* ── Topbar ──────────────────────────────────────────────────── */
    .topbar { height: 56px; flex: none; background: var(--white); border-bottom: 1px solid var(--neutral-light); display: flex; align-items: center; padding: 0 24px; gap: 16px; }
    .topbar-product { font-size: 12px; font-weight: 500; color: var(--neutral); letter-spacing: 0.1px; }
    .topbar-breadcrumb { display: flex; align-items: center; gap: 6px; font-size: 12px; color: var(--text-muted); margin-left: -10px; }
    .topbar-breadcrumb-sep { color: var(--neutral); font-size: 10px; }
    .topbar-breadcrumb-current { color: var(--text-heading); font-weight: 500; }
    .topbar-spacer { flex: 1; }
    .topbar-user { display: flex; align-items: center; gap: 10px; padding: 4px 14px 4px 4px; border-radius: 100px; background: var(--neutral-lighter); cursor: pointer; font-size: 13px; font-weight: var(--fw-semibold); color: var(--text-body); border: 0; transition: background var(--dur-fast) var(--ease-standard); }
    .topbar-user:hover { background: var(--neutral-light); }
    .topbar-user-avatar { width: 28px; height: 28px; border-radius: 50%; background: var(--white); display: grid; place-items: center; font-size: 12px; font-weight: var(--fw-bold); color: var(--text-body); border: 1px solid var(--neutral-light); }
    .topbar-user .fa-chevron-down { font-size: 10px; color: var(--neutral-dark); }

    /* ── Page ────────────────────────────────────────────────────── */
    .page { flex: 1; overflow-y: auto; overflow-x: hidden; padding: 16px 24px 40px; display: flex; flex-direction: column; gap: 0; }
    .page-head { display: flex; align-items: center; justify-content: space-between; gap: 24px; margin-bottom: 20px; }
    .page-title { font-size: 22px; font-weight: var(--fw-semibold); color: var(--text-heading); line-height: 1.2; }
    .page-actions { display: flex; gap: 8px; align-items: center; }

    /* ── Buttons ─────────────────────────────────────────────────── */
    .btn { font-family: var(--font-sans); font-weight: var(--fw-semibold); font-size: 13px; height: 36px; padding: 0 14px; border-radius: 6px; border: 0; display: inline-flex; align-items: center; gap: 8px; transition: all var(--dur-fast) var(--ease-standard); white-space: nowrap; }
    .btn--primary { background: var(--primary); color: var(--white); }
    .btn--primary:hover { background: var(--primary-light); }
    .btn--secondary { background: var(--white); color: var(--text-heading); border: 1px solid var(--neutral-light); }
    .btn--secondary:hover { border-color: var(--text-heading); }
    .btn--ghost { background: transparent; color: var(--text-heading); }
    .btn--ghost:hover { background: var(--neutral-lighter); }

    /* ── Filter card + bar ───────────────────────────────────────── */
    .plann-filter-card { background: var(--white); border-radius: 10px; padding: 12px 16px; margin-bottom: 20px; }
    .plann-filter-bar { display: flex; flex-direction: column; gap: 12px; }
    .plann-filter-header { display: flex; align-items: center; gap: 12px; flex-wrap: wrap; }
    .plann-filter-toggle { display: inline-flex; align-items: center; gap: 10px; padding: 8px 12px; background: var(--white); border: 1px solid var(--neutral-light); border-radius: 6px; font-family: inherit; font-size: 13px; font-weight: var(--fw-semibold); color: var(--text-heading); cursor: pointer; height: 38px; transition: border-color var(--dur-fast); }
    .plann-filter-toggle:hover { border-color: var(--text-heading); }
    .plann-filter-toggle-count { display: inline-flex; align-items: center; justify-content: center; min-width: 20px; height: 20px; padding: 0 6px; border-radius: 100px; background: var(--primary); color: var(--white); font-size: 11px; font-weight: var(--fw-bold); }
    .plann-filter-active-chip { display: inline-flex; align-items: center; gap: 8px; padding: 5px 8px 5px 10px; background: var(--neutral-lighter); border-radius: 6px; font-size: 12px; color: var(--text-heading); }
    .plann-filter-active-chip-label { color: var(--text-muted); font-weight: var(--fw-semibold); }
    .plann-filter-active-chip-value { font-weight: var(--fw-medium); }
    .plann-filter-active-chip-x { background: transparent; border: 0; width: 18px; height: 18px; border-radius: 4px; display: grid; place-items: center; cursor: pointer; color: var(--text-muted); font-size: 11px; }
    .plann-filter-active-chip-x:hover { background: var(--neutral-light); color: var(--text-heading); }
    .plann-filter-clear-all { background: transparent; border: 0; cursor: pointer; font-family: inherit; font-size: 12.5px; color: var(--primary); font-weight: var(--fw-semibold); padding: 4px 8px; border-radius: 4px; }
    .plann-filter-clear-all:hover { background: var(--primary-lighter); }
    .plann-filter-fields { display: flex; flex-wrap: wrap; gap: 14px 24px; align-items: center; padding: 4px; }
    .plann-filter-field { display: inline-flex; align-items: center; gap: 10px; }
    .plann-filter-field-label { font-size: 13px; color: var(--text-heading); font-weight: var(--fw-medium); }
    .plann-filter-field-select { position: relative; }
    .plann-filter-field-trigger { display: inline-flex; align-items: center; justify-content: space-between; gap: 14px; min-width: 140px; height: 38px; padding: 0 12px; background: var(--white); border: 1px solid var(--neutral-light); border-radius: 6px; cursor: pointer; font-family: inherit; font-size: 13px; font-weight: var(--fw-medium); color: var(--text-heading); }
    .plann-filter-field-trigger:hover { border-color: var(--text-heading); }
    .plann-filter-field-trigger[data-open="true"] { border-color: var(--primary); box-shadow: 0 0 0 3px var(--purple-lighter); }
    .plann-filter-dropdown { position: absolute; top: calc(100% + 4px); left: 0; min-width: 200px; max-height: 280px; overflow-y: auto; background: var(--white); border: 1px solid var(--neutral-light); border-radius: 8px; box-shadow: var(--shadow-popover); z-index: 30; padding: 4px 0; display: none; }
    .plann-filter-option { display: flex; align-items: center; justify-content: space-between; gap: 12px; padding: 9px 14px; cursor: pointer; font-size: 13px; color: var(--text-heading); border: 0; background: transparent; width: 100%; font-family: inherit; text-align: left; }
    .plann-filter-option:hover { background: var(--neutral-lighter); }
    .plann-filter-option-label { flex: 1; }
    .plann-filter-option-check { width: 18px; height: 18px; border: 1.5px solid var(--neutral); border-radius: 3px; background: var(--white); display: inline-grid; place-items: center; flex: none; color: var(--white); font-size: 11px; }
    .plann-filter-option[data-checked="true"] .plann-filter-option-check { background: var(--purple-dark); border-color: var(--purple-dark); }
    .plann-filter-option[data-checked="true"] .plann-filter-option-check::after { content: "✓"; }

    /* ── Toolbar ─────────────────────────────────────────────────── */
    .toolbar { display: flex; align-items: center; justify-content: space-between; padding: 0 4px; min-height: 28px; margin-bottom: 16px; }
    .toolbar-left, .toolbar-right { display: flex; align-items: center; gap: 8px; font-size: 12px; color: var(--text-muted); }
    .toolbar-count { color: var(--text-heading); font-weight: var(--fw-semibold); }

    /* ── Table ───────────────────────────────────────────────────── */
    .table-wrap { background: var(--white); border: 1px solid var(--neutral-light); border-radius: 10px; overflow: hidden; }
    .table-scroll { overflow-x: auto; }
    table.carteira { width: 100%; border-collapse: separate; border-spacing: 0; font-size: 12px; color: var(--text-heading); font-family: var(--font-sans); min-width: 900px; }
    table.carteira thead th { position: sticky; top: 0; text-align: left; background: var(--primary); color: var(--white); font-weight: var(--fw-semibold); font-size: 12px; padding: 0 12px; height: 33px; border-right: 1px solid var(--neutral); white-space: nowrap; z-index: 2; }
    table.carteira thead th.center, table.carteira tbody td.center { text-align: center; padding-left: 0; padding-right: 0; }
    table.carteira tbody td { padding: 0 12px; height: 48px; border-bottom: 1px solid var(--neutral-lighter); border-right: 1px solid var(--neutral-lighter); background: var(--white); vertical-align: middle; font-variant-numeric: tabular-nums; }
    table.carteira tbody td:last-child { border-right: 0; }
    table.carteira tbody td.num { text-align: right; }
    table.carteira tbody tr.pedido-row:hover td { background: var(--neutral-lighter); }
    table.carteira tbody tr.pedido-row.selected td { background: var(--primary-lighter); }
    tr.item-row td { background: #fbfbfd; height: 36px; padding: 0 10px; font-size: 11.5px; border-bottom: 1px solid var(--neutral-lighter); }
    tr.item-row:hover td { background: var(--neutral-lighter); }
    tr.item-row td.indent-cell { padding-left: 36px; color: var(--text-muted); }
    tr.item-row td.indent-cell::before { content: "└"; color: var(--neutral); margin-right: 8px; font-size: 10px; }
    tr.item-row td.produto-cell { font-weight: var(--fw-medium); }
    .cell-check { width: 16px; height: 16px; border: 1px solid var(--neutral); border-radius: 2px; background: var(--white); display: inline-flex; align-items: center; justify-content: center; cursor: pointer; transition: all var(--dur-fast); }
    .cell-check:hover { border-color: var(--secondary); border-width: 2px; }
    .cell-check[data-checked="true"] { background: var(--purple-dark); border-color: var(--secondary); }
    .cell-check[data-checked="true"]::after { content: "✓"; font-size: 11px; font-weight: var(--fw-bold); color: var(--white); }
    table.carteira thead .cell-check { background: transparent; border-color: rgba(255,255,255,0.6); }
    .cell-expand { width: 18px; height: 18px; display: inline-grid; place-items: center; cursor: pointer; color: var(--neutral-dark); background: transparent; border: 0; transition: transform var(--dur-fast) var(--ease-standard); font-size: 10px; }
    .cell-expand:hover { color: var(--text-heading); }
    .cell-expand[data-open="true"] { transform: rotate(90deg); }
    .header-expand { width: 18px; height: 18px; display: inline-grid; place-items: center; cursor: pointer; color: var(--white); font-size: 11px; border-radius: 4px; background: transparent; border: 0; transition: all var(--dur-fast); }
    .header-expand:hover { background: rgba(255,255,255,0.18); }
    .header-expand[data-open="true"] { transform: rotate(90deg); }
    .cell-pedido { display: flex; align-items: center; gap: 8px; }
    .cell-pedido-num--btn { background: transparent; border: 0; padding: 0; font-family: var(--font-mono); font-size: 12.5px; font-weight: var(--fw-bold); color: var(--text-heading); cursor: pointer; border-radius: 3px; }
    .cell-pedido-num--btn:hover { color: var(--primary); text-decoration: underline; }
    .cell-pedido-meta { font-size: 10.5px; color: var(--text-muted); }
    .cell-cliente { display: flex; flex-direction: column; gap: 1px; max-width: 200px; }
    .cell-cliente-name { font-weight: var(--fw-semibold); white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
    .cell-cliente-meta { font-size: 10.5px; color: var(--text-muted); display: flex; gap: 6px; align-items: center; }
    .status-cell { display: inline-flex; align-items: center; gap: 6px; font-size: 11px; font-weight: var(--fw-bold); padding: 4px 8px 4px 6px; border-radius: 5px; white-space: nowrap; border: 1px solid transparent; }
    .status-cell::before { content: ""; width: 6px; height: 6px; border-radius: 50%; }
    .status-cell--warning { color: var(--warning-dark); background: var(--warning-lighter); }
    .status-cell--warning::before { background: var(--warning); }
    .status-cell--success { color: var(--success-dark); background: var(--success-lighter); }
    .status-cell--success::before { background: var(--success); }
    .status-cell--danger { color: var(--danger); background: var(--danger-lighter); }
    .status-cell--danger::before { background: var(--danger); }
    .status-cell--neutral { color: var(--text-muted); background: var(--neutral-lighter); }
    .status-cell--neutral::before { background: var(--neutral); }
  </style>
</head>
<body>
<div class="app-shell">

  <!-- ── SIDEBAR ─────────────────────────────────────────────────── -->
  <aside class="sidebar">
    <div class="sidebar-logo" title="Plannera">
      <span style="font-size:20px;font-weight:700;color:#f7941e;">P</span>
    </div>

    <button class="sidebar-icon" data-active="true" aria-label="Carteira de Pedidos" type="button">
      <i class="fa-solid fa-box-archive" aria-hidden="true"></i>
      <span class="sidebar-tooltip">Carteira de Pedidos</span>
    </button>

    <button class="sidebar-icon" data-active="false" aria-label="Dashboard" type="button">
      <i class="fa-solid fa-chart-line" aria-hidden="true"></i>
      <span class="sidebar-tooltip">Dashboard</span>
    </button>

    <button class="sidebar-icon" data-active="false" aria-label="Reabastecimento" type="button">
      <i class="fa-solid fa-rotate" aria-hidden="true"></i>
      <span class="sidebar-tooltip">Reabastecimento</span>
    </button>

    <div class="sidebar-divider"></div>

    <button class="sidebar-icon" data-active="false" aria-label="Cadastros" type="button">
      <i class="fa-solid fa-database" aria-hidden="true"></i>
      <span class="sidebar-tooltip">Cadastros</span>
    </button>

    <div class="sidebar-spacer"></div>

    <button class="sidebar-icon" data-active="false" aria-label="Configurações" type="button">
      <i class="fa-solid fa-gear" aria-hidden="true"></i>
      <span class="sidebar-tooltip">Configurações</span>
    </button>
  </aside>

  <!-- ── MAIN COLUMN ─────────────────────────────────────────────── -->
  <div class="main-col">

    <!-- TOPBAR -->
    <div class="topbar">
      <div class="topbar-product">Gestão de Carteira</div>
      <div class="topbar-breadcrumb">
        <i class="fa-solid fa-chevron-right topbar-breadcrumb-sep"></i>
        <span class="topbar-breadcrumb-current">Pedidos</span>
      </div>
      <div class="topbar-spacer"></div>
      <button class="topbar-user" aria-label="Conta de usuário">
        <span class="topbar-user-avatar">A</span>
        <span>Admin-Plannera</span>
        <i class="fa-solid fa-chevron-down"></i>
      </button>
    </div>

    <!-- PAGE CONTENT -->
    <div class="page">

      <!-- Page header -->
      <div class="page-head">
        <span class="page-title">Carteira de Pedidos</span>
        <div class="page-actions">
          <button class="btn btn--secondary" type="button">
            <i class="fa-solid fa-download"></i> Exportar
          </button>
          <button class="btn btn--primary" type="button">
            <i class="fa-solid fa-plus"></i> Novo Pedido
          </button>
        </div>
      </div>

      <!-- FILTER PANEL -->
      <div class="plann-filter-card">
        <div class="plann-filter-bar">
          <div class="plann-filter-header">
            <button class="plann-filter-toggle" type="button" id="filterToggle">
              <i class="fa-solid fa-filter funnel"></i>
              Filtros
              <span class="plann-filter-toggle-count">1</span>
              <i class="fa-solid fa-chevron-down chevron"></i>
            </button>
            <div class="plann-filter-active-chip">
              <span class="plann-filter-active-chip-label">Status:</span>
              <span class="plann-filter-active-chip-value">Em aprovação</span>
              <button class="plann-filter-active-chip-x" type="button">×</button>
            </div>
            <button class="plann-filter-clear-all" type="button">Limpar tudo</button>
          </div>

          <div class="plann-filter-fields" id="filterFields">
            <div class="plann-filter-field">
              <label class="plann-filter-field-label">Status</label>
              <div class="plann-filter-field-select">
                <button class="plann-filter-field-trigger" data-open="false" type="button">
                  <span>Em aprovação</span>
                  <i class="fa-solid fa-chevron-down chevron"></i>
                </button>
                <div class="plann-filter-dropdown">
                  <button class="plann-filter-option" data-checked="false" type="button">
                    <span class="plann-filter-option-label" style="font-weight:700;text-transform:uppercase;font-size:11px;letter-spacing:.04em">Todos</span>
                    <div class="plann-filter-option-check"></div>
                  </button>
                  <button class="plann-filter-option" data-checked="true" type="button">
                    <span class="plann-filter-option-label">Em aprovação</span>
                    <div class="plann-filter-option-check"></div>
                  </button>
                  <button class="plann-filter-option" data-checked="false" type="button">
                    <span class="plann-filter-option-label">Aprovado</span>
                    <div class="plann-filter-option-check"></div>
                  </button>
                  <button class="plann-filter-option" data-checked="false" type="button">
                    <span class="plann-filter-option-label">Cancelado</span>
                    <div class="plann-filter-option-check"></div>
                  </button>
                </div>
              </div>
            </div>

            <div class="plann-filter-field">
              <label class="plann-filter-field-label">Classificação</label>
              <div class="plann-filter-field-select">
                <button class="plann-filter-field-trigger" data-open="false" type="button">
                  <span>Todas</span>
                  <i class="fa-solid fa-chevron-down chevron"></i>
                </button>
                <div class="plann-filter-dropdown">
                  <button class="plann-filter-option" data-checked="false" type="button">
                    <span class="plann-filter-option-label" style="font-weight:700;text-transform:uppercase;font-size:11px;letter-spacing:.04em">Todas</span>
                    <div class="plann-filter-option-check"></div>
                  </button>
                  <button class="plann-filter-option" data-checked="false" type="button">
                    <span class="plann-filter-option-label">Diamante</span>
                    <div class="plann-filter-option-check"></div>
                  </button>
                  <button class="plann-filter-option" data-checked="false" type="button">
                    <span class="plann-filter-option-label">Ouro</span>
                    <div class="plann-filter-option-check"></div>
                  </button>
                  <button class="plann-filter-option" data-checked="false" type="button">
                    <span class="plann-filter-option-label">Prata</span>
                    <div class="plann-filter-option-check"></div>
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- TOOLBAR -->
      <div class="toolbar">
        <div class="toolbar-left">
          <span><span class="toolbar-count">3</span> pedidos</span>
        </div>
        <div class="toolbar-right">
          <button class="btn btn--ghost btn--sm" type="button" style="height:30px;padding:0 10px;font-size:12px;">
            <i class="fa-solid fa-columns"></i> Colunas
          </button>
        </div>
      </div>

      <!-- TABLE -->
      <div class="table-wrap">
        <div class="table-scroll">
          <table class="carteira">
            <thead>
              <tr>
                <th class="center" style="width:40px;">
                  <div class="cell-check" data-checked="false" title="Selecionar todos"></div>
                </th>
                <th class="center" style="width:36px;">
                  <button class="header-expand" data-open="false" title="Expandir todos" type="button">
                    <i class="fa-solid fa-chevron-right"></i>
                  </button>
                </th>
                <th style="width:120px;">Pedido</th>
                <th style="width:200px;">Cliente</th>
                <th style="width:120px;">Status</th>
                <th style="width:100px;">Classif.</th>
                <th class="num" style="width:110px;">Qtd Sol.</th>
                <th class="num" style="width:110px;">Valor</th>
              </tr>
            </thead>
            <tbody>
              <!-- Pedido 1 -->
              <tr class="pedido-row" data-id="PED-001">
                <td class="center"><div class="cell-check" data-checked="false"></div></td>
                <td class="center">
                  <button class="cell-expand" data-open="false" type="button">
                    <i class="fa-solid fa-chevron-right"></i>
                  </button>
                </td>
                <td>
                  <div class="cell-pedido">
                    <button class="cell-pedido-num--btn" type="button">PED-001</button>
                    <span class="cell-pedido-meta">03/06</span>
                  </div>
                </td>
                <td>
                  <div class="cell-cliente">
                    <span class="cell-cliente-name">Atacado do Norte Ltda</span>
                    <div class="cell-cliente-meta"><span>Manaus, AM</span></div>
                  </div>
                </td>
                <td><span class="status-cell status-cell--warning">Em aprovação</span></td>
                <td>
                  <span class="classif classif--Ouro">Ouro</span>
                </td>
                <td class="num">4.200</td>
                <td class="num">R$ 84.600</td>
              </tr>
              <tr class="item-row" data-parent="PED-001" style="display:none">
                <td></td><td></td>
                <td class="indent-cell">Item 1</td>
                <td class="produto-cell">Refrigerante Cola 2L</td>
                <td></td><td></td>
                <td class="num">1.200</td>
                <td class="num">R$ 24.000</td>
              </tr>
              <tr class="item-row" data-parent="PED-001" style="display:none">
                <td></td><td></td>
                <td class="indent-cell">Item 2</td>
                <td class="produto-cell">Água Mineral 500ml</td>
                <td></td><td></td>
                <td class="num">3.000</td>
                <td class="num">R$ 60.600</td>
              </tr>

              <!-- Pedido 2 -->
              <tr class="pedido-row" data-id="PED-002">
                <td class="center"><div class="cell-check" data-checked="false"></div></td>
                <td class="center">
                  <button class="cell-expand" data-open="false" type="button">
                    <i class="fa-solid fa-chevron-right"></i>
                  </button>
                </td>
                <td>
                  <div class="cell-pedido">
                    <button class="cell-pedido-num--btn" type="button">PED-002</button>
                    <span class="cell-pedido-meta">05/06</span>
                  </div>
                </td>
                <td>
                  <div class="cell-cliente">
                    <span class="cell-cliente-name">Supermercados Sul S.A.</span>
                    <div class="cell-cliente-meta"><span>Porto Alegre, RS</span></div>
                  </div>
                </td>
                <td><span class="status-cell status-cell--success">Aprovado</span></td>
                <td>
                  <span class="classif classif--Diamante">Diamante</span>
                </td>
                <td class="num">8.500</td>
                <td class="num">R$ 193.750</td>
              </tr>

              <!-- Pedido 3 -->
              <tr class="pedido-row" data-id="PED-003">
                <td class="center"><div class="cell-check" data-checked="false"></div></td>
                <td class="center">
                  <button class="cell-expand" data-open="false" type="button">
                    <i class="fa-solid fa-chevron-right"></i>
                  </button>
                </td>
                <td>
                  <div class="cell-pedido">
                    <button class="cell-pedido-num--btn" type="button">PED-003</button>
                    <span class="cell-pedido-meta">07/06</span>
                  </div>
                </td>
                <td>
                  <div class="cell-cliente">
                    <span class="cell-cliente-name">Distribuidora Centro Oeste</span>
                    <div class="cell-cliente-meta"><span>Brasília, DF</span></div>
                  </div>
                </td>
                <td><span class="status-cell status-cell--danger">Cancelado</span></td>
                <td>
                  <span class="classif classif--Prata">Prata</span>
                </td>
                <td class="num">2.100</td>
                <td class="num">R$ 43.050</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>

    </div><!-- /page -->
  </div><!-- /main-col -->
</div><!-- /app-shell -->

<script>
  // Filter toggle
  document.getElementById('filterToggle').addEventListener('click', function() {
    const fields = document.getElementById('filterFields');
    const chevron = this.querySelector('.chevron');
    const open = fields.style.display !== 'none' && fields.style.display !== '';
    fields.style.display = open ? 'none' : 'flex';
    chevron.style.transform = open ? '' : 'rotate(180deg)';
  });

  // Dropdown triggers
  document.querySelectorAll('.plann-filter-field-trigger').forEach(t => {
    t.addEventListener('click', e => {
      e.stopPropagation();
      const dd = t.closest('.plann-filter-field-select').querySelector('.plann-filter-dropdown');
      const isOpen = t.dataset.open === 'true';
      document.querySelectorAll('.plann-filter-field-trigger').forEach(x => {
        x.dataset.open = 'false';
        x.closest('.plann-filter-field-select').querySelector('.plann-filter-dropdown').style.display = 'none';
      });
      t.dataset.open = isOpen ? 'false' : 'true';
      dd.style.display = isOpen ? 'none' : 'block';
    });
  });
  document.addEventListener('click', () => {
    document.querySelectorAll('.plann-filter-field-trigger').forEach(t => {
      t.dataset.open = 'false';
      t.closest('.plann-filter-field-select').querySelector('.plann-filter-dropdown').style.display = 'none';
    });
  });

  // Filter options
  document.querySelectorAll('.plann-filter-option').forEach(o => {
    o.addEventListener('click', e => {
      e.stopPropagation();
      o.dataset.checked = o.dataset.checked === 'true' ? 'false' : 'true';
    });
  });

  // Expand/collapse sub-rows
  document.querySelectorAll('.cell-expand').forEach(btn => {
    btn.addEventListener('click', () => {
      const row = btn.closest('tr');
      const id = row.dataset.id;
      const isOpen = btn.dataset.open === 'true';
      btn.dataset.open = isOpen ? 'false' : 'true';
      document.querySelectorAll(`tr.item-row[data-parent="${id}"]`).forEach(sub => {
        sub.style.display = isOpen ? 'none' : '';
      });
    });
  });

  // Checkboxes
  document.querySelectorAll('.cell-check').forEach(c => {
    c.addEventListener('click', () => {
      c.dataset.checked = c.dataset.checked === 'true' ? 'false' : 'true';
    });
  });

  // Remove chip
  document.querySelectorAll('.plann-filter-active-chip-x').forEach(x => {
    x.addEventListener('click', () => x.closest('.plann-filter-active-chip').remove());
  });

  // Clear all chips
  document.querySelectorAll('.plann-filter-clear-all').forEach(btn => {
    btn.addEventListener('click', () => {
      document.querySelectorAll('.plann-filter-active-chip').forEach(c => c.remove());
      document.querySelectorAll('.plann-filter-option').forEach(o => o.dataset.checked = 'false');
      document.querySelectorAll('.plann-filter-toggle-count').forEach(c => c.textContent = '0');
    });
  });
</script>
</body>
</html>
```
