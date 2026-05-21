# Filter Panel — Plann Design System

## ⚠️ REGRAS FIXAS
- O painel de filtros sempre fica dentro de `.plann-filter-card`
- Estrutura: header (toggle + chips ativos) → fields (campos de filtro)
- Dropdowns usam `data-open="true/false"` no trigger
- Opções selecionadas usam `data-checked="true"` na `.plann-filter-option`
- Contador no toggle usa `.plann-filter-toggle-count` (pill azul)

---

## HTML — Estrutura EXATA (copie e adapte textos/labels)

```html
<!-- Container branco envolvente -->
<div class="plann-filter-card">
  <div class="plann-filter-bar">

    <!-- ── Header: toggle + chips ativos + limpar tudo ── -->
    <div class="plann-filter-header">

      <!-- Botão toggle que expande/recolhe os campos -->
      <button class="plann-filter-toggle" type="button">
        <i class="fa-solid fa-filter funnel"></i>
        Filtros
        <!-- Contador de filtros ativos (some se = 0) -->
        <span class="plann-filter-toggle-count">2</span>
        <i class="fa-solid fa-chevron-down chevron"></i>
      </button>

      <!-- Chip de filtro ativo (repita para cada filtro aplicado) -->
      <div class="plann-filter-active-chip">
        <span class="plann-filter-active-chip-label">Status:</span>
        <span class="plann-filter-active-chip-value">Ativo, Pendente</span>
        <button class="plann-filter-active-chip-x" type="button" aria-label="Remover filtro Status">×</button>
      </div>

      <div class="plann-filter-active-chip">
        <span class="plann-filter-active-chip-label">Região:</span>
        <span class="plann-filter-active-chip-value">Sul</span>
        <button class="plann-filter-active-chip-x" type="button" aria-label="Remover filtro Região">×</button>
      </div>

      <!-- Limpar todos os filtros (só aparece se há filtros ativos) -->
      <button class="plann-filter-clear-all" type="button">Limpar tudo</button>
    </div>

    <!-- ── Campos de filtro (expansível via JS) ── -->
    <div class="plann-filter-fields">

      <!-- Campo 1: dropdown simples -->
      <div class="plann-filter-field">
        <label class="plann-filter-field-label">Status</label>
        <div class="plann-filter-field-select">
          <button class="plann-filter-field-trigger" data-open="false" type="button">
            <span>Todos</span>
            <i class="fa-solid fa-chevron-down chevron"></i>
          </button>

          <!-- Dropdown (visível quando data-open="true") -->
          <div class="plann-filter-dropdown" style="display:none;">
            <button class="plann-filter-option" data-checked="false" type="button">
              <span class="plann-filter-option-label todos">Todos</span>
              <div class="plann-filter-option-check"></div>
            </button>
            <button class="plann-filter-option" data-checked="true" type="button">
              <span class="plann-filter-option-label">Ativo</span>
              <div class="plann-filter-option-check"></div>
            </button>
            <button class="plann-filter-option" data-checked="true" type="button">
              <span class="plann-filter-option-label">Pendente</span>
              <div class="plann-filter-option-check"></div>
            </button>
            <button class="plann-filter-option" data-checked="false" type="button">
              <span class="plann-filter-option-label">Inativo</span>
              <div class="plann-filter-option-check"></div>
            </button>
          </div>
        </div>
      </div>

      <!-- Campo 2: outro dropdown -->
      <div class="plann-filter-field">
        <label class="plann-filter-field-label">Região</label>
        <div class="plann-filter-field-select">
          <button class="plann-filter-field-trigger" data-open="false" type="button">
            <span>Todas</span>
            <i class="fa-solid fa-chevron-down chevron"></i>
          </button>
          <div class="plann-filter-dropdown" style="display:none;">
            <button class="plann-filter-option" data-checked="false" type="button">
              <span class="plann-filter-option-label todos">Todas</span>
              <div class="plann-filter-option-check"></div>
            </button>
            <button class="plann-filter-option" data-checked="false" type="button">
              <span class="plann-filter-option-label">Norte</span>
              <div class="plann-filter-option-check"></div>
            </button>
            <button class="plann-filter-option" data-checked="false" type="button">
              <span class="plann-filter-option-label">Sul</span>
              <div class="plann-filter-option-check"></div>
            </button>
            <button class="plann-filter-option" data-checked="false" type="button">
              <span class="plann-filter-option-label">Sudeste</span>
              <div class="plann-filter-option-check"></div>
            </button>
          </div>
        </div>
      </div>

      <!-- Adicione quantos campos precisar seguindo o mesmo padrão -->

    </div><!-- /plann-filter-fields -->

  </div><!-- /plann-filter-bar -->
</div><!-- /plann-filter-card -->
```

