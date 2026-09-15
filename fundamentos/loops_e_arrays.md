# Método map()

Espera um **callback** como argumento. Isso é o mesmo que passar uma outra função como argumento para esta função. 

Por exemplo, vamos dizer que temos uma função `addOne` que recebe uma variável `num` como argumento e retorna essa variável incrementada em 1, e um array de números `[1, 2, 3, 4, 5]`. Digamos que nós queiramos incrementar todos esses elementos por 1 utilizando nossa função `addOne`.

Ao invés de utilizarmos um loop e iterar todo o array, podemos simplesmente utilizar o método do array `map`.

``` javascript
function addOne(num) {
    return num + 1;
}

const array = [1, 2, 3, 4, 5];
const mappedArray = array.map(addOne);

console.log(mappedArray); //saída: [2, 3, 4, 5, 6]
```

`map` retorna um novo array e não modifica o original.

```javascript
//array original inalterado
console.log(array); //saída: [1, 2, 3, 4, 5]
```

Refatorando o código, já que não estamos utilizando a função `addOne` em mais nenhum outro lugar e é uma função simples. Podemos defini-la como uma **arrow function**:

```javascript
const array = [1, 2, 3, 4, 5];
const mappedArray = array.map((num) => num + 1);

console.log(mappedArray); //saída: [2, 3, 4, 5, 6]
console.log(array); //saída: [1, 2, 3, 4, 5]
```

# Método filter()

O método `filter` é similar ao `map`. Ele irá iterar cada elemento do array e aplicar uma função **callback** em cada elemento. Entretanto, ao invés de transformar todos os valores do array, ele retorna um novo array composto apenas pelos elementos que retornaram um valor `true` na função **callback** (ele literalmente "filtra a pesquisa").

Digamos que temos uma função `isOdd` que retorna `true` se o número passado como argumento for ímpar e `false` caso não seja.

O método `filter` espera que o **callback** retorne, ou `true`, ou `false`. Se retornar `true` o valor é incluso na saída. Se não, não é. Considerando o array do exemplo passado, `[1, 2, 3, 4, 5]`, se quiséssemos remover todos os números pares deste array poderíamos usar o `filter()`dessa forma:

```javascript
function isOdd(num) {
    return num % 2 !== 0;
}

const array = [1, 2, 3, 4, 5];
const oddNums = array.filter(isOdd);

console.log(oddNums); //saída: [1, 3, 5]
console.log(array); //saída: [1, 2, 3, 4, 5]
```

- `filter()` irá iterar por `array` e passar todo elemento para o **callback** `isOdd`.
- `isOdd` retorna `true` para todo elemento do array que for ímpar.
- Se for um número par, `isOdd` retorna `false` e o elemento não é incluído na saída.