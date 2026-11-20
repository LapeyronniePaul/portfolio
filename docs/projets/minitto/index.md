---
title: Minitto
parent: Projets
nav_order: 1
---

# Minitto
{: .no_toc }

> Un petit robot marcheur à **ventouses** et à **« fulguro-poings »**, piloté en Bluetooth depuis un smartphone. Vainqueur du **combat de sumo** et du **tir à la corde** aux Ottolympiades.

<img class="illustration" src="{{ '/assets/images/Minitto.png' | relative_url }}" alt="Minitto, le robot marcheur à ventouses">

<!--
📷 PHOTO 1 (facultative, pour remplacer l’image du dessus si tu en as une meilleure) :
Minitto de face, posé sur un fond neutre (feuille blanche ou table claire), bien éclairé,
bras (poings) visibles des deux côtés et pieds-ventouses visibles. Prise légèrement en contre-plongée
pour lui donner un air « de combattant ».
-->

| | |
|---|---|
| **Statut** | Terminé |
| **Type** | Robot marcheur bipède |
| **Cerveau** | XIAO ESP32-C3 |
| **Pilotage** | Bluetooth Low Energy, application RemoteXY (15 m testés) |
| **Taille** | 15 × 15 × 12 cm |
| **Fabrication** | Impression 3D (PLA + TPU), Bambu Lab A1 mini |
| **Base de départ** | Otto DIY, version « Otto-MKS » du Makerspace d’Amiens |
| **Réalisation** | Seul, en environ un mois |

<details open markdown="block">
  <summary>Sommaire</summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

---

# Partie 1 : Minitto en bref

*Cette première partie se lit en 3 minutes et ne demande aucune connaissance en robotique. La partie 2 explique ensuite comment tout fonctionne.*

## Le projet en 30 secondes

Minitto est un petit robot qui **marche sur deux jambes**, un peu comme un manchot. Ses deux pieds sont des **ventouses** : des mini-pompes à air aspirent l’air et le collent au sol. Pendant qu’un pied avance, l’autre reste fixé. On ne peut donc pas le pousser, le soulever ou le faire tomber facilement.

Pour se battre, il possède deux **bras à ressort** qui donnent un **coup de poing sec** à distance. On le pilote en Bluetooth depuis un téléphone.

<!--
📷 PHOTO 2 (en action) :
Minitto en plein combat de sumo : un adversaire à côté de lui, un poing qui vient de partir
(bras tendu). Si tu as une photo ou une capture de vidéo de la compétition, c’est idéal.
Sinon, refais la scène avec un autre robot ou un objet.

![Minitto en plein combat de sumo]({{ '/assets/images/minitto/combat-sumo.jpg' | relative_url }})
-->

## D’où vient Minitto ?

Mon école, UniLaSalle Amiens, propose un projet d’électronique avec le **Makerspace d’Amiens** : construire un robot **Otto**, un petit marcheur open source. Chaque étudiant reçoit une **carte électronique déjà montée** et un **modèle 3D de base**. Le projet se termine par les **Ottolympiades**, une compétition entre robots avec quatre épreuves : combat de sumo, tir à la corde, course de vitesse et évitement d’obstacles.

