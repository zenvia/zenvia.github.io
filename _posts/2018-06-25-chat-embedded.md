---
layout: documentation
title: Integrando o Chatweb da ZCC em seu site
description: 
categories: docs
---

<style>
  iframe
  {
    width: 100%;
    height: 355px;
    border: 5px dashed black;
  }
</style>

## Índice
* [Introdução](#Introdução)
* [Glossário](#Glossário)
* [Configurações](#Configurações)
* [Exemplos](#Exemplos)
<br />

## Introdução
O Chatweb da [ZCC](../) também pode ser utilizado integrado em seu site.
Existem várias configurações e possibilidades de uso, mas a integração mais básica
pode ser feita assim:

```html
<html>
  <head>
    <title>Meu site de exemplo</title>
  </head>
  <body>
    <div>Conteúdo Original do site.</div>

    <!-- Início do código do chat -->
    <div class="znv-chat"></div>
    <script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
    <script>
        new ZenviaChat('id-do-chat-aqui').build();
    </script>
    <!-- Fim do código do chat -->
  </body>
</html>
```
<br />
No trecho do código:
<code class="highlight"><span class="s1">'id-do-chat-aqui'</span></code>
é necessário que seja utilizado um id válido de Chatweb, o qual pode ser obtido
na lista de integrações.
<br />
Um exemplo de Chatweb Embedded usando as configurações acima por ser visto
[mais abaixo](#Exemplos).
<br />
<br />
## Glossário
Existem três *"componentes"* no Chatweb Embedded:
* Botão flutuante
* Mensagem de boas-vindas e botão de início
* A janela do Chatweb
<br />
<br />
## Configurações
Existem algumas configurações que podem ser realizadas através de atributos da <code class="highlight"><span class="nt">div</span> <span class="s">znv-chat</span></code>:
* [data-embedded](#data-embedded): tipo do Chatweb embedded.
* [data-button](#data-button): texto do botão de iniciar o chat.
* [data-message](#data-message): mensagem em um balão convidando a iniciar o chat.
* [data-format](#data-format): formato da mensagem usada pra iniciar um bot.

### data-embedded
Controla o tipo de Chatweb embedded que será utilizado. As opções são:
* *button*: Quando clica no 
* *button+keyword*: 
* *buttonless*: 
* *room*: 

O valor padrão é: *button+keyword*

Veja [Configurações](#Configurações) para mais configurações.

### data-button
Controla o texto a ser exibido quando uma [data-message](#data-message) é definida ou quando [data-embedded](#data-embedded) é do tipo *button+keyword*, e o texto que é gerado para iniciar o bot caso a sala do chat não esteja inicializada ainda.

O valor padrão é: *Começar*

### data-message

O valor

### data-format

## Exemplos
#### [Exemplo de Embedded Chatweb usando as configurações padrão]({{ '/html/chat-embedded/default-config.html' | absolute_url }}):
<iframe src="{{ '/html/chat-embedded/default-config.html' | absolute_url }}"></iframe>
<br />
<br />
