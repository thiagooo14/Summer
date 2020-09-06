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
