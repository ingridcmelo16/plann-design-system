# Cores — Plann Design System

## ⚠️ REGRA OBRIGATÓRIA
- **NUNCA** use hex direto (ex: `#2d3558`, `#fff`)
- **SEMPRE** use as variáveis `var(--nome-token)`
- **NUNCA** adicione cores fora desta lista

---

## Bloco `:root` — COLE ESTE BLOCO COMPLETO EM TODA PÁGINA

```css
@import url('https://fonts.googleapis.com/css2?family=Epilogue:wght@400;500;600;700&display=swap');

:root {
  /* ── Primitivas ─────────────────────────────────────────────── */
  --blue-lighter:    #e3eaf6;
  --blue-light:      #495583;
  --blue-default:    #2d3558;
  --blue-dark:       #1f2747;

  --purple-dark:     #8d9aec;
  --purple-default:  #bcc8f5;
  --purple-light:    #e3eafc;
  --purple-lighter:  #f1f5ff;

  --grey-lighter:    #f4f5f9;
  --grey-light:      #dadeea;
  --grey-default:    #9ca2b8;
  --grey-dark:       #8f93a3;
  --grey-cool-2:     #ced1e1;

  --green-lighter:   #ebfcf0;
  --green-light:     #b4e6c4;
  --green-default:   #47b274;
  --green-dark:      #17653e;

  --red-lighter:     #fff0f0;
  --red-light:       #ebb6b6;
  --red-default:     #cb5158;
  --red-dark:        #832e3b;

  --yellow-lighter:  #fef8ee;
  --yellow-light:    #ffdcae;
  --yellow-default:  #f8b967;
  --yellow-dark:     #f7941e;

  --white:           #ffffff;
  --black:           #000000;

  /* ── Semânticas / aliases ───────────────────────────────────── */
  --primary:           var(--blue-default);
  --primary-light:     var(--blue-light);
  --primary-lighter:   var(--blue-lighter);
  --primary-dark:      var(--blue-dark);

  --secondary:         var(--purple-default);
  --secondary-dark:    var(--purple-dark);
  --secondary-light:   var(--purple-light);
  --secondary-lighter: var(--purple-lighter);

  --neutral:           var(--grey-default);
  --neutral-light:     var(--grey-light);
  --neutral-lighter:   var(--grey-lighter);
  --neutral-dark:      var(--grey-dark);

  --success:           var(--green-default);
  --success-light:     var(--green-light);
  --success-lighter:   var(--green-lighter);
  --success-dark:      var(--green-dark);

  --danger:            var(--red-default);
  --danger-light:      var(--red-light);
  --danger-lighter:    var(--red-lighter);
  --danger-dark:       var(--red-dark);

  --warning:           var(--yellow-default);
  --warning-light:     var(--yellow-light);
  --warning-lighter:   var(--yellow-lighter);
  --warning-dark:      var(--yellow-dark);

  --info:              var(--primary);
  --info-light:        var(--primary-light);
  --info-lighter:      var(--primary-lighter);

  /* ── Cores de superfície e texto ────────────────────────────── */
  --bg-page:               var(--neutral-lighter);
  --surface-primary:       var(--primary);
  --surface-highlight:     var(--white);

  --border-primary:    var(--neutral-light);
  --border-success:    var(--success);
  --border-warning:    var(--warning);
  --border-danger:     var(--danger);
  --border-info:       var(--primary);

  --text-heading:      var(--primary);
  --text-body:         var(--primary);
  --text-muted:        #626f86;
  --text-button:       var(--white);
  --text-disabled:     var(--neutral);

  --button-primary-default:   var(--primary);
  --button-primary-hover:     var(--primary-light);
  --button-primary-danger:    var(--danger);

  /* ── Sombras ────────────────────────────────────────────────── */
  --elev-1: 0 2px 4px rgba(0,0,0,0.25);
  --elev-2: 0 2px 8px rgba(0,0,0,0.25);
  --elev-3: 0 2px 12px rgba(0,0,0,0.25);
  --shadow-card:    0 1px 2px rgba(31,39,71,0.06), 0 1px 3px rgba(31,39,71,0.05);
  --shadow-popover: 0 4px 12px rgba(31,39,71,0.12);

  /* ── Animação ───────────────────────────────────────────────── */
  --ease-standard: cubic-bezier(.2,.6,.2,1);
  --ease-out:      cubic-bezier(.16,1,.3,1);
  --dur-fast:      120ms;
  --dur-base:      200ms;
  --dur-slow:      320ms;
}
```

---

## Tabela de referência rápida

| Token semântico | Valor hex | Uso |
|---|---|---|
| `--primary` | #2d3558 | Cor principal, textos, botões, header tabela, sidebar |
| `--primary-light` | #495583 | Hover de botões primary |
| `--primary-lighter` | #e3eaf6 | Backgrounds de info, row selecionada |
| `--secondary` | #bcc8f5 | Cor secundária, botões secundários |
| `--secondary-dark` | #8d9aec | Toggle on, checkbox checked |
| `--neutral` | #9ca2b8 | Texto desabilitado, bordas neutras |
| `--neutral-light` | #dadeea | Bordas padrão, divisores |
| `--neutral-lighter` | #f4f5f9 | Background da página |
| `--success` | #47b274 | Estados positivos |
| `--success-lighter` | #ebfcf0 | Background success |
| `--success-dark` | #17653e | Texto success |
| `--danger` | #cb5158 | Erros, destructive |
| `--danger-lighter` | #fff0f0 | Background danger |
| `--danger-dark` | #832e3b | Texto danger |
| `--warning` | #f8b967 | Alertas, avisos |
| `--warning-lighter` | #fef8ee | Background warning |
| `--warning-dark` | #f7941e | Texto warning |
| `--white` | #ffffff | Superfícies, textos em fundo escuro |
| `--bg-page` | (neutral-lighter) | Background da página |
| `--text-heading` | (primary) | Títulos e textos principais |
| `--text-muted` | #626f86 | Textos secundários/subtítulos |
