---
title: "Une exception s’est produite lors de l’exécution de l’orchestration de traitement par lots de mise à niveau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2221a498-98aa-43ab-bc4e-34dcbd92dcf0
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54cd439e180365010ec8881ce7165022dd7826d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-exception-has-occurred-during-the-execution-of-the-upgrade-batch-orchestration"></a>Une exception s'est produite lors de l'exécution de l'orchestration du traitement par lot de la mise à niveau.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|ExceptionOccuredDuringUpgrade|  
|Texte du message|Une exception s’est produite lors de l’exécution du lot de mise à niveau d’Orchestration. Message d'erreur = {0}|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que l'orchestration du traitement par lot de la mise à niveau n'a pas pu traiter le message correctement en raison de la condition d'erreur indiquée dans le champ MessageErreur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, déterminez la condition d'erreur à partir du champ ErrorMessage, résolvez l'erreur, puis renvoyez le message.