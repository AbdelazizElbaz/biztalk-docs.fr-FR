---
title: "Validation d’instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f906f2e9-2bf9-448b-927f-dd2d7d9b2272
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3db1903030bbde96f2587ac14b5d168345b31823
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instance-validation"></a>Validation de l’instance
L’Éditeur BizTalk appelle la **IInstanceValidator.ValidateInstance** méthode d’extension lorsque les conditions suivantes sont remplies :  
  
-   L’extension est définie comme norme à l’aide de la **Standard** propriété de la **schéma** nœud.  
  
-   Sur le **Pages de propriétés** boîte de dialogue associé au schéma, le **Type sortie générer l’Instance** est définie sur **natif.**  
  
-   Sur le **Pages de propriétés** boîte de dialogue associé au schéma, le **nom d’Instance d’entrée** est définie sur le nom d’un fichier contenant le message d’instance à valider.  
  
 Le fichier spécifié dans le **nom d’Instance d’entrée** propriété est passée en tant que paramètre à la **IInstanceValidator.ValidateInstance** (méthode).  
  
 En cas d’erreurs, les messages d’erreur sont retournées sous forme de tableau de **IValidationInfo** objets et s’affichent dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre liste des tâches.  
  
> [!NOTE]
>  Si le schéma contient des instructions de modèle et le fichier passé à la **ValidateInstance** méthode a été générée à l’aide correspondant **générer l’Instance** le message d’instance ne peut pas passer de la commande validation.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de l’Éditeur BizTalk](../core/extending-biztalk-editor.md)