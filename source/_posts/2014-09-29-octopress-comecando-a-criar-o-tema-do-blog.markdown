---
layout: post
title: "Octopress: Começando a criar o tema do blog"
date: 2014-09-29 02:03:40 -0300
comments: true
category: frameworks
tags:
  - html
  - css
  - javascript
---


Quando comecei a ideia do blog já tinha em mente criar um tema para poder disponibilizar, e com o Octopress é lindo de fazer isso.
Além do tema, pensei em disponibilizar tudo que fosse criando no blog, neste post vou mostrar como criei o tema e como estou usando ele aqui.<!--more-->

## Sobre o Octopress

[Octopress](http://octopress.org/) é um framework por cima do [Jekyll](http://jekyllrb.com/) que é um gerador de páginas estáticas em Ruby, que resumindo, permite a criação de um blog somente com HTML, CSS, e Javascript. O que o octopress faz é auxiliar (basicamente por rake tasks) nas tarefas de criar novos posts, páginas e principalmente fazer deploy.
Criar um blog com octopress é muito simples, basta seguir os passos da [documentação do site](http://octopress.org/docs/) que é sucesso.

Aqui no blog estou usando o [github pages](https://pages.github.com/) como “hospedagem” e o próprio octopress tem uma task para fazer deploy lá.

## Criando um tema para Octopress

Vamos logo ao assunto principal, né?!
Criar um tema no octopress é relativamente simples, mas é claro, se você quiser disponibilizar ele bonitinho para galera (que é o ideal), a história muda, mas não muito.
É o que eu estou começando a fazer com o tema aqui do blog.

O legal é que da para usar o tema `classic` (que é o default) como base, e editar os arquivos das pastas `sass` e `source`. Quando finalizar o tema, o ideal é colocar essas duas pastas em `.theme/nome_do_tema` para poder de fato instalar ele no seu blog com os comandos `rake install[nome_do_tema]` e `rake generate`. Com o próprio exemplo do tema padrão da pra aprender e qualquer coisa é só olhar as [docs do liquid](https://github.com/Shopify/liquid/wiki), a “markup language”, usada no Jekyll.

Simples né?

## EMD Theme

<figure>
![EMD Theme Screenshot]({{ root_url }}/images/posts/emd-theme-preview.png)
</figure>

EMD Theme é o nome que dei ao tema do blog, o design é inspirado no [Medium](http://medium.com) e os [PDS’s estão em um repositório separado](https://github.com/vidblog/emd-theme-layout).

Já o tema esta [**aqui**](https://github.com/vidblog/emd-theme) e para instalar existe alguns passos a mais que o normal, mas pretendo organizar ainda.

O tema foi pensado para ser focado no texto, sem muita coisa. Tem o básico para entregar o conteúdo com qualidade de leitura.

A graça de fazer o tema é ele ser usado em outros blogs, o que - por enquanto - não é 100% indicado, pois estou criando muitas coisas novas nele em pouco tempo e também organizando tudo. Mas quem quiser ja pode dar palpites e principalmente ajudar. É só  criar um **pull request**. :)

Ainda falta bastante coisa que eu quero adicionar e junto com o tema algumas rakes tasks e configurações no Octopress.


Vou falar mais sobre Octopress e Jekyll e deixar o tema completo para uso.


Abraços!
