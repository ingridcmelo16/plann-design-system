# Sidebar — Plann Design System

## ⚠️ REGRAS FIXAS
- Largura: **64px** — NUNCA mude
- Background: `var(--primary)` (#2d3558) — NUNCA mude
- **Só ícones** — sem texto, sem labels de seção visíveis
- Ícones: FontAwesome Solid (`fa-solid`)
- Tooltips aparecem à **direita** no hover
- `data-active="true"` no item ativo
- Logo no topo, sempre

---

## HTML — Estrutura EXATA

```html
<aside class="sidebar">
  <!-- Logo -->
  <div class="sidebar-logo" title="[Nome do Sistema]">
    <!-- SVG do logo Plannera -->
    <svg width="26" height="auto" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
      <!-- Use o asset real: /assets/logo-plannera.svg -->
      <!-- Fallback: letra P em destaque -->
      <text x="8" y="22" font-family="Epilogue, sans-serif" font-weight="700" font-size="18" fill="#f7941e">P</text>
    </svg>
  </div>

  <!-- Item ativo (data-active="true") -->
  <button
    class="sidebar-icon"
    data-active="true"
    aria-label="Carteira de Pedidos"
    type="button"
  >
    <i class="fa-solid fa-box-archive" aria-hidden="true"></i>
    <span class="sidebar-tooltip">Carteira de Pedidos</span>
  </button>

  <!-- Item inativo -->
  <button
    class="sidebar-icon"
    data-active="false"
    aria-label="Dashboard"
    type="button"
  >
    <i class="fa-solid fa-chart-line" aria-hidden="true"></i>
    <span class="sidebar-tooltip">Dashboard</span>
  </button>

  <!-- Divisor (opcional, entre grupos de ícones) -->
  <div class="sidebar-divider"></div>

  <!-- Mais itens... repita o padrão do button acima -->

  <!-- Spacer empurra itens do fundo pra baixo -->
  <div class="sidebar-spacer"></div>

  <!-- Itens do rodapé (ex: configurações, perfil) -->
  <button
    class="sidebar-icon"
    data-active="false"
    aria-label="Configurações"
    type="button"
  >
    <i class="fa-solid fa-gear" aria-hidden="true"></i>
    <span class="sidebar-tooltip">Configurações</span>
  </button>
</aside>
```

---

## CSS — LITERAL do Gestão de Carteira.html

```css
.sidebar {
  background: var(--primary);
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 12px 0;
  gap: 8px;
  overflow: visible;
  width: 64px;
  height: 100vh;
}

.sidebar-logo {
  width: 40px;
  height: 40px;
  display: grid;
  place-items: center;
  margin-bottom: 8px;
}

.sidebar-logo-svg {
  width: 26px;
  height: auto;
  fill: var(--warning-dark);
  display: block;
}

.sidebar-icon {
  width: 100%;
  height: 44px;
  display: grid;
  place-items: center;
  color: rgba(255, 255, 255, 0.55);
  cursor: pointer;
  transition: all var(--dur-fast) var(--ease-standard);
  position: relative;
  font-size: 16px;
  border: 0;
  border-radius: 0;
  background: transparent;
  text-decoration: none;
}

.sidebar-icon:hover {
  background: rgba(255, 255, 255, 0.08);
  color: var(--white);
}

.sidebar-icon[data-active="true"] {
  background: rgba(255, 255, 255, 0.10);
  color: var(--white);
}

.sidebar-tooltip {
  position: absolute;
  left: calc(100% + 12px);
  top: 50%;
  transform: translateY(-50%);
  background: var(--neutral);
  color: var(--white);
  padding: 6px 10px;
  border-radius: 6px;
  font-size: 12px;
  font-weight: 500;
  white-space: nowrap;
  opacity: 0;
  pointer-events: none;
  transition: opacity var(--dur-fast) var(--ease-standard);
  z-index: 100;
}

.sidebar-icon:hover .sidebar-tooltip {
  opacity: 1;
}

.sidebar-divider {
  width: 32px;
  height: 1px;
  background: rgba(255, 255, 255, 0.10);
  margin: 6px 0;
}

.sidebar-spacer {
  flex: 1;
}
```

---

## Ícones FontAwesome — referência de ícones comuns

| Módulo | Ícone sugerido |
|---|---|
| Carteira/Pedidos | `fa-box-archive` |
| Dashboard | `fa-chart-line` |
| Reabastecimento | `fa-rotate` |
| Sazonais | `fa-calendar-star` |
| Cadastros | `fa-database` |
| Dados | `fa-table` |
| Relatórios | `fa-file-chart-column` |
| Administração | `fa-sliders` |
| Configurações | `fa-gear` |
| Usuário/Perfil | `fa-circle-user` |

---

## Integração no app-shell

```html
<!-- Estrutura mínima de page layout -->
<div class="app-shell">
  <aside class="sidebar">
    <!-- sidebar aqui -->
  </aside>
  <div class="main-col">
    <!-- topbar + conteúdo aqui -->
  </div>
</div>

<style>
  .app-shell {
    display: grid;
    grid-template-columns: 64px 1fr;
    height: 100vh;
    overflow: hidden;
  }
  .main-col {
    display: flex;
    flex-direction: column;
    min-width: 0;
    height: 100vh;
    overflow: hidden;
  }
</style>
```
