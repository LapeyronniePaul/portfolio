---
title: Minitto
parent: Projets
nav_order: 1
---

# Minitto
{: .no_toc }

> Robot marcheur à base d'ESP32, piloté en Bluetooth depuis un smartphone, capable de s'accrocher grâce à des ventouses.

<img class="illustration" src="{{ '/assets/images/minitto.svg' | relative_url }}" alt="Minitto">

<!-- À MODIFIER : remplace l'image minitto.svg par une photo de ton robot (voir README) -->

## Présentation

Minitto est un robot marcheur dont le cerveau est un **ESP32**. Il se pilote en **Bluetooth Low Energy (BLE)** depuis une application smartphone créée avec **RemoteXY**.

Il se déplace grâce à **6 servomoteurs** (2 jambes, 2 pieds et 2 bras) et utilise **deux pompes à air reliées à des ventouses** pour s'accrocher pendant la marche.

*À compléter : pourquoi ce projet, ce qui t'a donné l'idée, ce que tu voulais apprendre.*

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
| Microcontrôleur | ESP32 |
| Servomoteurs | 6 (2 jambes, 2 pieds, 2 bras) |
| Ventouses | 2, actionnées par 2 pompes à air |
| Capteur | Ultrasons |
| Autres | Buzzer |
| Alimentation | *à compléter* |

## Logiciel

- Firmware en C++ (Arduino) pour ESP32
- Application de contrôle : RemoteXY, connexion BLE
- Dépôt du code : *à compléter (lien GitHub ou fichier ci-dessous)*

## Difficultés rencontrées

- Au démarrage, les servomoteurs pouvaient partir dans des positions incohérentes au lieu de se placer à 90° comme prévu dans le code d'initialisation. *À compléter : comment tu l'as résolu.*

## État d'avancement

**Statut :** en cours *(modifie si besoin)*

## Fichiers

*À compléter : mets tes fichiers (code, schémas, photos, PDF) dans le dossier `docs/projets/minitto/` puis ajoute un lien ici, par exemple :*

```
[Code du firmware](minitto.ino)
[Schéma de câblage](cablage.pdf)
```

## Prochaines étapes

- [ ] À compléter
