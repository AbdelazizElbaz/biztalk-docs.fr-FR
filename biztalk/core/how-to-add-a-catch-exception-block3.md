---
title: "Comment ajouter un Block3 d’Exception Catch | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scope shape [Orchestration Designer], Catch Exception block [Orchestration Designer]
- Catch Exception block [Orchestration Designer]
- Catch Exception block [Orchestration Designer], creating
- Catch Exception block [Orchestration Designer], exception handler
- Catch Exception block [Orchestration Designer], about Catch Exception blocks
- Orchestration Designer, errors
ms.assetid: 63ca4a60-b657-452a-86fd-78968ccf2933
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1040a27a5e1273d2ad80a722deb421878de36c12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a>Ajout d'un bloc Intercepter l'exception
Le **intercepter l’Exception** bloc représente un gestionnaire d’exceptions. **Intercepter Exception** blocs sont attachés à la fin d’un **étendue** forme dans le Concepteur d’Orchestration. Vous pouvez joindre autant **intercepter l’Exception** bloque dont vous avez besoin.  
  
 Vous pouvez configurer les gestionnaires d'exceptions afin qu'ils gèrent différents types d'exceptions. Sur chaque gestionnaire d’exceptions, vous spécifiez un type d’exception, qui doit être un message d’erreur ou d’un objet dérivé de la classe **System.Exception**. Si vous ne spécifiez pas un type d’exception, le bloc d’exception sera traité comme un gestionnaire d’exceptions général et pourra intercepter des exceptions qui ne dérivent pas de **System.Exception**.  
  
 Si une exception est levée qui correspond au type spécifié dans un gestionnaire d’exceptions, ce gestionnaire d’exceptions sera appelé. Lorsqu'elle ne correspond pas, elle est gérée par le gestionnaire d'exceptions par défaut.  
  
> [!NOTE]
>  Pour ajouter un **intercepter l’Exception** bloquer à un **étendue** mettre en forme le **Type de Transaction** propriété de la **étendue** forme doit être définie sur **Aucun** ou **longue**.  
  
### <a name="to-add-a-catch-exception-block"></a>Pour ajouter un bloc Intercepter l'exception  
  
1.  Avec le bouton droit le **étendue** forme à laquelle vous souhaitez ajouter un **intercepter l’Exception** bloquer, puis cliquez sur **nouveau gestionnaire d’exceptions**.  
  
     A **intercepter l’Exception** bloc est ajouté à l’orchestration qui suit immédiatement la **étendue** forme.  
  
2.  Dans la fenêtre Propriétés, définissez les propriétés ci-dessous.  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |Nom d'objet d'exception|Affecte un nom à l'objet d'exception intercepté par le gestionnaire d'exceptions.|  
    |Type d'objet d'exception|Détermine le type d'objet (issu de la classe System.Exception) que ce gestionnaire interceptera.|  
  
3.  À l’intérieur de la **intercepter l’Exception** bloquer, ajouter des formes pour créer le processus de gestion de l’exception.  
  
> [!NOTE]
>  Si vous spécifiez l’Exception générale en tant que le **Exception** l’objet de type, le **intercepter l’Exception** bloc intercepte une exception, y compris ceux qui ne sont pas dérivés de **System.Exception** . Dans ce cas, vous n'aurez pas accès à l'objet d'exception. Dans ce bloc, si vous utilisez un **lever Exception** forme avec le type d’Exception générale, vous relèverez l’exception interceptée.  
  
## <a name="see-also"></a>Voir aussi  
 [Exceptions](../core/exceptions.md)