---

## JavaScript mínimo para toggle e dropdowns

```js
// Toggle expande/recolhe os fields
document.querySelectorAll('.plann-filter-toggle').forEach(btn => {
  btn.addEventListener('click', () => {
    const bar = btn.closest('.plann-filter-bar');
    const fields = bar.querySelector('.plann-filter-fields');
    const chevron = btn.querySelector('.chevron');
    const isOpen = fields.style.display !== 'none';
    fields.style.display = isOpen ? 'none' : 'flex';
    chevron.style.transform = isOpen ? '' : 'rotate(180deg)';
  });
});

// Abre/fecha dropdown de filtro
document.querySelectorAll('.plann-filter-field-trigger').forEach(trigger => {
  trigger.addEventListener('click', (e) => {
    e.stopPropagation();
    const select = trigger.closest('.plann-filter-field-select');
    const dropdown = select.querySelector('.plann-filter-dropdown');
    const isOpen = trigger.dataset.open === 'true';
    // Fecha todos os outros
    document.querySelectorAll('.plann-filter-field-trigger').forEach(t => {
      t.dataset.open = 'false';
      t.closest('.plann-filter-field-select').querySelector('.plann-filter-dropdown').style.display = 'none';
    });
    trigger.dataset.open = isOpen ? 'false' : 'true';
    dropdown.style.display = isOpen ? 'none' : 'block';
  });
});

// Fecha ao clicar fora
document.addEventListener('click', () => {
  document.querySelectorAll('.plann-filter-field-trigger').forEach(t => {
    t.dataset.open = 'false';
    t.closest('.plann-filter-field-select').querySelector('.plann-filter-dropdown').style.display = 'none';
  });
});

// Toggle opção checked
document.querySelectorAll('.plann-filter-option').forEach(opt => {
  opt.addEventListener('click', (e) => {
    e.stopPropagation();
    const checked = opt.dataset.checked === 'true';
    opt.dataset.checked = checked ? 'false' : 'true';
  });
});

// Remover chip
document.querySelectorAll('.plann-filter-active-chip-x').forEach(btn => {
  btn.addEventListener('click', () => btn.closest('.plann-filter-active-chip').remove());
});
```

---

## CSS — LITERAL do Gestão de Carteira.html

