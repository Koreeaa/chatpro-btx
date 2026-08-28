# ChatPro dentro do Bitrix24

Aplicativo local estatico que exibe o painel do ChatPro dentro do
Bitrix24 e registra o item **ChatPro** na barra do negocio. O vendedor
clica ali e o ChatPro abre no slider lateral, em tela cheia.

Ja esta instalado no portal specologia.bitrix24.com.br (aplicativo
local ID 78). Este repositorio guarda o codigo-fonte.

## Arquivos

- `index.html` — a pagina do app: iframe do ChatPro + registro do
  item na barra do negocio (`placement.bind` em `CRM_DEAL_DETAIL_TOOLBAR`).
- `config.js` — a unica coisa que voce edita: a URL do ChatPro.
- `chatpro.zip` — os dois arquivos acima empacotados, pronto para subir.

## Como publicar uma alteracao

1. Edite `config.js` e/ou `index.html`.
2. Gere o zip com os dois na raiz:

       zip -X chatpro.zip index.html config.js

3. No Bitrix24: **Aplicativos -> Recursos para desenvolvedores ->
   Integracoes**, abra o registro do aplicativo local, marque
   **Estatico**, envie o novo `chatpro.zip` e clique em **Salvar**.
4. Abra o app uma vez (Aplicativos -> ChatPro). Ele mesmo refaz o
   registro do item na barra do negocio.

## Observacoes

- Permissoes necessarias no aplicativo: **CRM (crm)** e
  **Aplicativo incorporado (placement)**.
- Nao use GitHub Pages como manipulador: o Bitrix24 abre o handler
  com POST e o Pages responde 405. Por isso o app roda em modo
  Estatico, hospedado pelo proprio Bitrix24.
- Arquivos com SVG inline foram entregues vazios pelo empacotador do
  Bitrix24. Se um arquivo aparecer em branco no app, e isso — troque
  por CSS ou texto.
- Dentro do iframe o ChatPro comeca deslogado, porque o navegador
  separa cookies de um site quando ele roda embutido em outro. Cada
  pessoa faz login uma vez ali dentro. Se pedir senha toda vez, libere
  `chatpro.com.br` nas excecoes de cookies do Chrome.