Les ressources de l’école sont publiques : [Otto-MKS sur le site du Makerspace d’Amiens](https://doc.makerspace-amiens.fr/workshops/otto-mks/).

Je devais passer mon année sur la Coupe de France de robotique. Mais l’idée de la compétition m’a tellement plu que je me suis lancé **environ un mois avant la date de rendu**, seul, alors que les autres groupes avaient presque un semestre.

**Mon objectif** : sortir du cadre (dans les règles) pour fabriquer un Otto **plus rapide, plus puissant au sumo et plus fort au tir à la corde**.

## Ce qui rend Minitto différent

| | Otto d’origine | Minitto |
|---|---|---|
| **Taille (l × p × h)** | 10 × 10 × 15 cm | 15 × 15 × 12 cm |
| **Jambes et tête** | Hauteur standard | Raccourcies pour abaisser le centre de gravité |
| **Pieds** | Pieds plats | Ventouses reliées à des mini-pompes à vide |
| **Bras** | Aucun | Deux poings à élastique, déclenchés par servo |
| **Portée Bluetooth** | Standard | Antenne ajoutée (15 m testés) |
| **Matériaux** | PLA | PLA + TPU (souple) aux endroits qui encaissent les chocs |

Toutes les pièces du modèle de départ ont été **modifiées**.

<!--
📷 PHOTO 3 (comparaison) :
Minitto et un Otto « standard » côte à côte (un camarade en a sûrement un), vus de face,
sur la même table pour qu’on voie la différence de taille. Si tu n’en as pas,
fais plutôt une capture OnShape de la version d’origine et de la tienne, côte à côte.

![Minitto à côté d’un Otto standard]({{ '/assets/images/minitto/comparaison-otto.jpg' | relative_url }})
-->

## Trois idées clés

### 1. Se coller au sol

Face aux autres équipes, j’ai regardé leurs idées : beaucoup préparaient des **bras pelleteuses** pour soulever l’adversaire et le renverser. La parade la plus simple était de **ne pas pouvoir être soulevé**. D’où les ventouses.

Elles ont aussi servi pour le **tir à la corde** : Minitto ne peut pas être tiré, il lui suffit de **reculer pas à pas** en gardant toujours une ventouse fixée. Au passage, il peut aussi marcher sur les murs et au plafond.

### 2. Un coup sec

Pour le sumo, je voulais une arme. L’idée m’est venue en pensant à **Goldorak** et à son **fulguro-poing**. Les poings de Minitto sont lancés par un **élastique tendu** et déclenchés à distance par un petit servo. Les autres robots poussaient doucement ou soulevaient ; Minitto envoie un **choc** qui projette l’adversaire hors du ring, **tout en restant collé au sol**.

![Le fulguro-poing de Minitto]({{ '/assets/images/fulguro_poing.png' | relative_url }})

### 3. Une marche en deux modes

- **Avec pompes** : très lent (1 m en 6 min 47 s), mais **quasi inarrachable**. Utilisé au sumo et au tir à la corde.
- **Sans pompes** : environ **1 m en 35 s**. Utilisé pour la vitesse et le reste du temps.

## Résultats aux Ottolympiades

| Épreuve | Résultat |
|---|---|
| Combat de sumo | **1er** |
| Tir à la corde | **1er** (seul contre les 15 équipes de ma promotion) |
| Course de vitesse | 15e |

<!--
⚠️ À CONFIRMER avant de publier : l’évitement d’obstacles.
Tu m’as dit à la fois que tu avais fini 3e (en pilotant à la main) et que tu n’avais pas participé
car tu avais raté le départ. Si tu as vraiment participé, ajoute cette ligne dans le tableau :
| Évitement d’obstacles | 3e (pilotage manuel) |
Sinon, ne mets rien.
-->

![Minitto victorieux]({{ '/assets/images/image_minitti_victoire.png' | relative_url }})

*Une fois la victoire acquise, Minitto fait le show : haka, accroupissement, saut. Juste pour le plaisir.*

---

# Partie 2 : Comment ça marche ?

*Cette partie détaille la conception : mécanique, électronique, logiciel et difficultés rencontrées.*

## Vue d’ensemble

```
 Smartphone (application RemoteXY)
        │  Bluetooth Low Energy (antenne ajoutée, 15 m testés)
        ▼
 XIAO ESP32-C3 sur la carte fournie par l’école
   ├── 4 servos de marche ───► 2 jambes + 2 pieds
   ├── 2 servos de bras ─────► verrous des poings
   ├── 2 sorties pompes ─────► MOSFET ─► mini-pompes à vide ─► ventouses
   ├── buzzer                  (sons, animations)
   └── capteur à ultrasons     (prévu, non exploité dans le code)
```

<!--
📷 SCHÉMA 1 (à refaire en image si tu veux le rendre plus joli) :
Le schéma ci-dessus dessiné proprement (draw.io, Excalidraw ou à la main puis photo),
avec des icônes : téléphone, puce, 6 servos, 2 pompes, 2 ventouses, buzzer.
-->

## Mécanique et impression 3D

### Les modifications du modèle

Le modèle OnShape fourni par l’école a été retravaillé pièce par pièce :

- **Jambes et tête raccourcies** : le centre de gravité descend, le robot est plus stable et plus difficile à renverser.
- **Ventouses dans les pieds**, avec un tube souple qui les relie aux pompes fixées sous les pieds.
- **Deux bras à élastique** (les fulguro-poings), avec un verrou à servo.
- **Une antenne** pour contrôler le robot à plus longue distance.

<!--
📷 PHOTO 4 (CAO) :
Deux captures OnShape côte à côte : la jambe/tête d’origine et ta version raccourcie,
avec une flèche ou une ligne horizontale montrant le centre de gravité abaissé.

![Raccourcissement des jambes et de la tête]({{ '/assets/images/minitto/cao-jambes.png' | relative_url }})

📷 PHOTO 5 (pied) :
Un pied de Minitto vu de dessous : la ventouse, le tube souple et la mini-pompe.
Annote (flèches) « ventouse », « tube », « pompe » avec n’importe quel éditeur d’image.

![Pied à ventouse]({{ '/assets/images/minitto/pied-ventouse.jpg' | relative_url }})
-->

### Impression

| Donnée | Valeur |
|---|---|
| Imprimante | Bambu Lab A1 mini |
| Matériaux | PLA (structure) + TPU (pièces absorbant les chocs) |
| Fixation des servos | Vis directement dans le plastique |
| Coût du plastique | 1 € maximum |
| Temps d’impression | ≈ 15 h sur une seule A1 mini (2 h sur 8 machines en parallèle) |

<!--
📷 PHOTO 6 :
Toutes les pièces imprimées étalées sur une table (démonter le robot ou photographier
les pièces avant l’assemblage), PLA d’un côté et TPU de l’autre si possible.
Ajoute une légende « PLA » / « TPU ».

![Pièces imprimées de Minitto]({{ '/assets/images/minitto/pieces-imprimees.jpg' | relative_url }})
-->

### Les poings

Le principe est simple : un **élastique détendu = un poing lancé**.

1. On **arme** le bras à la main : l’élastique est tendu et le bras est bloqué par des crochets.
2. Un **disque cranté**, tourné par un servo, **verrouille** les crochets à un angle précis.
3. Pour tirer, le servo tourne à l’angle de **libération** : les crochets lâchent, l’élastique se détend et **propulse le poing**.

Dans le code, l’angle de verrouillage vaut 45° et celui de libération 90°.

```cpp
void recharge_poing() { // button_01 = gauche, button_02 = droite
  if (RemoteXY.button_01 == 1 && pg == 0) {
    Servo6.write(45);   // le servo verrouille le poing gauche (armé)
    pg = 1;
  }
  else if (RemoteXY.button_02 == 1 && pd == 0) {
    Servo5.write(45);   // idem pour le poing droit
    pd = 1;
  }
}

void coup_poing() {
  if (RemoteXY.button_01 == 1 && pg == 1) {
    Servo6.write(90);   // le servo libère le poing gauche : coup parti
    pg = 0;
  }
  else if (RemoteXY.button_02 == 1 && pd == 1) {
    Servo5.write(90);   // idem pour le poing droit
    pd = 0;
  }
}
```

![Coupe du poing, système d’amortissement](/assets/images/vue_de_coupe_du_poing_1.png)
*Le système d’amortissement (« airbag »), en rouge, imprimé en TPU.*

![Coupe du poing, système de libération](/assets/images/vue_en_coupe_du_poing_2.png)
*Le système de libération du poing, en blanc.*

<!--
📷 PHOTO 7 (très important) :
Gros plan sur un poing armé : on doit voir l’élastique tendu, le disque cranté,
les crochets et le servo. Prends-la sous 2 angles si possible (une avec le poing armé,
une avec le poing lancé) pour que le principe se comprenne tout seul.

📷 PHOTO 8 (facultative mais très visuelle) :
Une photo du robot qui frappe : un petit objet (gobelet en carton) projeté par le poing.
Une vidéo courte (GIF) fonctionne aussi très bien dans une page web.
-->

## Électronique

La **carte électronique est fournie par l’école** : c’était mon premier vrai projet d’électronique, je n’ai donc pas dessiné la carte moi-même (voir les pistes d’amélioration).

| Élément | Détail |
|---|---|
| Microcontrôleur | XIAO ESP32-C3 |
| Alimentation | Pile rechargeable 9 V, régulateur 5 V sur la carte |
| Servos | 6 × FT90B |
| Pompes | 2 mini-pompes à vide Dewin, commandées par MOSFET |
| Capteur | Ultrasons (prévu, non exploité) |
| Son | Buzzer |
| Antenne | Antenne externe du XIAO ESP32 (15 m testés) |

Servos et pompes partagent la **même alimentation**.

### Branchements (d’après le code)

| Fonction | Nom dans le code | Broche |
|---|---|---|
| Jambe gauche | `Servo1` | D7 |
| Pied gauche | `Servo2` | D8 |
| Pied droit | `Servo3` | D9 |
| Jambe droite | `Servo4` | D10 |
| Bras droit | `Servo5` | D6 |
| Bras gauche | `Servo6` | D3 |
| Pompe « droite » | `POMPE_DROITE_PIN` | D4 |
| Pompe « gauche » | `POMPE_GAUCHE_PIN` | D5 |
| Buzzer | `BUZZER_PIN` | D0 |
| Ultrasons (trig / echo) | `trig_pin` / `echo_pin` | D2 / D1 |

<!--
Si une seule attribution te paraît fausse après vérification sur le robot,
corrige directement ce tableau (les commentaires du code se contredisaient
sur le « gauche/droite » des bras et des pompes).

📷 PHOTO 9 :
La carte vue de dessus avec le XIAO et l’antenne, avec des annotations (flèches) :
« XIAO ESP32-C3 », « régulateur 5 V », « sorties servos », « sorties pompes », « antenne ».

📷 PHOTO 10 :
Le cœur du robot ouvert : la pile 9 V, la carte, le câblage des pompes.
-->

### Autonomie

| Situation | Autonomie |
|---|---|
| Robot allumé, servos immobiles | ≈ 5 jours |
| En mouvement sans pompes | ≈ 1 journée de tests |
| Avec les pompes | ≈ 1 h 30 |

Les pompes consomment beaucoup plus que les servos, d’où l’idée de ne les activer que lorsque c’est utile (sumo, tir à la corde).

## Logiciel

Le firmware est écrit en **C++ (Arduino IDE)** et n’utilise que deux bibliothèques : **RemoteXY** (interface et Bluetooth) et **ESP32Servo**. Chaque mouvement est une **fonction** (`MarcheAvant()`, `tournegauche()`, `coup_poing()`, etc.).

```cpp
#define BUZZER_PIN D0
#define POMPE_DROITE_PIN D4
#define POMPE_GAUCHE_PIN D5

#define REMOTEXY_BLUETOOTH_NAME "Minitto"
#define REMOTEXY_ACCESS_PASSWORD "VOTRE_MOT_DE_PASSE"

Servo Servo1; // jambe gauche
Servo Servo2; // pied gauche
Servo Servo3; // pied droit
Servo Servo4; // jambe droite
Servo Servo5; // bras droit
Servo Servo6; // bras gauche
```

Le programme principal tient en quelques lignes :

```cpp
void setup() {
  RemoteXY_Init();
  init_avec_pompe();        // servos à 90° et pompes allumées
  RemoteXY_delay(500);
  stop_sansacti_pompe();    // puis pompes éteintes
  // son_start();           // désactivé : voir « Le bug du démarrage »
}

void loop() {
  RemoteXYEngine.handler();
  mode_de_marche = modif_bouton_sansacti_pompe(mode_de_marche); // lit les boutons
  choix_joystick(mode_de_marche, roulement_de_marche);          // lit le joystick
  RemoteXY_delay(1);
}
```

### L’interface sur smartphone

L’application RemoteXY propose :

- **un joystick** : quatre zones (avant, arrière, gauche, droite), plus simple à programmer qu’un contrôle proportionnel ;
- **un sélecteur** qui change le rôle des **deux boutons**. On obtient plein de commandes avec très peu de boutons.

| Position du sélecteur | Bouton 1 | Bouton 2 |
|---|---|---|
| 0 | Haka | Accroupi |
| 1 | Coup de poing gauche | Coup de poing droit |
| 2 | Armer le poing gauche | Armer le poing droit |
| 3 | Marche **avec** pompes | Marche **sans** pompes |
| 4 | Couper la pompe droite | Couper la pompe gauche |
| 5 | Libre (réservé) | Libre (réservé) |

<!--
📷 CAPTURE 11 :
Une capture d’écran de l’application RemoteXY sur ton téléphone, avec le joystick,
le sélecteur et les deux boutons. Si possible, ajoute des flèches avec une légende.

![Interface RemoteXY]({{ '/assets/images/minitto/interface-remotexy.png' | relative_url }})

⚠️ À VÉRIFIER : dans le fichier .ino que tu m’as envoyé, les sons (musique, « pet »)
et les animations (saut) ne sont pas reliés au sélecteur dans le `loop` actuel (seuls le haka,
l’accroupissement, les poings et les pompes le sont). Si ta version de compétition avait
d’autres positions, modifie le tableau.
-->

## La marche

### Inspiration : les manchots

Comme Otto, Minitto n’a que **deux articulations par jambe** (jambe et pied), comme les manchots. J’ai essayé de **reproduire leurs mouvements aussi fidèlement que possible**. Ils sont **saccadés** : les mouvements se font par paliers de quelques angles, sans interpolation.

### Marche avec pompes : toujours une ventouse au sol

Un cycle de marche avant dure environ **5,6 secondes**, dont l’essentiel est consacré à **relâcher la ventouse** (attendre que l’air rentre) :

1. Les deux ventouses sont actives.
2. On coupe la pompe **gauche** et on attend 2 s que la ventouse lâche.
3. Les pieds s’inclinent et les jambes pivotent.
4. Les pieds reviennent à plat et la pompe gauche se rallume.
5. Même séquence côté droit.

```cpp
void MarcheAvant_pompe_majorite_gauche() {
  stop_pompe();                           // neutre, les deux ventouses actives
  pompe_gauche_eteindre();                // on relâche la ventouse gauche...
  RemoteXY_delay(2000);                   // ...et on attend que l’air rentre
  Servo3.write(110 + OFFSET_SERVO_3);
  Servo2.write(130 + OFFSET_SERVO_2);     // les pieds s’inclinent
  RemoteXY_delay(150);
  Servo1.write(50 + OFFSET_SERVO_1);
  Servo4.write(50 + OFFSET_SERVO_4);      // les jambes pivotent
  Servo2.write(110 + OFFSET_SERVO_2);
  RemoteXY_delay(150);
  Servo2.write(90 + OFFSET_SERVO_2);
  Servo3.write(90 + OFFSET_SERVO_3);      // retour des pieds à plat
  pompe_gauche_allumer();                 // la ventouse gauche s’accroche
  RemoteXY_delay(500);
  // ... même séquence pour le côté droit
}
```

Le zéro mécanique des servos est calibré à la main (tous les `OFFSET_SERVO_x` sont à 0). Après quelques essais, la **dérive** du robot était corrigée, donc il n’y a **pas d’alternance** entre les variantes « majorité gauche » et « majorité droite ».

### Marche sans pompes

Plus rapide : les pieds s’inclinent et les jambes pivotent sans attendre les pompes (un cycle dure environ une seconde).

### Vitesses mesurées

| Mode | Vitesse |
|---|---|
| Avec pompes | 1 m en 6 min 47 s |
| Sans pompes | 1 m en 35 s |

<!--
📷 SCHÉMA 2 (ou 4 photos) :
La marche en 4 temps vue de côté : (1) ventouses actives, (2) pied gauche relevé,
(3) jambes en avant, (4) pied reposé. Soit 4 photos de Minitto en pause aux positions clés,
soit 4 petits dessins avec une flèche pour indiquer le sens.
Pour la photo : maintiens le robot à la main dans chaque position.
-->

## Le bug du démarrage

### Symptôme

Au démarrage, les servos partaient parfois dans **toutes les directions** au lieu de se placer à 90°.

### Cause

Le **buzzer** était branché sur la broche **D0**, qui est une broche de **« strapping »** de l’ESP32-C3 : son état au démarrage influence le mode de boot de la puce. En jouant un petit son au démarrage, le buzzer agissait sur cette broche **au mauvais moment** : l’ESP32 ne démarrait plus normalement et les servos recevaient des ordres incohérents.

### Solution

J’ai **supprimé le son de démarrage** (`son_start()` est commenté dans `setup()`). Depuis, les servos se placent correctement.

> **Leçon** : sur un ESP32, toujours vérifier à quoi sert chaque broche avant de brancher quelque chose dessus.

## Les poings qui cassent

Les règles interdisent de **perdre une pièce** du robot pendant un combat. J’ai donc ajouté un **élément bloquant** qui arrête le poing en fin de course. Mais lors des tests, après **une dizaine de coups**, cette pièce en plastique se cassait.

J’ai ajouté une sorte d’**airbag en TPU** qui absorbe le choc et le répartit avant qu’il n’atteigne la partie rigide. Les prototypes suivants ont tenu.

<!--
📷 PHOTO 12 (facultative mais très parlante) :
Une photo d’une pièce cassée d’un de tes premiers prototypes à côté de la pièce finale
(avec la pièce TPU). Si tu as gardé la pièce cassée, c’est parfait pour raconter l’histoire.
-->

## Ce que j’aurais aimé améliorer

- **Ultrasons** : le capteur est prévu mais non exploité. Il devait automatiser des épreuves (course de vitesse, évitement d’obstacles). Les professeurs m’ayant autorisé à piloter à la main, je n’ai pas eu le temps de le coder.
- **Marche fluide** : remplacer les mouvements par paliers par un déplacement **degré par degré**, avec un délai réglable entre chaque degré.
- **Poings** : une **recharge automatique** (aujourd’hui, on arme à la main) n’était pas possible dans la place disponible sans perdre en puissance.
- **Carte électronique** : avec l’expérience acquise à la fin du projet, je dessinerais **ma propre carte**, adaptée à ce robot.

## Ressources et fichiers

- 📘 [Otto-MKS, Makerspace d’Amiens](https://doc.makerspace-amiens.fr/workshops/otto-mks/) : tutoriels, carte électronique et modèle 3D d’origine, publics sur le GitHub du Makerspace.
- 🤖 Projet d’origine : **Otto DIY**.

[Carte électronique]({{ '/journal/' | relative_url }}){: .btn .fs-5 .mb-4 .mb-md-0 }
[Code du firmware]({{ '/journal/' | relative_url }}){: .btn .fs-5 .mb-4 .mb-md-0 }
[Fichiers d’impression]({{ '/projets/minitto/' | relative_url }}){: .btn .fs-5 .mb-4 .mb-md-0 }

[Revenir en arrière]({{ '/projets/' | relative_url }}){: .btn .fs-5 .mb-4 .mb-md-0 }