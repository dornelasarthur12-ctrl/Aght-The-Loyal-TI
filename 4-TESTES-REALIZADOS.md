# Testes realizados (Chromium 'headless' via Playwright, em servidor local)

Cada item abaixo foi executado de verdade; resultado entre parênteses.

| Teste | Resultado |
|---|---|
| manifest.json acessível, JSON válido, campos obrigatórios | Passou |
| Chrome (CDP) sem erros de instalabilidade e sem erros de parse do manifest | Passou |
| Ícones 192/512 (any) e 192/512 (maskable) existem e têm o tamanho declarado | Passou |
| Service Worker registra e fica "activated"; página passa a ser controlada por ele | Passou |
| Pré-cache: 9 arquivos guardados | Passou |
| Caminhos funcionam na raiz (`/`) e em subpasta (`/meu-repo/`, como no GitHub Pages) | Passou |
| Jogo abre e desenha no canvas online | Passou |
| Jogo abre **offline** (recarregando sem rede) e desenha no canvas | Passou |
| Sem erros de JavaScript/console online e offline (teclas de jogo pressionadas) | Passou |
| localStorage (progresso salvo) funciona | Passou |
| Atualização: novo CACHE_VERSION troca o cache, remove o antigo, serve a nova versão (online e offline) | Passou |
| Celular simulado (Pixel 7, paisagem, toque): abre offline, 6 botões de controle presentes, sem erros | Passou |
| Código do jogo inalterado: `diff` com o original mostra só 1 linha de `<head>` trocada e 4 linhas adicionadas no fim | Passou |

## NÃO testado (sem acesso)
- Instalação real em um Android ou Windows físico (só os critérios de instalabilidade do Chrome foram verificados).
- Publicação no GitHub Pages / Cloudflare (precisa da sua conta).
- Jogar a campanha inteira: testei só abertura, título e entrada no jogo.
- Orientação travada em paisagem no Android instalado (declarada no manifest; o jogo já tem seu próprio bloqueio/rotação).

## Observações sobre o projeto original
- Você enviou **um único HTML** (não um ZIP): ele já é autocontido (imagens embutidas em base64, sem arquivos externos nem CDN), então não há dependências externas a cachear.
- Nenhum erro de console no original.
- O jogo usa o áudio via AudioContext: no celular o som só começa depois do primeiro toque (regra do navegador).

## Correção da abertura (texto sumido / tela preta) — versão v2
- Problema: o jogo original já tinha regras de CSS (`h1,p{display:none!important}` nos modos paisagem e PC) que escondiam os parágrafos do texto de abertura. Verificado no arquivo original: o texto não aparece nem lá (desktop e celular em paisagem).
- Correção: uma linha de CSS no `<head>` (`#intro .tx p{display:block!important}`) que só reexibe o texto da abertura.
- Resultado verificado: o texto rolante aparece no desktop e no celular simulado em paisagem; os 26 testes do PWA continuam passando.
- Não testei a abertura até o fim nem o resto do jogo depois dela.
