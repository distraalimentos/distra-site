# Distra Alimentos — Design System

Sistema de design compartilhado entre os projetos digitais da Distra.

## Arquivos

| Arquivo | Função |
|---------|--------|
| `tokens.css` | Variáveis CSS (cores, tipografia, espaçamento, sombras). Base de tudo. |
| `components.css` | Componentes prontos (botões, cards, badges, inputs). Requer `tokens.css`. |
| `tokens.json` | Tokens para importar no Figma via plugin Tokens Studio. |
| `index.html` | Documentação visual navegável. Abra no navegador. |

## Como aplicar em uma página nova

```html
<head>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Barlow+Condensed:wght@500;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="/design-system/tokens.css">
  <link rel="stylesheet" href="/design-system/components.css">
</head>
```

## Importar no Figma

1. Instale o plugin **Tokens Studio for Figma**
2. Settings → Import → carregue `tokens.json`
3. As cores, tipografia e espaçamentos aparecem como estilos prontos

---

## Arquitetura recomendada dos projetos

A Distra tem dois tipos de projeto digital, com necessidades técnicas diferentes:

### 1. `distra-site` — Institucional (público)
- **O que é:** site institucional + landing pages de campanhas/marcas
- **Tecnologia:** HTML/CSS estático (atual)
- **Características:** público, indexável pelo Google, sem login, leve
- **Estrutura sugerida:**
  ```
  distra-site/
  ├── index.html                  (institucional)
  ├── design-system/              (este pacote)
  ├── campanhas/
  │   ├── schar/index.html
  │   └── vitalin/index.html
  └── assets/
  ```

### 2. `distra-portal` — Aplicação (privado)
- **O que é:** portal de vendedores (histórico de pedidos), área do cliente (rastreio)
- **Tecnologia:** Next.js ou similar (precisa de backend, autenticação, integração ERP/Bling)
- **Características:** login obrigatório, acesso a dados de clientes, proteção LGPD
- **Por que separado:** misturar uma aplicação com dados sensíveis no mesmo repositório do site público é risco de segurança e manutenção

**O design system é compartilhado entre os dois** — mesmos tokens, mesma identidade visual.

---

## Regra de ouro

Nunca use valores hex ou tamanhos soltos no CSS. Sempre referencie um token.
Precisa de um valor novo? Adicione primeiro ao `tokens.css`.
