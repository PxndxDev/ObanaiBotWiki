---
description: >-
  Vous aimez vous battre ? Un bot Demon Slayer sans combat, est-ce vraiment
  fidèle à l'œuvre ? Bien sûr que non. Prenez vos meilleures armes, et
  battez-vous !
cover: ../.gitbook/assets/arènes.jpg
coverY: 35.87878787878788
---

# Arènes

## 1 \~ Explication principale de la mécanique

Les arènes sont un système de combat interactif à travers lequel des joueurs s'affrontent. Les combats se font en équipe (1 par équipe en cas de 1 contre 1), mais chaque équipe peut accueillir jusqu'à 4 joueurs. Rien que ça.

### Les rotations

Pour que les combats restent équilibrés malgré le nombre de joueurs, un système de rotation est en place. Pour éviter les gros pavés explicatifs, nous avons conçu pour vous un schéma simplifié pour comprendre comment il fonctionne :&#x20;

```
Attaquant = Joueur Équipe(1) aléatoire
Défenseur = cible visée par Attaquant (SI plusieurs adversaires possible)
```

On vous l'accorde, en réalité c'était très simple à comprendre.&#x20;

## 2 \~ Lancer une arène

Pour lancer une arène, il suffit de faire la commande `<prefix>fight` et de mentionner les joueurs à inviter (ou de saisir leur pseudonyme/identifiant). Pour créer deux équipes, séparez les noms des joueurs avec les caractères `&&` afin de démarquer les deux camps.

Voici des exemples :&#x20;

