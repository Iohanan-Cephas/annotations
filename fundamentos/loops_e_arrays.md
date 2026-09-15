# Método map()

Espera um **callback** como argumento. Isso é o mesmo que passar uma outra função como argumento para esta função. 

Por exemplo, vamos dizer que temos uma função `addOne` que recebe uma variável `num` como argumento e retorna essa variável incrementada em 1, e um array de números `[1, 2, 3, 4, 5]`. Digamos que nós queiramos incrementar todos esses elementos por 1 utilizando nossa função `addOne`.

Em vez de utilizarmos um loop e iterar todo o array, podemos simplesmente utilizar o método do array `map`.

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

O método `filter` é similar ao `map`. Ele irá iterar cada elemento do array e aplicar uma função **callback** em cada elemento. Entretanto, em vez de transformar todos os valores do array, ele retorna um novo array composto apenas pelos elementos que retornaram um valor `true` na função **callback** (ele literalmente "filtra a pesquisa").

Digamos que temos uma função `isOdd` que retorna `true` se o número passado como argumento for ímpar e `false` caso não seja.

O método `filter` espera que o **callback** retorne, ou `true`, ou `false`. Se retornar `true` o valor é incluso na saída. Se não, não é. Considerando o array do exemplo passado, `[1, 2, 3, 4, 5]`, se quiséssemos remover todos os números pares deste array poderíamos usar o `filter()` dessa forma:

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

# Método reduce()

Por fim, digamos que queremos multiplicar todos os números do nosso array entre si, dessa forma: `1 * 2 * 3 * 4 * 5`. Primeiro, teríamos que declarar uma variável `total` e inicializá-la em 1. Então, iríamos iterar por todo array com um loop `for` e multiplicar o `total` pelo número atual.

Não precisamos fazer tudo isso; nós temos o método `reduce` para esse serviço. Assim, como `map()` e `filter()`, ele espera um **callback**. Entretanto, tem duas diferenças neste método:
- A função **callback** espera dois argumentos ao invés de um. O primeiro argumento é o `accumulator`, que é valor atual do resultado *naquele momento da iteração*. Na primeira vez, esse valor pode ser o `initialValue`, ou o primeiro elemento do array se nenhum `initialValue` for fornecido. O segundo argumento do **callback** é `current` (valor atual), que é o item que está sendo atualmente iterado.
- O `reduce()` em si toma um `initialValue` como um segundo argumento opcional (depois do **callback**). O que ajuda quando não queremos que nosso valor inicial seja o primeiro elemento do array. Assim, se quiséssemos somar todos os números em um array, poderíamos chamar o método `reduce` sem um `initialValue`, mas se quiséssemos somar todos os números em um array e adicionar 10, então declararíamos 10 como `initialValue`.

```javascript
const array = [1, 2, 3, 4, 5];
const productOfAllNums = array.reduce((total, currentItem) => {
    return total * currentItem;
}, 1);

console.log(productOfAllNums); //saída: 120
console.log(array); //saída: [1, 2, 3, 4, 5]
```

Na função acima nós:
- Passamos o **callback**, que é o `(total, currentItem) => total * currentItem`.
- Initicializamos o `total` em `1`no segundo argumento.

# Prática rápida

Reescrever a função `sumOfTripledEvens(array)` utilizando estes 3 métodos.

```javascript
function sumOfTripledEvens(array) {
    let sum = 0;
    for (let i = 0; i < array.length; i++) {
        //verifica se o elemento do array no index i é par
        if (array[i] % 2 === 0) {
            // multiplica esse número por 3
            const tripleEvenNumber = array[i] * 3;
            // adiciona esse número triplicado ao total
            sum += tripleEvenNumber;
        } 
    }
    return sum;
}
```

<details>
<summary>Solução</summary>

```javascript
function sumOfTripledEvens(array) {
  return array
    .filter((num) => num % 2 === 0)
    .map((num) => num * 3)
    .reduce((acc, curr) => acc + curr);
}
```
