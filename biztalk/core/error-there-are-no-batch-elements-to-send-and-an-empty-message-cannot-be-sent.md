---
title: "Aucun élément de lot pour envoyer et un message vide ne peut pas être envoyé car il n’est pas configuré pour le tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0752079a-173e-4de3-96f4-e5de01b799b5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80dcf96feef006a2576afc5829e7927e003524a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="there-are-no-batch-elements-to-send-and-an-empty-message-cannot-be-sent-as-it-is-not-configured-for-party"></a>Il n'y a pas d'éléments par lot à envoyer et un message vide ne peut pas être envoyé car il n'est pas configuré pour le tiers
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|EmptyMessageNotAllowed|  
|Texte du message|Il n'y a pas d'éléments par lot à envoyer et un message vide ne peut pas être envoyé car il n'est pas configuré pour le tiers {0}|  
  
## <a name="explanation"></a>Explication  
 Cet avertissement indique qu'aucun message de traitement par lot n'a été envoyé dans un processus de traitement par lot basé sur la planification, car aucun élément par lot n'a été reçu lorsque le déclenchement du lot fut planifié et l'alerte signalant un lot vide n'a pas été activée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Afin d'éviter que cet avertissement ne s'affiche, configurez l'alerte signalant un lot vide comme suit :  
  
1.  Ouvrez la console Administration de BizTalk Server.  
  
2.  Accédez au nœud Tiers.  
  
3.  Ouvrez la boîte de dialogue Propriétés EDI du tiers.  
  
4.  Cliquez sur le nœud Paramètres de création de lots d'échange (pour obtenir le codage approprié).  
  
5.  Cliquez sur Planificateur.  
  
6.  Cliquez sur la propriété Envoyer une alerte signalant un lot vide.