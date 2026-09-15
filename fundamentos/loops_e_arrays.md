# Método map()

Espera um **callback** como argumento. Isso é o mesmo que passar uma outra função como argumento para esta função. 

Por exemplo, vamos dizer que temos uma função `addOne` que recebe uma variável `num` como argumento e retorna essa variável inccrmentada em um, e um array de números `[1, 2, 3, 4, 5]`. Digamos que nós queiramos incrementar todos esses elementos por 1 utilizando nossa função `addOne`.

Ao invés de utilizarmos um loop e iterar todo o array, podemos simplesmente utilizar o método do array `map`.

``` javascript
function addOne(num) {
    return num + 1;
}

const arr = [1, 2, 3, 4, 5];
const mappedArr = arr.map(addOne);

console.log(mappedArr); //saída: [2, 3, 4, 5, 6]
```

`map` retorna um novo array e não modifica o original.

```javascript
//array original inalterado
console.log(arr); //saída: [1, 2, 3, 4, 5]
```

Refatorando o código, já que não estamos utilizando a função `addOne` em mais nenhum outro lugar e é uma função simples. Podemos defini-la como uma função arrow:

```javascript
const arr = [1, 2, 3, 4, 5];
const mappedArr = arr.map((num) => num + 1);

console.log(mappedArr); //saída: [2, 3, 4, 5, 6]
console.log(arr); //saída: [1, 2, 3, 4, 5]
```
