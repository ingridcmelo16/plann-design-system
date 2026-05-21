# TextInput — Plann Design System

## Spec

| Prop | Values |
|------|--------|
| size | `small` (36px) `medium` (42px, default) `large` (50px) |
| label | string |
| error | string |
| disabled | boolean |

- All sizes: padding 8px 12px, font 14px, border-radius 4px
- Label: 12px semibold, above input
- Error message: 12px `#cb5158`, below input

| State | Border | Background | Shadow |
|-------|--------|-----------|--------|
| default | 1px solid `#dadeea` | `#ffffff` | — |
| hover | 1px solid `#2d3558` | `#ffffff` | — |
| focus | 2px solid `#2d3558` | `#ffffff` | `0 4px 5px rgba(0,0,0,.1)` |
| error | 1px solid `#cb5158` | `#ffffff` | — |
| disabled | 1px solid `#dadeea` | `#f4f5f9` | — |

---

## Componente React

```jsx
// TextInput.jsx
import styles from './TextInput.module.css';

export function TextInput({
  size = 'medium',
  label,
  error,
  disabled = false,
  id,
  ...props
}) {
  return (
    <div className={styles.wrapper}>
      {label && (
        <label htmlFor={id} className={styles.label}>{label}</label>
      )}
      <input
        id={id}
        disabled={disabled}
        className={`${styles.input} ${styles[size]} ${error ? styles.errorState : ''}`}
        {...props}
      />
      {error && <span className={styles.errorMsg}>{error}</span>}
    </div>
  );
}
```

```css
/* TextInput.module.css */
.wrapper {
  display: flex;
  flex-direction: column;
  gap: 4px;
  font-family: 'Epilogue', sans-serif;
}

.label {
  font-size: 12px;
  font-weight: 600;
  color: #2d3558;
}

.input {
  padding: 8px 12px;
  font-size: 14px;
  font-family: 'Epilogue', sans-serif;
  color: #2d3558;
  background: #ffffff;
  border: 1px solid #dadeea;
  border-radius: 4px;
  outline: none;
  transition: border 0.15s, box-shadow 0.15s;
}

.input::placeholder { color: #9ca2b8; }

.input:hover:not(:disabled):not(.errorState) {
  border-color: #2d3558;
}

.input:focus:not(:disabled) {
  border: 2px solid #2d3558;
  box-shadow: 0 4px 5px rgba(0, 0, 0, 0.1);
}

.input:disabled {
  background: #f4f5f9;
  cursor: not-allowed;
  color: #9ca2b8;
}

.errorState { border-color: #cb5158 !important; }

.errorMsg {
  font-size: 12px;
  color: #cb5158;
  font-family: 'Epilogue', sans-serif;
}

.small  { height: 36px; }
.medium { height: 42px; }
.large  { height: 50px; }
```

## Uso

```jsx
<TextInput label="Nome" placeholder="João Silva" size="medium" />

<TextInput
  label="Email"
  type="email"
  error="Insira um e-mail válido"
  size="medium"
/>

<TextInput label="Campo desabilitado" value="valor fixo" disabled />
```
