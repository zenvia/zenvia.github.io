---
layout: documentation
title: Mensagem de boas vindas no Chatweb
description: 
categories: webchat
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
* [Chatbot](#chatbot)
* [Acessando a tela](#acessando-a-tela)
* [Configuração do design do Chatweb](#configuração-do-design-do-chatweb)

<br />

## Chatbot

A mensagem de boas vindas é a primeira mensagem que será exibida para o usuário, ou seja,
será exibida quando o usuário abrir o Chatweb da [**Plataforma de Chatbots Zenvia**](../)
[integrado em seu site](../chat-embedded) conforme a mensagem abaixo.

<div class="center">
  <iframe src="{{ '/html/chatweb-boas-vindas/type-button.html' | absolute_url }}" scrolling="no"></iframe>
</div>

<br />

## Acessando a tela

A configuração dessa mensagem de boas vindas é feita através da tela de configuração do design do Chatweb. Para acessar esta tela, clique no menu *Integrações* e em seguida em *Chatweb*.

![Menu]({{ '/assets/img/chatweb-boas-vindas/menu-integracoes.png' | absolute_url }})

![Tela Integrações]({{ '/assets/img/chatweb-boas-vindas/integracoes.png' | absolute_url }})

<br />

## Configuração do design do Chatweb

No passo 3 da tela de configuração do design do Chatweb é possível configurar a mensagem de boas vindas.

![Tela Chatweb - Passo 3]({{ '/assets/img/chatweb-boas-vindas/chatweb-passo3.png' | absolute_url }})

**Observação:**

* A mensagem de boas vindas é obrigatório quando o chatbot começa com uma interação de usuário.

<br />

Há outras formas de acessar a tela de configuração do design do Chatweb.

A primeira é através do modal de criação de novo chatbot.

![Modal Novo Chatbot]({{ '/assets/img/chatweb-boas-vindas/novo-chatbot.png' | absolute_url }})

A segunda é através do modal de publicação do chatbot.

![Modal Publicar Chatbot]({{ '/assets/img/chatweb-boas-vindas/publicar-chatbot.png' | absolute_url }})

