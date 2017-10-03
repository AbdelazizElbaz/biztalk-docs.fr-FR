---
title: "Qualificateur de l’ID d’expéditeur non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfe9c51c-d569-4f14-a690-f145ef1bf6a4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b3192a21965360f6e10d7eb9a0a2ec7755d71e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-senderid-qualifier"></a>Qualificateur d'ID d'expéditeur non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12Ta1InvalidSenderIdQualifierDescription|  
|Texte du message|Qualificateur d'ID d'expéditeur non valide|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car le qualificateur d'expéditeur dans le champ ISA05 (pour un échange X12) ou le qualificateur d'expéditeur des échanges dans le champ UNB2.2 (pour un échange EDIFACT) ne correspond à aucune valeur de l'énumération établie par le schéma de service (X12ServiceSchema ou le EdifactServiceSchema dans BaseArtifacts.dll).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que le champ ISA07 ou UNB3.2 correspond à l'une des valeurs de l'énumération établie par le schéma de service. Demandez à l'expéditeur de renvoyer l'échange.