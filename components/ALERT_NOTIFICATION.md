# AlertNotification — Plann Design System

## Spec

| Prop | Values |
|------|--------|
| variant | `info` `success` `warning` `danger` |
| title | string (14px semibold) |
| description | string (14px regular, optional) |
| onClose | function (optional) |

- Border-radius: 4px
- Padding: 12px 16px
- Border-left: 4px solid (variant color)

| Variant | Background | Border | Text |
|---------|-----------|--------|------|
| info | `#e3eaf6` | `#2d3558` | `#2d3558` |
| success | `#ebfcf0` | `#47b274` | `#17653e` |
| warning | `#fef8ee` | `#f8b967` | `#f7941e` |
| danger | `#fff0f0` | `#cb5158` | `#832e3b` |

---

## Componente React

```jsx
// AlertNotification.jsx
import styles from './AlertNotification.module.css';

export function AlertNotification({ variant = 'info', title, description, onClose }) {
  return (
    <div className={`${styles.alert} ${styles[variant]}`} role="alert">
      <div className={styles.body}>
        <span className={styles.title}>{title}</span>
        {description && <span className={styles.description}>{description}</span>}
      </div>
      {onClose && (
        <button className={styles.close} onClick={onClose} aria-label="Fechar">✕</button>
      )}
    </div>
  );
}
```

```css
/* AlertNotification.module.css */
.alert {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 12px;
  padding: 12px 16px;
  border-radius: 4px;
  border-left: 4px solid;
  font-family: 'Epilogue', sans-serif;
}

.body {
  display: flex;
  flex-direction: column;
  gap: 4px;
  flex: 1;
}

.title {
  font-size: 14px;
  font-weight: 600;
}

.description {
  font-size: 14px;
  font-weight: 400;
}

.close {
  background: none;
  border: none;
  cursor: pointer;
  font-size: 14px;
  color: currentColor;
  padding: 0;
  flex-shrink: 0;
  line-height: 1;
  opacity: 0.7;
}

.close:hover { opacity: 1; }

.info    { background: #e3eaf6; border-color: #2d3558; color: #2d3558; }
.success { background: #ebfcf0; border-color: #47b274; color: #17653e; }
.warning { background: #fef8ee; border-color: #f8b967; color: #f7941e; }
.danger  { background: #fff0f0; border-color: #cb5158; color: #832e3b; }
```

## Uso

```jsx
<AlertNotification variant="info" title="Dica" description="Preencha todos os campos." />

<AlertNotification variant="success" title="Salvo!" description="Suas alterações foram salvas." onClose={() => {}} />

<AlertNotification variant="warning" title="Atenção" description="Seu plano expira em 3 dias." onClose={() => {}} />

<AlertNotification variant="danger" title="Erro" description="Não foi possível concluir a ação." onClose={() => {}} />
```
