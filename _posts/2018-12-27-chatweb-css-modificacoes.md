---
layout: documentation
title: Modificações possíveis de Estilo no Chatweb
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
* [Aonde modificar?](#aonde-modificar)
* [Cabeçalho](#cabeçalho)
* [Fundo da Conversa](#fundo-da-conversa)
* [Balões da Conversa](#balões-da-conversa)
* [Campo de digitação do usuário e ações](#campo-de-digitação-do-usuário-e-ações)

<br />

## Aonde modificar?

Entendemos que nem sempre o design do Chatweb satisfaz as necessidades dos clientes, seja por regra de negócio ou por estética. Para tanto, temos o campo *Editor de CSS*, na tela de criação da sala do Chatweb, que cumpre a missão de executar modificações mais avançadas, além daquelas propostas na criação do Chatweb como cor, avatar e logo.

Estas modificações avançadas que iremos ver nessa documentação, o editor está localizado logo depois do campo de escolha do avatar, você deve clicar na seta para expandi-lo, como o exemplo a seguir:

![Campo Editor CSS]({{ '/assets/img/chatweb-modificacoes-css/editor-css.png' | absolute_url }})

<br />

## Cabeçalho

O cabeçalho ou header do Chatweb pode ser modificado das seguintes formas: 

* Podemos modificar a cor de fundo do cabeçalho, ou seja a cor que fica de fundo do logo, com o seguinte código CSS:

```css
.chat-header {
  background: #32bbed !important;
}
```
<br />
Resultado esperado abaixo:

![Alteração cor Header]({{ '/assets/img/chatweb-modificacoes-css/cor-fundo-header.png' | absolute_url }})

<br />

* Podemos também remover o cabeçalho, se você não quiser que apareça o logo e nem o espaço destinado a ele, com o seguinte código CSS:

```css
.chat-header{
  display: none !important;
}
```
<br />
Resultado esperado abaixo:

![Remoção Header]({{ '/assets/img/chatweb-modificacoes-css/remove-header.png' | absolute_url }})

<br />

## Fundo da Conversa

O fundo ou background da conversa do Chatweb pode ser modificado das seguintes formas: 

* Podemos modificar a cor de fundo da conversa, com o seguinte código CSS:

```css
body{
  background-color: #f2ffe6 !important;
}
```
<br />
Resultado esperado abaixo:

![Alteração cor Body]({{ '/assets/img/chatweb-modificacoes-css/cor-fundo-body.png' | absolute_url }})

<br />

* Podemos modificar o fundo inserindo uma imagem, para tanto, você precisará do link da imagem, utilizamos o seguinte código CSS:

```css
body{
  background-image: url(https://i.pinimg.com/236x/8f/ba/cb/8fbacbd464e996966eb9d4a6b7a9c21e--sultan.jpg)  !important;
}
```
<br />
Resultado esperado abaixo:

![Alteração imagem Body]({{ '/assets/img/chatweb-modificacoes-css/imagem-fundo-body.png' | absolute_url }})

<br />

## Balões da Conversa

Os balões da conversa, assim como a sua fonte podem ser modificados das seguintes formas: 

* Podemos modificar o tamanho da fonte, com o seguinte código CSS:

```css
.message-thread .message {
  font-size: 17px !important;
}
```
<br />
Resultado esperado abaixo:

![Alteração tamanho fonte]({{ '/assets/img/chatweb-modificacoes-css/tamanho-fonte.png' | absolute_url }})

<br />

* Podemos modificar a cor da fonte do balão do seu bot, com o seguinte código CSS:

```css
.message-received .message-content {
  color: #7d1e78 !important;
}
```
<br />
Resultado esperado abaixo:

![Alteração tamanho fonte]({{ '/assets/img/chatweb-modificacoes-css/cor-fonte.png' | absolute_url }})

<br />

* Podemos modificar a cor da fonte do balão da resposta do usuário, com o seguinte código CSS:

```css
.message-sent .message-content {
  color: #32bbed !important;
}
```
<br />
Resultado esperado abaixo:

![Alteração tamanho fonte]({{ '/assets/img/chatweb-modificacoes-css/cor-fonte-usuario.png' | absolute_url }})

<br />

* Podemos modificar a cor do balão do seu bot, com o seguinte código CSS:

```css
.message-received .message-content {
  background-color: #32bbed !important;
}
```
<br />
Resultado esperado abaixo:

![Alteração tamanho fonte]({{ '/assets/img/chatweb-modificacoes-css/cor-balao-bot.png' | absolute_url }})

<br />

* Podemos modificar a cor do balão da resposta do usuário, com o seguinte código CSS:

```css
.message-sent .message-content {
  background-color: #32bbed !important;
}
```
<br />
Resultado esperado abaixo:

![Alteração tamanho fonte]({{ '/assets/img/chatweb-modificacoes-css/cor-balao-usuario.png' | absolute_url }})

<br />

**Observação:**

* O nome das classes CSS devem ser exatamente como escritas nessa documentação, assim como o uso do !important em alguns casos, senão o seu código não irá substituir o original do Chatweb e a modificação *não será feita*.