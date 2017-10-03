---
title: "Comment ajouter un Block6 d’Exception Catch | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exception handling, Catch Exception block
- Catch Exception blocks
- exceptions, Catch Exception block
ms.assetid: 404312dd-773b-44fe-8b65-7de3d0af2f79
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4be60ddbe45ef4b4f293d7959dc774254e7cd3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a>Ajout d'un bloc Intercepter l'exception
Le **intercepter l’Exception** bloc représente un gestionnaire d’exceptions. **Intercepter Exception** blocs sont attachés à la fin d’un **étendue** forme dans le Concepteur d’Orchestration. Dans BizTalk Server, vous pouvez joindre autant **intercepter l’Exception** bloque dont vous avez besoin.  
  
 Vous pouvez configurer les gestionnaires d'exceptions afin qu'ils gèrent différents types d'exceptions. Sur chaque gestionnaire d'exceptions, vous devez indiquer le type d'exception, qui est un message d'erreur ou un objet provenant de la classe `System.Exception`. Si vous ne précisez pas le type d'erreur, le bloc d'exception est alors traité comme un gestionnaire d'exceptions général et pourra intercepter des exceptions qui ne proviennent pas de la classe `System.Exception`.  
  
 Lorsqu'une exception générée correspond au type spécifié, le gestionnaire d'exceptions approprié est appelé. Si une autre exception est levée, elle est gérée par le Gestionnaire d’exceptions par défaut.  
  
> [!NOTE]
>  Pour ajouter un **intercepter l’Exception** bloquer à un **étendue** mettre en forme le **Type de Transaction** propriété de la **étendue** forme doit être définie sur None ou Long En cours d’exécution.  
  
## <a name="adding-and-populating-a-catch-exception-block"></a>Ajout et renseignement d'un bloc Intercepter l'exception  
  
#### <a name="to-add-and-populate-a-catch-exception-block"></a>Pour ajouter et renseigner un bloc Intercepter l'exception  
  
1.  Avec le bouton droit le **étendue** forme que vous souhaitez ajouter un **intercepter l’Exception** bloquer à, puis cliquez sur **nouveau gestionnaire d’exceptions**.  
  
     A **intercepter l’Exception** bloc est ajouté à l’orchestration qui suit immédiatement la **étendue** forme.  
  
2.  Dans le **propriétés** fenêtre, spécifiez les propriétés. La propriété la plus importante est la **Type d’objet Exception** , car il s’agit du type de message, elle intercepte.  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |Nom d'objet d'exception|Affecte un nom à l'objet d'exception intercepté par le gestionnaire d'exceptions.|  
    |Type d'objet d'exception|Détermine le type d'objet (issu de la classe System.Exception) que ce gestionnaire interceptera.|  
  
3.  Dans le **propriétés** fenêtre, cliquez sur le **Type d’objet Exception** liste. Cette liste contient l'exception générale qui est générée par l'adaptateur.  
  
     Le nom apparaît comme l'erreur que vous définissez dans le port vers le système principal (par exemple, PS.SQLExecute.Fault).  
  
4.  Ajouter un nom pour le **nom de l’objet Exception**, par exemple, de Test.  
  
     À l’intérieur de la **intercepter l’Exception** bloquer, ajouter des formes pour créer le processus de gestion de l’exception.  
  
    1.  Avec le bouton ci-dessous le **intercepter l’Exception**, pointez sur **insérer une forme**, puis sélectionnez **construire un Message**.  
  
         ![](../core/media/siebeladapter-20-exceptionhandling-constructmessage.gif "SiebelAdapter_20_ExceptionHandling_ConstructMessage")  
  
    2.  Double-cliquez dans **MessageAssignment** pour ouvrir l’éditeur de texte et entrez l’assignation du Message.  
  
         Entrez le nom que vous définissez dans le **nom de l’objet Exception** à partir de la **intercepter l’Exception**et le nouveau message que vous avez créé pour l’erreur.  
  
         Par exemple, tapez `Message_3 = Test`.  
  
         ![](../core/media/siebeladapter-21-exceptionhandling-message3test.gif "SiebelAdapter_21_ExceptionHandling_Message3Test")  
  
## <a name="see-also"></a>Voir aussi  
 [Comment ajouter une forme étendue](../core/how-to-add-a-scope-shape1.md)   
 [Exécution du Message d’Exception](../core/completing-the-exception-message3.md)   
 [À l’aide de la gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling2.md)