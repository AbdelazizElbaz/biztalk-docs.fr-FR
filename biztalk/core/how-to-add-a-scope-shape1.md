---
title: "Comment ajouter un Shape1 étendue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scope shapes, adding
- Scope shapes, Catch Exception blocks
- Catch Exception blocks, Scope shapes
- adding, Scope shapes
ms.assetid: dfe039d1-4c4a-4e21-ae03-7ca534aafec3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 094f744f7d4d6d1c405ea50d222beb8c0a67920e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-scope-shape"></a>Ajout d'une forme Étendue
Pour ajouter une forme Étendue, procédez comme suit.  
  
### <a name="to-add-a-scope-shape"></a>Pour ajouter une forme Étendue  
  
1.  Cliquez sur la flèche située sous le **ReceiveFromIn** de port, pointez sur **insérer une forme**, puis cliquez sur **étendue**.  
  
     ![](../core/media/siebeladapter-18-exceptionhandling-insertscope.gif "SiebelAdapter_18_ExceptionHandling_InsertScope")  
  
     Dans la forme Étendue, définissez les opérations susceptibles de rencontrer une erreur.  
  
     Par exemple, ajoutez un port d'envoi et de réception dans une orchestration SQLExecute. Dans cet exemple, vous envoyez un message vers DB2. DB2 renvoie une réponse. Il exécute le reste de l’orchestration et retourne des informations sur le port OutFile.  
  
2.  Dans la forme étendue, définissez la **Transaction** à **aucun**.  
  
3.  Avec le bouton droit à l’intérieur de la forme étendue, puis sélectionnez **nouveau gestionnaire d’exceptions**.  
  
     ![](../core/media/siebeladapter-19-exceptionhandling-newexception.gif "SiebelAdapter_19_ExceptionHandling_NewException")  
  
     Cette opération permet de créer le bloc Intercepter l'exception. Si une exception se produit dans le serveur principal, elle est interceptée dans le bloc intercepter l’Exception.  
  
4.  Vous devez ajouter la logique au bloc Intercepter l'exception.  
  
     La logique la plus importante à définir est le type de message d'erreur que vous pensez recevoir.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de la gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling2.md)