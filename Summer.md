# JavaScript ES6 - Higher Order Functions - map e reduce
## O que vamos aprender?
Hoje você vai aprender duas poderosas (e complexas) *Higher-Order Functions*: array.map e o array.reduce

Essas duas funções são utilizadas para manipular e criar Arrays. elas têm o intuito de deixar seu código mais legível, conciso e expressivo.

## Você será capaz de:
- Manipular e construir Arrays

- Tratar dados em Arrays de maneira mais limpa e eficaz

- Indexar dados de um Array com array.map

- Agregar dados com array.reduce

## Porque isso é importante?
Como já visto anteriormente as *HOFs* ajudam bastante na redução da quantidade de código escrito e na legibilidade deste.

O map e o reduce são duas *HOFs* muito importantes, pois elas facilitam muito na criação e manipulação de arrays. Com elas, você fará muito mais operações com muito menos linhas.
## Conteúdos
### Map

A função map possui a mesma estrutura das outras HOFs, ela transforma todos os itens de um array para outro array!

![Alt Text](https://miro.medium.com/max/1000/1*4EGwsCicbWJeml2aAm714A.gif)

Para entender melhor vamos imaginar um grupo de RPG representado no seguinte array:
```js
const party = [
  { name: 'Daniel', class: 'Paladino', lvl: 15 },
  { character: 'Patolino', class: 'Mago', lvl: 20 },
  { character: 'Conan', class: 'Bárbaro', lvl: 21 },
  { character: 'Arsenal', class: 'Mestre', lvl: 42 },
];

```

Se você quisesse subir o `lvl` de todos os personagens, utilizando o for você faria da seguinte maneira:
```js
const party = [
  { character: 'Daniel', class: 'Paladino', lvl: 15 },
  { character: 'Patolino', class: 'Mago', lvl: 20 },
  { character: 'Conan', class: 'Bárbaro', lvl: 21 },
  { character: 'Arsenal', class: 'Mestre', lvl: 42 },
];
let lvlUp = [];
for (let i = 0; i < party.length; i += 1) {
  lvlUp.push(party[i].lvl + 1);
}

console.log(lvlUp); // [16, 21, 22, 43]
```

Agora com o map
```js
const party = [
  { character: 'Daniel', class: 'Paladino', lvl: 15 },
  { character: 'Patolino', class: 'Mago', lvl: 20 },
  { character: 'Conan', class: 'Bárbaro', lvl: 21 },
  { character: 'Arsenal', class: 'Mestre', lvl: 42 },
];

const lvlUp = party.map(partyMembe => partyMembe.lvl + 1);

console.log(lvlUp); // [16, 21, 22, 43]
```

Veja que o for foi substituído por apenas uma linha de código.

A função adicionou 1 a todos os valores de lvl e retornou um array novo com cada um dos valores. Note que o tamanho do array party e lvlUp é o mesmo (quatro elementos).

Outro exemplo que podemos fazer é juntar o character com sua respectiva class. Veja como ficaria com o for:
```js
const party = [
  { character: 'Daniel', class: 'Paladino', lvl: 15 },
  { character: 'Patolino', class: 'Mago', lvl: 20 },
  { character: 'Conan', class: 'Bárbaro', lvl: 21 },
  { character: 'Arsenal', class: 'Mestre', lvl: 42 },
];

let member = [];
for (let i = 0; i < party.length; i += 1) {
  member.push(`${party[i].character} ${party[i].class}`);
}

console.log(member);
```

Já com o Map:
```js
const party = [
  { character: 'Daniel', class: 'Paladino', lvl: 15 },
  { character: 'Patolino', class: 'Mago', lvl: 20 },
  { character: 'Conan', class: 'Bárbaro', lvl: 21 },
  { character: 'Arsenal', class: 'Mestre', lvl: 42 },
];

const member = party.map(partyMembe => `${partyMembe.character} ${partyMembe.class}`);

console.log(member); // ["Daniel Paladino", "Patolino Mago", "Conan Barbaro", "Arsenal Mestre"]
```

#### Vamos Praticar um pouco!
1. dobre o lvl dos membros

2. crie um array que junta primeiro a class e depois o character dos membros

3. crie um array que retorne apenas as class 

Agora imagine que temos dois arrays, uma para o personagem e outra para sua defesa.
```js
const character = ['Daniel', 'Patolino', 'Conan', 'Arsenal'];
const armor = [20, 12, 16, 25];
```

Com o .map podemos podemos unir os dois arrays em um só, dessa forma teremos o array:
```js
const charArmor = [{ Daniel: 20 }, ...];
```

Antes de prosseguir, tente pensar como você faria para resolver esse problema. Vale lembrar que as HOFs podem receber vários parâmetros, não apenas o elemento que esta interada!
```js
const character = ['Daniel', 'Patolino', 'Conan', 'Arsenal'];
const armor = [20, 12, 16, 25];

const charArmor = (listChar, listArmor) => {
  return listChar.map((char, i) => ({ [char]: listArmor[i] }));
};

const armorClass = charArmor(character, armor);

console.log(armorClass);
```

Lembre-se que o .map não altera o array, ele interage com os elementos e retorna um novo array.

### Vamos praticar mais um pouco!
Para fixar melhor o map, transforme os for a seguir utilizando o .map:

1. 
```js
const atack = [15, 11, 9, 1, 20];

const result = [];

for (let i = 0; i < atack.length; i += 1) {
  if (atack[i] > 10) {
    result.push('hit');
  } else {
    result.push('miss');
  }
}

console.log(result); //[hit, hit, miss, miss, hit]
```

2.
```js
const character = [
  { class: 'Mago', lvl: 14 },
  { class: 'Druída', lvl: 13 },
  { class: 'Clériga', lvl: 3 },
  { class: 'Ladino', lvl: 9 },
  { class: 'Guerreira', lvl: 11 },
];

let classLvl = [];

for (let i = 0; i < character.length; i += 1) {
  classLvl.push(`${character[i].class} de nível ${character[i].lvl}`);
}

console.log(classLvl);
```

## Reduce 
Diferente das outras *HOF's* o Reduce precisa receber um parâmetro a mais, o acumulador, também chamado de acc, ele é responsável por acumular todos os valores e devolver o resultado final.

![Alt Text](https://miro.medium.com/max/1000/1*dhTC_FFgiH3mKROrnDj12w.gif)

Para entender melhor, vamos imaginar que você quer calcular o dano que seu grupo deu no inimigo, para isso vamos usar o seguinte array:
```js
const character = [
  { golpe: 'Espada Justiceira', dano: 24 },
  { golpe: 'Bola de Fogo', dano: 22 },
  { golpe: 'Meteoro de Pégasus', dano: 25 },
  { golpe: 'Choque do Trovão', dano: 17 },
];
```

Com o for seria feito da seguinte maneira:
```js
const dmg = [
  { golpe: 'Espada Justiceira', dano: 24 },
  { golpe: 'Bola de Fogo', dano: 19 },
  { golpe: 'Meteoro de Pégasus', dano: 25 },
  { golpe: 'Choque do Trovão', dano: 17 },
];

let totalDmg = 0;

for (let i = 0; i < dmg.length; i++) {
  totalDmg = totalDmg + dmg[i].dano;
}

console.log(totalDmg);
```

Veja que foi preciso setar uma variável com o valor inicial de 0, e a cada interação do for ele pega o valor atual e adiciona o valor do `dano`. Agora veja como fazer com o reduce.
```js
const dmg = [
  { golpe: 'Espada Justiceira', dano: 24 },
  { golpe: 'Bola de Fogo', dano: 18 },
  { golpe: 'Meteoro de Pégasus', dano: 25 },
  { golpe: 'Choque do Trovão', dano: 17 },
];

const totalDmg = dmg.reduce((valorAcumulador, valorArray) => valorAcumulador + valorArray.dano, 0);

console.log("total de dano:", totalDmg); // total de dano: 84
```

A sintaxe utilizada para o reduce é a seguinte:
```js
  array.reduce(function(acc, arr), valorInicial)
```

Nesse exemplo, o primeiro parâmetro, a função, recebe o `valorAcumulador` que a cada interação é adicionado o `valorArray` referente ao `dano`.

No final da função temos o segundo parâmetro o `valorInicial` ele se relaciona com o que queremos receber no final. Como queremos receber um número que representa a soma de todos os danos, passamos o `0` para iniciar a soma.

* Experimente trocar o `0` para outro valores, como por exemplo `5` ou `-10` e veja o que acontece.

Agora imagine que você quer separar quem causou uma quantidade par, e quem causou uma quantidade ímpar de dano. 
```js
const dmg = [
  { golpe: 'Espada Justiceira', dano: 24 },
  { golpe: 'Bola de Fogo', dano: 18 },
  { golpe: 'Meteoro de Pégasus', dano: 25 },
  { golpe: 'Choque do Trovão', dano: 17 },,
];

const grupDmg = dmg.reduce((acc, arr) => {
  const danoParOuImpar = arr.dano %2 === 0 ? 'par' : 'impar';

  acc[danoParOuImpar].push(arr); // valores pares serão empurrados para o valor de par do acumulador e ímpares para o de ímpar 
  return acc; // O acumulador é retornado da primeira para a segunda interação e assim respectivamente
}, { par: [], impar: []}); // valor inicial de acc

console.log(grupDmg);
/*Object {
  impar:[Object {
    dano: 25,
    golpe: "Meteoro de Pégasus"
  }, Object {
    dano: 17,
    golpe: "Choque do Trovão"
  }],
  par: [Object {
    dano: 24,
    golpe: "Espada Justiceira"
  }, Object {
    dano: 18,
    golpe: "Bola de Fogo"
  }]
}*/
```

Repare que agora como queremos que o retorno seja um objeto, o valor inicial é passado para o objeto com as chaves que queremos retornar!

### Vamos praticar mais um pouco!

Ainda usando o array:
```js
const dmg = [
  { golpe: 'Espada Justiceira', dano: 24 },
  { golpe: 'Bola de Fogo', dano: 18 },
  { golpe: 'Meteoro de Pégasus', dano: 25 },
  { golpe: 'Choque do Trovão', dano: 17 },
];
```
1. Crie um reduce que calcule a soma do dano recebido por todos os golpes, sabendo que o inimigo absorve 5 do dano total.

2. Crie um reduce que agrupe em um objeto os golpes que causaram 20 ou mais pontos de dano e os que causaram menos!

Dica: use um array que agrupe os golpes maiores e menores.

#### map + reduce

Podemos também usar as duas *HOFs* que aprendemos hoje.
Imagine que você queira dobrar o dano e depois totalizar o dano causado. Como você faria isso?
```js
const dmg = [
  { golpe: 'Espada Justiceira', dano: 24 },
  { golpe: 'Bola de Fogo', dano: 18 },
  { golpe: 'Meteoro de Pégasus', dano: 25 },
  { golpe: 'Choque do Trovão', dano: 17 },
];

const doubleDamage = dmg.map (d => d.dano *2);
const totalDmg = doubleDamage.reduce ((acc, arr) => acc + arr, 0);

console.log('20 é 20:', doubleDamage); // "20 é 20:" [48, 36, 50, 34]
console.log('total de dano:', totalDmg)// "total de dano:" 168
```

Porém, podemos também juntar as duas *HOFs* em um único comando:

```js
const doubleDamage = dmg.map (d => d.dano *2).reduce ((acc, arr) => acc + arr, 0);

console.log('dano total:', doubleDamage);// "dano total:" 168
```

O resultado do map é um array, que encadeado com o reduce é como se fizéssemos:
```js
[48, 36, 50, 34].reduce ((acc, arr) => acc + arr, 0);
```

## Exercícios

Vamos testar o que aprendemos?

1. Crie uma string com os nomes, classes e golpe de todos os personagens. 

Retorne a string da seguinte maneira

`name`, o `class` usou `golpe`
```js
const party = [
  {
    name: 'Daniel',
    class: 'Paladino',
    lvl: 15,
    defesa: 20,
    ataque: {
      golpe: 'Espada justiceira',
      dano: 35,
    },
   },
   {
     name: 'Patolino',
     class: 'Mago',
     lvl: 20,
     defesa: 12,
     ataque: {
       golpe: 'Bola de fogo',
       dano: 32,
      },
    },
   {
    name: 'Conan',
    class: 'Barbaro',
    lvl: 21,
    defesa: 16,
    ataque: {
      golpe: 'Golpe fulminante',
      dano: 27,
    },
   },
   {
    name: 'Arsenal',
    class: 'Mestre',
    lvl: 42,
    defesa: 25,
    ataque: {
      golpe: 'Vingadora Sagrada',
      dano: 42,
    },
   },
];
```

2. Crie uma string que contenha os golpes e seus respectivos danos. Se o valor do acerto for igual a 20, dobre o valor do dano.

Retorne a string da seguinte maneira:

`golpe` causou `dano` pontos de dano
```js
const ataque = [
  { golpe: 'Espada justiceira', acerto: 20, dano: 24 },
  { golpe: 'Bola de fogo', acerto: 7, dano: 18 },
  { golpe: 'Meteoro de pegasus', acerto: 9, dano: 25 },
  { golpe: 'Choque do trovão', acerto: 14, dano: 17 },
  { golpe: 'Force Push', acerto: 18, dano: 17 },
  { golpe: 'Detroid Smash', acerto: 20, dano: 26 },
];
```

3. Sendo o acerto 11 ou mais, crie uma string dizendo se o golpe acertou ou falhou. Caso acerte, passe o valor do dano.

Retorne a string da seguinte maneira:

`golpe` acertou e causou `dano` pontos de dano

`golpe` falhou 
```js
const ataque = [
  { golpe: 'Espada justiceira', acerto: 20, dano: 24 },
  { golpe: 'Bola de fogo', acerto: 7, dano: 18 },
  { golpe: 'Meteoro de pegasus', acerto: 9, dano: 25 },
  { golpe: 'Choque do trovão', acerto: 14, dano: 17 },
  { golpe: 'Force Push', acerto: 18, dano: 17 },
  { golpe: 'Detroid Smash', acerto: 2, dano: 26 },
];
```

4. Utilizando o reduce, calcule a soma do dano referente ao seguinte array. Sabendo que o inimigo absorve 3 do dano de **cada** golpe
```js
const dano = [24, 18, 25, 17, 43, 27, 32, 35];
```

5. Calcule o dano médio causado pelos golpes
```js
const ataque = [
  { golpe: 'Espada justiceira', acerto: 20, dano: 24 },
  { golpe: 'Bola de fogo', acerto: 7, dano: 18 },
  { golpe: 'Meteoro de pegasus', acerto: 9, dano: 25 },
  { golpe: 'Choque do trovão', acerto: 14, dano: 17 },
  { golpe: 'Force Push', acerto: 18, dano: 16 },
  { golpe: 'Detroid Smash', acerto: 20, dano: 26 },
];
```

6. Usando map e reduce, calcule o dano total. Caso o valor do acerto seja 20, dobre o valor do dano. Caso o valor do acerto seja 10 ou menos, zere o dano. Caso contrário, some o dano normalmente.
```js
const ataque = [
  { golpe: 'Espada justiceira', acerto: 20, dano: 24 },
  { golpe: 'Bola de fogo', acerto: 7, dano: 18 },
  { golpe: 'Meteoro de pegasus', acerto: 9, dano: 25 },
  { golpe: 'Choque do trovão', acerto: 14, dano: 17 },
  { golpe: 'Force Push', acerto: 18, dano: 16 },
  { golpe: 'Detroid Smash', acerto: 20, dano: 26 },
];
```

## Recursos Adicionais
[documentação do reduce](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)
[documentação do map](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
[video sobre .map .redue e .filter](https://www.youtube.com/watch?v=D_MExaVe95w)
[Resumo de .map .reduce e .filter (inglês)](https://medium.com/@js_tut/map-filter-and-reduce-animated-7fe391a35a47)
