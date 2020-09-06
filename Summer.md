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
  {character:'Daniel', class:'Paladino', lvl:15},
  {character:'Patolino', class:'Mago', lvl:20},
  {character:'Conan', class:'Barbaro', lvl:21},
  {character:'Arsenal', class:'Mestre', lvl:42}
];
```

Se Você quisesse subir o `lvl` de todos os personagens, utilizando o for você faria da seguinte maneira:
```js
const party = [
  {character:'Daniel', class:'Paladino', lvl:15},
  {character:'Patolino', class:'Mago', lvl:20},
  {character:'Conan', class:'Barbaro', lvl:21},
  {character:'Arsenal', class:'Mestre', lvl:42}
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
  {character:'Daniel', class:'Paladino', lvl:15},
  {character:'Patolino', class:'Mago', lvl:20},
  {character:'Conan', class:'Barbaro', lvl:21},
  {character:'Arsenal', class:'Mestre', lvl:42}
];

const lvlUp = party.map((partyMembe) => partyMembe.lvl + 1)

console.log(lvlUp); // [16, 21, 22, 43]
```

Veja que o for foi substituido por apenas uma linha de codigo.

A Função Adicionoi 1 a todos os valores de lvl e retornou um array novo com cada um dos valores. Note que o amanho do array party e lvlUp é o mesmo (4 elementos).

outro exemplo que podemos fazer é Juntar o character com sua respectiva class, Veja como ficaria com o for
```js
const party = [
  {character:'Daniel', class: 'Paladino', lvl: 15},
  {character:'Patolino', class: 'Mago', lvl: 20},
  {character:'Conan', class: 'Barbaro', lvl: 21},
  {character:'Arsenal', class: 'Mestre', lvl: 42}
];

let member = [];
for(let i = 0; i <party.length; i += 1){
  member.push(`${party[i].character} ${party[i].class}`)
}

console.log(member)
```

e com o Map
```js
const party = [
  {character:'Daniel', class: 'Paladino', lvl: 15},
  {character:'Patolino', class: 'Mago', lvl: 20},
  {character:'Conan', class: 'Barbaro', lvl: 21},
  {character:'Arsenal', class: 'Mestre', lvl: 42}
];

const member = party.map((partyMembe) => `${partyMembe.character} ${partyMembe.class}`);

console.log(member) // ["Daniel Paladino", "Patolino Mago", "Conan Barbaro", "Arsenal Mestre"]
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
const charArmor = [{ Daniel:20}, ...]
```

Antes de proceguir, tente pensar como você faria para resolver esse problema, Vale lembrar que as HOFs podem receber vários parâmetros, não apenas o elemento que esta interada!

```js
 const character = ['Daniel', 'Patolino', 'Conan', 'Arsenal'];
 const armor = [20, 12, 16, 25];

const charArmor = (listChar, listArmor) => {
  return listChar.map((char, i) => (
    { [char]: listArmor[i] }
  ));
};

const armorChar = charArmor(character, armor);

console.log(charArmor)
```


## Reduce

## Exercícios
###### Tempo sugerido para realização: 120 minutos
## Recursos Adicionais
