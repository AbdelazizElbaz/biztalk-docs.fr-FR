---
title: "L'échange comportait une erreur structurelle. Une cause possible est le terminateur de segment non valide en raison d’une ligne de chariot manquante et- ou de saut de ligne des séparateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 035e37d5-d4a8-49d0-8d75-3bcf2426cac7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e983e44b1284bf16e06dbfc90159afc0ed5608c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-had-structural-error-a-likely-cause-is-invalid-segment-terminator-due-to-missing-carriage-line-and-or-line-feed-seperators"></a>L'échange comportait une erreur structurelle. Une cause possible est le terminateur de segment non valide en raison d’une ligne de chariot manquante et- ou de saut de ligne des séparateurs
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EfactInterchangeStructuralErrorAfterUnb|  
|Texte du message|L’échange avec l’id '{0}', id d’expéditeur « {{1} », id de récepteur « {{2} » comportait une erreur structurelle. Une cause possible est le terminateur de segment non valide due à l’absence de séparateurs de retour chariot et/ou de saut de ligne. La partie située après que l’erreur a été interrompue, reportez-vous à la file d’attente pour plus d’informations|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception, le pipeline d'envoi ou l'orchestration du traitement par lot n'ont pas pu traiter l'échange EDIFACT, car un segment de ce dernier ne disposait pas du terminateur de segment requis. Pour un échange entrant, les séparateurs sont identifiés dans le segment UNA ou, si ce dernier n'est pas présent, dans la propriété de pipeline EfactDelimiters. Pour un échange sortant, les séparateurs sont identifiés sur la page Définition du segment UNA de la boîte de dialogue Propriétés EDI.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que tous les segments de l'échange disposent du terminateur de segment requis, puis procédez à un nouvel envoi de l'échange.