{% tabs %}
{% tab title="Combat 1 contre 1" %}
![](https://cdn.discordapp.com/attachments/958432585585934406/993982175676469419/unknown.png)
{% endtab %}

{% tab title="Combat 1 contre 2+" %}
![](https://cdn.discordapp.com/attachments/958432585585934406/993982583832584255/unknown.png)
{% endtab %}

{% tab title="Combat 2+ contre 1+" %}
![](https://cdn.discordapp.com/attachments/958432585585934406/993982927262187651/unknown.png)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Par défaut l'auteur du message se trouve automatiquement dans la première équipe.
{% endhint %}

Pour qu'un combat puisse être lancé, tous les joueurs impliqués doivent répondre favorablement au bot, même l'auteur de la commande.

## 3 \~ Variables

Durant votre combat, vous devez prêter attention à deux éléments ; votre stamina et vos points de vie. Vous devez trouver la stratégie idéale pour ne pas gaspiller trop de stamina, sans pour autant mettre vos points de vie en danger.&#x20;

Votre stamina monte ou baisse en fonction de vos choix, et sert de bride pour vos attaques et défenses.

Vos points de vie sont votre moteur. Tant qu'ils sont supérieurs à 0, vous restez en jeu. Ils ne peuvent pas remonter, alors faites vos choix avec parcimonie.

Durant les combats, il y a des variables secondaires présentes en arrière-plan. Premièrement, le ratio de contre qui définit le pourcentage de chance du défenseur de contrer votre attaque et de renvoyer des dégâts. Il y a également le ratio de fail, qui définit vos chances de rater votre attaque ou votre défense.

## 4 \~ Phase d'Attaque

Lorsque c'est à votre tour, quand la rotation vous a sélectionné comme attaquant, vous devez faire un choix. Il y a des informations partout, des données partout, et vous ne savez pas quoi faire.

Voici comment ça marche.

### A. Affichage

La page du choix d'attaque ressemble à ça :&#x20;

![](../.gitbook/assets/attaque\_base.png)

En premier lieu s'affiche le numéro du tour ainsi que les dégâts infligés lors du tour précédent (si tour précédent il y a). Puis apparaissent ensuite les points de vie et la stamina de l'attaquant (vous) et de votre cible (défenseur).

Viennent ensuite les choix.

### B. Les choix primaires

{% tabs %}
{% tab title="L'attaque rapide" %}
**Emoji : 👊**\
****\
****L'attaque rapide régénère de l'endurance et convertit un faible pourcentage de votre force en dégâts. C'est un choix utile pour temporiser et regagner en stamina, mais peut également être fort pour feinter son adversaire.

**Données mathématiques :**&#x20;

```
dégâts = 55% force
stamina = +1
```
{% endtab %}

{% tab title="L'attaque chargée" %}
**Emoji : 💥**\
****\
****L'attaque chargée est une attaque puissante qui renvoie une plus grande quantité de dégâts que l'attaque rapide. Elle coûte cher en endurance, mais est très rentable pour mettre la pression sur l'adversaire sans trop dépenser.

**Données mathématiques :**&#x20;

```
dégâts = 65% force
stamina = -2
ratio de fail = +10%
```
{% endtab %}

{% tab title="L'attaque prudente (ou anti-contre)" %}
**Emoji : ❄️**\
\
L'attaque prudente ou anti-contre est une attaque très stratégique qui réduit drastiquement le taux de contre du défenseur. Elle fait des dégâts moyens et coûte peu de stamina. Cette attaque est très forte pour feinter son adversaire, ou assurer des petits dégâts.

**Données mathématiques :**&#x20;

```
dégâts = 50% force
stamina = -1
ratio de contre = -30%
```
{% endtab %}

{% tab title="L'attaque spéciale" %}
**Emoji : 💀**\
\
L'attaque spéciale ou ultime est l'attaque la plus puissante du jeu. Avec un coût à 5 de stamina, elle renvoie d'énormes dégâts. Cependant assurez-vous que la défense de votre adversaire est basse, car en cas de raté, vous serez dans un gros désavantage.

**Données mathématiques :**&#x20;

```
dégâts = 90% force
stamina = -5
ratio de fail = +20%
```
{% endtab %}
{% endtabs %}

### C. Les choix secondaires

{% tabs %}
{% tab title="Changer de cible" %}
**Emoji : 🎯**\
\
Le changement de cible est un choix à part entière très puissant, car il permet de choisir la cible que vous souhaitez attaquer. Lorsque vous cliquez sur le bouton, vous choisissez votre nouvelle cible et vous pouvez ensuite choisir votre attaque. Voici un exemple illustré :&#x20;

![](https://cdn.discordapp.com/attachments/992872062546874498/993995746070249573/unknown.png)
{% endtab %}

{% tab title="Abandonner" %}
**Emoji : 🧽**\
\
Ce choix... Est simple. Vous cliquez, vous confirmez, ou pas, et... C'est tout.
{% endtab %}
{% endtabs %}

Cependant, votre cible sait se défendre, et c'est pour cela que nous allons voir les différents choix défensifs. Car même après avoir déterminé le nombre de dégâts brutes que vous allez mettre, il faut prendre en compte l'encaissement de l'adversaire.

## 5 \~ Phase de Défense

Lorsque c'est à vous de défendre, vous ne connaissez bien évidemment pas le choix de votre attaquant. L'affichage du panel est semblable à celui de l'attaque.&#x20;

### A. Affichage

Voyez par vous-même :&#x20;

![](../.gitbook/assets/défense\_base.png)

L'organisation des données est le même que pour l'attaque, si vous ne vous en rappelez-plus, on vous y emmène [ici](arenes.md#4-phase-dattaque).&#x20;

### B. Les choix primaires

{% tabs %}
{% tab title="La défense rapide" %}
**Emoji : 🛡️**

\
La défense rapide est une défense risquée mais optimale pour temporiser dans un combat. Elle restaure la stamina et contre presque parfaitement des petites attaques.

**Données mathématiques :**&#x20;

```
encaissement = 50% défense
stamina = +1
ratio de contre = +5%
```
{% endtab %}

{% tab title="La défense chargée" %}
**Emoji : 💥**\
\
La défense chargée est une défense coûteuse mais très efficace. Elle encaisse une majeure partie des dégâts peu importe l'attaque. Cependant, attention à ne pas vous rater, car elle peut vous causer du tord.

**Données mathématiques :**&#x20;

```
encaissement = 75% défense
stamina = -2
ratio de contre = +5
ratio de fail = +10%
```
{% endtab %}

{% tab title="Le contre" %}
**Emoji : ☄️**\
\
Cette défense est sans doute une des plus dure à maîtriser. Elle coûte peu de stamina, ne possède pas un grand encaissement, mais possède un potentiel de dégâts énorme. Elle peut renvoyer à l'attaquant des dégâts assez élevés pour retourner une situation dangereuse.

**Données mathématiques :**&#x20;

```
encaissement (si pas contré) = 40% défense
stamina = -1
ratio de contre = +25%
ratio de fail = +10%
dégâts de contre = 40% force (défenseur) - 15% défense (attaquant)
```
{% endtab %}
{% endtabs %}

### C. Les choix secondaires

Il n'y a qu'un seul choix secondaire : jeter l'éponge, abandonner, déclarer forfait... Peu importe comment vous l'appelez. Vous n'allez jamais l'utiliser, pas vrai, parce que vous êtes courageux ! (ou pas ?)

## 6 \~ Les fins d'arène

Lorsqu'un joueur périt ou déclare forfait, il se retrouve exclu de son équipe. Lorsqu'une équipe ne contient plus aucun joueur, l'autre équipe est déclarée vainqueur, et tous ses joueurs encore en vie bénéficient des bonus de victoire.

Voici un exemple illustré ci-dessous :&#x20;

![](https://cdn.discordapp.com/attachments/992872062546874498/994004695922266112/unknown.png)
