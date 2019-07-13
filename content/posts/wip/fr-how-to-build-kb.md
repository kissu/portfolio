# How to build a KB

Alors, nous allons tout d’abord parler de ce qu’il vous faudra commander. En effet, il faut des pièces un peu spéciales pour faire un clavier mécanique.

En voici la liste avec un lien cliquable sur chaque composant et son prix

| Composant                         | Intérêt                                                                       | Details                                                               |  Prix  |
| --------------------------------- | ----------------------------------------------------------------------------- | --------------------------------------------------------------------- | :----: |
| [Case: Tofu]                      | Le boîtier dans lequel vous allez mettre tout le contenu de votre clavier     | En alu, sobre, simple                                                 |  88$   |
| [PCB: DZ60RGB ANSI]               | Ce qui va envoyer vos inputs lorsque vous allez appuyer sur une touche        | Pas besoin de souder/dessouder                                        |  55$   |
| [Switchs: Zilent v2 65g]          | Tout ce qui donne au méca sa nature si particulière                           | Très chers mais font partie des meilleurs switchs tactiles silencieux |  84$   |
| [Keycaps: Akko World Tour keyset] | Voici ce sur quoi vous allez tapoter au quotidien                             | PBT, profile OEM, pas trop cher et ANSI standard                      |  43$   |
| [Plate: brass]                    | Ajoute de la stabilité et donne un feeling différent                          | _Optionnel mais recommandé_                                           |  40$   |
| [Stabilisateurs: GMK screw-in]    | Nécessaires pour les touches dites modifiers (Enter, Shift, Backspace etc...) | Simples a monter et avec un bon son                                   |  13$   |
| [Cable]                           |                                                                               | USB-C                                                                 |   5$   |
| [Switch/Keycap puller]            | Va vous permettre d'enlever vos switchs/keycaps sans les endommager           |                                                                       | 3,50$  |
| [Lubrifiant: Superlube]           | Va rendre vos stabs plus silencieux et avec un meilleur feeling               | **Uniquement** pour les stabs                                         | 8,60€  |
| [Pinceaux]                        | Pour appliquer différents types de lubrifiants                                | Pratique si vous voulez rendre votre clavier + silencieux/smooth      | 12,21€ |
| **Total**                         |                                                                               |                                                                       |  XXX   |

| Composant **optionnel**          | Intérêt                                                  | Prix  |
| -------------------------------- | -------------------------------------------------------- | ----- |
| [Isolant acoustique: Sorbothane] | Permettra d'étouffer la résonance du son dans votre case | 26$   |
| [Vis en nylon]                   | Si vous préférez cela au rondelles en plastique fournies | 4,19€ |

[Case: Tofu]: https://kbdfans.com/products/kbdfans-tofu-60-aluminum-case?variant=13786761723962
[PCB: DZ60RGB ANSI]: https://kbdfans.com/products/dz60rgb-ansi-mechanical-keyboard-pcb?variant=22887658782768
[Switchs: Zilent v2 65g]: https://kbdfans.com/products/zealios-tealios-zilents?variant=28744897396784
[Keycaps: Akko World Tour keyset]: https://www.banggood.com/AKKO-World-Tour-Tokyo-114-Keys-Cherry-Profile-Dyesub-PBT-Keycaps-Keycap-Set-for-Mechanical-Keyboard-p-1411856.html?akmClientCountry=FR&&cur_warehouse=USA
[Plate: brass]: https://kbdfans.com/products/brass-60-plate?variant=19387696218170
[Stabilisateurs: GMK screw-in]: https://kbdfans.com/products/gmk-screw-in-stabilizers?variant=22154915348528
[Cable]: https://kbdfans.com/products/usb-c-typec-usb-cable?variant=6868040384570
[Switch/Keycap puller]: https://kbdfans.com/products/product?variant=7446401351738
[Lubrifiant: Superlube]: https://www.amazon.fr/Multipurpose-synth%C3%A9tique-bas%C3%A9-sur-graisse/dp/B00C5014K8/ref=sr_1_1?__mk_fr_FR=%C3%85M%C3%85%C5%BD%C3%95%C3%91&keywords=multipurpose+graisse&qid=1562943680&s=gateway&sr=8-1
[Pinceaux]: https://www.amazon.fr/Artists-Modelmakers-Extra-Detail-ArtMaster/dp/B00A39DAMS/ref=sr_1_1?__mk_fr_FR=%C3%85M%C3%85%C5%BD%C3%95%C3%91&keywords=modelmakers+set+of+8+artmaster&qid=1562943790&s=gateway&sr=8-1

[Isolant acoustique: Sorbothane]: https://www.amazon.com/Isolate-Sorbothane-Acoustic-Vibration-Damping/dp/B019GBMG14/ref=sr_1_7?keywords=sorbothane&qid=1561179209&s=gateway&sr=8-7
[Vis en nylon]: https://www.amazon.fr/sourcingmap%C2%AE-Phillips-Nylon-croix-pi%C3%A8ces/dp/B012TAFF58/ref=sr_1_fkmr3_1?__mk_fr_FR=%C3%85M%C3%85%C5%BD%C3%95%C3%91&keywords=tete+philips+tete+croix+nylon&qid=1562943741&s=gateway&sr=8-1-fkmr3

Il vous faudra ensuite quelques outils que vous devez déjà avoir chez vous:
- [ ] pincette métallique
- [ ] pince coupante
- [ ] tournevis cruciforme
- [ ] ciseaux
- [ ] des pansements

Presque tous les composants sont en livraison gratuite et sont livres sous une dizaine de jours.

Voila, maintenant que vous avez tout commande et recu, il est temps de passer au build en lui meme !
![Les cartons de KBD](build-kb/packages.jpg)

Voici un peu ce que donnent toutes les pieces une fois rassemblees.
![Case + Sortbothane + PCB + Plate](build-kb/requirements.jpg)
![Tout le reste](build-kb/requirements2.jpg)

La premiere chose a faire est de verifier que tout ce que vous avez recu n'est pas endommage.
Comme par exemple votre PCB.

Pour cela, aller sur votre ordinateur, branchez le PCB en USB et aller a [cette adresse](https://config.qmk.fm/#/test) pour verifier que tout marche comme il faut.

Il vous suffit pour cela de fermer le circuit a l'aide de votre pincette entre les 2 trous qui vont accueillir les pattes du switch. Vous devriez voir les touches s'illuminer au fur et a mesure que vous avancez.

Oh, ne paniquez pas si les 4 derniers
![Testons le PCB](build-kb/test_pcb.jpg)

Links
https://bulkresizephotos.com/en?resize_type=filesize&resize_value=65000
