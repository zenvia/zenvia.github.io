---
layout: documentation
title: Integrando o Chatweb da ZCC em seu site
description: 
categories: docs
---

<style>
  iframe
  {
    width: 75%;
    height: 600px;
    border: 5px dashed #808080;
    overflow: hidden;
  }
  iframe body
  {
    overflow: hidden;
  }
  .center
  {
    text-align: center;
    width: 100%;
  }
  div.highlight
  {
    text-align: center;
  }
  pre.highlight
  {
    width: 75%;
    margin: auto;
    text-align: left;
  }
  section img
  {
    border: 3px solid #808080;
  }
</style>

## Índice
* [Introdução](#introdução)
* [Glossário](#glossário)
* [JavaScript](#javascript)
* [Configurações](#configurações)
  * [data-embedded](#data-embedded)
  * [data-button](#data-button)
  * [data-message](#data-message)
  * [data-format](#data-format)
  * [data-color](#data-color)
  * [data-width](#data-width)
  * [data-height](#data-height)
* [Integrações alternativas](#integrações-alternativas)
  * [Link/URL](#linkurl)

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
é necessário que seja utilizado um [id válido de Chatweb](#chat-id).
<br />
Um exemplo de Chatweb Embedded usando as configurações acima pode ser visto abaixo.
#### [Exemplo de Embedded Chatweb usando as configurações padrão]({{ '/html/chat-embedded/default-config.html' | absolute_url }}):
<div class="center">
  <iframe src="{{ '/html/chat-embedded/default-config.html' | absolute_url }}" scrolling="no"></iframe>
</div>
<br />
<br />

## Glossário
Os *"componentes"* do Chatweb Embedded são:
* *Botão flutuante*<br />
![Botão flutuante]({{ '/assets/img/chat-embedded/botao-flutuante.png' | absolute_url }})
* *Botão de início* e *mensagem de boas-vindas*<br />
![Botão de início]({{ '/assets/img/chat-embedded/botao-iniciar.png' | absolute_url }})
&nbsp;&nbsp;
![Mensagem de boas-vindas]({{ '/assets/img/chat-embedded/botao-iniciar-mensagem.png' | absolute_url}})
* *Janela do Chatweb*<br />
![Janela do Chatweb]({{ '/assets/img/chat-embedded/janela.png' | absolute_url }})
<br id="chat-id" />
* *Chat id*<br />
O *chat id* é o identificador da *"identidade"* do *bot*, a qual é usada pra determina
inúmeras informações pra uso no Chatweb, como o nome e logo do *bot*, assim como qual
*bot* será usado para executar a *conversa*.<br />
<br />
O *Chat id* pode ser obtido na lista de integrações, disponível no painel de controla
da ZCC.
<br />
<br />

## JavaScript
Alguns métodos são disponibilizados para permitir o controle e uso do Chatweb por elementos do site, tornando o uso do [botão flutuante](#botão-flutuante) opcional.

Os seguintes métodos estão disponível pra uso:
* *open()*: abre a [janela do Chatweb](#janela-do-chatweb).
* *close()*: fecha a [janela do Chatweb](#janela-do-chatweb).
* *toggle()*: abre ou fecha a [janela do Chatweb](#janela-do-chatweb) de acordo com seu estado atual.
<br />

Um exemplo de uso pode ser visto em [data-embedded="buttonless"](#buttonless).
<br />
<br />

## Configurações
Existem algumas configurações que podem ser realizadas através de atributos da <code class="highlight"><span class="nt">div</span> <span class="s">znv-chat</span></code>:
* [data-embedded](#data-embedded): tipo do Chatweb embedded.
* [data-button](#data-button): texto do botão de iniciar o chat.
* [data-message](#data-message): mensagem em um balão convidando a iniciar o chat.
* [data-format](#data-format): formato da mensagem usada pra iniciar um bot.
* [data-color](#data-color): altera a cor do [botão flutuante](#botão-flutuante).
* [data-width](#data-width): altera a largura da [janela do chatweb](#janela-do-chatweb).
* [data-height](#data-height): altera a altura da [janela do chatweb](#janela-do-chatweb).

### data-embedded
Controla o tipo de Chatweb embedded que será utilizado. O valor padrão é, *button+keyword*, mas será alterado para *button*.

As opções são:
* *button*: Quando clica no [botão flutuante](#botão-flutuante), abre diretamente a [janela do chatweb](#janela-do-chatweb), sem exibir o [botão de início](#botão-de-início) ou a [mensagem de boas-vindas](#mensagem-de-boas-vindas).
<br />
#### [Exemplo de Embedded Chatweb usando data-embedded="button"]({{ '/html/chat-embedded/type-button.html' | absolute_url }}):

```html
<div class="znv-chat"
  data-embedded="button"
></div>
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
<script>
    new ZenviaChat('85b287488b82d36ca599382fd36c2695').build();
</script>
```
<br />
<div class="center">
  <iframe src="{{ '/html/chat-embedded/type-button.html' | absolute_url }}" scrolling="no"></iframe>
</div>

* *button+keyword*: Quando clica no [botão flutuante](#botão-flutuante), exibe o [botão de início](#botão-de-início), daí uma vez clicado, exibe a [janela do chatweb](#janela-do-chatweb).
<br />
#### [Exemplo de Embedded Chatweb usando data-embedded="button+keyword"]({{ '/html/chat-embedded/type-button+keyword.html' | absolute_url }}):

```html
<div class="znv-chat"
  data-embedded="button+keyword"
></div>
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
<script>
    new ZenviaChat('85b287488b82d36ca599382fd36c2695').build();
</script>
```
<br />
<div class="center">
  <iframe src="{{ '/html/chat-embedded/type-button+keyword.html' | absolute_url }}" scrolling="no"></iframe>
</div>
<br id="buttonless" />
* *buttonless*: Não cria o botão flutuante. O site precisa chamar o [javascript](#javascript) de abertura da janela em algum item de seu site.
<br />
#### [Exemplo de Embedded Chatweb usando data-embedded="buttonless"]({{ '/html/chat-embedded/type-buttonless.html' | absolute_url }}):

```html
<iframe src="../sample.html"></iframe>
<!-- Início do código do chat -->
<div class="znv-chat"
  data-embedded="buttonless"
></div>
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
<script>
    var zchat = new ZenviaChat('85b287488b82d36ca599382fd36c2695').build();
</script>
<!-- Fim do código do chat -->
<div class="example">
  <input type="button" value="open()" onclick="zchat.open()" />
  <input type="button" value="close()" onclick="zchat.close()" />
  <input type="button" value="toggle()" onclick="zchat.toggle()" />
</div>
```
<br />
<div class="center">
  <iframe src="{{ '/html/chat-embedded/type-buttonless.html' | absolute_url }}" scrolling="no"></iframe>
</div>

* *room*: Cria a [janela do chatweb](#janela-do-chatweb) logo de início, e sem ser flutuante, de forma *inline*. Seu objetivo é permitir integrar o Chatweb em elementos do site.
<br />
#### [Exemplo de Embedded Chatweb usando data-embedded="room"]({{ '/html/chat-embedded/type-inline.html' | absolute_url }}):

```html
<section class="hero is-white">
  <div class="hero-body">
    <div class="container">
      <!-- Inserindo a janela do chat na página -->
      <div class="znv-chat"
        data-embedded="room"
        data-width="500px"
        data-height="500px"
        style="float: right; margin-left: 10px; border: 5px solid black;"
      ></div>
      <!-- Conteúdo da página -->
      <h3 class="title is-4">Sobre nós</h3>
      <div class="content">
        <p>Somos uma empresa que acredita no futuro! Acima de tudo, no futuro das relações entre empresas e clientes.</p>
        <p> Com uma história de mais de 14 anos e a liderança em mobilidade corporativa no Brasil, oferecemos soluções capazes de fazer com que os clientes percebam os processos de negócio das empresas como experiências ricas em significado e valor.</p>
        <p>Vem simplificar o mundo com a gente!</p>
      </div>
    </div>
  </div>
</section>
<!-- Início do código do chat -->
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
<script>
    new ZenviaChat('85b287488b82d36ca599382fd36c2695').build();
</script>
<!-- Fim do código do chat -->
```
<br />
<div class="center">
  <iframe src="{{ '/html/chat-embedded/type-inline.html' | absolute_url }}" scrolling="no"></iframe>
</div>

<br id="data-button"/>
### data-button
Controla o texto a ser exibido quando uma [data-message](#data-message) é definida ou quando [data-embedded](#data-embedded) é do tipo *button+keyword*, e o conteúdo da
mensagem que é gerada para iniciar o *bot* caso a sala do chat não esteja ainda
inicializada.

O valor padrão é: *Começar*
#### [Exemplo de Embedded Chatweb usando data-button="Olá"]({{ '/html/chat-embedded/config-keyword.html' | absolute_url }}):

```html
<div class="znv-chat"
  data-button="Olá!"
></div>
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
<script>
    new ZenviaChat('85b287488b82d36ca599382fd36c2695').build();
</script>
```
<br />
<div class="center">
  <iframe src="{{ '/html/chat-embedded/config-keyword.html' | absolute_url }}" scrolling="no"></iframe>
</div>
<br />

### data-message
Define uma [mensagem de boas-vindas](#mensagem-de-boas-vindas) pra ser exibida em um balão
acima do [botão flutuante](#botão-flutuante).

Quando utilizada, o balão é carregado já aberto quando o site carrega.

Não tem valor padrão.
#### [Exemplo de Embedded Chatweb usando data-message]({{ '/html/chat-embedded/type-button+message.html' | absolute_url }}):

```html
<div class="znv-chat"
  data-message="Olá! Eu sou o Testbot! Vamos conversar?"
></div>
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
<script>
    new ZenviaChat('85b287488b82d36ca599382fd36c2695').build();
</script>
```
<br />
<div class="center">
  <iframe src="{{ '/html/chat-embedded/type-button+message.html' | absolute_url }}" scrolling="no"></iframe>
</div>
<br />

### data-format
Define o formato da mensagem que *pode* ser gerada quando o [botão de início](#botão-de-início) é clicado. Existem cenários onde essa mensagem não é gerada.

Os formatos disponíveis são:
* *text*: A mensagem inicial fica visível na conversa
* *json*: A mensagem inicial não fica visível na conversa, e ainda permite o envio de informações adicionais ao *bot*.

O valor padrão é *json*, exceto quando o [data-embedded](#data-embedded) é configurado como *button+keyword*.
<br />

### data-color
Define a cor do [botão flutuante](#botão-flutuante).

O valor padrão é: *#333*.
#### [Exemplo de Embedded Chatweb usando data-color="#FF7F00"]({{ '/html/chat-embedded/config-color.html' | absolute_url }}):

```html
<div class="znv-chat"
  data-color="#FF7F00"
></div>
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
<script>
    new ZenviaChat('85b287488b82d36ca599382fd36c2695').build();
</script>
```
<br />
<div class="center">
  <iframe src="{{ '/html/chat-embedded/config-color.html' | absolute_url }}" scrolling="no"></iframe>
</div>
<br />

### data-width
Define a *largura* da [janela flutuante](#janela-do-chatweb) do chatweb.

O valor padrão é: *375px*, exceto quando [data-embedded](#data-embedded) é configurado como *room*, aí o valor padrão passa a ser *100%*.
<br />

### data-height
Define a *altura* da [janela flutuante](#janela-do-chatweb) do chatweb.

O valor padrão é: *567px*, exceto quando [data-embedded](#data-embedded) é configurado como *room*, aí o valor padrão passa a ser *100%*.
<br />
<br />

## Integrações alternativas
### Link/URL
São URLs que quando acessadas, iniciam o *bot* identificado pelo [chat id](#chat-id) utilizado em sua composição.

Podem ser utilizados em diversos cenários, sendo portanto, bem flexível.
<br />
<br />

###### Domínios:
Existem diversas opções de domínio que podem ser usados para esse propósito.
Segue algumas delas:
* fale.chat
* sac.chat
* pesquisa.chat
* zenvia.chat

E algumas opções com suporte a *https*:
* seuchat.com
* chat.zenvia.com
* chatbot.zenvia.com
* m.chatbot.zenvia.com
<br />
<br />

###### Composição:
O URL de redirecionamento a um *bot* possui o seguinte formato:<br />
*http://\[domínio\]/bot/[\[chat id\]](#chat-id)*<br />
<br />
ou<br />
<br />
*http://\[domínio\]/bot/[\[chat id\]](#chat-id)/[\[palavra-chave\]](#data-button)*<br />
<br />
<br />

###### Exemplos (funcionais):
[http://chat.zenvia.com/bot/85b287488b82d36ca599382fd36c2695](http://chat.zenvia.com/bot/85b287488b82d36ca599382fd36c2695)<br />
