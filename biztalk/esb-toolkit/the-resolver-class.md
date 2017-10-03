---
title: La classe Resolver | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9ebd6c2-fd86-471a-bc50-b1b89f701fab
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1359bcbb9c6c918fc0ee6d5e67bacb8e3559c84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-resolver-class"></a>La classe de programme de résolution
Le **résolveur** classe est une structure simple qui expose une paire nom/valeur. Le service Web du programme de résolution retourne une collection générique d’instances de cette classe à partir de ses méthodes.  
  
 Le programme d’installation ESB Core installe et enregistre le **Microsoft.Practices.ESB.Resolver.dll** assembly avec la classe de programme de résolution dans le global assembly cache.  
  
 L’utilisation d’une nom/valeur basée sur le dictionnaire approche rend plus faciles à ajouter de nouveaux éléments dans les futures mises à jour et réduit la taille du résultat de la résolution en évitant d’inclusion des propriétés non pertinentes qui dépendent de la méthode de résolution et le type de programme de résolution en cours.  
  
 Le **résolveur** classe expose deux propriétés :  
  
-   **Nom**. Il s’agit du nom d’une paire nom/valeur qui contient des informations qui sont retournées après qu’une chaîne de connexion est résolue.  
  
-   **Valeur**. Il s’agit de la valeur qui correspond au nom de la paire nom/valeur.