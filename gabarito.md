## fixação
1.dobre o lvl dos membros
```js
const dobleLVL = party.map((party) => party.lvl * 2)
```
2. crie um array que junta primeiro a class e depois o character dos membros
```js
const member = party.map((party) => `${party.class} ${party.character}`);
```

3. crie um array que retorne apenas as class 
```js
const class = party.map((party) => party.class);
```
###### refatoração

1.
```js
const atack = [15, 11, 9, 1, 20];

const result = atack.map (atk => ((atk > 10) ? 'hit' : 'miss'))

console.log(result);
```

2.
```js
const character = [
  { class: 'Mago', lvl: 14 },
  { class: 'Druida', lvl: 13 },
  { class: 'Cleriga', lvl: 3 },
  { class: 'Ladino', lvl: 9 },
  { class: 'MaGuerreirago', lvl: 11 },
];

const classLvl = character.map(char => `${char.class} de nível ${char.lvl}`);

console.log(classLvl);

```
###### fixação reduce
1. apos o inimigo receber todos os danos, ele absorve 5, crie um reduce que calcule o dano que reduza 5 do dano
```js
const dmg = [
  { golpe: 'Espada justiceira', dano: 24 },
  { golpe: 'Bola de fogo', dano: 18 },
  { golpe: 'Meteoro de pegasus', dano: 25 },
  { golpe: 'Choque do trovão', dano: 17 },
];

const totalDmg = dmg.reduce((valorAcumulador, valorArray) => valorAcumulador + valorArray.dano, -5);

console.log("total de dano:", totalDmg);
```
2.crie um reduce que agrupe os golpes em quais causaram mais de 20 pontos e os que causaram menos!
```js
const dmg = [
  { golpe: 'Espada justiceira', dano: 24 },
  { golpe: 'Bola de fogo', dano: 18 },
  { golpe: 'Meteoro de pegasus', dano: 25 },
  { golpe: 'Choque do trovão', dano: 17 },
];

const grupDmg = dmg.reduce((acc, arr) => {
  const danoMAiorOuMenor = arr.dano >= 20 ? 'Maior' : 'Menor';

  acc[danoMAiorOuMenor].push(arr);
  return acc;
}, { Maior: [], Menor: []});

console.log(grupDmg);
```
## Exercicio

1.

2.

3.

4.

5.

6.

#### bonus

7.

8.

9.