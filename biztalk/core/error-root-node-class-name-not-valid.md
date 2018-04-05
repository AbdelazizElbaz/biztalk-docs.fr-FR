---
title: 'Erreur : nom de classe du nœud racine non valide | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.rootNodeClassNameNotValid
ms.assetid: 48b4f7e4-8c20-4e94-86be-1425ea62f8c5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ff170609ef37b1d7f2b00a4d4ca3952b89eef9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---root-node-class-name-not-valid"></a>Erreur : nom de classe du nœud racine non valide
**Code d’erreur**  
  
 BEC2012  
  
 **Explication**  
  
 Le **RootNode TypeName** propriété de l’un des nœuds racines de ce schéma n’est pas valide. Étant donné que la valeur de la **RootNode TypeName** propriété est utilisée comme nom d’un nom de classe c# généré automatiquement, elle doit être un identificateur c# valid et ne peut pas être un mot clé BizTalk réservé.  
  
 **Action de l’utilisateur**  
  
 Sélectionnez le nœud racine indiqué, puis, dans le Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, modifier le **RootNode TypeName** propriété une valeur qui est un identificateur c# valide et n’est pas un mot clé BizTalk réservé.