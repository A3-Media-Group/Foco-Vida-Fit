# Foco Vida Fit — Site

Site completo do blog Foco Vida Fit (fitness, nutrição e saúde), pronto para subir no GitHub.

## Como subir para o GitHub

1. Baixe e descompacte esta pasta.
2. No terminal, dentro da pasta:
   ```
   git init
   git add .
   git commit -m "Site inicial Foco Vida Fit"
   git branch -M main
   git remote add origin https://github.com/SEU-USUARIO/SEU-REPO.git
   git push -u origin main
   ```
3. Se o repositório já existir no GitHub (ex: A3-Media-Group/Foco-Vida-Fit), troque a URL do `remote add` pela dele.

## Como publicar (GitHub Pages)

1. No repositório, vá em **Settings → Pages**.
2. Em "Branch", selecione `main` e pasta `/ (root)`.
3. Salve. O site ficará disponível em `https://SEU-USUARIO.github.io/SEU-REPO/`.

Para usar o domínio próprio (focovidafit.com.br), configure um registro CNAME apontando para o GitHub Pages e adicione um arquivo `CNAME` na raiz com o domínio — ou aponte o domínio para a hospedagem que preferir, já que os arquivos são HTML estático.

## Como publicar (Hostinger via Git)

Este é um site **100% estático** (sem build, sem `package.json`, sem framework) — o navegador interpreta os arquivos `.dc.html` direto, usando `support.js`. Não existe pasta de saída (`dist`/`build`) para configurar.

1. No painel da Hostinger, em **Site → Git**, aponte o deploy para a branch `main` deste repositório.
2. **Diretório de destino:** raiz do repositório (`/`) — não existe subpasta de build para apontar.
3. Confirme que a Hostinger não está com o **"Construtor de Site" / página "em breve"** ativado para o domínio — esse modo tem prioridade sobre o deploy Git e é a causa mais comum de aparecer uma página genérica no lugar do site.
4. Depois de qualquer push, force um novo deploy no painel (**Deploy now** / **Sincronizar**) caso não haja auto-deploy configurado, e limpe o cache do navegador/CDN antes de conferir.

`index.html` (raiz) contém o mesmo conteúdo da home (`index.dc.html`), duplicado — não um redirecionamento — para que qualquer servidor que sirva `index.html` por padrão já mostre o site real, sem depender de um refresh funcionar. **Se editar a home, aplique a mudança nos dois arquivos** (`index.dc.html` e `index.html`). Os links internos de navegação (menu, rodapé) continuam apontando para `index.dc.html`.

## SEO / meta tags e crawlers (og:*, twitter:*, JSON-LD)

O `support.js` processa o bloco `<helmet>` (dentro do `<body>`) via JavaScript no navegador — ótimo para reagir a mudanças de tema/rota, mas invisível para crawlers que não executam JS (Facebook, WhatsApp, Twitter/X, LinkedIn; o Facebook Sharing Debugger reporta isso como "a propriedade og:image foi inferida"). Por isso, em toda página (`*.dc.html`), as tags que precisam existir na resposta HTML crua são colocadas diretamente no `<head>` real do documento, antes de `<script src="./support.js">`:

- `<title>`, `<link rel="canonical">`, `<link rel="icon">`
- `<meta name="description">`, `<meta name="robots">` (quando presente)
- todas as `<meta property="og:*">` e `<meta name="twitter:*">`
- todos os `<script type="application/ld+json">` (Article, FAQPage, Recipe, Organization, WebSite etc.)

O bloco `<helmet>` no `<body>` continua existindo, mas só com o que é puramente apresentacional e não afeta crawlers: `<link rel="preconnect">`, o `<link rel="stylesheet">` das fontes do Google Fonts, o `<style>` inline e (na home) o `<script src="image-slot.js">`.

**Ao criar uma página nova, copie o `<head>` de uma página existente** (ex.: qualquer `artigo-*.dc.html`) em vez de colocar essas tags dentro do `<helmet>` — isso é sem build/SSR, então a única forma de garantir que o crawler veja as tags é elas já estarem no HTML estático desde o início.

## Estrutura
- Páginas principais: `index.dc.html`, `blog.dc.html`, `receitas.dc.html`, `sobre.dc.html`, `contato.dc.html`, páginas legais, `404.dc.html`
- 15 artigos: `artigo-*.dc.html`
- 10 receitas: `receita-*.dc.html`
- Componentes: `Header.dc.html`, `Footer.dc.html`, `ArticleCard.dc.html`, `RecipeCard.dc.html`, `AdSlot.dc.html`, `Newsletter.dc.html`, `CookieBanner.dc.html`, `TrustBadge.dc.html`, `BackToTop.dc.html`
- Runtime: `support.js` (necessário — não remova), `image-slot.js`
- Dados: `site-data.js`
- SEO: `sitemap.xml`, `robots.txt`, `ads.txt` (troque o Publisher ID do AdSense em `ads.txt` antes de publicar)

## Pendências
- Restam 35 dos 50 artigos planejados.
- Formulários de contato/newsletter salvam localmente (`localStorage`) por enquanto — não há backend real nem envio de e-mail; trocar por uma API/serviço de formulário quando houver um.
- `ads.txt` ainda tem o Publisher ID placeholder — trocar pelo real antes de ativar o AdSense.
- Ícones de Instagram/YouTube/TikTok no rodapé apontam para "#" — trocar pelos links reais quando as contas existirem.
- Imagens ainda em JPEG — converter para WebP é uma melhoria de performance pendente (nenhuma ferramenta de conversão disponível no ambiente atual).
