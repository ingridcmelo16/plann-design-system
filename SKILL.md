---
name: plann-design-system
description: Plann Design System completo com estruturas HTML EXATAS para Sidebar, Topbar, Filtros e Tabelas. Use esta skill SEMPRE que criar interfaces, componentes ou HTML para Plann. Trigger obrigatório quando mencionar Plann, design system, criar interface, componentes, sidebar, topbar, filtros, tabela ou qualquer trabalho de frontend. NUNCA invente estruturas - SEMPRE copie as documentadas aqui.
---

# Plann Design System — Skill Principal

## ⚠️ REGRAS OBRIGATÓRIAS — LEIA ANTES DE QUALQUER COISA

1. **NUNCA INVENTE** — Copie EXATAMENTE as estruturas documentadas nesta skill
2. **NUNCA USE CORES FORA DA LISTA** — Apenas variáveis CSS documentadas em `tokens/COLORS.md`
3. **NUNCA IMPROVISE CLASSES CSS** — Use as classes exatas dos exemplos
4. **SEMPRE USE EPILOGUE** — É a ÚNICA fonte tipográfica permitida (`font-family: 'Epilogue', sans-serif`)
5. **SEMPRE USE ESPAÇAMENTOS MÚLTIPLOS DE 4PX** — Base 8px, nunca valores aleatórios
6. **NUNCA CRIE COMPONENTES CUSTOM** — Use os componentes documentados aqui
7. **NUNCA USE TAILWIND, REACT, JSX** — HTML e CSS puro apenas
8. **SEMPRE INCLUA OS TOKENS CSS** — O bloco `:root { }` deve estar em toda página

---

## 📦 QUANDO USAR ESTA SKILL

- Qualquer pedido de interface, tela, componente ou HTML para Plann/Plannera
- Quando mencionar: sidebar, topbar, filtros, tabela, dashboard, painel
- Quando pedir: criar tela, construir interface, montar layout, adicionar componente
- Qualquer trabalho de frontend no produto Plann

---

## 📁 ÍNDICE — O QUE ESTÁ DISPONÍVEL

### Estruturas de Layout (copie sempre literalmente)
| Arquivo | O que contém |
|---|---|
| `structures/SIDEBAR.md` | Sidebar 64px navy com ícones FontAwesome + tooltips |
| `structures/TOPBAR.md` | Topbar 56px com breadcrumb, spacer e user pill |
| `structures/FILTER_PANEL.md` | Painel de filtros com toggle, dropdowns e chips |
| `structures/TABLE.md` | Tabela hierárquica com header navy, checkboxes, expand |

### Componentes (use os exatos, não adapte)
| Arquivo | O que contém |
|---|---|
| `components/BUTTON.md` | Botões: primary, secondary, tertiary, destructive |
| `components/BADGE.md` | Badges coloridas: success, danger, warning, info, neutral |
| `components/TEXT_INPUT.md` | Input de texto com label, erro, disabled |
| `components/PAGINATION.md` | Paginação numérica |
| `components/RADIO_BUTTON.md` | Radio button |
| `components/TOGGLE.md` | Toggle switch |
| `components/TOOLTIP.md` | Tooltip top/bottom/left/right |
| `components/ALERT_NOTIFICATION.md` | Alertas coloridos com ícone e fechar |

### Tokens
| Arquivo | O que contém |
|---|---|
| `tokens/COLORS.md` | Todas as variáveis CSS de cor — copie o bloco `:root` inteiro |
| `tokens/TYPOGRAPHY.md` | Classes de tipografia e variáveis de fonte |
| `tokens/SPACING.md` | Escala de espaçamento e variáveis |

### Exemplo completo
| Arquivo | O que contém |
|---|---|
| `examples/FULL_PAGE.md` | HTML completo funcional com sidebar + topbar + filtros + tabela |

---

## 🔄 WORKFLOW — COMO USAR

1. **Leia** `tokens/COLORS.md` → cole o bloco `:root` completo no `<style>`
2. **Leia** `tokens/TYPOGRAPHY.md` → cole as classes de tipografia
3. **Leia** `tokens/SPACING.md` → cole as variáveis de espaçamento
4. **Leia** `structures/SIDEBAR.md` → copie HTML e CSS exatos
5. **Leia** `structures/TOPBAR.md` → copie HTML e CSS exatos
6. **Leia** `structures/FILTER_PANEL.md` se tiver filtros → copie HTML e CSS
7. **Leia** `structures/TABLE.md` se tiver tabela → copie HTML e CSS
8. **Leia** os componentes necessários de `components/` → copie exatamente
9. **Adapte apenas** os textos, labels, ícones e dados — nunca a estrutura

---

## 🚫 O QUE NUNCA FAZER

```
❌ Inventar variáveis CSS que não existem
❌ Usar font-family diferente de Epilogue
❌ Usar cores hex fora da lista (ex: #333, #f0f0f0, #4caf50)
❌ Criar classes CSS custom sem usar as do DS
❌ Usar Tailwind, Bootstrap, ou qualquer framework externo
❌ Criar sidebar com largura diferente de 64px
❌ Criar topbar com altura diferente de 56px
❌ Inventar variantes de botão não documentadas
```

---

## ✅ CHECKLIST ANTES DE ENTREGAR

- [ ] Import Epilogue do Google Fonts no `<head>`
- [ ] Bloco `:root` com todos os tokens CSS presente
- [ ] Sidebar com `.sidebar` e `.sidebar-icon` corretos
- [ ] Topbar com `.topbar` correto (sem search bar!)
- [ ] Todas as cores usando `var(--nome-token)`
- [ ] Espaçamentos múltiplos de 4px
- [ ] Nenhuma cor hex inventada
- [ ] Nenhum componente custom inventado
