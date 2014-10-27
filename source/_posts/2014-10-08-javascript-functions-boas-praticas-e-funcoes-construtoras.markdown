---
layout: post
title: "Javascript functions: boas práticas e funções construtoras"
date: 2014-10-08 19:18:00 -0300
comments: true
category: javascript
tags:
  - javascript
---

Criar uma função é muito fácil, é só aprender a sintaxe básica e mandar bala, mas pra que? Vamos aprender o básico sobre esse assunto com uma pequena introdução sobre como utilizar funções em javascript.<!--more-->

> Generally speaking, a function is a "subprogram" that can be called by code external (or internal in the case of recursion) to the function. Like the program itself, a function is composed of a sequence of statements called the function body. Values can be passed to a function, and the function can return a value. ([Ref](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions))


## Criando UMA função:

O primeiro ponto que procuro pensar é em criar funções que façam uma única coisa.

Um exemplo: 
```js
function getFullName(name, lastName) {
     return name + “ “ + lastName;
}
```

Forma de invocar:
```js
getFullName(“Nome”, “Sobrenome”); // “Nome Sobrenome"
```

## Funções em Objetos

No javascript, praticamente, tudo é um objeto e um objeto pode ter funções:
```js
var myObject = {
     getFullName: function(name, lastName) {
          return name + “ “ + lastName;
     }
}
```

A forma de invocar a função é bem simples:
```js
myObject.getFullName(“Nome”, “Sobrenome”); // “Nome Sobrenome"
```

### Tomando alguns cuidados

Quando chamamos a função acima deixamos fácil a quebra de encapsulamento e permitimos a alteração do atributo `getFullName`:
```js
// Alterando o valor de getFullName:
myObject.getFullName = function() {
          return “Nome”;
}

// Chamando a função:
myObject.getFullName(“Nome”, “Sobrenome”); // “Nome"
```

Pra resolver isso, podemos criar uma função de forma que ela mantenha suas variáveis dentro do seu escopo:
```js
var fullName = function(name, lastName) {
     var first = name,
           last = lastName;
     
     return {
          get: function() {
               return first + “ “ + last;
          }
     };
};
```

Para chamar essa função é mais ou menos assim:
```js
fullName(“Nome”, “Sobrenome”).get(); // “Nome Sobrenome"
```

Não existe a melhor forma, mas é um exemplo de como retornar somente a função e não permitir a alteração dos atributos como no último exemplo.

### Organizando seu código

Vale lembrar a importância que existe em organizar seu código.
No front-end existem as camadas de `HTML`, `CSS` e `Javascript` e não devemos misturar responsabilidades de uma camada com a outra.

Porém, ainda encontramos isso hoje em dia:
```html
<a href=“#” style=“color: red” onClick=“clickFunction()”>Link</a>
```

Em uma linha temos html, css e javascript. *Isso é bem ruim*.

## Funções construtoras

Existe o conceito de orientação a objeto no javascript e funções construtoras é uma parte.
Podemos chamar uma função com `new` na frente e isso instancia essa função e executa seu construtor. Mais ou menos assim:
```js
var Person = function(name, lastName) {
     this.name = name;
     this.lastName = lastName;
};

// Chamando a função com new
var person = new Person(“Nome”, “Sobrenome”);
var person2 = new Person(“Nome 2”, “Sobrenome 2”);
```

Ao fazer isso, guardamos o retorno do construtor na variável `person` e, através dela, podemos acessar as variáveis que foram criadas dentro do construtor:
```js
console.log(person.name); // “Nome”
console.log(person.lastName); // “Sobrenome”

console.log(person2.name); // “Nome 2”
console.log(person2.lastName); // “Sobrenome 2" 
```

Uma boa prática é que esse tipo de função comece com letra maiúscula, como se fosse uma classe em outras linguagens.
__PS. No EcmaScript 6 (ES6 Harmony) teremos um `class` :).__

### Criando funções usando prototype

No exemplo acima, poderíamos criar uma função direto dentro do construtor, mas não é uma boa ideia, pois para cada nova instancia as funções seriam criadas novamente. Um exemplo:

```js
var Person = function(name, lastName) {
     this.name = name;
     this.lastName = lastName;
     this.getFullName = function() {
          return this.name + “ “ + this.lastName;
     };
}; 

var person = new Person(“Nome”, “Sobrenome”);
var person2 = new Person(“Nome 2”, “Sobrenome 2”);

person.getFullName(); // “Nome Sobrenome"
person2.getFullName(); // “Nome2 Sobrenome2"
```

Feito assim, temos uma função `getFullName` na variável `person` e outra na variável `person2`. Usando `prototype` a função será criada dentro do objeto `Person`:
```js
var Person = function(name, lastName) {
     this.name = name;
     this.lastName = lastName;
};


Person.prototype.getFullName = function() {
     return this.name + “ “ + this.lastName;
};

var person = new Person(“Nome”, “Sobrenome”);
var person2 = new Person(“Nome 2”, “Sobrenome 2”); 

person.getFullName(); // “Nome Sobrenome"
person2.getFullName(); // “Nome2 Sobrenome2" 
```

Tranquilo, né?

## Ufa...

Existem diversas formas de trabalhar com funções em javascript e vou me aprofundar em algumas durante a vida deste blog. Por hora, aprendemos como criar e chamar uma função das maneiras mais comuns (e simples) e vale lembrar a importância de avaliar como você vai organizar seu código, não tem uma forma “certa”.
