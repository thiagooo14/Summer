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

const classLvl = character.map(char => `${char.class} ${char.lvl}`);

console.log(classLvl);

```

