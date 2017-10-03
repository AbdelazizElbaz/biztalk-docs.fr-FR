---
title: "L’élément de lot est suspendu car sa validation a échoué | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea5e19e8-4592-40f4-bffe-85ab27653fd5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7022041d8d47e1bfa52eb7ef45764c17ed1a2d8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-batch-element-is-being-suspended-as-it-failed-validation"></a>L'élément de traitement par lots est suspendu car sa validation a échoué
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|BatchElementSuspended|  
|Texte du message|L'élément de traitement par lots est suspendu car sa validation a échoué. Est de l’erreur : {0}|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que l'orchestration de traitement par lot n'a pas pu ajouter un document informatisé à un échange traité par lot car la validation du document informatisé effectuée par l'orchestration de traitement par lot a échoué. L'échange sera généré sans le document informatisé dont la validation a échoué. L'orchestration de traitement par lot définit la propriété de contexte EDI.BatchElementValidationFailure sur « True ». L'orchestration BatchSuspend récupère le message en fonction de cette propriété de contexte et publie les informations sur l'erreur avant d'être interrompue.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, expliquez le problème à l'expéditeur du document informatisé, en fonction des indications du message d'erreur. Demandez à l'expéditeur de résoudre le problème qui a provoqué l'échec de la validation, puis de renvoyer le document informatisé.