---
layout: post
title: Javascript – Qual a diferença de usar for ou forEach
feature-img: "assets/img/javascript-cover.png"
tags: [javascript,dev]
---

Se recentemente você começou estudar Javascript, ou utiliza a linguagem há algum tempo, já deve ter se questionado a diferença entre usar for (loop clássico) e forEach (método em arrays).

Neste post, gostaria discutir as vantagens de utilização dos respectivos loops. Vamos lá ;)

## Preparando o código

{% highlight js %}
var i, values = [], sum = 0;

for (i = 0; i < 10000; i++) {
    values[i] = i;
}

function add(val) {
    sum += val;
}

// for simples
for (i = 0; i < values.length; i++) {
    add(values[i]);
}

// forEach
values.forEach(add);
{% endhighlight %}


## Performance vs Legibilidade do Código

Quanto a performance a diferença pode ser imperceptível em sua aplicação, no entanto em boa parte das utilizações, o loop clássico for é mais rápido! Caso queira comparar os resultados, segue testes realizados por desenvolvedores da comunidade [Clique Aqui](https://jsperf.com/for-vs-foreach) . 

Como dito esse desempenho pode não fazer diferença na sua aplicação, e o uso excessivo de for pode tornar o código mais difícil de ler. Com o uso de forEach , teremos menos linhas de código, e eliminamos as variáveis temporárias de contador. Tornando o código mais fácil de ler e aumentando sua manutenibilidade.

## Quando utilizar o laço For?

Imagine uma lista longa de produtos e, assim que encontrar um que corresponda a alguns critérios, quero realizar alguma ação. Com a utilização do forEach(), iria iterar sobre cada produto, resultando em iterações desnecessárias, potencialmente causando problemas de desempenho, dependendo do tamanho da matriz.

Com um loop for, você tem a capacidade de impedir que o loop continue até o fim da interação. Por exemplo:

{% highlight js %}
for (var i = 0; i < produtos.length; i++) {
  if (comparaCriterios(products[i])) {
    facaAlgo();
    break;
  }
}
{% endhighlight %}

No exemplo acima utilizamos a palavra chave **break**, para podemos impedir que o loop continue assim que encontramos o que procurávamos. A partir do *ES6*, há um novo método para encontrar um elemento, que é bem semelhante ao que fazemos no código acima. Este método é o [find()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find).

## Conclusão

Esse post é uma abordagem direta para podermos analisar os cenários de utilização dos loops for e forEach na linguagem JavaScript. A prática e estudo constante dos recursos da linguagem contribuem para a escrita de códigos limpos e eficientes.

O post foi baseado no artigo [The for Loop vs. forEach in JavaScript](https://thejsguy.com/2016/07/30/javascript-for-loop-vs-array-foreach.html) onde o autor analisa mais a fundo o desempenho dos loops.






