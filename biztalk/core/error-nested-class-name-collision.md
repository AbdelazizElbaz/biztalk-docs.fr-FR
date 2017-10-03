---
title: "Erreur : Collision de nom de classe imbriquée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edit.error.nestedClassNameCollision
ms.assetid: dd636d25-d0c1-41be-a2ba-b38ea97b973d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4a9fa7a9f57088b3fb93e2eb6024e9b6aad49c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---nested-class-name-collision"></a>Erreur : Collision de nom de classe imbriquée
**Code d’erreur**  
  
 BEC2017  
  
 **Explication**  
  
 Le **nom de Type** propriété de ce schéma a été trouvée pour être le même que le **RootNode TypeName** propriété de l’un des nœuds racines dans le schéma. Les classes imbriquées portant le même nom ne sont pas prises en charge par C#. Par conséquent, une erreur est renvoyée.  
  
 **Action de l’utilisateur**  
  
 Changez l'une des valeurs de propriété concernées de façon à ne plus avoir de conflit de nom. Vous pouvez :  
  
-   Sélectionnez le fichier de schéma approprié dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, puis, dans la fenêtre Propriétés, modifiez la **nom de Type** propriété à une valeur valide unique.  
  
     \- ou -  
  
-   Sélectionnez le nœud racine indiqué, puis, dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, modifier le **RootNode TypeName** propriété à une valeur valide unique.