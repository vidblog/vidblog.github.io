---
layout: post
title: "Backbone.js: Introdução ao framework"
date: 2015-01-30 17:48:53 -0200
comments: true
category: javascript
tags:
  - javascript
  - backbonejs
---

Sem muita mágica, o Backbone.js te ajuda a estruturar melhor seu javascript com conceitos de Models e Views. Além de ajudar a interagir com API’s (backend).<!--more-->

> With Backbone, you represent your data as Models, which can be created, validated, destroyed, and saved to the server. Whenever a UI action causes an attribute of a model to change, the model triggers a "change" event; all the Views that display the model's state can be notified of the change, so that they are able to respond accordingly, re-rendering themselves with the new information.
([Ref](http://backbonejs.org/))

## Backbone.js

Normalmente, quando iniciamos uma aplicação ou grande parte fica no backend e o javascript fica responsável por adicionar um efeito ou outro no DOM (plugins de jQuery rs) ou, ainda, consumimos uma API e exibimos (tratamos) as informações no front-end (tudo com jQuery).  Hoje em dia, isso é cada vez mais criticado e técnicas para estruturar melhor o javascript são criadas constantemente (a maioria das vezes com base em conceitos de backend).

É ai que o backbone.js entra, cada _View_ é responsável por sua "área" dentro do site, evitando aqueles seletores jQuery espalhados pela aplicação toda.

### Partiu codar

Para começar a usar o backbonejs é bem simples. Para esse post precisamos de um html qualquer que tenha uma div (ou o que você quiser) com o id `#main` (só porque usei esse id para explicar a parte de Views) e, claro, do backbonejs (que tem dependência do [underscore](http://underscorejs.org/)  >= 1.5.0 e jQuery).

## Views

As Views são responsáveis por exibir informações recebidas do Model e fazer modificações no DOM. A ideia é que para cada “área” do site deve existir uma View responsável por alterar somente o que estiver dentro dessa “área”.

### Backbone.View

{% gist 0602bfc1c0d69126faf4 %}

O que esse código faz é imprimir na tela `<p>Backbone View :)</p>`, onde `el` (`#main`) é a área que essa View cuida.

## Models

É parte de representação de dados, que nos permite interagir com API’s, validando, excluindo e gravando dados.

### Backbone.Model

{% gist 00bac046d01286796003 %}

Está é a maneira mais simples de trabalhar com o Model, usando os métodos `get` e `set` para tratar as informações.

*Num próximo post vou focar mais em como trabalhar com Views e Models em conjunto.*

## Router & History

Quando criamos uma aplicação baseada em javascript, perdemos o histórico de ações e navegação que ocorre no browser. Por exemplo, se você tratar via javascript um link que exibe algum conteúdo na tela, você pode perceber que não existe uma maneira de chegar até essa parte da aplicação através de uma url.

### Backbone.Router

Com a parte de rotas do backbone, podemos basear nossa aplicação por url’s.

{% gist d2d0e12c75ffcc5b2ab3 %}

Nesse exemplo, definimos um Router e passamos uma rota `home` <br /> (ex: http://endereco/#home) através do objeto `routes` onde a chave é o caminho e o valor é a função que será invocada quando essa rota for acessada.

Para iniciar as rotas, precisamos chamar a função `start` do `Backbone.History: `Backbone.history.start({root: “home"})` (A opção root define qual rota será a primeira a ser chamada).

E para navegar até uma rota via código temos o método <br /> `navigate`: `router.navigate(“home”, {trigger: true})`, onde o primeiro argumento é a rota que você deseja ir e o segundo são options. <br /> A option `trigger: true` faz o update da url no navegador.

Isso é bem o básico sobre as rotas no backbone. Podemos,  por exemplo, passar uma opção (`{pushState: true}`) para o `Backbone.history.start` que remove o `#`  das url’s habilitando a API de History do HTML5 (que fica muito melhor).


## Collections e outras coisas...

Existe muuuita coisa legal no backbone que eu não cheguei nem perto de explicar. Esse post é apenas uma introdução (bem) básica de como podemos começar a usar a estrutura do backbone sem medo.

*Collections, Models, Views, Router… pretendo criar posts para cada uma dessas partes.*
