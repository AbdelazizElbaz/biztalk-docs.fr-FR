---
title: "Comment ajouter un Block4 d’Exception Catch | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Catch Exception blocks, adding
- exception handling, Catch Exception blocks
ms.assetid: 632fa089-a1af-4126-b32b-68d4d8942387
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b409f25fc32c609bb4c1a80c0582cdb1c363e965
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a>Ajout d'un bloc Intercepter l'exception
Le **intercepter l’Exception** bloc représente un gestionnaire d’exceptions. **Intercepter Exception** blocs sont attachés à la fin d’un **étendue** forme dans le Concepteur d’Orchestration. Vous pouvez joindre autant **intercepter l’Exception** bloque dont vous avez besoin.  
  
 Vous pouvez configurer les gestionnaires d'exceptions afin qu'ils gèrent différents types d'exceptions. Sur chaque gestionnaire d'exceptions, vous devez indiquer le type d'exception, qui est une exception ou un objet provenant de la classe System. Lorsqu'une exception générée correspond au type spécifié, le gestionnaire d'exceptions approprié est appelé.  
  
> [!NOTE]
>  Pour ajouter un **intercepter l’Exception** bloquer à un **étendue** mettre en forme, la propriété Type de Transaction de la **étendue** forme doit être définie sur **aucun** ou  **Long terme**.  
  
|Ajout et renseignement d’un bloc intercepter l’Exception|  
|---------------------------------------------------|  
|1.  Avec le bouton droit le **étendue** forme que vous souhaitez ajouter un **intercepter l’Exception** bloquer à, puis cliquez sur **nouveau gestionnaire d’exceptions**.<br />     A **intercepter l’Exception** bloc est ajouté à l’orchestration qui suit immédiatement la **étendue** forme.<br />2.  Dans le **propriétés** fenêtre, spécifiez les propriétés. La plus importante est la **Type d’objet Exception**; il s’agit du type de message, elle intercepte.<br />     **Nom de l’objet exception**<br />     -Attribue un nom à l’objet exception interceptée par le Gestionnaire d’exceptions.<br />     **Type d’objet exception**<br />     -Détermine le type d’objet (dérivé de System.Exception) que ce gestionnaire interceptera.<br />3.  Dans le **propriétés** fenêtre, ouvrez le **Type d’objet Exception** liste. Cette liste contient le **Exception générale**.<br />4.  À l’intérieur de la **intercepter l’Exception** bloquer, ajouter des formes pour créer le processus de gestion de l’exception.<br />5.  Avec le bouton ci-dessous le **intercepter l’Exception**, pointez sur **insérer une forme**, puis sélectionnez **construire un Message**.<br />6.  Double-cliquez dans **MessageAssignment** pour activer l’éditeur de texte, entrez l’assignation du Message.<br />     Par exemple, tapez Message_3 = Test.<br />     ![](../core/media/siebeladapter-21-exceptionhandling-message3test.gif "SiebelAdapter_21_ExceptionHandling_Message3Test")|  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution du Message d’Exception](../core/completing-the-exception-message2.md)   
 [Comment ajouter une forme étendue](../core/how-to-add-a-scope-shape3.md)   
 [À l’aide de la gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling1.md)