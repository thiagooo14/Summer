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

4.
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

const atkChar = party.map(atk => `${atk.name}, o ${atk.class} usou ${atk.ataque.golpe}`)
console.log(atkChar);
```

2. 
```js
const ataque = [
  { golpe: 'Espada justiceira', acerto: 20, dano: 24 },
  { golpe: 'Bola de fogo', acerto: 7, dano: 18 },
  { golpe: 'Meteoro de pegasus', acerto: 9, dano: 25 },
  { golpe: 'Choque do trovão', acerto: 14, dano: 17 },
  { golpe: 'Force Push', acerto: 18, dano: 17 },
  { golpe: 'Detroid Smash', acerto: 20, dano: 26 },
];

const hitDamage = ataque.map((atk) =>
  atk.acerto === 20
    ? `${atk.golpe} causa ${atk.dano * 2} pontos de dano`
    : `${atk.golpe} causa ${atk.dano} pontos de dano`
);


console.log(hitDamage);
```
3. 
```js
const ataque = [
  { golpe: 'Espada justiceira', acerto: 20, dano: 24 },
  { golpe: 'Bola de fogo', acerto: 7, dano: 18 },
  { golpe: 'Meteoro de pegasus', acerto: 9, dano: 25 },
  { golpe: 'Choque do trovão', acerto: 14, dano: 17 },
  { golpe: 'Force Push', acerto: 18, dano: 17 },
  { golpe: 'Detroid Smash', acerto: 20, dano: 26 },
];

const hit = ataque.map(atk =>
  atk.acerto > 10
    ? `${atk.golpe} acertou e causou ${atk.dano} pontos de danos`
    : `${atk.golpe} falhou`
);

console.log(hit);
```

4. 
```js
const dano = [24, 18, 25, 17, 43, 27, 32, 35];

const danoTotal = dano.reduce((acc, arr) => acc + arr, -dano.length * 3);

console.log(danoTotal);
```

5.
```js
const ataque = [
  { golpe: 'Espada justiceira', acerto: 20, dano: 24 },
  { golpe: 'Bola de fogo', acerto: 7, dano: 18 },
  { golpe: 'Meteoro de pegasus', acerto: 9, dano: 25 },
  { golpe: 'Choque do trovão', acerto: 14, dano: 17 },
  { golpe: 'Force Push', acerto: 18, dano: 16 },
  { golpe: 'Detroid Smash', acerto: 20, dano: 26 },
];

const avgDmg = ataque.reduce((acc, arr) => acc + arr.dano , 0) / ataque.length

console.log(avgDmg)
```

6.
```js
  { golpe: 'Espada justiceira', acerto: 20, dano: 24 },
  { golpe: 'Bola de fogo', acerto: 7, dano: 18 },
  { golpe: 'Meteoro de pegasus', acerto: 9, dano: 25 },
  { golpe: 'Choque do trovão', acerto: 14, dano: 17 },
  { golpe: 'Force Push', acerto: 18, dano: 16 },
  { golpe: 'Detroid Smash', acerto: 20, dano: 26 },

const hitDamage = ataque.map(atk =>{
  if(atk.acerto === 20){
    return atk.dano * 2
  } else if (atk.acerto > 10){
    return atk.dano
  } else {
    return 0
  }
}).reduce((acc, arr) => acc + arr, 0)

console.log(hitDamage);
```
