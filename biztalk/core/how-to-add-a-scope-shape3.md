---
title: Comment ajouter un Shape3 étendue | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Scope shapes, adding
ms.assetid: 8068ce97-4409-4c88-89e8-6505b56cefc5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8231dfed1ea84ba5c11e0352f789b92cc38d0f83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-scope-shape"></a>Ajout d'une forme Étendue
La procédure suivante permet d'ajouter une forme Étendue.  
  
### <a name="to-add-a-scope-shape"></a>Pour ajouter une forme Étendue  
  
1.  Cliquez sur la flèche située sous le **réception** de port, pointez sur **insérer une forme**, puis sélectionnez **étendue**.  
  
     ![](../core/media/siebeladapter-18-exceptionhandling-insertscope.gif "SiebelAdapter_18_ExceptionHandling_InsertScope")  
  
     Dans le **étendue** forme, vous définissez les opérations pouvant rencontrer une erreur.  
  
     Par exemple, ajoutez un port d'envoi et de réception dans une orchestration SQLExecute. Dans cet exemple, envoyez un message vers SERVER. SERVER renvoie une réponse. Il exécute le reste de l'orchestration et renvoie des informations vers le port OutFile.  
  
2.  Dans le **étendue** mettre en forme, définissez le **Transaction** à **aucun**.  
  
3.  Avec le bouton droit à l’intérieur de la **étendue** mettre en forme, puis sélectionnez **nouveau gestionnaire d’exceptions**.  
  
     ![](../core/media/siebeladapter-19-exceptionhandling-newexception.gif "SiebelAdapter_19_ExceptionHandling_NewException")  
  
     Cette opération crée le **intercepter l’Exception** bloc. Si une exception se produit dans le système principal, elle est interceptée le **intercepter l’Exception** bloc.  
  
4.  Dans le **intercepter l’Exception** bloc, vous devez ajouter la logique.  
  
     La logique la plus importante que vous devez définir est le type de message d’erreur que vous attendez à recevoir.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de la gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling1.md)