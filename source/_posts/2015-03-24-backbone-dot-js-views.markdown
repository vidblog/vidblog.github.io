---
layout: post
title: "Backbone.js: Views"
date: 2015-03-24 17:39:44 -0300
comments: true
category: javascript
tags:
  - javascript
  - backbonejs
---

Evitar código "macarrão", separar responsabilidades, tratar eventos e atualizar dados vindo do model.<!--more-->

# Backbone.View

No [primeiro post sobre backbone que eu fiz aqui](/javascript/backbone-dot-js-introducao-ao-framework/), falei do básico do básico e não cheguei nem perto de explicar o que a parte de Views pode fazer por você. Agora vamos entrar a fundo nas Views e deixar nosso código *lindo de organizado* e com fácil entendimento.

Então, já sabemos como instanciar uma Backbone.View, agora vamos ver um exemplo de algumas `options` que ela aceita:

{% gist 5b1aac933c7fed18cab7 %}

## Render

O método `render` é, basicamente a função que chamamos para renderizar o conteúdo dentro do `el`:

{% gist 6201b9d1d2d74c673dd0 %}

Lembrando que cada view controla somente sua "área", então dentro da `function` render nós sempre trabalhamos com o `this.el` que é o elemento que a View controla.

Outra coisa legal é que existe um `this.$el` que "herda" as funções do jQuery (vamos usá-lo).

Para exibir a view temos o retorno do `el` já com o conteúdo, ou seja, nosso `View.el` já esta pronto para ser jogado no DOM:

{% gist 27f8c4f81b4664b34370 %}

## Templates

Podemos definir um template para a view ao invés de deixar tudo dentro do método `render`:

{% gist 45c2c0f1d8afd549a660 %}

É usado o `_.template` do [underscore.js](http://underscorejs.org/#template) para gerar o template.

## Events

A parte de events do backbone.js nos permite controlar eventos do DOM e delegá-los para alguma função dentro do escopo da `View`.

{% gist 81825fe2f8db21933e76 %}

O objeto events funciona assim:
A `key` tem o evento seguido do seletor (quando o event é para o `el` não precisa passar o seletor): Ex. `”click .item”`.
O `value` é a função que será chamada quando ocorrer o tal evento: Ex. `"clicked"`.

[Na doc do backbone.js tem uma lista com os eventos que ele ouve.](http://backbonejs.org/#Events-catalog)

# Trabalhando com dados do model

Até agora não colocamos nenhuma informação dinâmica na renderização da View, vamos fazer isso agora.

Vamos usar o mesmo esquema do template, só que com algumas alterações no método `render` e no próprio template (para receber as informações):

{% gist d42ed9195b5ba35561f1 %}

Simples, né?

# E...

Tem bastante coisa legal ainda, como `attributes` defaults para caso a view não receba as variáveis que o template espera, eventos entre views, etc...

A parte de atualizar, adicionar e remover dados vou deixar para o próximo post: `Models & Views`.
