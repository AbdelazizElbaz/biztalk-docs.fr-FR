---
title: "Comment ajouter un SMB1 d’Exception Catch | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, adding Catch Exception block
- Catch Exception blocks, adding
- exception handling, Catch Exception blocks
ms.assetid: 8e4b264b-b3b0-4d83-81df-a14dc2ddeea2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7922a1527e0f6359427be992c4cc9963f8c7d93e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a>Ajout d'un bloc Intercepter l'exception
Le **intercepter l’Exception** bloc représente un gestionnaire d’exceptions. **Intercepter Exception** blocs sont attachés à la fin d’un **étendue** forme dans le Concepteur d’Orchestration. Vous pouvez joindre autant **intercepter l’Exception** bloque dont vous avez besoin.  
  
 Vous pouvez configurer les gestionnaires d'exceptions afin qu'ils gèrent différents types d'exceptions. Sur chaque gestionnaire d'exceptions, vous devez indiquer le type d'exception, qui est une exception ou un objet provenant de la classe `System`. Si une exception est levée qui correspond au type spécifié dans un gestionnaire d’exceptions, ce gestionnaire d’exceptions sera appelé.  
  
> [!NOTE]
>  Pour ajouter un **intercepter l’Exception** bloquer à un **étendue** mettre en forme, la propriété Type de Transaction de la **étendue** forme doit être définie sur **aucun** ou  **Long terme**.  
  
### <a name="to-add-and-populate-a-catch-exception-block"></a>Pour ajouter et remplir un bloc intercepter l’Exception  
  
1.  Avec le bouton droit le **étendue** forme à laquelle vous souhaitez ajouter un **intercepter l’Exception** bloquer, puis cliquez sur **nouveau gestionnaire d’exceptions**.  
  
     A **intercepter l’Exception** bloc est ajouté à l’orchestration qui suit immédiatement la **étendue** forme.  
  
2.  Dans le **propriétés** fenêtre, spécifiez les propriétés.  
  
     La plus importante des propriétés est Type d'objet d'exception ; il s'agit du type de message à intercepter.  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |Nom d'objet d'exception|Affecte un nom à l'objet d'exception intercepté par le gestionnaire d'exceptions.|  
    |Type d'objet d'exception|Détermine le type d'objet (issu de la classe System.Exception) que ce gestionnaire interceptera.|  
  
3.  Dans le **propriétés** fenêtre, dans le **Type d’objet Exception** liste, sélectionnez le **Exception générale**.  
  
4.  À l’intérieur de la **intercepter l’Exception** bloquer, ajouter des formes pour créer le processus de gestion de l’exception.  
  
5.  Avec le bouton ci-dessous le **intercepter l’Exception** bloquer, pointez sur **insérer une forme**, puis sélectionnez **construire un Message**.  
  
6.  Double-cliquez dans **MessageAssignment** pour activer l’éditeur de texte et entrez l’assignation du Message.  
  
     Par exemple, tapez `Message_3 = Test`.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution du Message d’Exception](../core/completing-the-exception-message5.md)   
 [Comment ajouter une forme étendue](../core/how-to-add-a-scope-shape2.md)   
 [À l’aide de la gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling3.md)