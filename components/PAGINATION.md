# Pagination — Plann Design System

## Spec

| Prop | Values |
|------|--------|
| total | number of pages |
| current | active page (1-indexed) |
| onChange | function(page) |

- Button: 36×36px, border-radius 4px, border 1px `#dadeea`, font 12px medium
- Gap between buttons: 4px

| State | Background | Border | Text |
|-------|-----------|--------|------|
| default | `#ffffff` | `#dadeea` | `#2d3558` |
| hover | `#e3eafc` | `#8d9aec` | `#2d3558` |
| active | `#e3eafc` | `#8d9aec` | `#2d3558` |
| disabled | `#ffffff` | `#dadeea` | `#9ca2b8` |

---

## Componente React

```jsx
// Pagination.jsx
import styles from './Pagination.module.css';

export function Pagination({ total, current, onChange }) {
  const pages = Array.from({ length: total }, (_, i) => i + 1);

  return (
    <nav className={styles.nav} aria-label="Paginação">
      <button
        className={styles.btn}
        onClick={() => onChange(current - 1)}
        disabled={current === 1}
        aria-label="Página anterior"
      >
        ‹
      </button>

      {pages.map((page) => (
        <button
          key={page}
          className={`${styles.btn} ${page === current ? styles.active : ''}`}
          onClick={() => onChange(page)}
          aria-current={page === current ? 'page' : undefined}
        >
          {page}
        </button>
      ))}

      <button
        className={styles.btn}
        onClick={() => onChange(current + 1)}
        disabled={current === total}
        aria-label="Próxima página"
      >
        ›
      </button>
    </nav>
  );
}
```

```css
/* Pagination.module.css */
.nav {
  display: flex;
  align-items: center;
  gap: 4px;
  font-family: 'Epilogue', sans-serif;
}

.btn {
  width: 36px;
  height: 36px;
  border-radius: 4px;
  border: 1px solid #dadeea;
  background: #ffffff;
  color: #2d3558;
  font-family: 'Epilogue', sans-serif;
  font-size: 12px;
  font-weight: 500;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.15s, border-color 0.15s;
}

.btn:hover:not(:disabled) {
  background: #e3eafc;
  border-color: #8d9aec;
}

.btn:disabled {
  color: #9ca2b8;
  cursor: not-allowed;
}

.active {
  background: #e3eafc;
  border-color: #8d9aec;
}
```

## Uso

```jsx
const [page, setPage] = useState(1);

<Pagination total={10} current={page} onChange={setPage} />

// With data fetching
<Pagination
  total={Math.ceil(totalItems / itemsPerPage)}
  current={currentPage}
  onChange={(p) => { setCurrentPage(p); fetchData(p); }}
/>
```
