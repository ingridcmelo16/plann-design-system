# Toggle — Plann Design System

## Spec

| Prop | Values |
|------|--------|
| size | `small` `medium` (default) `large` |
| checked | boolean |
| disabled | boolean |
| onChange | function |

| Size | Track | Handle |
|------|-------|--------|
| small | 36×20px | 12px |
| medium | 42×24px | 16px |
| large | 50×32px | 20px |

- Border-radius: 100px (pill)
- All handles: 4px inset from track edge

| State | Track background | Track border | Handle |
|-------|-----------------|-------------|--------|
| off default | `#ffffff` | 1px `#9ca2b8` | `#9ca2b8` at left |
| on default | `#8d9aec` | none | `#ffffff` at right |
| off disabled | `#ffffff` | 1px `#dadeea` | `#dadeea` |
| on disabled | `#dadeea` | none | `#ffffff` |

---

## Componente React

```jsx
// Toggle.jsx
import styles from './Toggle.module.css';

export function Toggle({ size = 'medium', checked = false, disabled = false, onChange, label }) {
  return (
    <label className={`${styles.wrapper} ${disabled ? styles.disabled : ''}`}>
      <span
        className={`${styles.track} ${styles[size]} ${checked ? styles.on : styles.off} ${disabled ? styles.disabledTrack : ''}`}
        onClick={() => !disabled && onChange?.(!checked)}
        role="switch"
        aria-checked={checked}
        tabIndex={disabled ? -1 : 0}
        onKeyDown={(e) => e.key === ' ' && !disabled && onChange?.(!checked)}
      >
        <span className={`${styles.handle} ${styles[`handle_${size}`]} ${checked ? styles.handleOn : ''}`} />
      </span>
      {label && <span className={styles.label}>{label}</span>}
    </label>
  );
}
```

```css
/* Toggle.module.css */
.wrapper {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  font-family: 'Epilogue', sans-serif;
}

.disabled { cursor: not-allowed; }

.label { font-size: 14px; color: #2d3558; }

.track {
  position: relative;
  border-radius: 100px;
  transition: background 0.2s, border 0.2s;
  flex-shrink: 0;
}

.small  { width: 36px; height: 20px; }
.medium { width: 42px; height: 24px; }
.large  { width: 50px; height: 32px; }

.off {
  background: #ffffff;
  border: 1px solid #9ca2b8;
}

.on {
  background: #8d9aec;
  border: none;
}

.disabledTrack.off { border-color: #dadeea; }
.disabledTrack.on  { background: #dadeea; }

.handle {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  border-radius: 50%;
  background: #9ca2b8;
  transition: left 0.2s, background 0.2s;
}

.handle_small  { width: 12px; height: 12px; left: 4px; }
.handle_medium { width: 16px; height: 16px; left: 4px; }
.handle_large  { width: 20px; height: 20px; left: 6px; }

.handleOn { background: #ffffff; }

.small  .handleOn { left: calc(36px - 12px - 4px); }
.medium .handleOn { left: calc(42px - 16px - 4px); }
.large  .handleOn { left: calc(50px - 20px - 6px); }

.disabledTrack .handle { background: #dadeea; }
.disabledTrack.on .handle { background: #ffffff; }
```

## Uso

```jsx
const [active, setActive] = useState(false);

<Toggle checked={active} onChange={setActive} label="Notificações" />

<Toggle size="small" checked={active} onChange={setActive} />

<Toggle size="large" checked={true} onChange={() => {}} label="Modo escuro" />

<Toggle checked={false} disabled label="Funcionalidade indisponível" />
```
