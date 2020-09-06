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
![Alt Text](https://miro.medium.com/max/1000/1*4EGwsCicbWJeml2aAm714A.gif)

A função map possui a mesma estrutura das outras HOFs, ela transforma todos os itens de um array para outro array!

Para entender melhor vamos imaginar um grupo de RPG representado no seguinte array:
```js
const party = [
  { character: 'Daniel', class: 'Paladino', lvl: 15 },
  { character: 'Patolino', class: 'Mago', lvl: 20 },
  { character: 'Conan', class: 'Barbaro', lvl: 21 },
  { character: 'Arsenal', class: 'Mestre', lvl: 42 },
];

```

Se Você quisesse subir o `lvl` de todos os personagens, utilizando o for você faria da seguinte maneira:
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

A Função Adicionoi 1 a todos os valores de lvl e retornou um array novo com cada um dos valores. Note que o amanho do array party e lvlUp é o mesmo (4 elementos).

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

![Alt Text](https://miro.medium.com/max/1000/1*dhTC_FFgiH3mKROrnDj12w.gif)



## Exercícios
###### Tempo sugerido para realização: 120 minutos
## Recursos Adicionais
