---
title: "Une exception s’est produite lors de l’envoi du lot dans l’orchestration de traitement par lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c58b2fa9-d036-4e09-a0f8-77a2f983881a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a3e61cc7375acf5d9faf0d72ab36127532c66ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-exception-has-occurred-during-the-batch-submission-in-the-batching-orchestration"></a>Une exception s'est produite lors de la soumission du lot dans l'orchestration du traitement par lots
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|ExceptionOccured|  
|Texte du message|Une exception s'est produite lors de la soumission du lot dans l'orchestration du traitement par lots. Id de lot = {0}, {{1} message d’erreur|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que l'orchestration de traitement par lot n'a pas pu ajouter un élément de lot à un lot en raison de la condition d'erreur mentionnée dans le champ ErrorMessage.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, déterminez la condition d'erreur à partir du champ ErrorMessage, résolvez l'erreur, puis renvoyez le message.