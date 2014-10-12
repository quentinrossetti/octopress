---
layout: post
title: "Translate custom folder in OSX"
date: 2014-10-08 19:06:13 +0000
comments: true
categories: [OSX, I18n]
---

Sous Mac OSX chaque dossier a des propriétés : ses permissions (droits de lecture, écriture), son icône, ou encore son nom *traduit*. Dans cet article il sera question de cette dernière propriété.

## Comprendre les chemins localisés

Prenons comme exemple le dossier utilisateur. En tant qu'utilisateur français les noms des dossiers sont "Bureau", "Documents", "Images".

<img src="{{ root_url }}/images/001-finder-perso.png" alt="Finder" />

Pourtant si l'on ouvre un *Terminal* (dans *Spotlight* tapez "Terminal" pour l'ouvrir) et que l'on rentre la commande `ls` on remarque que les noms des dossiers sont en anglais ("Desktop", "Documents", "Pictures").

<img src="{{ root_url }}/images/001-terminal-perso.png" alt="Terminal" />

Pour opérer cette traduction le Finder dispose de fichiers de traduction.

## Créer ses propres dossiers traduits

Ce ficher de traduction peut être édité pour modifier ou ajouter vos propres traductions. Par exemple dans les images précédentes j'ai crée un dossier "Development" avec la commande `mkdir Development`. Pour le traduire en "Développement" il faut modifier le ficher `/System/Library/CoreServices/SystemFolderLocalizations/fr.lproj/SystemFolderLocalizations.strings` avec votre éditeur de texte favoris.

<img src="{{ root_url }}/images/001-strings.png" alt="Editeur" />

Comme vous pouvez le voir il est très facile de modifier des traductions existantes ou d'en rajouter soi-même.

## Pour les dossiers en dehors du dossier personnel

La technique si dessus est cependant limité aux seuls dossiers situés directement dans le dossier personnel (c'est à dire `/Users/<you>`). Il y a une méthode pour surmonter cela.

  * Créez votre dossier avec le vrai nom en utilisant la ligne de commande (`mkdir MyDir.localized`)
  * Dans ce répertoire créez-en un autre `mkdir .localized`
  * Ensuite vous créez des fichiers texte nommés `fr.strings` ou `it.string` par exemple dans ce dossier
  * Ces fichiers contiennent vos traductions dans ce format: `"MyDir" = "Mon Dossier";`
  
Cette dernière technique est issue de la documentation des développeurs Mac dans [cet article](https://developer.apple.com/library/mac/documentation/MacOSX/Conceptual/BPInternational/Articles/LocalizingPathnames.html).

## Conclusion

Avec OSX vous pouvez sans trop de difficulté changer et même créer vos propre traduction.