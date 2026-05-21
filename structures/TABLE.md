# Table — Plann Design System

## ⚠️ REGRAS FIXAS
- Header: background `var(--primary)`, texto branco, height 33px
- Linhas de pedido: height 48px, background branco, hover `var(--neutral-lighter)`
- Linhas de item (sub-row): height 36px, background `#fbfbfd`
- Separadores verticais: `1px solid var(--neutral-lighter)` entre células
- Checkboxes: `.cell-check` (16×16px, roxo quando checked)
- Sempre dentro de `.table-wrap` → `.table-scroll` → `table.carteira`
- Font-size da tabela: 12px

---

## HTML — Estrutura EXATA

```html
<!-- Wrapper da tabela -->
<div class="table-wrap">
  <div class="table-scroll">
    <table class="carteira">

      <!-- CABEÇALHO -->
      <thead>
        <tr>
          <!-- Coluna checkbox (centralizada, sem padding) -->
          <th class="center" style="width:40px;">
            <div class="cell-check" data-checked="false" title="Selecionar todos"></div>
          </th>

          <!-- Coluna expand (centralizada) -->
          <th class="center" style="width:36px;">
            <button class="header-expand" data-open="false" title="Expandir todos">
              <i class="fa-solid fa-chevron-right"></i>
            </button>
          </th>

          <!-- Colunas de dados -->
          <th style="width:130px;">Pedido</th>
          <th style="width:200px;">Cliente</th>
          <th style="width:90px;">Status</th>
          <th style="width:110px;">Classificação</th>
          <th class="center" style="width:100px;">Data Entrega</th>
          <th style="width:120px;">
            Qtd Solicitada
            <!-- Hint opcional abaixo do título -->
            <span class="th-hint">cliente</span>
          </th>
          <th style="width:120px;">
            Qtd Sugerida
            <span class="th-hint th-hint--calc">
              <i class="fa-solid fa-calculator"></i>calculada
            </span>
          </th>
          <th class="num" style="width:110px;">Valor (R$)</th>
          <th style="width:240px;">Observações</th>
        </tr>
      </thead>

      <!-- CORPO -->
      <tbody>

        <!-- ── Linha de pedido (pai, expansível) ── -->
        <tr class="pedido-row" data-id="PED-001">
          <!-- Checkbox -->
          <td class="center">
            <div class="cell-check" data-checked="false"></div>
          </td>

          <!-- Botão expand -->
          <td class="center">
            <button class="cell-expand" data-open="false">
              <i class="fa-solid fa-chevron-right"></i>
            </button>
          </td>

          <!-- Número do pedido -->
          <td>
            <div class="cell-pedido">
              <button class="cell-pedido-num--btn" type="button">PED-001</button>
              <span class="cell-pedido-meta">03/06</span>
            </div>
          </td>

          <!-- Cliente -->
          <td>
            <div class="cell-cliente">
              <span class="cell-cliente-name">Atacado do Norte Ltda</span>
              <div class="cell-cliente-meta">
                <span>Manaus, AM</span>
                <span class="otif-chip otif-chip--good">OTIF 97%</span>
              </div>
            </div>
          </td>

          <!-- Status -->
          <td>
            <span class="status-cell status-cell--warning">Em aprovação</span>
          </td>

          <!-- Classificação -->
          <td>
            <span class="classif classif--Ouro">Ouro</span>
          </td>

          <!-- Data -->
          <td class="center">
            <span class="date-cell">15/06/2025</span>
          </td>

          <!-- Qtd solicitada -->
          <td class="num">4.200</td>

          <!-- Qtd sugerida (editable) -->
          <td class="num editable">
            3.800
            <i class="fa-solid fa-pencil cell-edit-hint"></i>
          </td>

          <!-- Valor -->
          <td class="num">R$ 84.600,00</td>

          <!-- Observações -->
          <td>
            <span class="obs-cell">Cliente pediu antecipação de prazo</span>
          </td>
        </tr>

        <!-- ── Linhas de item (sub-rows, filhos do pedido) ── -->
        <tr class="item-row" data-parent="PED-001">
          <td></td>
          <td></td>
          <td class="indent-cell">Item 1</td>
          <td class="produto-cell">
            <span class="cat-pill">Bebidas</span>
            Refrigerante Cola 2L
          </td>
          <td></td>
          <td class="sku-cell">SKU-4421</td>
          <td class="center">—</td>
          <td class="num">1.200</td>
          <td class="num editable">1.000</td>
          <td class="num">R$ 24.000,00</td>
          <td></td>
        </tr>

        <tr class="item-row" data-parent="PED-001">
          <td></td>
          <td></td>
          <td class="indent-cell">Item 2</td>
          <td class="produto-cell">
            <span class="cat-pill">Bebidas</span>
            Água Mineral 500ml (cx 24un)
          </td>
          <td></td>
          <td class="sku-cell">SKU-1102</td>
          <td class="center">—</td>
          <td class="num">3.000</td>
          <td class="num editable">2.800</td>
          <td class="num">R$ 60.600,00</td>
          <td></td>
        </tr>

        <!-- ── Segunda linha de pedido ── -->
        <tr class="pedido-row" data-id="PED-002">
          <td class="center">
            <div class="cell-check" data-checked="false"></div>
          </td>
          <td class="center">
            <button class="cell-expand" data-open="false">
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
              <div class="cell-cliente-meta">
                <span>Porto Alegre, RS</span>
                <span class="otif-chip otif-chip--warn">OTIF 81%</span>
              </div>
            </div>
          </td>
          <td>
            <span class="status-cell status-cell--success">Aprovado</span>
          </td>
          <td>
            <span class="classif classif--Diamante">Diamante</span>
          </td>
          <td class="center">
            <span class="date-cell">20/06/2025</span>
          </td>
          <td class="num">8.500</td>
          <td class="num editable">8.500</td>
          <td class="num">R$ 193.750,00</td>
          <td>
            <span class="obs-cell obs-cell-empty">—</span>
          </td>
        </tr>

      </tbody>
    </table>
  </div><!-- /table-scroll -->
</div><!-- /table-wrap -->
```

