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
<br />

## Configurações
Existem algumas configurações que podem ser realizadas através de atributos da <code class="highlight"><span class="nt">div</span> <span class="s">znv-chat</span></code>:
* [data-embedded](#data-embedded)
* [data-button](#data-button)
* [data-message](#data-message)
* [data-format](#data-format)

### data-embedded
Controla o tipo de chatweb embedded que será utilizado. As opções são:
* button
* button+keyword
* buttonless
* inline

### data-button
Controla o texto a ser exibido quando o [data-embedded](#data-embedded) é do tipo *button+keyword*.

O valor padrão é: 

### data-message

### data-format

## Exemplos
#### [Exemplo de Embedded Chatweb usando as configurações padrão]({{ '/html/chat-embedded/default-config.html' | absolute_url }}):
<iframe src="{{ '/html/chat-embedded/default-config.html' | absolute_url }}"></iframe>
<br />
<br />
