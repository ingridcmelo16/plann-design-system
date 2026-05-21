# Badge — Plann Design System

## Spec

| Prop | Values |
|------|--------|
| variant | `success` `danger` `warning` `info` `neutral` |
| dot | `boolean` — 6×6px dot before label |

| Variant | Background | Text |
|---------|-----------|------|
| success | `#ebfcf0` | `#17653e` |
| danger | `#fff0f0` | `#832e3b` |
| warning | `#fef8ee` | `#f7941e` |
| info | `#e3eaf6` | `#2d3558` |
| neutral | `#f4f5f9` | `#9ca2b8` |

- Border-radius: 100px
- Padding: 2px 8px
- Font: 12px / semibold (600)
- Dot: 6×6px circle, gap 4px

---

## Componente React

```jsx
// Badge.jsx
import styles from './Badge.module.css';

export function Badge({ variant = 'neutral', dot = false, children }) {
  return (
    <span className={`${styles.badge} ${styles[variant]}`}>
      {dot && <span className={styles.dot} />}
      {children}
    </span>
  );
}
```

```css
/* Badge.module.css */
.badge {
  display: inline-flex;
  align-items: center;
  gap: 4px;
  padding: 2px 8px;
  border-radius: 100px;
  font-size: 12px;
  font-weight: 600;
  font-family: 'Epilogue', sans-serif;
  line-height: 1.5;
}

.dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background-color: currentColor;
  flex-shrink: 0;
}

.success { background: #ebfcf0; color: #17653e; }
.danger  { background: #fff0f0; color: #832e3b; }
.warning { background: #fef8ee; color: #f7941e; }
.info    { background: #e3eaf6; color: #2d3558; }
.neutral { background: #f4f5f9; color: #9ca2b8; }
```

## Uso

```jsx
<Badge variant="success">Ativo</Badge>
<Badge variant="danger">Erro</Badge>
<Badge variant="warning" dot>Pendente</Badge>
<Badge variant="info" dot>Em andamento</Badge>
<Badge variant="neutral">Inativo</Badge>
```
