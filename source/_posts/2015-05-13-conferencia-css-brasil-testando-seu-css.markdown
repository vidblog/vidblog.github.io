---
layout: post
title: "Conferência CSS Brasil: Testando seu CSS"
date: 2015-05-13 15:23:10 -0300
comments: true
category: css
tags:
  - css
  - testes
---

No dia 9 de maio rolou a 1ª Conferência CSS Brasil e vou transformar em posts o que vi por lá! E o primeiro post será sobre a palestra do Eduardo Matos.<!--more--> ([Slides](http://pt.slideshare.net/100000187316458/testes-de-css))

## Pra que testar CSS?

Num projeto grande, com uma equipe grande e muita coisa rolando ao mesmo tempo, a chance de aparecer erros aumenta muito. Temos diversas práticas para minimizar erros e **testar o CSS nos permite garantir mais uma camada**.

## Formas de testar seu CSS

Existem várias formas de testar seu CSS, assim como vários tipos de testes:

### CSSLint

<figure>
  <img src="{{ root_url }}/images/posts/csslint.png" />
</figure>

Acredito que seja o mais simples. O [CSSLint](http://csslint.net/) vai avaliar as linhas do seu código e te retornar uma lista de possíveis erros (assim como o JSLint).

Podemos usar o CSSLint com algum task runner (grunt) e tornar esse teste bem prático ([Informações sobre integração](https://github.com/CSSLint/csslint/wiki/Build-System-Integration)).

### Style Stats

<figure>
  <img src="{{ root_url }}/images/posts/stylestats.png" />
</figure>

[Esse cara](http://www.stylestats.org/) é mais um feedback do seu CSS. Com ele temos um relatório sobre as regras do seu css, possibilitando visualizar de maneira prática se o arquivo está muito complexo ou tem cores semelhantes que poderiam virar uma única, por exemplo.

*Também dá pra integrar com o algum task runner.*

## Testando Layouts

Essa parte, pra mim, é a mais interessante, garantir de maneira prática que o layout não quebrou é sensacional.

Existem algumas ferramentas para te ajudar nessa tarefa, mas vou falar sobre uma: [BackstopJS](http://garris.github.io/BackstopJS/).

O BackstopJS faz um tipo de teste chamado de “teste de regressão”. 

### BackstopJS

<figure>
  <img src="{{ root_url }}/images/posts/backstopjs.png" />
</figure>

Minha ideia aqui não é fazer um tutorial e sim falar sobre as vantagens e desafios de implementar esse tipo de teste no projeto.

O que um teste de regressão faz é - basicamente - tirar prints do layout atual para comparar com uma nova print (já com suas alterações) e caso tenha diferenças entre os prints os testes não vão passar.

O BackstopJS disponibiliza uma interface bem legal, similar ao [mocha](http://mochajs.org/) ou [jasmine](http://jasmine.github.io/) que ja conhecemos. 

Eu indico o mesmo [link que tem no slide](https://css-tricks.com/automating-css-regression-testing/). Não é tão simples, mas esse link explica exatamente tudo que você precisa saber para começar a usar e testar seu CSS magicamente.

## Quem deve criar os testes?

Por mais que a parte do código fique na mão do front-end, o designer também precisa participar dessa camada (na minha opinião). Sua função seria analisar para evitar excessos e em alguns casos até corrigir testes.
