# 📮 Busca CEP — Correios Brasil

<div align="center">

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![API](https://img.shields.io/badge/ViaCEP-API-00C853?style=for-the-badge&logo=json&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

**Aplicação web para consulta de endereços por CEP com verificação CAPTCHA visual.**  
Interface moderna, responsiva e 100% client-side — sem backend necessário.

[🔍 Ver Demo](#-demonstração) · [🚀 Como Usar](#-como-usar) · [📡 API](#-api-utilizada) · [🤝 Contribuir](#-contribuindo)

</div>

---

## 📋 Sumário

- [Sobre o Projeto](#-sobre-o-projeto)
- [Demonstração](#-demonstração)
- [Funcionalidades](#-funcionalidades)
- [Tecnologias](#-tecnologias)
- [Pré-requisitos](#-pré-requisitos)
- [Instalação](#-instalação)
- [Como Usar](#-como-usar)
- [API Utilizada](#-api-utilizada)
- [Estrutura do Projeto](#-estrutura-do-projeto)
- [Detalhes Técnicos](#-detalhes-técnicos)
- [Captcha Visual](#-captcha-visual)
- [Personalização](#-personalização)
- [Perguntas Frequentes](#-perguntas-frequentes)
- [Contribuindo](#-contribuindo)
- [Licença](#-licença)

---

## 🧭 Sobre o Projeto

O **Busca CEP** é uma aplicação web de página única (SPA) desenvolvida com **HTML5, CSS3 e JavaScript puro** para consulta de endereços brasileiros a partir do Código de Endereçamento Postal (CEP).

A aplicação foi projetada para ser:

- **Zero-dependência** — sem frameworks, sem npm, sem build tools
- **Client-side only** — roda diretamente no navegador
- **Segura** — possui verificação CAPTCHA antes de cada consulta
- **Acessível** — responsiva e compatível com os principais navegadores
- **Visual** — interface com estética dark/editorial de alto impacto

> **Referência oficial:** Os dados retornados são os mesmos disponíveis em [buscacepinter.correios.com.br](https://buscacepinter.correios.com.br/app/endereco/index.php), consultados via API pública ViaCEP como intermediária (os Correios não permitem CORS em chamadas diretas).

---

## 🖥️ Demonstração

```
┌──────────────────────────────────┐
│  ● Correios Brasil               │
│                                  │
│  Busca                           │
│  CEP                             │
│                                  │
│  Consulte endereços por código   │
│  postal. Via API pública.        │
│                                  │
│  [ Código CEP          ]         │
│  [ 01310-100           ]         │
│                                  │
│  [ CAPTCHA VISUAL  ] [↺]        │
│  [ Digite o código     ]         │
│                                  │
│  [ PESQUISAR ENDEREÇO  ]         │
│                                  │
│  ✓ Endereço encontrado           │
│  CEP        01310-100            │
│  Logradouro Av. Paulista         │
│  Bairro     Bela Vista           │
│  Cidade     São Paulo            │
│  Estado     SP                   │
└──────────────────────────────────┘
```

---

## ✨ Funcionalidades

| Funcionalidade | Descrição |
|---|---|
| 🔢 **Máscara de CEP** | Formatação automática `00000-000` ao digitar |
| 🛡️ **CAPTCHA Canvas** | Código visual gerado dinamicamente com ruído |
| 🔄 **Refresh de CAPTCHA** | Botão para gerar novo código de verificação |
| ⌨️ **Atalho por teclado** | Pressionar `Enter` dispara a pesquisa |
| ⏳ **Estado de carregamento** | Spinner animado durante a requisição |
| ✅ **Resultado detalhado** | CEP, logradouro, bairro, cidade, UF, IBGE, DDD |
| ❌ **Tratamento de erros** | Mensagens claras para CEP inválido, CAPTCHA errado e falha de rede |
| 📱 **Responsivo** | Funciona em desktop, tablet e mobile |

---

## 🛠️ Tecnologias

- **HTML5** — Estrutura semântica e Canvas API para o CAPTCHA
- **CSS3** — Custom Properties, Grid, animações e pseudo-elementos
- **JavaScript (ES6+)** — Fetch API, async/await, manipulação de DOM
- **[ViaCEP API](https://viacep.com.br/)** — Serviço gratuito de consulta de CEPs brasileiros
- **[Google Fonts](https://fonts.google.com/)** — Fontes Syne e DM Mono

---

## ✅ Pré-requisitos

Nenhuma dependência externa necessária. Apenas:

- Um **navegador moderno** com suporte a ES6+ (Chrome 60+, Firefox 55+, Safari 11+, Edge 79+)
- **Conexão com a internet** para consultar a API ViaCEP

---

## 📦 Instalação

### Opção 1 — Abrir diretamente

Basta baixar o arquivo e abrir no navegador:

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/busca-cep.git

# Entre na pasta
cd busca-cep

# Abra o arquivo no navegador
open busca-cep.html       # macOS
start busca-cep.html      # Windows
xdg-open busca-cep.html   # Linux
```

### Opção 2 — Servir localmente (recomendado)

Para evitar restrições de CORS em alguns navegadores, use um servidor local:

```bash
# Python 3
python -m http.server 8080

# Node.js (npx)
npx serve .

# PHP
php -S localhost:8080
```

Acesse: `http://localhost:8080/busca-cep.html`

### Opção 3 — Deploy estático

Faça o deploy gratuito em serviços como:

- **GitHub Pages** — `Settings > Pages > Deploy from branch`
- **Netlify** — arraste e solte a pasta no [app.netlify.com](https://app.netlify.com)
- **Vercel** — `vercel deploy`

---

## 🚀 Como Usar

1. **Digite o CEP** no campo de código postal (apenas números ou com hífen)
2. **Leia o CAPTCHA** visual exibido na tela
3. **Digite o código** exatamente como mostrado (letras maiúsculas, sem espaços)
4. Clique em **"Pesquisar Endereço"** ou pressione `Enter`
5. O **endereço completo** será exibido abaixo do formulário

> 💡 Se o CAPTCHA estiver difícil de ler, clique no botão **↺** para gerar um novo código.

---

## 📡 API Utilizada

### ViaCEP

A aplicação consome a **[API pública ViaCEP](https://viacep.com.br/)**, um serviço gratuito, sem autenticação e com suporte a CORS.

**Endpoint:**

```
GET https://viacep.com.br/ws/{cep}/json/
```

**Exemplo de Resposta:**

```json
{
  "cep": "01310-100",
  "logradouro": "Avenida Paulista",
  "complemento": "de 1 a 610 - lado par",
  "bairro": "Bela Vista",
  "localidade": "São Paulo",
  "uf": "SP",
  "ibge": "3550308",
  "gia": "1004",
  "ddd": "11",
  "siafi": "7107"
}
```

**Resposta para CEP inexistente:**

```json
{
  "erro": true
}
```

> ⚠️ **Por que não os Correios diretamente?**  
> O endpoint oficial dos Correios (`buscacepinter.correios.com.br`) não possui cabeçalhos CORS habilitados, impossibilitando chamadas diretas de aplicações client-side. O ViaCEP é um espelho confiável e gratuito que republica os mesmos dados.

---

## 📁 Estrutura do Projeto

```
busca-cep/
│
├── busca-cep.html          # Arquivo principal (contém HTML, CSS e JS)
├── README.md               # Documentação do projeto
└── LICENSE                 # Licença MIT
```

> O projeto é intencionalmente **single-file** para máxima portabilidade. Toda a lógica, estilos e marcação estão no `busca-cep.html`.

---

## 🔍 Detalhes Técnicos

### Formatação de CEP

```javascript
function formatCEP(value) {
  return value
    .replace(/\D/g, '')           // Remove não-dígitos
    .replace(/^(\d{5})(\d)/, '$1-$2') // Insere hífen após 5 dígitos
    .slice(0, 9);                 // Limita a 9 caracteres (00000-000)
}
```

### Consulta à API

```javascript
async function searchCEP() {
  const cepRaw = document.getElementById('cepInput').value.replace(/\D/g, '');
  const res = await fetch(`https://viacep.com.br/ws/${cepRaw}/json/`);
  const data = await res.json();

  if (data.erro) {
    // CEP não encontrado
    return;
  }
  // Exibe resultado...
}
```

### Validações realizadas

| Validação | Condição | Mensagem de Erro |
|---|---|---|
| CEP vazio ou incompleto | `cepRaw.length !== 8` | CEP inválido. Informe os 8 dígitos |
| CAPTCHA em branco | `!captchaInput` | Preencha o código de verificação |
| CAPTCHA incorreto | `captchaInput !== captchaCode` | Código de verificação incorreto |
| CEP não encontrado | `data.erro === true` | CEP não encontrado |
| Falha de rede | `catch` na Fetch API | Erro de conexão |

---

## 🛡️ Captcha Visual

O CAPTCHA é gerado dinamicamente via **HTML5 Canvas API**, sem dependências externas.

### Características

- **6 caracteres** alfanuméricos aleatórios (sem caracteres ambíguos como `0/O`, `1/I/l`)
- **Rotação individual** de cada caractere (±0.4 rad)
- **Cores distintas** por posição para dificultar OCR automatizado
- **5 linhas de ruído** com opacidade reduzida
- **30 pontos de ruído** distribuídos aleatoriamente
- **Fonte monoespaçada** com tamanho variável por caractere
- **Novo código gerado** automaticamente após cada tentativa (correta ou não)

### Caracteres disponíveis

```
ABCDEFGHJKLMNPQRSTUVWXYZ23456789
```
> Caracteres ambíguos (`I`, `O`, `0`, `1`) foram intencionalmente removidos.

---

## 🎨 Personalização

### Alterar cores (CSS Variables)

```css
:root {
  --bg: #0e0f11;        /* Cor de fundo principal */
  --surface: #16181c;   /* Cor de fundo do card */
  --border: #2a2d33;    /* Cor das bordas */
  --accent: #f5c518;    /* Cor de destaque (amarelo) */
  --accent2: #e8733a;   /* Cor de destaque secundária (laranja) */
  --text: #f0eff0;      /* Cor do texto */
  --muted: #7a7d85;     /* Cor do texto secundário */
  --success: #3ecf8e;   /* Cor de sucesso (verde) */
  --error: #f87171;     /* Cor de erro (vermelho) */
}
```

### Alterar fonte

Substitua no `<head>`:

```html
<link href="https://fonts.googleapis.com/css2?family=SUA+FONTE&display=swap" rel="stylesheet"/>
```

E nas variáveis CSS:

```css
body { font-family: 'Sua Fonte', monospace; }
h1   { font-family: 'Sua Fonte Display', sans-serif; }
```

### Alterar comprimento do CAPTCHA

```javascript
// Linha do gerador de CAPTCHA — altere o 6 para outro valor
captchaCode = Array.from({length: 6}, () => chars[...]).join('');
```

---

## ❓ Perguntas Frequentes

**O projeto funciona offline?**  
Não. A consulta de CEP requer conexão com a internet para acessar a API ViaCEP.

**Preciso de servidor web?**  
Não obrigatoriamente. O arquivo pode ser aberto diretamente no navegador. Porém, para evitar restrições em alguns ambientes, recomenda-se um servidor local simples.

**Os dados são oficiais dos Correios?**  
Sim. O ViaCEP consome e republica os dados oficiais dos Correios com atualização periódica.

**O CAPTCHA é acessível?**  
O CAPTCHA atual é visual. Para projetos que exijam acessibilidade total (WCAG 2.1 AAA), recomenda-se adicionar uma alternativa de áudio ou utilizar serviços como reCAPTCHA v3.

**Posso usar em produção?**  
Sim, desde que respeite os [termos de uso do ViaCEP](https://viacep.com.br/) (uso gratuito, não-comercial em larga escala requer contato).

**Quantas requisições posso fazer?**  
O ViaCEP não divulga um rate limit exato, mas é recomendado evitar requisições automatizadas em massa.

---

## 🤝 Contribuindo

Contribuições são muito bem-vindas! Siga os passos abaixo:

1. **Fork** o repositório
2. Crie uma **branch** para sua feature:
   ```bash
   git checkout -b feature/minha-melhoria
   ```
3. **Commit** suas alterações:
   ```bash
   git commit -m "feat: adiciona suporte a busca por logradouro"
   ```
4. **Push** para a branch:
   ```bash
   git push origin feature/minha-melhoria
   ```
5. Abra um **Pull Request**

### Convenção de commits

Utilizamos o padrão [Conventional Commits](https://www.conventionalcommits.org/):

| Prefixo | Uso |
|---|---|
| `feat:` | Nova funcionalidade |
| `fix:` | Correção de bug |
| `docs:` | Atualização de documentação |
| `style:` | Formatação, sem mudança de lógica |
| `refactor:` | Refatoração de código |
| `chore:` | Tarefas de manutenção |

---

## 📊 Compatibilidade de Navegadores

| Navegador | Versão mínima | Status |
|---|---|---|
| Chrome | 60+ | ✅ Suportado |
| Firefox | 55+ | ✅ Suportado |
| Safari | 11+ | ✅ Suportado |
| Edge | 79+ | ✅ Suportado |
| Opera | 47+ | ✅ Suportado |
| IE 11 | — | ❌ Não suportado |

---

## 📄 Licença

Distribuído sob a licença **MIT**. Veja o arquivo [`LICENSE`](LICENSE) para mais informações.

```
MIT License

Copyright (c) 2026

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.
```

---

## 🙏 Agradecimentos

- [ViaCEP](https://viacep.com.br/) — pela API pública e gratuita de consulta de CEPs
- [Correios Brasil](https://www.correios.com.br/) — pela base de dados oficial de endereços
- [Google Fonts](https://fonts.google.com/) — pelas fontes Syne e DM Mono

---

<div align="center">

Feito com ☕ e 💛 no Brasil

**[⬆ Voltar ao topo](#-busca-cep--correios-brasil)**

</div>
