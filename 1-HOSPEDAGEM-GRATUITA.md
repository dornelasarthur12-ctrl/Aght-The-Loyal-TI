# Como publicar de graça (GitHub Pages)

Um PWA só pode ser instalado quando está em um endereço **https**. O GitHub Pages dá isso de graça.
Não publiquei nada por você: preciso de uma conta sua e da sua autorização.

## Passo a passo (pelo site, sem programar)
1. Crie uma conta grátis em https://github.com (se ainda não tiver).
2. Clique em **+ → New repository**. Nome sugerido: `aght-the-loyal`. Deixe **Public**. Clique **Create repository**.
3. Clique em **uploading an existing file**.
4. **Descompacte o ZIP no computador** e arraste para a página o *conteúdo* da pasta: `index.html`, `manifest.json`, `service-worker.js`, `.nojekyll`, a pasta `icons`. (Arraste os arquivos e a pasta, não o ZIP.)
   - Se o navegador não aceitar a pasta `icons`, envie os arquivos de dentro dela criando antes o caminho `icons/` pelo botão **Add file → Create new file**, ou use o GitHub Desktop.
5. Clique **Commit changes**.
6. Vá em **Settings → Pages**. Em *Build and deployment*, escolha **Deploy from a branch**, branch **main**, pasta **/ (root)** e **Save**.
7. Espere 1–2 minutos. O endereço será `https://SEU-USUARIO.github.io/aght-the-loyal/`.

## Alternativa: Cloudflare Pages (também grátis)
Em https://pages.cloudflare.com → *Create project → Direct Upload* → arraste a pasta do projeto. O arquivo `_headers` já está incluído.

## Publicar uma atualização depois
1. Edite o jogo (`index.html`).
2. Em `service-worker.js`, troque `const CACHE_VERSION = 'v1';` por `'v2'` (depois `'v3'`…).
3. Envie os arquivos de novo (substituindo). Quem já instalou recebe a nova versão ao abrir o jogo com internet (pode ser preciso fechar e abrir o app uma segunda vez).

## Observação
Os dados salvos do jogo (localStorage) ficam no aparelho e **não** passam de um endereço para outro: se mudar o endereço do jogo, o progresso salvo não vem junto.
