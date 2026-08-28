# ChatPro dentro do Bitrix24

Botao destacado na barra do negocio/lead/contato. O vendedor clica e o
ChatPro abre no slider lateral do Bitrix24, em tela cheia.

## 1. Editar

Abra `config.js` e confirme a URL das conversas:

    window.CHATPRO_URL = "https://app.chatpro.com.br/";

Se ao entrar no ChatPro a barra de endereco mostrar algo mais especifico
(ex.: `.../chats`), use essa URL — o painel ja abre direto na lista.

## 2. Hospedar

Suba os quatro arquivos (`index.html`, `botao.html`, `install.html`,
`config.js`) juntos, na mesma pasta, em qualquer host com HTTPS:
GitHub Pages, Netlify, Cloudflare Pages, Vercel ou seu proprio servidor.

Anote as duas URLs que sairem, por exemplo:

    https://SEU-HOST/chatpro/index.html
    https://SEU-HOST/chatpro/install.html

## 3. Criar o aplicativo no Bitrix24

Aplicativos -> Recursos para desenvolvedores -> Outro -> Aplicativo local.

| Campo                          | Valor                                  |
|--------------------------------|----------------------------------------|
| Tipo                           | Estatico                               |
| Seu caminho do manipulador     | .../index.html                         |
| Caminho de instalacao inicial  | .../install.html                       |
| Apenas script                  | desmarcado                             |
| Texto do item de menu          | ChatPro                                |
| Atribuir permissoes            | CRM (crm) + Incorporacoes (placement)  |

Clique em Create. A tela de instalacao roda sozinha e mostra em quais
lugares o botao foi registrado.

## 4. Conferir

Abra qualquer negocio: o botao verde "Abrir ChatPro" aparece na barra
superior do card. Clicando, o ChatPro abre no slider.

## Se der errado

- **A instalacao acusa erro de permissao**: falta o escopo `placement`.
  Edite o aplicativo, adicione e reinstale.
- **A tela de instalacao nao consegue chamar a API** (modo Estatico sem
  autenticacao): troque o tipo para Servidor e hospede em algo que
  responda POST — Cloudflare Workers ou seu servidor. Os arquivos sao
  os mesmos.
- **O ChatPro pede login toda vez**: o navegador esta bloqueando cookies
  de terceiros. Libere `chatpro.com.br` nas excecoes do Chrome.

## Depois

Da pra fazer o botao abrir direto a conversa do telefone daquele
negocio, em vez da lista toda — depende de o ChatPro aceitar um numero
na URL. Vale testar abrindo uma conversa la e olhando a barra de
enderecos.
