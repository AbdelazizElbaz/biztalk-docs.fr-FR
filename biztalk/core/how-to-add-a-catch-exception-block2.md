---
title: "Comment ajouter un Block2 d’Exception Catch | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Catch Exception blocks
- exceptions, Catch Exception blocks
ms.assetid: 7c8b6024-e8dc-4417-83f9-bf4032644b91
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e48ce1e6f0646acdf63ed33582f382f1baed797
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a>Ajout d'un bloc Intercepter l'exception
Le **intercepter l’Exception** bloc représente un gestionnaire d’exceptions. **Intercepter Exception** blocs sont attachés à la fin d’un **étendue** forme dans le Concepteur d’Orchestration. Vous pouvez joindre autant **intercepter l’Exception** bloque dont vous avez besoin.  
  
 Vous pouvez configurer les gestionnaires d'exceptions afin qu'ils gèrent différents types d'exceptions. Vous devez spécifier un type d'exception sur chaque gestionnaire d'exceptions. Il peut s'agir d'une exception ou d'un objet dérivé de la classe `System`. Si une exception est levée qui correspond au type spécifié dans un gestionnaire d’exceptions, ce gestionnaire d’exceptions sera appelé.  
  
> [!NOTE]
>  Pour ajouter un bloc intercepter l’Exception à une forme étendue, la propriété de Type de Transaction de la forme étendue doit être définie **aucun** ou **Long terme**.  
  
### <a name="to-add-and-populate-a-catch-exception-block"></a>Pour ajouter et remplir un bloc intercepter l’Exception  
  
1.  Avec le bouton droit le **étendue** forme à laquelle vous souhaitez ajouter un **intercepter l’Exception** bloquer, puis cliquez sur **nouveau gestionnaire d’exceptions**.  
  
     A **intercepter l’Exception** bloc est ajouté à l’orchestration qui suit immédiatement la **étendue** forme.  
  
2.  Dans le **propriétés** fenêtre, spécifiez les propriétés.  
  
     La propriété la plus importante est la **Type d’objet Exception**; il s’agit du type de message, elle intercepte.  
  
3.  Dans le **propriétés** windows, dans le **Type d’objet Exception** liste, sélectionnez **Exception générale**.  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |**Nom de l’objet exception**|Affecte un nom à l'objet d'exception intercepté par le gestionnaire d'exceptions.|  
    |**Type d’objet exception**|Détermine le type d'objet (issu de la classe System.Exception) que ce gestionnaire interceptera.|  
  
4.  Dans le bloc Intercepter l'exception, ajoutez des formes afin de créer la procédure de gestion de l'exception.  
  
    1.  Avec le bouton ci-dessous le **CatchException** et pointez sur **insérer une forme**, puis sélectionnez **construire un Message**.  
  
    2.  Double-cliquez dans **MessageAssignment** pour ouvrir l’éditeur de texte et entrez l’assignation du Message.  
  
         Par exemple, tapez `Message_3 = Test`.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution du Message d’Exception](../core/completing-the-exception-message4.md)   
 [Comment ajouter une forme étendue](../core/how-to-add-a-scope-shape4.md)   
 [À l’aide de la gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling4.md)