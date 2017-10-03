---
title: "Comment ajouter un Block5 d’Exception Catch | Documents Microsoft"
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
ms.assetid: 4875060c-976c-40e7-830a-ffd1a47ba68a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6c045677fb2d177377725a3f11e81a5c5c70f9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a>Ajout d'un bloc Intercepter l'exception
Pour ajouter un **intercepter l’Exception** bloquer à un **étendue** mettre en forme le **Type de Transaction** propriété de la **étendue** forme doit être définie sur **Aucun** ou **longue**.  
  
### <a name="to-add-a-catch-exception-block"></a>Pour ajouter un bloc intercepter l’exception  
  
1.  Cliquez sur le **étendue** mettre en forme, puis cliquez sur **nouveau gestionnaire d’exceptions**.  
  
     A **intercepter l’Exception** bloc est ajouté à l’orchestration qui suit immédiatement la **étendue** forme.  
  
2.  Dans le **propriétés** fenêtre, spécifiez les propriétés.  
  
     La propriété la plus importante est la **Type d’objet Exception**; il s’agit du type de message, elle intercepte.  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |**Nom de l’objet exception**|Affecte un nom à l'objet d'exception intercepté par le gestionnaire d'exceptions.|  
    |**Type d’objet exception**|Détermine le type d'objet (issu de la classe System.Exception) que ce gestionnaire interceptera.|  
  
3.  Dans le **propriétés** fenêtre, dans le **Type d’objet Exception** liste, sélectionnez **Exception générale**.  
  
4.  À l’intérieur de la **intercepter l’Exception** bloquer, ajouter des formes pour créer le processus de gestion de l’exception.  
  
    1.  Avec le bouton ci-dessous le **CatchException** et pointez sur **insérer une forme**, puis sélectionnez **construire un Message**.  
  
    2.  Double-cliquez dans **MessageAssignment** pour ouvrir l’éditeur de texte et entrez l’assignation du Message.  
  
         Par exemple, tapez `Message_3 = Test`.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution du Message d’Exception](../core/completing-the-exception-message1.md)   
 [Comment ajouter une forme étendue](../core/how-to-add-a-scope-shape5.md)   
 [À l’aide de la gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling5.md)