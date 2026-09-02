# Site de Currículo Pessoal — meu-curriculo

**Estudante:** Denilson Uate
**Turma:** 2º Ano — Programação e Design Web, Universidade Licungo (Faculdade de Ciências e Tecnologia)
**Disciplina / Trabalho:** Trabalho Prático I — Site de Currículo Pessoal (HTML5 + CSS3 puro)

## Descrição do projeto

Site pessoal de currículo/portfólio, composto por 5 páginas HTML interligadas por um menu
de navegação comum, estilizado exclusivamente com CSS3 puro (sem frameworks) e sem
JavaScript. Toda a interatividade (menu ativo, transições, formulário) é feita com HTML e CSS.

### Como visualizar

Não é necessário nenhum servidor nem instalação: basta abrir o ficheiro `index.html` num
navegador (duplo clique ou "Abrir com..."). Todos os caminhos de CSS e imagens são relativos.

## Páginas do site

| Página | Ficheiro | Conteúdo |
|---|---|---|
| Home | `index.html` | Apresentação pessoal, avatar, tagline, vídeo local mostrando o código HTML5/CSS3 de uma primeira página, mensagem de boas-vindas em voz, chamada para ação para a página de contacto |
| Currículo | `about.html` | Formação académica, experiência, lista de competências e tabela de proficiência técnica, certificados |
| Portfólio | `portfolio.html` | Grelha (CSS Grid) de projetos com imagem, título e descrição; curta-metragem de animação (licença aberta) incorporado via YouTube |
| Hobbies | `hobbies.html` | Cartões de hobbies organizados com Flexbox |
| Contacto | `contact.html` | Formulário completo com validação nativa HTML5 |

## Estrutura de pastas

```
meu-curriculo/
├── index.html
├── about.html
├── portfolio.html
├── hobbies.html
├── contact.html
├── css/
│   ├── estilo.css       (estilos partilhados: header, footer, tipografia, variáveis)
│   └── responsivo.css   (media queries, mobile-first)
├── assets/
│   ├── img/              (avatar, projetos, certificados, hobbies, poster do vídeo)
│   ├── video/             (vídeo local: demonstração de código HTML5/CSS3)
│   ├── audio/             (mensagem de boas-vindas em voz, mp3 + wav)
│   └── ficheiros/         (CV em PDF de exemplo)
└── README.md
```

> **Nota:** as imagens e o CV incluídos são conteúdo de exemplo gerado para cumprir os
> requisitos técnicos do trabalho. O áudio de boas-vindas usa voz sintetizada (não é uma
> gravação humana real) — se preferir, grave a sua própria voz antes da entrega final.
> Substitua também as imagens e o CV pelos seus próprios ficheiros.

## Principais tags HTML e recursos CSS/HTML utilizados

### HTML semântico
- **`<header>` / `<nav>` / `<main>` / `<section>` / `<article>` / `<aside>` / `<footer>`** — estruturam cada página em regiões com significado próprio, em vez de `<div>` genéricas ("div soup"), o que também melhora a acessibilidade (landmarks).
- **`<figure>` / `<figcaption>`** — usados nos certificados (`about.html`) para associar uma legenda semântica à imagem.
- **`<video controls poster>` e `<source type="video/mp4">`** — vídeo nativo na Home, mostrando a escrita do código HTML5/CSS3 de uma primeira página até ao resultado no navegador, com imagem de pré-visualização antes de carregar.
- **`<iframe>`** — vídeo em português sobre HTML5 e CSS3 (Curso em Vídeo) incorporado via YouTube na página de Portfólio, a título de exemplo desta técnica.
- **`<audio controls>` e `<source type="audio/mpeg">`** — mensagem de boas-vindas em voz (áudio local, com `<source>` em mp3 e wav) na Home.
- **`<table>` com `<thead>`/`<tbody>`, `rowspan`/`colspan`** — tabela de proficiência técnica em `about.html`, agrupando tecnologias por área.
- **`<fieldset>` / `<legend>`** — agrupam secções relacionadas do formulário de contacto (dados pessoais, detalhes do pedido, mensagem).

