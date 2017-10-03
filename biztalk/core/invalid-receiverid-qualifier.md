---
title: "Qualificateur d’ID de destinataire non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52d60f7e-6f16-424d-91b8-dc8181206249
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86c9adc1fa20f244d1061b67878e433d73dfa72d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-receiverid-qualifier"></a>Qualificateur d'ID de destinataire non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12Ta1InvalidReceiverIdQualifierDescription|  
|Texte du message|Qualificateur d'ID de destinataire non valide|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car le qualificateur du récepteur du champ ISA07 (pour un échange X12) ou le qualificateur de code du récepteur dans le champ UNB3.2 (pour un échange EDIFACT) n'était pas conforme à une valeur dans l'énumération établie par le schéma de service (X12ServiceSchema ou EdifactServiceSchema dans BaseArtifacts.dll).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que le champ ISA07 ou UNB3.2 correspond à l'une des valeurs de l'énumération établie par le schéma de service. Demandez à l'expéditeur de renvoyer l'échange.