---

## CSS — LITERAL do Gestão de Carteira.html

```css
.table-wrap {
  background: var(--white);
  border: 1px solid var(--neutral-light);
  border-radius: 10px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.table-scroll {
  overflow-x: auto;
  overflow-y: visible;
}

table.carteira {
  width: 100%;
  border-collapse: separate;
  border-spacing: 0;
  font-size: 12px;
  color: var(--text-heading);
  font-family: var(--font-sans);
}

/* Header navy */
table.carteira thead th {
  position: sticky;
  top: 0;
  text-align: left;
  background: var(--primary);
  color: var(--white);
  font-weight: var(--fw-semibold);
  font-size: 12px;
  padding: 0 12px;
  height: 33px;
  border-right: 1px solid var(--neutral);
  border-bottom: 0;
  white-space: nowrap;
  z-index: 2;
}

table.carteira thead th.center,
table.carteira tbody td.center {
  text-align: center;
  padding-left: 0;
  padding-right: 0;
}

/* Hint abaixo do título de coluna */
.carteira thead th .th-hint {
  display: block;
  font-size: 9.5px;
  font-weight: var(--fw-medium);
  color: rgba(255, 255, 255, 0.55);
  margin-top: 1px;
  text-transform: none;
}
.carteira thead th .th-hint--calc {
  color: rgba(255, 255, 255, 0.7);
}
.carteira thead th .th-hint i { font-size: 9px; margin-right: 3px; }

/* Header expand caret */
.header-expand {
  width: 18px;
  height: 18px;
  display: inline-grid;
  place-items: center;
  cursor: pointer;
  color: var(--white);
  font-size: 11px;
  border-radius: 4px;
  background: transparent;
  border: 0;
  transition: all var(--dur-fast) var(--ease-standard);
}
.header-expand:hover { background: rgba(255, 255, 255, 0.18); }
.header-expand[data-open="true"] { transform: rotate(90deg); }

/* Body rows */
table.carteira tbody td {
  padding: 0 12px;
  height: 48px;
  border-bottom: 1px solid var(--neutral-lighter);
  border-right: 1px solid var(--neutral-lighter);
  background: var(--white);
  vertical-align: middle;
  font-variant-numeric: tabular-nums;
}
table.carteira tbody td:last-child { border-right: 0; }
table.carteira tbody td.num { text-align: right; }

/* Pedido row states */
table.carteira tbody tr.pedido-row { transition: background var(--dur-fast); }
table.carteira tbody tr.pedido-row:hover td { background: var(--neutral-lighter); }
table.carteira tbody tr.pedido-row.selected td { background: var(--primary-lighter); }

/* Item sub-rows */
tr.item-row td {
  background: #fbfbfd;
  height: 36px;
  padding: 0 10px;
  font-size: 11.5px;
  color: var(--text-body);
  border-bottom: 1px solid var(--neutral-lighter);
}
tr.item-row:hover td { background: var(--neutral-lighter); }
tr.item-row td.indent-cell {
  padding-left: 36px;
  color: var(--text-muted);
}
tr.item-row td.indent-cell::before {
  content: "└";
  color: var(--neutral);
  margin-right: 8px;
  font-size: 10px;
}
tr.item-row td.produto-cell {
  font-weight: var(--fw-medium);
  color: var(--text-heading);
}
tr.item-row td.produto-cell .cat-pill {
  display: inline-block;
  font-size: 9.5px;
  background: var(--neutral-lighter);
  color: var(--text-muted);
  padding: 1px 6px;
  border-radius: 4px;
  margin-right: 8px;
  font-weight: var(--fw-semibold);
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
tr.item-row td.sku-cell {
  font-family: var(--font-mono);
  color: var(--text-muted);
  font-size: 11px;
}

/* Checkbox */
.cell-check {
  width: 16px;
  height: 16px;
  border: 1px solid var(--neutral);
  border-radius: 2px;
  background: var(--white);
  display: inline-flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  flex: none;
  transition: background var(--dur-fast), border-color var(--dur-fast), border-width var(--dur-fast);
  vertical-align: middle;
}
.cell-check:hover { border-color: var(--secondary); border-width: 2px; }
.cell-check[data-checked="true"] {
  background: var(--purple-dark);
  border-color: var(--secondary);
}
.cell-check[data-checked="true"]::after {
  content: "✓";
  font-size: 11px;
  font-weight: var(--fw-bold);
  line-height: 1;
  color: var(--white);
}

/* Checkbox no header navy */
table.carteira thead .cell-check {
  background: transparent;
  border-color: rgba(255, 255, 255, 0.6);
}
table.carteira thead .cell-check:hover { border-color: var(--secondary); border-width: 2px; }
table.carteira thead .cell-check[data-checked="true"] {
  background: var(--purple-dark);
  border-color: var(--secondary);
}

/* Expand caret */
.cell-expand {
  width: 18px;
  height: 18px;
  display: inline-grid;
  place-items: center;
  cursor: pointer;
  color: var(--neutral-dark);
  background: transparent;
  border: 0;
  transition: transform var(--dur-fast) var(--ease-standard), color var(--dur-fast);
  font-size: 10px;
}
.cell-expand:hover { color: var(--text-heading); }
.cell-expand[data-open="true"] { transform: rotate(90deg); color: var(--text-heading); }

/* Pedido number (link) */
.cell-pedido {
  display: flex;
  align-items: center;
  gap: 8px;
}
.cell-pedido-num--btn {
  background: transparent;
  border: 0;
  padding: 0;
  font-family: var(--font-mono);
  font-size: 12.5px;
  font-weight: var(--fw-bold);
  color: var(--text-heading);
  cursor: pointer;
  border-radius: 3px;
  transition: color var(--dur-fast), background var(--dur-fast);
}
.cell-pedido-num--btn:hover { color: var(--primary); text-decoration: underline; }
.cell-pedido-meta { font-size: 10.5px; color: var(--text-muted); }

/* Cliente */
.cell-cliente { display: flex; flex-direction: column; gap: 1px; max-width: 220px; }
.cell-cliente-name {
  font-weight: var(--fw-semibold);
  color: var(--text-heading);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.cell-cliente-meta {
  font-size: 10.5px;
  color: var(--text-muted);
  display: flex;
  gap: 6px;
  align-items: center;
}

/* OTIF */
.otif-chip {
  font-size: 9.5px;
  font-weight: var(--fw-bold);
  padding: 1px 6px;
  border-radius: 3px;
  white-space: nowrap;
}
.otif-chip--good { color: var(--success-dark); background: var(--success-lighter); }
.otif-chip--warn { color: var(--warning-dark); background: var(--warning-lighter); }
.otif-chip--bad  { color: var(--danger); background: var(--danger-lighter); }

/* Status cell */
.status-cell {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-size: 11px;
  font-weight: var(--fw-bold);
  padding: 4px 8px 4px 6px;
  border-radius: 5px;
  cursor: pointer;
  white-space: nowrap;
  border: 1px solid transparent;
  transition: all var(--dur-fast) var(--ease-standard);
}
.status-cell:hover { border-color: var(--neutral); }
.status-cell::before {
  content: "";
  width: 6px;
  height: 6px;
  border-radius: 50%;
}
.status-cell--info    { color: var(--primary);      background: var(--primary-lighter); }
.status-cell--info::before    { background: var(--primary); }
.status-cell--warning { color: var(--warning-dark); background: var(--warning-lighter); }
.status-cell--warning::before { background: var(--warning); }
.status-cell--success { color: var(--success-dark); background: var(--success-lighter); }
.status-cell--success::before { background: var(--success); }
.status-cell--danger  { color: var(--danger);       background: var(--danger-lighter); }
.status-cell--danger::before  { background: var(--danger); }
.status-cell--neutral { color: var(--text-muted);   background: var(--neutral-lighter); }
.status-cell--neutral::before { background: var(--neutral); }

/* Classificação */
.classif {
  display: inline-flex;
  align-items: center;
  font-size: 10px;
  font-weight: var(--fw-bold);
  letter-spacing: 0.04em;
  text-transform: uppercase;
  padding: 3px 8px;
  border-radius: 4px;
  white-space: nowrap;
  border: 1px solid;
}
.classif--Diamante { color: #6e35d4; background: #f3edff; border-color: #d8c5ff; }
.classif--Ouro     { color: var(--warning-dark); background: var(--warning-lighter); border-color: var(--warning-light); }
.classif--Prata    { color: var(--text-muted); background: var(--neutral-lighter); border-color: var(--neutral-light); }
.classif--Bronze   { color: #a55229; background: #fbe9d7; border-color: #e8c8a7; }

/* Editable cells */
td.editable {
  background: linear-gradient(to top, rgba(248, 185, 103, 0.05), transparent) !important;
}
td.editable:hover {
  background: rgba(248, 185, 103, 0.12) !important;
  cursor: text;
}
.cell-edit-hint {
  opacity: 0;
  color: var(--warning-dark);
  font-size: 10px;
  margin-left: 4px;
  transition: opacity var(--dur-fast) var(--ease-standard);
}
td.editable:hover .cell-edit-hint { opacity: 1; }

/* Observações */
.obs-cell {
  font-size: 11.5px;
  color: var(--text-muted);
  font-style: italic;
  max-width: 240px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.obs-cell-empty { color: var(--neutral-light); }

/* Date cell */
.date-cell {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-size: 12px;
  color: var(--text-heading);
  font-variant-numeric: tabular-nums;
}
```

---

## JavaScript mínimo (expand/collapse sub-rows, checkbox)

```js
// Expand/collapse item-rows
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

// Checkbox individual
document.querySelectorAll('.cell-check').forEach(chk => {
  chk.addEventListener('click', () => {
    chk.dataset.checked = chk.dataset.checked === 'true' ? 'false' : 'true';
  });
});
```
