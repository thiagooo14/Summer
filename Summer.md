# JavaScript ES6 - Higher Order Functions - map e reduce
## O que vamos aprender?
  Hoje Você vai aprender duas poderosas (e complexas) *Higher-Order Functions*: Array.map e o Array.reduce
  Essas Duas Funções são utilizadas para Manipular e criar Arrays. elas tem o intuito de deixar seu codigo mais legivel, conciso e expressivo

## Você será capaz de:
- Manipular e construir Arrays
- Tratar dados em Arrays de maneira mais limpa e eficaz
- Indexar dados de um Array com array.map
- Agregar dados com array.reduce

## Porque isso é importante?
  Como Ja visto anteriormente as *HOFs* ajudam bastante na redução e compreenção de codigos. map e reduce são duas *HOFs* muito importantes, porem mais complicadas, Elas facilitam muito na criação e manipulação de arrays.
## Conteúdos
### Map
A Função map possui a mesma estrutura das outras HOFs, ela transforma todos os itens de um array para outro Arry!

Para Entender Melhor vammos imaginar um grupo de RPG representado no seguinte array:
```js
const party = [
  {Character:'daniel', class:'paladino', lvl:15},
  {Character:'Patolino', class:'Mago', lvl:20},
  {Character:'Conan', class:'Barbaro', lvl:21},
  {Character:'Arsenal', class:'Mestre', lvl:42}
];
```

Se Você quisesse subir o lvl de todos os personagens, utilizando o for você faria da seguinte maneira:
```js
const party = [
  {Character:'daniel', class:'paladino', lvl:15},
  {Character:'Patolino', class:'Mago', lvl:20},
  {Character:'Conan', class:'Barbaro', lvl:21},
  {Character:'Arsenal', class:'Mestre', lvl:42}
];
let lvlUp = []
for ( let i = 0; i < party.length; i += 1){
  lvlUp.push(party[i].lvl + 1)
}

console.log(lvlUp); // [16, 21, 22, 43]
```

Agora com o map
```js
const party = [
  {Character:'daniel', class:'paladino', lvl:15},
  {Character:'Patolino', class:'Mago', lvl:20},
  {Character:'Conan', class:'Barbaro', lvl:21},
  {Character:'Arsenal', class:'Mestre', lvl:42}
];

const lvlUp = party.map((party) => party.lvl + 1)

console.log(lvlUp); // [16, 21, 22, 43]
```

veja que o for foi substituido por apenas uma linha de codigo

## Tempo sugerido para realização: 120 minutos
## __Exercícios__
## __Recursos Adicionais__
