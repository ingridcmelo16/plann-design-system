# Tooltip — Plann Design System

## Spec

| Prop | Values |
|------|--------|
| content | string |
| variant | `primary` (default) `neutral` |
| position | `top` (default) `bottom` `left` `right` |
| children | trigger element |

- Height: 36px
- Padding: 8px
- Border-radius: 2px
- Font: 12px semibold white
- Arrow: 6px pointing toward element
- Appears on hover, hides on mouse leave

| Variant | Background |
|---------|-----------|
| primary | `#2d3558` |
| neutral | `#9ca2b8` |

---

## Componente React

```jsx
// Tooltip.jsx
import styles from './Tooltip.module.css';

export function Tooltip({ content, variant = 'primary', position = 'top', children }) {
  return (
    <span className={styles.wrapper}>
      {children}
      <span className={`${styles.tooltip} ${styles[variant]} ${styles[position]}`}>
        {content}
      </span>
    </span>
  );
}
```

```css
/* Tooltip.module.css */
.wrapper {
  position: relative;
  display: inline-flex;
}

.tooltip {
  position: absolute;
  height: 36px;
  padding: 0 8px;
  border-radius: 2px;
  font-family: 'Epilogue', sans-serif;
  font-size: 12px;
  font-weight: 600;
  color: #ffffff;
  white-space: nowrap;
  display: flex;
  align-items: center;
  pointer-events: none;
  opacity: 0;
  transition: opacity 0.15s;
  z-index: 100;
}

.wrapper:hover .tooltip { opacity: 1; }

.primary { background: #2d3558; }
.neutral { background: #9ca2b8; }

/* Positions */
.top {
  bottom: calc(100% + 8px);
  left: 50%;
  transform: translateX(-50%);
}

.bottom {
  top: calc(100% + 8px);
  left: 50%;
  transform: translateX(-50%);
}

.left {
  right: calc(100% + 8px);
  top: 50%;
  transform: translateY(-50%);
}

.right {
  left: calc(100% + 8px);
  top: 50%;
  transform: translateY(-50%);
}

/* Arrows */
.tooltip::after {
  content: '';
  position: absolute;
  border: 6px solid transparent;
}

.top::after {
  top: 100%;
  left: 50%;
  transform: translateX(-50%);
  border-top-color: inherit;
}

.bottom::after {
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%);
  border-bottom-color: inherit;
}

.left::after {
  left: 100%;
  top: 50%;
  transform: translateY(-50%);
  border-left-color: inherit;
}

.right::after {
  right: 100%;
  top: 50%;
  transform: translateY(-50%);
  border-right-color: inherit;
}
```

## Uso

```jsx
<Tooltip content="Salvar alterações" position="top">
  <button>Salvar</button>
</Tooltip>

<Tooltip content="Remover item" variant="neutral" position="bottom">
  <span>Excluir</span>
</Tooltip>

<Tooltip content="Informação extra" position="right" variant="primary">
  <InfoIcon />
</Tooltip>
```
