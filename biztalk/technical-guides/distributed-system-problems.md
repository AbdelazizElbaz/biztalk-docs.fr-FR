---
title: "Distributed problèmes système | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 287b0adb-d5f9-4e47-80f8-0ba5d90c7864
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24abe471a66e8bc0724ad731388c5a0e7c07b573
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="distributed-system-problems"></a>Problèmes de systèmes distribués
Les travaux de restauration ne sont pas connaissance des erreurs ou des problèmes sur les autres ordinateurs dans un système distribué de destination. Par exemple, supposons que l’ordinateur A restaurer la base de données de gestion BizTalk et la base de données des suivis BizTalk et ordinateur B restaure la base de données MessageBox de BizTalk. Les deux ordinateurs restaurer correctement les jeux de sauvegarde 1 à 25. Ensemble 26, toutefois, comporte un fichier de sauvegarde de journal endommagé de la base de données MessageBox de BizTalk. Ordinateur A restaure ses bases de données correctement, mais l’ordinateur B échoue restaurer le fichier endommagé.  
  
 Dans ce cas, force une sauvegarde complète sur le système source. Poursuivre l’exemple ci-dessus, supposons que le problème a été identifiée et une sauvegarde complète a été créée pour le jeu de 35. Ordinateur A puis restaurations jeux 26 à 34, car il n’est pas conscient du problème sur l’ordinateur B. ordinateur B échouera jusqu'à ce qu’il voit 35 du jeu de sauvegarde complète et 36 (n’oubliez pas que ceci doit toujours être une sauvegarde de journal complet suivantes pour un jeu soit restauration du jeu de sauvegarde de journal suivante d). Lorsque les jeux de 35 et 36 arrive sur l’ordinateur B, il se corrigera d’elle-même à l’aide de 35. Une fois la réparation terminée, les ordinateurs A et B seront synchronisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes d’envoi de journaux](../technical-guides/troubleshooting-log-shipping.md)