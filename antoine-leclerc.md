# Revue de code du TP1 de Antoine Leclerc

## Revue component

### ListeLego.vue

**Problème alertes**

```js{4}
const detailsVisible = ref<number | null>(null);

const toggleDetails = (id: number) => {
  detailsVisible.value = detailsVisible.value === id ? null : id;
};

const dismissAlert = () => {
  alertVisible.value = false;
};
```

La fermeture de l'une alerte ferme toutes les alertes sans prendre en compte si l'utilisateur a vu toutes les alertes.

## Revue TS

### Database.ts

Mauvais nommage : le nom du fichier Database.ts
doit être changer puisqu'il n'est pas une Database.

[Convention de nommage](https://fr.wikipedia.org/wiki/Convention_de_nommage#:~:text=Une%20convention%20de%20nommage%20dans,code%20source%20et%20la%20documentation.https:/)

### Function.ts

**Problème génération id**

```js{4}
export const ajouterProduit = (produit: PieceLego) => {
  tousLesPieces.value.push({
    ...produit,
    id: tousLesPieces.value.length + 1,
  });
  produits.value = [...tousLesPieces.value];
};
```

Risque de dupplication d'id --->id: tousLesPieces.value.length + 1

La génération d'id ne prend pas en compte les id déjà présent et l'utilisation de la longeur de 'tousLesPieces' ne prend pas en compte la suppression.

Par exemple, si il y a 8 object dans la liste, l'id du prochain ajout sera l'id '9'. Maintenant, si on ajoute un oject et qu'on surpprime un object autre que celui qu'on vient d'ajouter. La génération d'id va redonner l'id '9' au prochain object ajouter alors qu'un object avec l'id '9' est déjà présent.
