---
description: Cette page expliquera comment fonctionnent les entraînements
cover: ../../.gitbook/assets/entrainements.jpg
coverY: 0
---

# Entrainements

## 1 \~ Lancer un entraînement

L'entraînement permet aux joueurs d'améliorer leurs statistiques et de devenir plus puissant. Lancer un entraînement est une chose très simple. Il suffit simplement de faire la commande `<prefix>train` et de spécifier le nom de l'aptitude à améliorer. Voici un exemple ci-dessous :&#x20;

![](https://cdn.discordapp.com/attachments/958432552044097536/993530945640615956/unknown.png)

Pour améliorer vos aptitudes à un certain niveau, vous devez avoir l'expérience nécessaire. Par exemple, pour monter sa force au niveau 4, il faut être niveau 3 minimum en expérience, et ceci pour toutes les aptitudes.

## 2 \~ Les paliers

Durant les combats, pour éviter un déséquilibre, des paliers de niveaux sont mis en places. C'est avec ses paliers que la force et la défense de combat sont calculés. Voici un petit tableau récapitulatif des premiers paliers :&#x20;

| Palier 1                                     | Palier 2                                  |
| -------------------------------------------- | ----------------------------------------- |
| <p>Puissance: 10</p><p>Intervalle: 10~30</p> | <p>Puissance: 20<br>Intervalle: 31~60</p> |

| Palier 3                                  | Palier 4                                   |
| ----------------------------------------- | ------------------------------------------ |
| <p>Puissance: 30<br>Intervalle: 61~90</p> | <p>Puissance: 40<br>Intervalle: 91~120</p> |

Et ce schéma ce complète à l'infini pour tout niveau. Les seules aptitudes concernées sont la force et la défense. L'intervalle ici représente l'aptitude après application des bonus des corbeaux et du grimoire, ainsi que celui de la catégorie. (et ne prend pas que en compte le niveau).

{% hint style="info" %}
Voici pour les petits curieux la formule mathématique JavaScript du calcul des puissances de paliers ainsi que celle qui calcule votre intervalle :&#x20;
{% endhint %}

{% code title="aptitudes_calc.js" %}
```javascript
// ici force et defense représentent la puissance du palier
const force = Math.ceil(playerAttacking.aptitudes.force / 30) * 10;
const defense = Math.ceil(playerDefending.aptitudes.defense / 30) * 10;

// --------------------------------------------------//

// ici il y a les formules pour chaque aptitude
const force = player.stats.force * 10 * grimoireBoost * crowBoost
const defense = player.stats.defense * 10 * grimoireBoost * crowBoost
const speed = player.stats.speed * 10 * grimoireBoost * crowBoost
const agility = player.stats.agility * 10 * grimoireBoost * crowBoost
```
{% endcode %}

## 3 \~ Durée d'un entraînement

Les entraînements durent au minimum 30 minutes par aptitude, et le temps augmente à chaque niveau. Pour connaitre le temps d'entraînement d'une aptitude, faites :&#x20;

{% code title="training_time.txt" %}
```
temps = 15 + (15 x niveauAptitude)
```
{% endcode %}

## 4 \~ Récompenses d'un entraînement

Les entraînements donnent toujours entre 100 et 250 d'expérience. Cette quantité peut varier en fonction des bonus actifs ou non (grimoires ou corbeaux).
