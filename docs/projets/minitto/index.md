---
title: Minitto
parent: Projets
nav_order: 1
---

# Minitto
{: .no_toc }
 
> Robot de combat sumo à base d'ESP32, piloté en Bluetooth depuis un smartphone, capable de marcher sur deux jambes s'accrocher grâce à des ventouses.

<img class="illustration" src="{{ '/assets/images/Minitto.png' | relative_url }}" alt="Minitto">

## Présentation

Ce robot prend place au seins d'un concour de robotique organisé par mon école que vous retrouverz sur le site Makerspace Amiens. 

liens vers le site : 

Pour participer a ce concour on nous a donner une carte électronique et une base modéliser en 3D.

A partir de cette base, l'objectif était de modifier le model pour avoir le meilleur robot au :
- tire a la corde
- course de vitesse
- combat de sumo
- évitement d'obstacle

Minitto est un robot marcheur dont le cerveau est un **ESP32-C3**. Il se pilote en **Bluetooth Low Energy (BLE)** depuis une application smartphone créée avec **RemoteXY**.

Il se déplace grâce à **4 servomoteurs** (2 jambes et 2 pieds) et utilise **deux pompes à air reliées à des ventouses** pour s'accrocher au sol pendant la marche. Il est par conséquent très lent mais est pratiquement impossible a décrocher.

j'ai penser ce robot pour qu'il soit fort au combat de sumo, au tire a la corde et en évitement d'obstacle.

Pour qu'il soit fort au **combat de sumo**, j'ai dans un premier temps décider de lui ajouter des **fulguro poing**. 
### ![alt text](fulguro_poing.png)
cette idée m'est venu en penssant a un robot de combat : goldorak. J'ai donc dévelloper cette idée mais quand j'ai regarder les idée de mes adversaires, j'ai compris que je devais contrer l'idée de tous mes adversaires les plus dangereux en les empechant de me soulever avec un bras pelteuse, la meilleur idée qui m'est venu a donc été de me fixer au sol avec des **pompes a aires** et des **ventouses**.

pour le **tire a la corde**, les **ventouses** empecherais que mes adversaires puissent me déplacer et il me sufirait donc de seulement **reculer en prenant soin de toujours garder un pied ventouser** et en reculant petit a petit.

pour l'évitement d'obstacle, j'ai ajouter un **détecteur a ultrason** me permetant de connaitre précisément l distance netre l'obstacle et le robot et donc me permetre de réagir plus rapidement en cas de danger de choque.

## Fonctionnalités

- Pilotage à distance en Bluetooth (BLE) depuis l'application RemoteXY
- Marche à l'aide de 2 jambes et 2 pieds articulés
- 2 bras actionnés par servomoteurs
- Accroche par ventouses et pompes à air pendant la marche
- Capteur à ultrasons pour détecter les obstacles
- Buzzer sonore

## Matériel

| Élément | Détail |
|---------|--------|
| Microcontrôleur | ESP32-C3 |
| Servomoteurs-mini | 6 (2 jambes, 2 pieds, 2 bras) |
| Ventouses | 2, actionnées par 2 pompes à air |
| Capteur | Ultrasons |
| haut-parleur | Buzzer |
| Alimentation | pile 9V + un régulateur 5V |
| mini-pompes à air | 2 (1 / jambe) |
| impression 3D | PLA (bambu LAB A1 mini) |

## Logiciel

- Firmware en C++ (ArduinoIDE) pour ESP32
- Application de contrôle : RemoteXY, connexion BLE
- Dépôt du code : *à compléter (lien GitHub ou fichier ci-dessous)*

## Difficultés rencontrées

- Au démarrage, les servomoteurs pouvaient partir dans des positions incohérentes au lieu de se placer à 90° comme prévu dans le code d'initialisation. 
ce problème provenais de la construction de la carte, le buzzer était conecter au pin 0 qui est un pin de straping sur l'ESP32 C3. Au lancement du robot, le pin recevais du courant ce qui réecrivais le code et déreglais faisait partir les servos moteurs dans tous les sens.

- le mouvement de marche avant, arrière, gauche, droite a été long et complexe a coder car il a falut faire beaucoup de test, a chaque modifications, j'ai du retester le code, corriger les erreurs, retester ... et cela jusqu'a temp que le robot ce déplace rapidement le plus droits possible et de manière constante.

- J'ai eu du mal a coder l'évitement d'obstacle de manière automatique, car il falait etre capable de diférentier un obstacle d'un mur et ensuite choisir comment éviter l'obstacle de la manière la plus optimisé.



## État d'avancement

**Statut :** terminé

## Fichiers

*À compléter : mets tes fichiers (code, schémas, photos, PDF) dans le dossier `docs/projets/minitto/` puis ajoute un lien ici, par exemple :*

```
[Code du firmware](minitto.ino)
[Schéma de câblage](cablage.pdf)
```


