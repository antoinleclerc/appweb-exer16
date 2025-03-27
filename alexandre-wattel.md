---
outline: deep
---

# Revu de code Projet TP1 d'Alexandre Wattel.

Le Tp est très bien fait en général, il y a juste quelques améliorations à faire.

Problème d'import dans :

- AfficherDetails.vue
- AfficherListeProduit.vue
- AfficherRecherche.vue

## AfficherDetails.vue

### Import peut être améliorer

Le ".ts" est inutile.

[Source](https://www.typescriptlang.org/docs/handbook/modules/theory.html#module-resolution)

````md
```js{4}
import {
  produitSelectionne,
  initModal,
} from "../script/produit/afficherDetailsProduit.ts";
```
````

### Amélioration

Juste enlever le ".ts".

````md
```js{4}
import {
  produitSelectionne,
  initModal,
} from "../script/produit/afficherDetailsProduit";
```
````

## AfficherListeProduit.vue

### Import peut être améliorer

Le ".ts" est inutile.

[Source](https://www.typescriptlang.org/docs/handbook/modules/theory.html#module-resolution)

````md
```js{4}
import {
  produits,
  supprimerProduit,
  checkStockProduit,
} from "../script/produit/produit.ts";
import { afficheDetails } from "../script/produit/afficherDetailsProduit.ts";
import {
  modifierStateEtProduit,
  duppliquerStateEtProduit,
} from "../script/form/formState.ts";
```
````

### Amélioration

Juste enlever le ".ts".

````md
```js{4}
import {
  produits,
  supprimerProduit,
  checkStockProduit,
} from "../script/produit/produit";
import { afficheDetails } from "../script/produit/afficherDetailsProduit";
import {
  modifierStateEtProduit,
  duppliquerStateEtProduit,
} from "../script/form/formState";
```
````

## AfficherRecherche.vue

### Utilisation d'un type

dans les fonctions tu utilise le type **"any"**

````md
```js{4}
const modifier = (produit: any) => {
  modifierStateEtProduit(produit);
};

const dupliquer = (produit: any) => {
  duppliquerStateEtProduit(produit);
};
```
````

### correction

Utilise un type **produit** pour éviter les erreurs de type

````md
```js{4}
const modifier = (produit: Produit) => {
    modifierStateEtProduit(produit);
};

const dupliquer = (produit: Produit) => {
    duppliquerStateEtProduit(produit);
};
```
````

### Import peut être améliorer

Le ".ts" est inutile.

[Source](https://www.typescriptlang.org/docs/handbook/modules/theory.html#module-resolution)

````md
```js{4}
import { listeRechercheProduit } from "../script/produit/rechercheProduit.ts";
import {
  supprimerProduit,
  checkStockProduit,
} from "../script/produit/produit.ts";
import { afficheDetails } from "../script/produit/afficherDetailsProduit.ts";
import {
  modifierStateEtProduit,
  duppliquerStateEtProduit,
} from "../script/form/formState.ts";
```
````

### Amélioration

Juste enlever le ".ts".

````md
```js{4}
import { listeRechercheProduit } from "../script/produit/rechercheProduit";
import {
  supprimerProduit,
  checkStockProduit,
} from "../script/produit/produit";
import { afficheDetails } from "../script/produit/afficherDetailsProduit";
import {
  modifierStateEtProduit,
  duppliquerStateEtProduit,
} from "../script/form/formState";
```
````
