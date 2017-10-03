---
title: "Numéro de contrôle dupliqué transaction trouvée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b2779a0-b365-4c4b-81c7-8f9284748b6e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe63d3814bcce178164054ab8dcf673eeb4f395a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-duplicate-control-number-found"></a>Numéro de contrôle dupliqué du document informatisé trouvé
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12TsDuplicateNumberFoundDescription|  
|Texte du message|Numéro de contrôle dupliqué du document informatisé trouvé|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange X12 entrant, car le numéro de contrôle d'un document informatisé d'un groupe de cet échange était le même que celui d'un autre document informatisé de ce groupe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
-   Modifiez les numéros de contrôle des documents informatisés dans l'échange entrant de sorte qu'il n'y ait plus de numéros de contrôle en double pour les documents informatisés dans un groupe.  
  
-   Désactivez la vérification de numéros de contrôle de documents informatisés en double, comme suit :  
  
    1.  Ouvrez la console Administration de BizTalk Server.  
  
    2.  Ouvrez la boîte de dialogue Propriétés EDI du tiers qui a envoyé l'échange.  
  
    3.  Pour les échanges X12, désactivez « Vérifiez qu'aucun doublon n'existe pour ST2 (numéro de contrôle du document informatisé) dans le groupe » dans la page Propriétés du processus d'échange X12 de la boîte de dialogue Propriétés EDI.  
  
    4.  Pour les échanges EDIFACT, désactivez « Vérifiez qu'aucun doublon n'existe pour UNH1 (numéro de contrôle du document informatisé) dans le groupe » dans la page Propriétés du traitement de l'échange EDIFACT de la boîte de dialogue Propriétés EDI.