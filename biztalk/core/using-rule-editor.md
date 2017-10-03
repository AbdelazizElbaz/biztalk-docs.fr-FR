---
title: "À l’aide de la règle d’éditeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Rule Editor [Business Rule Composer], about Rule Editor
- Rule Editor [Business Rule Composer], Conditions Editor
- Business Rule Composer, Rule Editor
- Rule Editor [Business Rule Composer], Actions Editor
- Rule Editor [Business Rule Composer]
ms.assetid: 6559a8d1-6caf-4c6e-ac80-acaa4eb57938
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57041914d688b8d0dbe2bd0558e8572878218164
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-rule-editor"></a>À l’aide de la règle d’éditeur
L'Éditeur des règles permet d'afficher et de modifier les conditions (dans l'Éditeur des conditions) et les actions (dans l'Éditeur des actions) qui correspondent à la règle sélectionnée.  
  
## <a name="conditions-editor"></a>Éditeur des conditions  
 Utilisez l'Éditeur des conditions (qui fait partie de l'Éditeur des règles) pour consulter et modifier les conditions de déclenchement des règles. Vous pouvez ajouter des prédicats intégrés à l’aide du menu contextuel, faire glisser des éléments depuis l’Explorateur de faits pour définir des arguments et des prédicats et entrer en ligne de valeurs d’argument en cliquant sur un lien d’argument.  
  
 Utilisez le menu contextuel pour accéder aux options ci-dessous.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Ajouter le AND logique**|Ajouter un opérateur pour combiner deux ou plusieurs prédicats pour former un opérateur logique **AND** expression.|  
|**Ajouter ou logique**|Ajouter un opérateur pour combiner deux ou plusieurs prédicats pour former un opérateur logique **OR** expression.|  
|**Ajouter le NOT logique**|Ajoutez l’opérateur **pas** pour exclure un prédicat ou une expression logique.|  
|**Prédicats**|Ajouter une expression de prédicat basée sur l’un des prédicats intégrés fournis par le modèle d’objet de règle, tels que les **est égal à** opérateur.|  
|**Prédicats \ après**|Représenter le prédicat temporel qui répond à la question « time1 se situe-t-il chronologiquement après time2 ? ».|  
|**Prédicats \ avant**|Représenter le prédicat temporel qui répond à la question « time1 se situe-t-il chronologiquement avant time2 ? ».|  
|**Prédicats \ entre**|Représenter le prédicat temporel qui répond à la question « time1 se situe-t-il chronologiquement entre time2 et time3 ? ».|  
|**Prédicats \ égal**|Représenter l'opérateur relationnel d'égalité.|  
|**Prédicats \ existe**|Représenter le prédicat d'existence de l'attribut ou de l'élément XML utilisé dans les conditions de règle.|  
|**Prédicats \ supérieurà**|Représenter l'opérateur relationnel supérieur à.|  
|**Prédicats \ Supérieurégalà**|Représenter l'opérateur relationnel supérieur ou égal à.|  
|**Prédicats \ LessThan**|Représenter l'opérateur relationnel inférieur à.|  
|**Prédicats \ Inférieurégalà**|Représenter l'opérateur relationnel inférieur ou égal à.|  
|**Prédicats \ correspondance**|Déterminer si une expression régulière est présente dans une chaîne d'entrée spécifique.|  
|**Prédicats \ NotEqual**|Représenter l'opérateur relationnel d'inégalité.|  
|**Prédicats \ plage**|Tester si une valeur est comprise dans une plage.|  
|**Supprimer l’opérateur logique**|Supprimer l’opérateur logique sélectionné (**AND**, **OR**, ou **pas**).|  
|**Supprimer le prédicat**|Supprimer le prédicat sélectionné.|  
|**Monter**|Déplacer le prédicat d'une position ou d'un niveau vers le haut.|  
|**Descendre**|Déplacer le prédicat d'une position ou d'un niveau vers le bas.|  
|**Atteindre le vocabulaire**|Trouver, dans l'Explorateur de faits, la définition de vocabulaire qui correspond à l'argument ou au prédicat sélectionné.|  
|**Atteindre le fait source**|Rechercher, dans l'Explorateur de faits, l'élément XML, la colonne de base de données ou la méthode .NET qui correspond à l'argument ou au prédicat sélectionné.|  
|**Réinitialiser l’argument**|Supprimer l'argument sélectionné (et tout argument imbriqué associé) et rétablir la définition initiale.|  
|**A la valeur null**|Remplacer l'argument sélectionné par une définition constante de type Null.|  
|**Chaîne vide**|Remplacer l'argument sélectionné par une valeur de chaîne vide.|  
  
## <a name="actions-editor"></a>Éditeur des actions  
 L'Éditeur des actions (qui fait partie de l'Éditeur des règles) permet de consulter et de modifier les actions à exécuter lors du déclenchement d'une règle. Vous pouvez ajouter des actions intégrées à l’aide du menu contextuel, faire glisser des éléments à partir de l’Explorateur de faits pour définir des actions et des arguments et entrer en ligne de valeurs d’argument en cliquant sur un lien d’argument.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Supprimer l’action**|Supprimer l'action sélectionnée.|  
|**Atteindre le vocabulaire**|Trouver, dans l'Explorateur de faits, la définition de vocabulaire qui correspond à l'action ou à l'argument sélectionné.|  
|**Atteindre le fait source**|Trouver, dans l'Explorateur de faits, la méthode .NET, la colonne de base de données ou l'élément XML qui correspond à l'action ou à l'argument sélectionné.|  
|**Monter**|Déplacer l'action d'une position ou d'un niveau vers le haut.|  
|**Descendre**|Déplacer l'action d'une position ou d'un niveau vers le bas.|  
|**Réinitialiser l’argument**|Supprimer l'argument sélectionné (et tout argument imbriqué associé) et rétablir la définition initiale.|  
|**A la valeur null**|Remplacer l'argument sélectionné par une définition constante de type Null.|  
|**Chaîne vide**|Remplacer l'argument sélectionné par une valeur de chaîne vide.|  
|**Fonctions**|Ajouter un argument basé sur l’une des fonctions intégrées fournies par le modèle d’objet de règle, tels que les **ajouter** opérateur.|  
|**Assert**|Ajouter un nouveau fait dans la mémoire de travail de l'instance du moteur de règles.|  
|**Retrait**|Supprimer un fait de la mémoire de travail de l'instance du moteur de règles.|  
|**RetractByType**|Supprimer un fait d'un type particulier de la mémoire de travail de l'instance du moteur de règles.|  
|**Désactiver**|Réinitialiser la mémoire de travail et l'agenda de l'instance du moteur de règles.|  
|**Arrêter**|Mettre fin au processus.|  
|**Update**|Mettre à jour un fait de la mémoire de travail de l'instance du moteur de règles.|  
  
## <a name="output-window"></a>fenêtre Sortie  
 La fenêtre Sortie permet d'afficher les résultats du test réalisé sur une version de stratégie sélectionnée.  
  
 Utilisez le menu contextuel pour accéder aux options ci-dessous.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Effacer tout**|Supprimer tout le texte affiché dans la fenêtre Sortie.|  
|**Copier**|Copier dans le Presse-papiers le texte sélectionné dans la fenêtre Sortie.|  
|**Tout sélectionner**|Sélectionner tout le texte contenu dans la fenêtre Sortie.|  
|**Enregistrer dans un fichier**|Enregistrer le texte de la fenêtre Sortie dans un fichier spécifié.|