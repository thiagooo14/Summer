# JavaScript ES6 - Higher Order Functions - map e reduce
## O que vamos aprender?
  Hoje Você vai aprender duas poderosas (e complexas) *Higher-Order Functions*: Array.map e o Array.reduce
  Essas duas funções são utilizadas para manipular e criar Arrays. elas tem o intuito de deixar seu codigo mais legível, conciso e expressivo

## Você será capaz de:
- Manipular e construir Arrays
- Tratar dados em Arrays de maneira mais limpa e eficaz
- Indexar dados de um Array com array.map
- Agregar dados com array.reduce

## Porque isso é importante?
  Como ja visto anteriormente as *HOFs* ajudam bastante na redução da quantidade de código escrito e na legibilidade deste.
  map e reduce são duas *HOFs* muito importantes, pois elas facilitam muito na criação e manipulação de arrays. Com elas, você fará muito mais operações com muito menos linhas.
## Conteúdos
### Map

A função map possui a mesma estrutura das outras HOFs, ela transforma todos os itens de um array para outro array!

![Alt Text](https://miro.medium.com/max/1000/1*4EGwsCicbWJeml2aAm714A.gif)

Para entender melhor vamos imaginar um grupo de RPG representado no seguinte array:
```js
const party = [
  { character: 'Daniel', class: 'Paladino', lvl: 15 },
  { character: 'Patolino', class: 'Mago', lvl: 20 },
  { character: 'Conan', class: 'Barbaro', lvl: 21 },
  { character: 'Arsenal', class: 'Mestre', lvl: 42 },
];

```

Se você quisesse subir o `lvl` de todos os personagens, utilizando o for você faria da seguinte maneira:
```js
const party = [
  { character: 'Daniel', class: 'Paladino', lvl: 15 },
  { character: 'Patolino', class: 'Mago', lvl: 20 },
  { character: 'Conan', class: 'Barbaro', lvl: 21 },
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
  { character: 'Conan', class: 'Barbaro', lvl: 21 },
  { character: 'Arsenal', class: 'Mestre', lvl: 42 },
];

const lvlUp = party.map(partyMembe => partyMembe.lvl + 1);

console.log(lvlUp); // [16, 21, 22, 43]
```

Veja que o for foi substituido por apenas uma linha de codigo.

A função adicionoi 1 a todos os valores de lvl e retornou um array novo com cada um dos valores. Note que o amanho do array party e lvlUp é o mesmo (4 elementos).

outro exemplo que podemos fazer é Juntar o character com sua respectiva class, Veja como ficaria com o for
```js
const party = [
  { character: 'Daniel', class: 'Paladino', lvl: 15 },
  { character: 'Patolino', class: 'Mago', lvl: 20 },
  { character: 'Conan', class: 'Barbaro', lvl: 21 },
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
  { character: 'Conan', class: 'Barbaro', lvl: 21 },
  { character: 'Arsenal', class: 'Mestre', lvl: 42 },
];

const member = party.map(partyMembe => `${partyMembe.character} ${partyMembe.class}`);

console.log(member); // ["Daniel Paladino", "Patolino Mago", "Conan Barbaro", "Arsenal Mestre"]
```

#### Vamos Praticar um pouco
1. dobre o lvl dos membros
2. crie um array que junta primeiro a class e depois o character dos membros
3. crie um array que retorne apenas as class 

agora imagine que temos dois arrays, uma para o personagem e outra para sua defesa
```js
const character = ['Daniel', 'Patolino', 'Conan', 'Arsenal'];
const armor = [20, 12, 16, 25];
```

com o .map podemos podemos unir os dois arrays em um só, dessa forma teremos o array:
```js
const charArmor = [{ Daniel: 20 }, ...];
```

Antes de proceguir, tente pensar como você faria para resolver esse problema, Vale lembrar que as HOFs podem receber vários parâmetros, não apenas o elemento que esta interada!

```js
const character = ['Daniel', 'Patolino', 'Conan', 'Arsenal'];
const armor = [20, 12, 16, 25];

const charArmor = (listChar, listArmor) => {
  return listChar.map((char, i) => ({ [char]: listArmor[i] }));
};

const armorClass = charArmor(character, armor);

console.log(armorClass);
```

Vale lembrar que o .map não altera o array, ele interrage com os elementos e retorna um novo array.

### vamos praticar mais um pouco
para fixar melhor o map, transforme os for a seguir utilizando o .map

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
  { class: 'Druida', lvl: 13 },
  { class: 'Cleriga', lvl: 3 },
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
Diferente das outras *HOF's* o Reduce precia receber um parâmetro a mais, o acumulador, também chamado de acc, ele é responsável por acumular todos os valores e devolver o resultado final.

![Alt Text](https://miro.medium.com/max/1000/1*dhTC_FFgiH3mKROrnDj12w.gif)

Para entender melhor, vamos imaginar que você quer calcular o dano que seu grupo deu no inimigo, para isso vamos usar o seguinte array:
```js
const character = [
  { golpe: 'Espada justiceira', dano: 24 },
  { golpe: 'Bola de fogo', dano: 22 },
  { golpe: 'Meteoro de pegasus', dano: 25 },
  { golpe: 'Choque do trovão', dano: 17 },
];
```

com o for seria feito da seguinte maneira:
```js
const dmg = [
  { golpe: 'Espada justiceira', dano: 24 },
  { golpe: 'Bola de fogo', dano: 19 },
  { golpe: 'Meteoro de pegasus', dano: 25 },
  { golpe: 'Choque do trovão', dano: 17 },
];

let totalDmg = 0;

for (let i = 0; i < dmg.length; i++) {
  totalDmg = totalDmg + dmg[i].dano;
}

console.log(totalDmg);
```

veja que foi preciso setar uma variavel, com o valor inicial de 0, e a cada interação do for ele pega o valor atual e adiciona o valor do `dano`, agora veja como fazer com o reduce.
```js
const dmg = [
  { golpe: 'Espada justiceira', dano: 24 },
  { golpe: 'Bola de fogo', dano: 18 },
  { golpe: 'Meteoro de pegasus', dano: 25 },
  { golpe: 'Choque do trovão', dano: 17 },
];

const totalDmg = dmg.reduce((valorAcumulador, valorArray) => valorAcumulador + valorArray.dano, 0);

console.log("total de dano:", totalDmg); // total de dano: 84
```

a sintaxe utilizada para o reduce é a seguinte:
```js
  array.reduce(function(acc, arr), valorInicial)
```

Nesse exemplo, o primeiro parametro, a função, recebe o `valorAcumulador` que a cada interação é adicionado o `valorArray` referente ao `dano`.
No final da função temos o segundo parametro o `valorInicial` ele se relaciona com o que queremos receber no final, como queremos receber um numero que representa a soma de todos os danos, passamos `0` para iniciar a soma.

* Experimente Trocar o `0` para outro valores, como por exemplo `5` ou `-10` e veja o que acontece

Agora imagine que você separar quem causou uma quantidade par, e quem causou uma quantidade impra de dano. 
```js
const dmg = [
  { golpe: 'Espada justiceira', dano: 24 },
  { golpe: 'Bola de fogo', dano: 18 },
  { golpe: 'Meteoro de pegasus', dano: 25 },
  { golpe: 'Choque do trovão', dano: 17 },,
];

const grupDmg = dmg.reduce((acc, arr) => {
  const danoParOuImpar = arr.dano %2 === 0 ? 'par' : 'impar';

  acc[danoParOuImpar].push(arr); // valores pares serão empurrados para o valor de par do acumulador e impares para o de impar 
  return acc; // O acumulador é retornado da primeira para a segunda interação e assim respectivamente
}, { par: [], impar: []}); // valor inicial de acc

console.log(grupDmg);
/*Object {
  impar:[Object {
    dano: 25,
    golpe: "meteoro de pegasus"
  }, Object {
    dano: 17,
    golpe: "Choque do trovão"
  }],
  par: [Object {
    dano: 24,
    golpe: "Espada justiceira"
  }, Object {
    dano: 18,
    golpe: "Bola de fogo"
  }]
}*/
```

Repare que agora como queremos que o retorno seja um um objeto, o valor inicial é passado o objeto com as chaves que queremos retornar!

### vamos praticar mais um pouco
ainda usando o array:
```js
const dmg = [
  { golpe: 'Espada justiceira', dano: 24 },
  { golpe: 'Bola je jogo', dano: 18 },
  { golpe: 'Meteoro de pegasus', dano: 25 },
  { golpe: 'Choque do trovão', dano: 17 },
];
```
1.crie um reduce que calcule a soma do dano recebido por todos os golpes, sabendo que o inimigo absorve 5 do dano total.
<!-- ver depois -->
2.crie um reduce que agrupe em um objeto os golpes que causaram 20 ou mais pontos de dano e os que causaram menos!
Dica: use um array que agrupe os golpes maiores e menores
<!-- ver depois -->
#### map + reduce

Podemos tambêm usar as duas *HOFs* que aprendemos hoje.
Imagine que você queira dobrar o dano e depois totalizar o dano causado! como você faria isso?
```js
const dmg = [
  { golpe: 'Espada justiceira', dano: 24 },
  { golpe: 'Bola je jogo', dano: 18 },
  { golpe: 'Meteoro de pegasus', dano: 25 },
  { golpe: 'Choque do trovão', dano: 17 },
];

const doubleDamage = dmg.map (d => d.dano *2);
const totalDmg = doubleDamage.reduce ((acc, arr) => acc + arr, 0);

console.log('20 é 20:', doubleDamage); // "20 é 20:" [48, 36, 50, 34]
console.log('total de dano:', totalDmg)// "total de dano:" 168
```

Porem, podemos, tambêm, juntar as duas *HOFs* em um unico comando:

```js
const doubleDamage = dmg.map (d => d.dano *2).reduce ((acc, arr) => acc + arr, 0);

console.log('dano total:', doubleDamage);// "dano total:" 168
```

O resultado do map, é um array, que encadeado com o reduce é como se fizesse(mos):
```js
[48, 36, 50, 34].reduce ((acc, arr) => acc + arr, 0);
```

## Exercícios
<!-- Criar alguns exercicios -->
## Recursos Adicionais

<!-- lembrar de arrumar o MD depois! -->

 documentação do reduce: https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce

documentação do map: https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/map
