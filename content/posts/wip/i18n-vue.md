Issue en rapport [i18n](https://github.com/3print/easyplv-v3/issues/28)
⚠️  Code commence depuis #3.

Cette PR a pour role de mettre en place toutes les traductions pour les vues au niveau :fr:, la partie :es: (la plus importante au final), pourra etre faite plus tard.
En effet, ce n'est pas urgent et puis il suffira juste de completer le contenu des fichiers de traduction, le setup et les balises seront deja en place pour le tout.

D'ailleurs, pour comparer les 2 versions (:es:/:fr:), on pourra se connecter sur l'app avec le compte `admin_es` (pwd: `admin`) pour voir les traductions qui manquent. Cf la [PR pour la seed](https://github.com/3print/easyplv-v3/pull/42).

Je vais faire un rapide debrief de comment s'utilise i18n avec le setup actuel. :bookmark_tabs:
On a globalement 2 endroits ou se trouvent les traductions, le premier est dans `app/javascript/packs/utils/locales` et le deuxieme est au sein meme du composant que l'on veut traduire, entre des balises i18n.

En partant de ce principe, prenons un fichier local avec:
```vue
<i18n>
fr:
  basket: "Panier"
  salut: "Hello dude"
es:
</i18n>
```

et le fichier de traduction globale
```vue
main:
  product_name: "Nom du produit"
  orientation: "Orientation"
```

Les differentes facons que nous avons pour faire les traductions sont les suivantes:
- utiliser la solution la moins friendly mais [la plus efficace](https://kazupon.github.io/vue-i18n/guide/directive.html#t-vs-v-t), a savoir `v-t`:
```vue
<template>
  <div>
    <h1 v-t="'basket'"></h1>
  </div>
</template>
```
Ici, le contenu du tag `h1` va etre remplace par le contenu de la cle `basket` et donc generer un titre avec le mot `Panier`. A utiliser le plus souvent possible svp. :pray:

- la solution la plus simple et la plus jolie, ie `$t`:
```vue
<template>
  <div>
    <p>{{ $t('salut') }}</p>
  </div>
</template>
```
Tres proche de la syntaxe en moustaches habituelle de Vue, il suffira de mettre la cle que l'on souhaite. :bike:
Cette solution bien que pratique n'est de preference a utiliser que lorsque la premiere est trop contraignante.
Comme dans l'exemple suivant:
```vue
# CampaignCalendar.vue
<h4>
  <i class="fa fa-calendar"></i>{{ $t('operation_calendar') }}
</h4>
```
Ici on ne ne peut pas appliquer de `v-t` sur le tag `h4` sinon on n'aura plus l'icone. Pour eviter de creer un `span` inutile, il vaut mieux utiliser la solution du `$t`.

- on peut traduire les attributs aussi, comme par exemple les placehoder et les options.
```vue
# TemplateOrientation.vue
<i18n>
fr:
  portrait: "Portrait"
  landscape: "Paysage"
</i18n>

<template>
  <label v-t="'main.orientation'"></label>
  <v-select
    :options="[this.$i18n.t('portrait'), this.$i18n.t('landscape')]"
    :placeholder="this.$i18n.t('main.orientation')">
  </v-select>
</template>
```

Ici, plusieurs choses sont a prendre en compte, on fait une traduction du label depuis le fichier global (cf plus haut) donc on utilise la key contenu dans ce fichier la: `main.orientation`
Le fichier global a pour vocation de garder des traductions qui seront reutilises partout a travers l'app, histoire de ne pas avoir les memes dans tous les composants...

Il n'y a pas besoin de faire quoi que ce soit, si l'on est un utilisateur avec la langue :fr: par exemple, Vue ira chercher la traduction dans le tag `i18n` local du composant, si la cle ne s'y trouve pas, il ira chercher dans le fichier global, s'il ne s'y trouve pas la bas non plus, il affichera juste la cle. :woman_shrugging:

On remplit les options par un array de traductions locales.

~~On traduit aussi le placeholder. Il faut plusieurs choses~~
Me suis rendu compte qu'en fait non, ca marche tres bien sans aucune autre manip... :skull:

- il y a aussi le fonctionnement de l'[interpolation de certains tags](https://kazupon.github.io/vue-i18n/guide/interpolation.html) qu'il est interessant de voir car ca sera certainement pas mal utilise. Ca peut vraiment ajouter une couche de dynamisme tout en evitant les soucis de XSS.
En voici un exemple
```vue
# ProductCreation.vue
<template>
...
<i18n
  :places="{ max_number: counter_remaining_chars }"
  path="max_chars"
  tag="p">
</i18n>
...
</template>

# Exemple d'interpolation neste
<template>
...
<i18n
  :places="{ thing: this.$i18n.t('interpolate_var')}"
  path="interpolate_sentence"
  tag="tag">
  <nested_tag
    :href="data_url"
    place="interpolate_nested_var"> {{ $t('interpolate_nested_sentence') }}
  </nested_tag>
</i18n>
...
</template>
```
Oui, il vaut mieux utiliser des snippets pour ce genre de blocs de code ! :muscle:  :dolphin:

---
Niveau configuration:
- il n'y a pour l'instant pas de fallback, pour des raisons de debug plus rapides. Il faudra penser a le decomenter la ligne dans le fichier `main.js` quand ce sera le cas. Puis le set sur un fallback :es: d'ailleurs non ?
- il y a des warnings qui apparaissent si on utilise des traductions `i18n` depuis des cles locales **et** globales, le lien pour l'[issue en question](https://github.com/kazupon/vue-i18n/issues/201) a ete laisse au niveau de l'option `silentTranslationWarn`. Si jamais on ne veut pas avoir sa console spam par les erreurs, on peut toujours passer le tag a `true`
- si jamais on a besoin de `localize` automatique, on pourra utiliser le package [i18next](https://www.i18next.com)
- actuellement, on utilise `"this.$i18n.t('key')"` pour traduire, il se trouve que l'on peut aussi utiliser `"this.$t('key')"` voire meme `"$t('key')"`, cependant j'ai cru comprendre que parfois ca peut poser probleme, si quelqu'un est assez confiant pour faire un `replace all` ou a le temps/envie de se pencher dessus...en attendant je laisse la forme longue au cas ou (il se peut qu'au vu de notre version - `^7.8.0`, tout fonctionne parfaitement)
---
Todo:
- [ ] traduire le flatpickr de facon automatique
- [ ] (mineur) verifier que l'on peut utiliser une forme raccourcie pour les traductions, voici quelques pistes: issue  [#108](https://github.com/kazupon/vue-i18n/issues/108), [#119](https://github.com/kazupon/vue-i18n/issues/119#issuecomment-284198547) et [#149](https://github.com/kazupon/vue-i18n/issues/149#issuecomment-296348086)

NB: **toutes** les entrees :fr: n'ont pas ete traduites car certaines choses ont ete mises en tant que placeholder et seront dynamisees par la suite.