### Validação de formulário (HTML5 nativo, sem JavaScript)
- `required`, `minlength`, `maxlength` — no campo de nome e na mensagem.
- `type="email"` — validação automática de formato de email pelo navegador.
- `type="tel"` com `pattern="8[2-7][0-9]{7}"` — valida números moçambicanos de 9 dígitos.
- `type="date"` com `min` — impede escolher datas anteriores ao início do prazo.
- `type="number"` com `min`/`max`/`step` — limita o orçamento a um intervalo razoável.
- `type="file"` com `accept=".pdf,application/pdf"` — restringe o anexo a ficheiros PDF.

### CSS — seletores e pseudo-classes/elementos
- **Seletores avançados**: descendente (`.card-body h3`), filho direto (`nav.main-nav li > a` via `.quick-skills > li`), irmão adjacente (`nav.main-nav li + li`), atributo (`input[type="email"]`, `.card a[href^="http"]`).
- **`:hover`, `:focus` / `:focus-visible`** — estados interativos em links, cartões e campos de formulário.
- **`:first-child`, `:last-child`, `:nth-child()`** — destaque no primeiro item da timeline académica e zebra striping na tabela de competências.
- **`::before` / `::after`** — marcador `>` antes do link de navegação ativo e sublinhado animado ao passar o rato.
- **`:target` e classe `.active`** — a página atual é destacada no menu através da classe `active`, aplicada manualmente em cada ficheiro HTML.

### CSS — layout
- **Flexbox** (`hobbies.html`): `flex-direction: row`, `flex-wrap: wrap`, `justify-content: center`, `align-items: stretch` organizam os cartões de hobbies.
- **CSS Grid** (`portfolio.html`): `grid-template-columns: repeat(auto-fit, minmax(260px, 1fr))` cria uma grelha de projetos responsiva sem media queries adicionais.
- **`position: sticky`** no `header.site-header`, mantendo o menu visível durante o scroll. A diferença entre `static`, `relative`, `absolute`, `fixed` e `sticky` está explicada em comentário no final de `estilo.css`.

### CSS — responsividade
- Meta viewport (`width=device-width, initial-scale=1.0`) em todas as páginas.
- Abordagem **mobile-first**: `estilo.css` define a base para ecrãs pequenos; `responsivo.css` amplia o layout com `@media (min-width: 481px)` (tablet) e `@media (min-width: 769px)` (desktop).
- Unidades relativas (`rem`, `%`, `vw`, `ch`, `1fr`) combinadas com unidades fixas (`px` em bordas e sombras) conforme o contexto.

### CSS — estilo visual avançado
- **Variáveis CSS (`:root`)** para cores, espaçamentos, tipografia e sombras, reaproveitadas em todo o site.
- **`transition`** nos cartões, botões e campos de formulário; **`@keyframes fade-rise`** para uma entrada suave dos blocos de conteúdo.
- **`linear-gradient`** nos botões primários; **`box-shadow`** nos cartões e **`text-shadow`** pontual na tipografia de destaque.
- **Tipografia**: `Fraunces` (títulos, serifada com carácter) + `Inter` (texto corrido) + `JetBrains Mono` (rótulos, navegação, dados técnicos), com pilha de alternativas de sistema em cada `font-family`.

## Acessibilidade
- Todas as imagens têm `alt` descritivo (nunca vazio ou genérico).
- Todos os campos do formulário têm `<label for="...">` associado ao respetivo `id`.
- Landmarks semânticos (`header`, `nav`, `main`, `footer`) e `aria-label` no menu de navegação.
- Foco de teclado sempre visível (`:focus-visible` com contorno em destaque).
- Contraste alto entre texto (creme) e fundo (azul-marinho escuro).

## Organização do repositório
O histórico de commits reflete a evolução do trabalho por etapas (estrutura de pastas,
estilos partilhados, cada página, formulário, responsividade, revisão final) — não é
um único commit final.
