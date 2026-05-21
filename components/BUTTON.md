# Button — Plann Design System

## Variantes
| Variant | BG | Text | Hover | Disabled |
|---|---|---|---|---|
| primary | #2d3558 | #fff | #495583 | #9ca2b8 |
| secondary | #fff | #2d3558 | bg #2d3558 text #fff | #9ca2b8 |
| tertiary | transparent | #2d3558 | #bcc8f5 | transparent |
| destructive | #cb5158 | #fff | #ebb6b6 | #fff0f0 |

## Tamanhos
| Size | Height | Padding | Font | Icon |
|---|---|---|---|---|
| small | 36px | 8px 12px | 14px bold | 12px |
| medium | 42px | 0 12px | 14px bold | 16px |
| large | 50px | 0 16px | 14px bold | 18px |
| xlarge | 50px | 0 24px | 16px bold | 18px |

- Gap ícone/texto: 8px · Border-radius: 4px
- Square = só ícone, sem texto (proporção 1:1)
- Máximo 1 primary button por seção

---

## Componente React

```jsx
// Button.jsx
import styles from './Button.module.css';

export function Button({
  variant = 'primary',
  size = 'medium',
  square = false,
  leftIcon,
  rightIcon,
  disabled = false,
  onClick,
  children,
  ...rest
}) {
  return (
    <button
      className={[
        styles.btn,
        styles[variant],
        styles[size],
        square ? styles.square : '',
      ].join(' ')}
      disabled={disabled}
      onClick={onClick}
      {...rest}
    >
      {leftIcon && <span className={styles.icon}>{leftIcon}</span>}
      {children}
      {rightIcon && <span className={styles.icon}>{rightIcon}</span>}
    </button>
  );
}
```

```css
/* Button.module.css */
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  border: none;
  border-radius: 4px;
  font-family: 'Epilogue', sans-serif;
  font-weight: 700;
  cursor: pointer;
  white-space: nowrap;
  transition: background 120ms, color 120ms, border-color 120ms;
}
.btn:disabled { cursor: not-allowed; }

.primary { background: #2d3558; color: #fff; }
.primary:hover:not(:disabled) { background: #495583; }
.primary:disabled { background: #9ca2b8; }

.secondary { background: #fff; color: #2d3558; border: 1px solid #2d3558; }
.secondary:hover:not(:disabled) { background: #2d3558; color: #fff; }
.secondary:disabled { background: #9ca2b8; border-color: #9ca2b8; }

.tertiary { background: transparent; color: #2d3558; }
.tertiary:hover:not(:disabled) { background: #bcc8f5; }
.tertiary:disabled { color: #9ca2b8; }

.destructive { background: #cb5158; color: #fff; }
.destructive:hover:not(:disabled) { background: #ebb6b6; }
.destructive:disabled { background: #fff0f0; color: #ebb6b6; }

.small  { height: 36px; padding: 8px 12px; font-size: 14px; }
.medium { height: 42px; padding: 0 12px;   font-size: 14px; }
.large  { height: 50px; padding: 0 16px;   font-size: 14px; }
.xlarge { height: 50px; padding: 0 24px;   font-size: 16px; min-width: 384px; }

.square.small  { width: 36px; padding: 0; }
.square.medium { width: 42px; padding: 0; }
.square.large  { width: 50px; padding: 0; }

.icon { display: flex; align-items: center; }
```

## Uso

```jsx
// Primary small com ícone direita
<Button variant="primary" size="small" rightIcon={<ArrowRight size={12} />}>
  Continuar
</Button>

// Secondary medium
<Button variant="secondary" size="medium">Cancelar</Button>

// Destructive com ícone
<Button variant="destructive" size="medium" leftIcon={<Trash size={16} />}>
  Excluir
</Button>

// Square (só ícone)
<Button variant="primary" size="medium" square>
  <Plus size={16} />
</Button>

// Disabled
<Button variant="primary" size="medium" disabled>Salvar</Button>
```
