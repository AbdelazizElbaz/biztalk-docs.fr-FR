---
title: "Une exception de persistance s’est produite lors de l’envoi du lot dans l’Orchestration de traitement par lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf6e832f-9d01-46e7-aaf5-2b402d509fac
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eae4f48209dc4f5afefbc69c40706a31f2b00b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-persistence-exception-has-occurred-during-the-batch-submission-in-the-batching-orchestration"></a>Une exception de persistance s'est produite durant l'envoi par lot de l'orchestration de traitement par lot
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|PersistenceExceptionOccured|  
|Texte du message|Une exception de persistance s'est produite durant l'envoi par lot de l'orchestration de traitement par lot. Id de lot = {0}, message d’erreur = {{1}. Vérifiez vos abonnements de port d'envoi et corrigez-les.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu envoyer un échange traité par lot, car aucun port d'envoi n'est abonné à celui-ci.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous qu’un port d’envoi s’abonne au lot en définissant les propriétés de filtre suivantes pour le port d’envoi : EDI. DestinationPartyName = \<Nom_tiers >, EDI. BatchEncodingType = EDIFACT ou X12 et EDI. ToBeBatched = False.