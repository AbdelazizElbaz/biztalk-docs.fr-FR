---
title: "Utilisation des filtres avec la forme d’un Message de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters, receive messages
- messages, filters
ms.assetid: 5310039b-6719-4971-933a-2da0573fb5e7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1434e9704e073cfef1503ef550409e6d6414bb7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-filters-with-the-receive-message-shape"></a>Utilisation des filtres avec la forme d’un Message de réception
Une expression de filtre est un paramètre facultatif qu'il est possible d'appliquer à une forme de réception d'une orchestration spécifiant la valeur True pour la propriété Activer. Si vous définissez une expression de filtre, l'orchestration ne sera activée que si un message entrant remplit les conditions spécifiées dans l'expression de filtre. En l'absence d'expression de filtre, tout message entrant auquel est abonnée l'orchestration pourra activer cette dernière.  
  
 La création d'une expression de filtre permet de comparer la propriété d'un message entrant sur la partie gauche de l'expression avec une constante de la partie droite de l'expression. Vous pouvez également créer des expressions composées en appliquant des opérateurs AND et OR à deux ou plusieurs expressions. Enfin, vous avez la possibilité de ne pas définir d'expression de filtre, auquel cas tous les messages seront acceptés.  
  
 Une expression de filtre peut ressembler à ce qui suit :  
  
```  
InvoiceSchema.Quantity >= 1000  
```  
  
 Dans cet exemple, un message entrant est présenté à l'orchestration. L’orchestration a une activation **réception** forme (le **Activation** est définie sur **True** afin que la réception d’un message donné entraînent l’orchestration à exécuter ) avec l’expression de filtre précédente appliquée. Le message entrant doit avoir la propriété nommée Quantity dans l’espace de noms **InvoiceSchema**. L'orchestration n'acceptant que les factures portant sur au moins 1 000 articles, le moteur d'exécution vérifie le message entrant avant son exécution.  
  
 Le tableau suivant montre les opérateurs qu'il est possible d'utiliser dans les expressions de filtre.  
  
|Opérateur| Description|Exemple|  
|--------------|-----------------|-------------|  
|==|égal à|ReqMsg(Total) == 100|  
|!=|différent de|ReqMsg(Total) != 100|  
|<|inférieur à|ReqMsg(Total) \< 100|  
|>|supérieur à|ReqMsg(Total) > 100|  
|<=|inférieur ou égal à|ReqMsg(Total) \<= 100|  
|>=|supérieur ou égal à|ReqMsg(Total) >= 100|  
|existe|existe|ReqMsg(Description) existe|  
  
> [!NOTE]
>  Les valeurs de chaîne dans les expressions de filtre sont placées entre guillemets, par exemple : reqmsg (description) = « État ». Les valeurs de caractère sont interdites dans une expression de filtre.  
  
> [!NOTE]
>  Si votre réception avec activation est associée à un port à liaison directe et que vous envoyez par la suite un message du même type doté de la même valeur pour la propriété testée dans votre filtre, vous allez créer une boucle infinie. Le message sera envoyé dans la base de données MessageBox, où il sera de nouveau récupéré, car il remplit les critères du filtre. Pour éviter ce problème, vous pouvez filtrer sur une autre propriété, envoyer un message d'un type différent ou penser à modifier la valeur de la propriété avant d'envoyer un message du même type.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer la forme réception](../core/how-to-configure-the-receive-shape.md)   
 [À l’aide de corrélations dans les Orchestrations](../core/using-correlations-in-orchestrations.md)   
 [À l’aide des champs distinctifs et les champs de propriété](../core/using-distinguished-fields-and-property-fields.md)   
 [À l’aide de Messages dans les Orchestrations](../core/using-messages-in-orchestrations.md)