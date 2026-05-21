# Espaçamento — Plann Design System

## ⚠️ REGRA OBRIGATÓRIA
- Espaçamentos sempre múltiplos de **4px**
- Prefira usar as variáveis CSS ao invés de valores fixos
- **Nunca** use valores como 5px, 7px, 9px, 11px, 13px, 15px, etc.

---

## Variáveis CSS de espaçamento (já incluídas no `:root` de COLORS.md)

```css
/* Escala base (0–14) */
--space-0:   0;
--space-1:   4px;
--space-2:   8px;
--space-3:   16px;
--space-4:   24px;
--space-5:   32px;
--space-6:   40px;
--space-7:   48px;
--space-8:   56px;
--space-9:   64px;
--space-10:  72px;
--space-11:  80px;

/* Spacing-stack (ritmo vertical) */
--stack-2xs: 4px;
--stack-xs:  8px;
--stack-sm:  16px;
--stack-md:  24px;
--stack-lg:  32px;

/* Spacing-inline (ritmo horizontal) */
--inline-nano: 8px;
--inline-xxxs: 16px;
--inline-xxs:  24px;
--inline-xs:   32px;

/* Border radius */
--radius-xs:    2px;    /* checkbox */
--radius-sm:    4px;    /* botões, inputs */
--radius-md:    8px;    /* cards, modals */
--radius-lg:    12px;   /* dropdowns, popovers */
--radius-pill:  9999px; /* pills, avatars */
--radius-full:  50%;    /* círculos */
```

---

## Tabela de referência rápida

| Valor | Variável | Uso comum |
|---|---|---|
| 4px | `--space-1` / `--stack-2xs` | Gap mínimo, margem interna pequena |
| 8px | `--space-2` / `--stack-xs` | Gap padrão entre ícone e texto, padding interno |
| 12px | *(sem variável — use 12px direto)* | Padding de botões, inputs, células de tabela |
| 16px | `--space-3` / `--stack-sm` | Padding de seções, gap entre itens |
| 24px | `--space-4` / `--stack-md` | Gap entre cards, padding lateral |
| 32px | `--space-5` / `--stack-lg` | Espaçamento entre seções grandes |
| 40px | `--space-6` | Padding de página |
| 48px | `--space-7` | Alturas de topbar, componentes grandes |

---

## Valores de altura de componentes (fixos, não altere)

| Componente | Altura |
|---|---|
| Sidebar | 100vh, 64px largura |
| Topbar | 56px |
| Botão small | 36px |
| Botão medium | 42px |
| Botão large / xlarge | 50px |
| Input small | 36px |
| Input medium | 42px |
| Input large | 50px |
| Toggle small | 20px track |
| Toggle medium | 24px track |
| Toggle large | 32px track |
| Linha de tabela (pedido) | 48px |
| Linha de tabela (item) | 36px |
| Header de tabela | 33px |