```css
.plann-filter-card {
  background: var(--white);
  border-radius: 10px;
  padding: 12px 16px;
  margin-top: 20px;
  margin-bottom: 20px;
}

.plann-filter-bar {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.plann-filter-header {
  display: flex;
  align-items: center;
  gap: 12px;
  flex-wrap: wrap;
}

.plann-filter-toggle {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 8px 12px;
  background: var(--white);
  border: 1px solid var(--neutral-light);
  border-radius: 6px;
  font-family: var(--font-sans);
  font-size: 13px;
  font-weight: var(--fw-semibold);
  color: var(--text-heading);
  cursor: pointer;
  transition: border-color var(--dur-fast) var(--ease-standard);
  height: 38px;
}
.plann-filter-toggle:hover { border-color: var(--text-heading); }
.plann-filter-toggle .funnel { font-size: 12px; color: var(--text-heading); }
.plann-filter-toggle .chevron { font-size: 10px; color: var(--neutral-dark); transition: transform var(--dur-fast); }

.plann-filter-toggle-count {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-width: 20px;
  height: 20px;
  padding: 0 6px;
  border-radius: 100px;
  background: var(--primary);
  color: var(--white);
  font-size: 11px;
  font-weight: var(--fw-bold);
}

.plann-filter-active-chip {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 5px 8px 5px 10px;
  background: var(--neutral-lighter);
  border-radius: 6px;
  font-size: 12px;
  color: var(--text-heading);
  max-width: 340px;
}
.plann-filter-active-chip-label {
  color: var(--text-muted);
  font-weight: var(--fw-semibold);
}
.plann-filter-active-chip-value {
  font-weight: var(--fw-medium);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.plann-filter-active-chip-x {
  background: transparent;
  border: 0;
  width: 18px;
  height: 18px;
  border-radius: 4px;
  display: grid;
  place-items: center;
  cursor: pointer;
  color: var(--text-muted);
  font-size: 11px;
}
.plann-filter-active-chip-x:hover {
  background: var(--neutral-light);
  color: var(--text-heading);
}

.plann-filter-clear-all {
  background: transparent;
  border: 0;
  cursor: pointer;
  font-family: var(--font-sans);
  font-size: 12.5px;
  color: var(--primary);
  font-weight: var(--fw-semibold);
  padding: 4px 8px;
  border-radius: 4px;
}
.plann-filter-clear-all:hover { background: var(--primary-lighter); }

.plann-filter-fields {
  display: flex;
  flex-wrap: wrap;
  gap: 14px 24px;
  align-items: center;
  padding: 4px;
}

.plann-filter-field {
  display: inline-flex;
  align-items: center;
  gap: 10px;
}

.plann-filter-field-label {
  font-size: 13px;
  color: var(--text-heading);
  font-weight: var(--fw-medium);
  font-family: var(--font-sans);
}

.plann-filter-field-select {
  position: relative;
}

.plann-filter-field-trigger {
  display: inline-flex;
  align-items: center;
  justify-content: space-between;
  gap: 14px;
  min-width: 140px;
  height: 38px;
  padding: 0 12px;
  background: var(--white);
  border: 1px solid var(--neutral-light);
  border-radius: 6px;
  cursor: pointer;
  font-family: var(--font-sans);
  font-size: 13px;
  font-weight: var(--fw-medium);
  color: var(--text-heading);
}
.plann-filter-field-trigger:hover { border-color: var(--text-heading); }
.plann-filter-field-trigger[data-open="true"] {
  border-color: var(--primary);
  box-shadow: 0 0 0 3px var(--purple-lighter);
}
.plann-filter-field-trigger .chevron {
  font-size: 10px;
  color: var(--neutral-dark);
}

.plann-filter-dropdown {
  position: absolute;
  top: calc(100% + 4px);
  left: 0;
  min-width: 240px;
  max-height: 320px;
  overflow-y: auto;
  background: var(--white);
  border: 1px solid var(--neutral-light);
  border-radius: 8px;
  box-shadow: var(--shadow-popover);
  z-index: 30;
  padding: 4px 0;
}

.plann-filter-option {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  padding: 9px 14px;
  cursor: pointer;
  font-size: 13px;
  color: var(--text-heading);
  border: 0;
  background: transparent;
  width: 100%;
  font-family: var(--font-sans);
  text-align: left;
}
.plann-filter-option:hover { background: var(--neutral-lighter); }

.plann-filter-option-label {
  flex: 1;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.plann-filter-option-label.todos {
  font-weight: var(--fw-bold);
  text-transform: uppercase;
  letter-spacing: 0.04em;
  font-size: 11.5px;
}

.plann-filter-option-check {
  width: 18px;
  height: 18px;
  border: 1.5px solid var(--neutral);
  border-radius: 3px;
  background: var(--white);
  display: inline-grid;
  place-items: center;
  flex: none;
  color: var(--white);
  font-size: 11px;
}
.plann-filter-option[data-checked="true"] .plann-filter-option-check {
  background: var(--purple-dark);
  border-color: var(--purple-dark);
}
.plann-filter-option[data-checked="true"] .plann-filter-option-check::after {
  content: "✓";
}
```
