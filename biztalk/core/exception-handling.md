---
title: La gestion des exceptions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00a9125c-7c7c-4d2a-ae04-c923cd89683c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 520f4eb47fb98bf497753a8348031f7c2ab93d29
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exception-handling"></a>Gestion des exceptions
Le **RuleEngine** classe a la propriété **CompensationHandlerInfo**, qui à son tour possède deux propriétés : **CompensationHandler** et **UserData**. Le **CompensationHandler** propriété est de type **RuleEngineCompensationHandler**et le **UserData** propriété est de type **objet** . La définition de la **RuleEngineCompensationHandler** est comme suit :  
  
```  
public delegate bool RuleEngineCompensationHandler(  
   Exception ex,  
   object userData  
);  
```  
  
 Le consommateur du moteur de règle spécifie le gestionnaire et les données utilisateur au moteur de règles à l’aide de la **CompensationHandlerInfo** propriété de la **RuleEngine** classe. Le gestionnaire doit avoir la même signature que le **RuleEngineCompensationHandler** déléguer. En cas d'exception d'exécution, le moteur appelle le gestionnaire et lui transmet l'exception et les données prédéfinies de l'utilisateur en tant que paramètres. Si le gestionnaire renvoie la valeur `true`, le moteur de règles continue le traitement. Dans le cas contraire, le moteur de règles abandonne le traitement et renvoie à l'utilisateur l'exception initiale. Comme vous pouvez le voir, vous pouvez utiliser ce mécanisme de gestion des exceptions que si vous appelez la stratégie à l’aide de la **RuleEngine.Execute** (méthode).  
  
 Si vous utilisez la **Policy.Execute** méthode pour exécuter une stratégie, vous devez utiliser un bloc try-catch pour intercepter les exceptions générées par le moteur de règles lors de l’exécution de la stratégie.  
  
 Si vous utilisez la **appeler règles** forme pour exécuter une stratégie, utilisez la **intercepter l’Exception** bloquer pour le **étendue** forme pour intercepter une exception levée par le moteur de règles lors de l’exécution la stratégie.  
  
## <a name="see-also"></a>Voir aussi  
 [L’ajout d’un bloc intercepter l’Exception](../core/how-to-add-a-catch-exception-block3.md)