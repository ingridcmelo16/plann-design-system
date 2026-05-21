# Topbar — Plann Design System

## ⚠️ REGRAS FIXAS
- Altura: **56px** — NUNCA mude
- Background: `var(--white)` — NUNCA mude
- **SEM search bar** — estrutura é: produto + breadcrumb + spacer + user pill
- Border-bottom: `1px solid var(--neutral-light)`
- Padding: `0 24px`

---

## HTML — Estrutura EXATA

```html
<div class="topbar">
  <!-- Nome do sistema/módulo (pequeno, muted) -->
  <div class="topbar-product">Gestão de Carteira</div>

  <!-- Breadcrumb da página atual -->
  <div class="topbar-breadcrumb">
    <i class="fa-solid fa-chevron-right topbar-breadcrumb-sep"></i>
    <span class="topbar-breadcrumb-current">Pedidos</span>
  </div>

  <!-- Spacer empurra user pill para direita -->
  <div class="topbar-spacer"></div>

  <!-- User pill -->
  <button class="topbar-user" aria-label="Conta de usuário">
    <span class="topbar-user-avatar">A</span>
    <span>Admin-Plannera</span>
    <i class="fa-solid fa-chevron-down"></i>
  </button>
</div>
```

### Variação com breadcrumb de múltiplos níveis
```html
<div class="topbar">
  <div class="topbar-product">S&OE</div>
  <div class="topbar-breadcrumb">
    <i class="fa-solid fa-chevron-right topbar-breadcrumb-sep"></i>
    <span>Sazonais</span>
    <i class="fa-solid fa-chevron-right topbar-breadcrumb-sep"></i>
    <span class="topbar-breadcrumb-current">Faseamento</span>
  </div>
  <div class="topbar-spacer"></div>
  <button class="topbar-user" aria-label="Conta de usuário">
    <span class="topbar-user-avatar">G</span>
    <span>Gael</span>
    <i class="fa-solid fa-chevron-down"></i>
  </button>
</div>
```

---

## CSS — LITERAL do Gestão de Carteira.html

```css
.topbar {
  height: 56px;
  flex: none;
  background: var(--white);
  border-bottom: 1px solid var(--neutral-light);
  display: flex;
  align-items: center;
  padding: 0 24px;
  gap: 16px;
}

.topbar-product {
  font-size: 12px;
  font-weight: 500;
  color: var(--neutral);
  letter-spacing: 0.1px;
}

.topbar-breadcrumb {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 12px;
  color: var(--text-muted);
  margin-left: -10px;
}

.topbar-breadcrumb-sep {
  color: var(--neutral);
  font-size: 10px;
}

.topbar-breadcrumb-current {
  color: var(--text-heading);
  font-weight: 500;
}

.topbar-spacer {
  flex: 1;
}

.topbar-iconbtn {
  width: 36px;
  height: 36px;
  border: 0;
  background: transparent;
  color: var(--text-body);
  border-radius: 8px;
  cursor: pointer;
  display: grid;
  place-items: center;
  font-size: 15px;
  transition: background var(--dur-fast) var(--ease-standard);
  position: relative;
}

.topbar-iconbtn:hover {
  background: var(--neutral-lighter);
}

.topbar-iconbtn .bell-dot {
  position: absolute;
  top: 8px;
  right: 9px;
  width: 7px;
  height: 7px;
  border-radius: 50%;
  background: var(--danger);
  border: 2px solid var(--white);
}

.topbar-user {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 4px 14px 4px 4px;
  border-radius: 100px;
  background: var(--neutral-lighter);
  cursor: pointer;
  font-size: 13px;
  font-weight: var(--fw-semibold);
  color: var(--text-body);
  border: 0;
  transition: background var(--dur-fast) var(--ease-standard);
  font-family: var(--font-sans);
}

.topbar-user:hover {
  background: var(--neutral-light);
}

.topbar-user-avatar {
  width: 28px;
  height: 28px;
  border-radius: 50%;
  background: var(--white);
  display: grid;
  place-items: center;
  font-size: 12px;
  font-weight: var(--fw-bold);
  color: var(--text-body);
  border: 1px solid var(--neutral-light);
}

.topbar-user .fa-chevron-down {
  font-size: 10px;
  color: var(--neutral-dark);
}
```
