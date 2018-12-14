---
layout: documentation
title: Integrando o Web Chat em seu site
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
* [Informações de contexto do site disponíveis no *Chatbot*](#informações-de-contexto-do-site-disponíveis-no-chatbot)
* [JavaScript](#javascript)
* [Configurações](#configurações)
  * [embedded](#embedded)
  * [button](#button)
  * [message](#message)
  * [format](#format)
  * [color](#color)
  * [width](#width)
  * [height](#height)
  * [user](#user)
* [Integrações alternativas](#integrações-alternativas)
  * [Link/URL](#linkurl)

<br />

## Introdução
O Web Chat também pode ser utilizado integrado em seu site.
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
    <script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
    <script>new ZenviaChat('id-do-chat-aqui').build();</script>
    <!-- Fim do código do chat -->
  </body>
</html>
```
<br />
No trecho do código:
<code class="highlight"><span class="s1">'id-do-chat-aqui'</span></code>
é necessário que seja utilizado um [Id válido de Web Chat](#chat-id).
<br />
Um exemplo de Web Chat Embedded usando as configurações acima pode ser visto abaixo.
#### [Exemplo de Web Chat Embedded usando as configurações padrão]({{ '/html/chat-embedded/default-config.html' | absolute_url }}){:target="_blank"}:
<div class="center">
  <iframe src="{{ '/html/chat-embedded/default-config.html' | absolute_url }}" scrolling="no"></iframe>
</div>
<br />
<br />

## Glossário
Os *"componentes"* do Web Chat Embedded são:
* ***Botão flutuante***<br id="botão-flutuante"/>
![Botão flutuante]({{ '/assets/img/chat-embedded/botao-flutuante.png' | absolute_url }})
<br />
<br />
* ***Botão de início***<br id="botão-de-início" />
![Botão de início]({{ '/assets/img/chat-embedded/botao-iniciar.png' | absolute_url }})
<br />
<br />
* ***Mensagem de boas-vindas*** e ***botão de início***<br id="mensagem-de-boas-vindas" />
![Mensagem de boas-vindas]({{ '/assets/img/chat-embedded/botao-iniciar-mensagem.png' | absolute_url}})
<br />
<br />
* ***Janela do Web Chat***<br id="janela-do-web-chat" />
![Janela do Web Chat]({{ '/assets/img/chat-embedded/janela.png' | absolute_url }})
<br />
<br />
* ***Id Web Chat***<br id="chat-id" />
O *Id Web Chat* é o identificador da *"identidade"* do *Chatbot*, a qual é usada para determinar
inúmeras informações para uso no Web Chat, como o nome e logo do *Chatbot*, assim como qual
*Chatbot* será usado para executar a *conversa*.<br />
<br />
O *Id Web Chat* pode ser obtido na lista de integrações, disponível no painel de controle.
<br />
<br />

## Inicialização
A inicialização do chat é composta de 3 etapas:
1. [Carregamento do script](#carregamento-do-script)
2. [Configuração](#configuração-e-construção)
3. [Construção](#configuração-e-construção)

### Carregamento do script
A etapa mais simples da inicialização: simplesmente o código do Web Chat é carregado na página. Isso é feito através do seguinte bloco *HTML*:
```html
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
```

Esse bloco HTML pode ser inserido tanto na tag *head* da página como na tag *body*.
Esse bloco precisa ser inserido antes dos blocos das outras etapas da inicialização
do Web Chat.

### Configuração e Construção
As etapas de configuração e contrução podem ser executadas separadamente, mas, *normalmente*,
é mais simples e mais fácil efetuá-las em conjunto.

A etapa de configução é composta da criação da instância da classe *ZenviaChat* na página, seguida, **opcionalmente**, de configurações descritas na seção de [configurações](#configurações) dessa documentação.

Para efetuar a criação da instância da classe *ZenviaChat*, é necessário fornecer o [Id Web Chat](#chat-id).

A etapa de construção consiste execução do método *build()*. Esse método que faz o
[botão flutuante](#botão-flutuante) do Web Chat aparecer na página.

Exemplo contendo as etapas de configuração e construção:
```html
<script>
    new Zenvia('id-do-chat-aqui')
      .button('Tirar dúvidas')
      .build();
</script>
```
<br />

#### Elemento para construção do Web Chat
Opcionalmente, e particularmente importante para Web Chat Embedded utilizando a configuração
[embedded("room")](#room), é possível indicar o *id* de um elemento da página onde os
elementos do Web Chat serão criados. Esse *id* é indicado como parâmetro no método
*build()*. Exemplo:
```html
<div id="id-do-elemento-html"></div>
<script>
    new Zenvia('id-do-chat-aqui')
      .build('id-do-elemento-html');
</script>
```

Em exemplo prático pode ser visto em [embedded("room")](#room).
<br />
<br />

## Informações de contexto do site disponíveis no *Chatbot*
Todo Web Chat Embedded, por padrão, durante sua [inicialização](#inicialização), envia informações do contexto do site onde ele está integrado, como *URL* do site, *hostname*, *path* e *query string*. Todas as informações de contexto estão agrupadas dentro da variável <code>website</code> e seus atributos são os seguintes:
* **url:** URL do site onde o Web Chat está integrado.
* **hostname:** Hostname do site onde o Web Chat está integrado.
* **path:** Path do site onde o Web Chat está integrado.
* **rawQueryParams:** Dado bruto dos parâmetros *query string* da página onde o Web Chat está integrado.
* **queryParams:** Parâmetros *query string* separados em "nome do parâmetro" e "valor do parâmetro.
* **referrer:** Agrupamento das informações referentes à página que continha o link para o site onde o Web Chat está integrado. Similar à variável website, possui os seguintes atributos:
  * **url:** URL do site que continha o link para o site onde o Web Chat está integrado.
  * **hostname:** Hostname do site que continha o link para o site onde o Web Chat está integrado.
  * **path:** Path do site que continha o link para o site onde o Web Chat está integrado.
  * **rawQueryParams:** Dado bruto dos parâmetros *query string* do site que continha o link para o site onde o Web Chat está integrado.
  * **queryParams:** Parâmetros *query string* separados em "nome do parâmetro" e "valor do parâmetro do site que continha o link para o site onde o Web Chat está integrado.

Se, por exemplo, um usuário entrou no Google, pesquisou por "Empresa XYZ" e clicou no anúncio da Empresa XYZ que o Google forneceu ele será direcionado ao site da empresa. Caso ele interaja com o *Chatbot* integrado à essa página, a variável <code>website</code> seria disponibilizada para uso no *Chatbot* contendo uma estrutura parecida com a seguinte:

```json
{
  "url": "https://www.empresa-xyz.com/produtos/X-Produto?utm_source=google&utm_medium=cpc&utm_campaign=google_xproduto&gclid=IsAEAIaIQobChMIyr38o_CS3QIVFoCRCh0jPwlbEAAYASAAEgKWXfD_BwE",
  "hostname": "www.empresa-xyz.com",
  "path": "/produtos/X-Produto",
  "rawQueryParams": "utm_source=google&utm_medium=cpc&utm_campaign=google_xproduto&gclid=IsAEAIaIQobChMIyr38o_CS3QIVFoCRCh0jPwlbEAAYASAAEgKWXfD_BwE",
  "queryParams": {
    "utm_source": "google",
    "utm_medium": "cpc",
    "utm_campaign": "google_xproduto",
    "gclid": "IsAEAIaIQobChMIyr38o_CS3QIVFoCRCh0jPwlbEAAYASAAEgKWXfD_BwE"
  },
  "referrer": {
    "url": "https://www.google.com.br/",
    "hostname": "www.google.com.br",
    "path": "/",
    "rawQueryParams": "",
    "queryParams": {}
  }
}
```
<br />

Para acessar algum destes atributos diretamente no *Chatbot*, basta utilizar a diretiva <code>#{session['website']}</code> respeitando a hierarquia da variável, como por exemplo:
* <code>#{session['website']['queryParams']['utm_source']}</code> ou somente <code>#{website.queryParams.utm_source}</code> retornará o valor **google**.
* <code>#{session['website']['referrer']['hostname']}</code> ou <code>#{website.referrer.hostname}</code> retornará o valor **www.google.com.br**.
<br />
<br />

É possível incluir informações extras nos dados do website que serão enviadas para o *Chatbot*. Essas informações ficarão na variável <code>extra</code> dentro de <code>website</code>. Para enviar informações extras para o *Chatbot*, é necessário setar o campo <code>extraData</code> durante a integração do Web Chat em seu site conforme mostrado abaixo:

```html
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
<script>
  new ZenviaChat('id-do-chat-aqui')
    .extraData({ campoA: 'valor A', campoX: 'valor de X', outroCampo: { campoInterno: "um valor qualquer" }})
    .build();
</script>
```
<br />

Vale salientar que o campo **extraData** pode assumir qualquer estrutura pois é um objeto JavaScript ou pode ser somente uma string. Para acessar os dados extras no *Chatbot* basta utilizar a diretiva <code>#{session['website']['extra']}</code> respeitando a hierarquia do objeto enviado, como por exemplo:
* <code>#{session['website']['extra']['outroCampo']['campoInterno']}</code> retornará o conteúdo **um valor qualquer**.
<br />
<br />

## JavaScript
Alguns métodos são disponibilizados para permitir o controle e uso do Web Chat por elementos do site, tornando o uso do [botão flutuante](#botão-flutuante) opcional.

Os seguintes métodos estão disponível para uso:
* ***open()***: abre a [janela do Web Chat](#janela-do-web-chat).
* ***close()***: fecha a [janela do Web Chat](#janela-do-web-chat).
* ***toggle()***: abre ou fecha a [janela do Web Chat](#janela-do-web-chat) de acordo com seu estado atual.
* ***destroy()***: fecha (caso aberta) a [janela do Web Chat](#janela-do-web-chat) e remove da página todos os elementos criados pelo Web Chat.
<br />

Um exemplo de uso pode ser visto em [embedded('buttonless')](#buttonless).
<br />
<br />

## Configurações
Existem algumas configurações que podem ser realizadas através de métodos da instância da
classe *ZenviaChat*:
* [embedded](#embedded): tipo do Web Chat embedded.
* [button](#button): texto do botão de iniciar o chat.
* [message](#message): mensagem em um balão convidando a iniciar o chat.
* [format](#format): formato da mensagem usada para iniciar um *Chatbot*.
* [color](#color): altera a cor do [botão flutuante](#botão-flutuante).
* [width](#width): altera a largura da [janela do Web Chat](#janela-do-web-chat).
* [height](#height): altera a altura da [janela do Web Chat](#janela-do-web-chat).
* [user](#user): determina qual o *id* do usuário.

### embedded
Controla o tipo de Web Chat embedded que será utilizado. O valor padrão é *button+keyword*,
mas o recomendado é utilizar o valor *button* em seu lugar.

As opções são:
* ***button***: Quando clica no [botão flutuante](#botão-flutuante), abre diretamente a [janela do Web Chat](#janela-do-web-chat), sem exibir o [botão de início](#botão-de-início).
<br />
#### [Exemplo de Web Chat Embedded usando embedded('button')]({{ '/html/chat-embedded/type-button.html' | absolute_url }}){:target="_blank"}:

```html
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
<script>
    new ZenviaChat('85b287488b82d36ca599382fd36c2695')
      .embedded('button')
      .build();
</script>
```
<br />
<div class="center">
  <iframe src="{{ '/html/chat-embedded/type-button.html' | absolute_url }}" scrolling="no"></iframe>
</div>
<br />
* ***button+keyword***: Quando clica no [botão flutuante](#botão-flutuante), exibe o [botão de início](#botão-de-início), daí uma vez clicado, exibe a [janela do Web Chat](#janela-do-web-chat).
<br />
#### [Exemplo de Web Chat Embedded usando embedded('button+keyword')]({{ '/html/chat-embedded/type-button+keyword.html' | absolute_url }}){:target="_blank"}:

```html
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
<script>
    new ZenviaChat('85b287488b82d36ca599382fd36c2695')
      .embedded('button+keyword')
      .build();
</script>
```
<br />
<div class="center">
  <iframe src="{{ '/html/chat-embedded/type-button+keyword.html' | absolute_url }}" scrolling="no"></iframe>
</div>
<br id="buttonless" />
* ***buttonless***: Não cria o botão flutuante. O site precisa chamar o [javascript](#javascript) de abertura da janela em algum item de seu site.
<br />
#### [Exemplo de Embedded Web Chat usando embedded('buttonless')]({{ '/html/chat-embedded/type-buttonless.html' | absolute_url }}){:target="_blank"}:

```html
<!-- Início do código do chat -->
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
<script>
    var zchat = new ZenviaChat('85b287488b82d36ca599382fd36c2695')
      .embedded('buttonless')
      .build();
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
<br id="room" />
* ***room***: Cria a [janela do Web Chat](#janela-do-web-chat) logo de início, e sem ser flutuante, de forma *inline*. Seu objetivo é permitir integrar o Web Chat em elementos do site.
<br />
<br />
Por conta disso, normalmente se faz necessário a criação de um
<code class="highlight"><span class="nt">div</span></code>
com
<code class="highlight"><span class="na">id</span></code>.
<br />
No exemplo abaixo, essa
<code class="highlight"><span class="nt">div</span></code>
está com o
<code class="highlight"><span class="na">id</span></code>:
<code class="highlight"><span class="s">elemento-html</span></code>.
<br />
<br />
Algumas informações adicionais podem ser emcontradas em
[elemento para construção do Web Chat](#elemento-para-construção-do-web-chat).
<br />
<br />
#### [Exemplo de Web Chat Embedded usando embedded('room')]({{ '/html/chat-embedded/type-inline.html' | absolute_url }}){:target="_blank"}:

```html
<section class="hero is-white">
  <div class="hero-body">
    <div class="container">
      <!-- ELEMENTO HTML ONDE A JANELA DO CHAT SERÁ INSERIDA -->
      <div id="elemento-html" style="
          width: 500px;
          height: 500px;
          float: right;
          margin-left: 10px;
          border: 5px solid black;">
      </div>
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
    new ZenviaChat('85b287488b82d36ca599382fd36c2695')
      .embedded('room')
      .build('elemento-html');
</script>
<!-- Fim do código do chat -->
```
<br />
<div class="center">
  <iframe src="{{ '/html/chat-embedded/type-inline.html' | absolute_url }}" scrolling="no"></iframe>
</div>

<br />
### button
Controla o texto a ser exibido quando uma [message](#message) é definida ou quando [embedded](#embedded) é do tipo *button+keyword*, e o conteúdo da
mensagem que é gerada para iniciar o *Chatbot* caso a sala do chat não esteja ainda
inicializada.

O valor padrão é: *Começar*
#### [Exemplo de Web Chat Embedded usando button('Olá')]({{ '/html/chat-embedded/config-keyword.html' | absolute_url }}){:target="_blank"}:

```html
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
<script>
    new ZenviaChat('85b287488b82d36ca599382fd36c2695')
      .button('Olá!')
      .build();
</script>
```
<br />
<div class="center">
  <iframe src="{{ '/html/chat-embedded/config-keyword.html' | absolute_url }}" scrolling="no"></iframe>
</div>
<br />

### message
Define uma [mensagem de boas-vindas](#mensagem-de-boas-vindas) para ser exibida em um balão
acima do [botão flutuante](#botão-flutuante).

Quando utilizada, o balão é carregado já aberto quando o site carrega,
e a configuração [embedded](#embedded) automaticamente muda para *button*.

Não tem valor padrão.
#### [Exemplo de Web Chat Embedded usando message]({{ '/html/chat-embedded/type-button+message.html' | absolute_url }}){:target="_blank"}:

```html
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
<script>
    new ZenviaChat('85b287488b82d36ca599382fd36c2695')
      .message('Olá! Eu sou o Testbot! Vamos conversar?')
      .build();
</script>
```
<br />
<div class="center">
  <iframe src="{{ '/html/chat-embedded/type-button+message.html' | absolute_url }}" scrolling="no"></iframe>
</div>
<br />

### format
Define o formato da mensagem que *pode* ser gerada quando o [botão de início](#botão-de-início) é clicado. Existem cenários onde essa mensagem não é gerada.

Os formatos disponíveis são:
* ***text***: A mensagem inicial fica visível na conversa
* ***json***: A mensagem inicial não fica visível na conversa, e ainda permite o envio de informações adicionais ao *Chatbot*.

O valor padrão é *json*, exceto quando o [embedded](#embedded) é configurado como *button+keyword*.
<br />

### color
Define a cor do [botão flutuante](#botão-flutuante).

O valor padrão é: *#333*.
#### [Exemplo de Web Chat Embedded usando color('#FF7F00')]({{ '/html/chat-embedded/config-color.html' | absolute_url }}){:target="_blank"}:

```html
<script src="https://static.zenvia.com/embed/js/zenvia-chat.min.js"></script>
<script>
    new ZenviaChat('85b287488b82d36ca599382fd36c2695')
      .color('#FF7F00')
      .build();
</script>
```
<br />
<div class="center">
  <iframe src="{{ '/html/chat-embedded/config-color.html' | absolute_url }}" scrolling="no"></iframe>
</div>
<br />

### width
Define a *largura* da [janela flutuante](#janela-do-web-chat) do Web Chat.

O valor padrão é: *400px*, exceto quando [embedded](#embedded) é configurado como *room*, aí o valor padrão passa a ser *100%*.
<br />

### height
Define a *altura* da [janela flutuante](#janela-do-web-chat) do Web Chat.

O valor padrão é: *567px*, exceto quando [embedded](#embedded) é configurado como *room*, aí o valor padrão passa a ser *100%*.
<br />

### user
Define o *id* do usuário no Web Chat. Juntamente com o [Id Web Chat](#chat-id), determina o id da conversa.

Por padrão, esse id é gerado aleatoriamente, e armazenado no navegador até que o mesmo
seja encerrado. Dessa forma, esse id será sempre o mesmo enquanto o usuário não
fechar o navegador, então mesmo que o usuário saia da página ou abra várias abas,
a conversa carregada será sempre a mesma.

Mas também é possível utilizar algum outro identificador, como por exemplo, um e-mail.
<br />
<br />

## Integrações alternativas
### Link/URL
São URLs que quando acessadas, iniciam o *Chatbot* identificado pelo [Id Web Chat](#chat-id) utilizado em sua composição.

Podem ser utilizados em diversos cenários, sendo portanto, bem flexível.
<br />
<br />

###### Domínios:
Existem diversas opções de domínio que podem ser usados para esse propósito.
Seguem algumas delas com suporte a *https*:
* zenvia.chat
* seuchat.com
<br />
<br />

###### Composição:
O URL de redirecionamento a um *Chatbot* possui o seguinte formato:<br />
*http://\[domínio\]/bot/[\[Id Web Chat\]](#chat-id)*<br />
<br />
ou<br />
<br />
*http://\[domínio\]/bot/[\[Id Web Chat\]](#chat-id)/[\[palavra-chave\]](#button)*<br />
<br />
<br />

###### Exemplos (funcional):
[http://chat.zenvia.com/bot/85b287488b82d36ca599382fd36c2695](http://chat.zenvia.com/bot/85b287488b82d36ca599382fd36c2695){:target="_blank"}<br />
