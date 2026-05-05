# P1 Marketing — Site institucional

Site estático de uma única página (`index.html`), sem build, sem dependências Node.

## Estrutura

```
P1SITE-deploy/
├── index.html       # Página única, todo CSS e JS inline
├── P1-11.svg        # Logo P1
└── assets/
    ├── Syncopate-Bold.ttf
    ├── Syncopate-Regular.ttf
    └── Inter-VariableFont_opsz,wght.ttf
```

Não tem package.json, node_modules, build pipeline, nada. Abra `index.html` em qualquer navegador e funciona.

## Como rodar local

Basta abrir o `index.html` direto no navegador, OU servir via qualquer servidor estático:

```bash
# Python
python3 -m http.server 8080

# Node
npx serve .
```

## Deploy (opções, mais simples pra mais avançada)

### 1. Vercel (recomendado, 30 segundos)

1. Acesse [vercel.com](https://vercel.com) e faça login com GitHub.
2. Clique em **Add New → Project**.
3. Importe o repositório.
4. Em **Framework Preset**, selecione **Other**.
5. Deixe **Root Directory** em branco e clique em **Deploy**.

Pronto. URL final do tipo `https://p1-marketing.vercel.app`. Deploy automático a cada push.

### 2. Netlify

1. [netlify.com](https://netlify.com) → login com GitHub.
2. **Add new site → Import an existing project**.
3. Escolha o repo. Build command vazio, publish directory `.` (ponto).
4. Deploy.

### 3. GitHub Pages (grátis, usa domínio github.io)

1. No repositório, vá em **Settings → Pages**.
2. Em **Source**, selecione `Deploy from a branch`.
3. Branch: `main` / folder: `/ (root)`.
4. Save. Em 1-2 minutos a URL fica disponível em `https://<usuario>.github.io/<repo>/`.

### 4. Cloudflare Pages

1. [pages.cloudflare.com](https://pages.cloudflare.com) → Connect to Git.
2. Escolha o repo. Build command vazio. Build output `/`.
3. Deploy.

## Domínio próprio

Todas as 4 plataformas acima suportam domínio custom (ex: `p1.com.br`) gratuitamente, em geral editando o DNS pra apontar pra plataforma. Cada uma tem doc passo-a-passo no painel.

## Subindo pro GitHub do zero

Se ainda não tem o repo:

```bash
cd P1SITE-deploy
git init
git add .
git commit -m "initial commit: P1 site"
git branch -M main
git remote add origin https://github.com/<usuario>/<repo>.git
git push -u origin main
```

## Notas técnicas

- Tudo é **vanilla HTML + CSS + JS**. Zero frameworks, zero build.
- Animações usam `requestAnimationFrame` e CSS transforms.
- Fontes servidas localmente (`assets/`), zero requisição externa.
- Suporta `prefers-reduced-motion` (acessibilidade total).
- Responsivo com breakpoint em 1024px:
  - **Desktop/tablet grande**: scroll-driven completo, puzzle com fuga lateral L↔R, zoom progressivo
  - **Mobile**: puzzle segue pinado no centro, peças encaixam por tela, texto com backdrop blur para legibilidade. Sem fuga lateral
- iOS Safari: usa `dvh` (dynamic viewport height), URL bar que some/aparece não causa pulos
- Graceful degradation: mesmo se JS falhar, todo conteúdo textual fica visível e utilizável

## Contato

Site desenvolvido por Leonardo Ferreira.
[leonardoferreirr.com.br](https://leonardoferreirr.com.br)
