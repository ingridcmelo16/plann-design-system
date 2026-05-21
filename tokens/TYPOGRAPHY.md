# Tipografia — Plann Design System

## ⚠️ REGRA OBRIGATÓRIA
- **Epilogue** é a ÚNICA fonte do produto. Nunca use Inter, Roboto, Arial ou qualquer outra.
- Sempre faça o import via Google Fonts no `<head>`.

---

## Import obrigatório no `<head>`

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Epilogue:wght@400;500;600;700&display=swap" rel="stylesheet">
```

---

## Variáveis CSS de tipografia (já incluídas no `:root` de COLORS.md)

```css
--font-sans:  'Epilogue', system-ui, -apple-system, sans-serif;
--font-mono:  ui-monospace, 'SF Mono', 'JetBrains Mono', Menlo, monospace;

--fw-regular:  400;
--fw-medium:   500;
--fw-semibold: 600;
--fw-bold:     700;

--lh-tight:  1.2;
--lh-normal: 1.5;

--fs-12: 12px;
--fs-14: 14px;
--fs-16: 16px;
--fs-18: 18px;
--fs-22: 22px;
--fs-25: 25px;
--fs-28: 28px;
--fs-32: 32px;
```

---

## Classes de tipografia semântica

```css
/* Cole estas classes no <style> de qualquer página */

.heading-xl {
  font-family: var(--font-sans);
  font-weight: var(--fw-semibold);   /* 600 */
  font-size: var(--fs-32);           /* 32px */
  line-height: var(--lh-tight);      /* 1.2 */
  color: var(--text-heading);
}

.heading-lg {
  font-family: var(--font-sans);
  font-weight: var(--fw-medium);     /* 500 */
  font-size: var(--fs-28);           /* 28px */
  line-height: var(--lh-tight);
  color: var(--text-heading);
}

.heading-md {
  font-family: var(--font-sans);
  font-weight: var(--fw-medium);     /* 500 */
  font-size: var(--fs-25);           /* 25px */
  line-height: var(--lh-tight);
  color: var(--text-heading);
}

.heading-sm {
  font-family: var(--font-sans);
  font-weight: var(--fw-medium);     /* 500 */
  font-size: var(--fs-22);           /* 22px */
  line-height: var(--lh-tight);
  color: var(--text-heading);
}

.heading-xs {
  font-family: var(--font-sans);
  font-weight: var(--fw-medium);     /* 500 */
  font-size: var(--fs-18);           /* 18px */
  line-height: var(--lh-tight);
  color: var(--text-heading);
}

.body-lg {
  font-family: var(--font-sans);
  font-weight: var(--fw-semibold);   /* 600 */
  font-size: var(--fs-16);           /* 16px */
  line-height: var(--lh-normal);     /* 1.5 */
  color: var(--text-body);
}

.body-md {
  font-family: var(--font-sans);
  font-weight: var(--fw-regular);    /* 400 */
  font-size: var(--fs-14);           /* 14px */
  line-height: var(--lh-normal);
  color: var(--text-body);
}

.body-sm {
  font-family: var(--font-sans);
  font-weight: var(--fw-regular);    /* 400 */
  font-size: var(--fs-12);           /* 12px */
  line-height: var(--lh-normal);
  color: var(--text-body);
}
```

---

## Tabela de referência rápida

| Token | Tamanho | Peso | Line-height | Uso |
|---|---|---|---|---|
| `heading-xl` | 32px | 600 | 1.2 | Título principal da página |
| `heading-lg` | 28px | 500 | 1.2 | Seção importante |
| `heading-md` | 25px | 500 | 1.2 | Subtítulo |
| `heading-sm` | 22px | 500 | 1.2 | Card title |
| `heading-xs` | 18px | 500 | 1.2 | Label de seção |
| `body-lg` | 16px | 600 | 1.5 | Texto em destaque |
| `body-md` | 14px | 400 | 1.5 | Texto padrão de UI |
| `body-sm` | 12px | 400 | 1.5 | Labels, legendas, meta |
