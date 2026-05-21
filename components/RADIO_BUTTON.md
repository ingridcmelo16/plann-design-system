# RadioButton — Plann Design System

## Spec

| Prop | Values |
|------|--------|
| size | `small` (20×20px, default) `xsmall` (16×16px) |
| checked | boolean |
| disabled | boolean |
| name | string (group name) |
| value | string |
| label | string (optional) |

- Border-radius: 50% (circle)
- Selected inner dot: 6×6px white circle, centered

| State | Background | Border | Dot |
|-------|-----------|--------|-----|
| unselected default | `#ffffff` | 1px `#9ca2b8` | — |
| unselected hover | `#ffffff` | 1px `#bcc8f5` | — |
| selected default | `#8d9aec` | 1px `#bcc8f5` | white 6×6px |
| selected hover | `#bcc8f5` | 1px `#8d9aec` | white 6×6px |
| disabled | `#ffffff` | 1px `#ced1e1` | — |

---

## Componente React

```jsx
// RadioButton.jsx
import styles from './RadioButton.module.css';

export function RadioButton({ size = 'small', checked, disabled, onChange, label, name, value, id }) {
  return (
    <label className={`${styles.wrapper} ${disabled ? styles.disabled : ''}`}>
      <input
        type="radio"
        id={id}
        name={name}
        value={value}
        checked={checked}
        disabled={disabled}
        onChange={(e) => onChange?.(e.target.value)}
        className={`${styles.radio} ${styles[size]}`}
      />
      {label && <span className={styles.label}>{label}</span>}
    </label>
  );
}
```

```css
/* RadioButton.module.css */
.wrapper {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  font-family: 'Epilogue', sans-serif;
}

.disabled { cursor: not-allowed; opacity: 0.6; }

.label { font-size: 14px; color: #2d3558; }

.radio {
  appearance: none;
  border-radius: 50%;
  border: 1px solid #9ca2b8;
  background: #ffffff;
  cursor: pointer;
  flex-shrink: 0;
  transition: border 0.1s, background 0.1s;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}

.small  { width: 20px; height: 20px; }
.xsmall { width: 16px; height: 16px; }

.radio:hover:not(:disabled) {
  border-color: #bcc8f5;
}

.radio:checked {
  background: #8d9aec;
  border-color: #bcc8f5;
}

.radio:checked:hover:not(:disabled) {
  background: #bcc8f5;
  border-color: #8d9aec;
}

.radio:disabled { border-color: #ced1e1; cursor: not-allowed; }

/* White inner dot when checked */
.radio:checked::after {
  content: '';
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: #ffffff;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

## Uso

```jsx
const [plan, setPlan] = useState('monthly');

<RadioButton name="plan" value="monthly" label="Mensal" checked={plan === 'monthly'} onChange={setPlan} />
<RadioButton name="plan" value="yearly" label="Anual" checked={plan === 'yearly'} onChange={setPlan} />

<RadioButton size="xsmall" name="size" value="sm" label="Pequeno" checked={size === 'sm'} onChange={setSize} />

<RadioButton name="option" value="x" label="Indisponível" disabled />
```
