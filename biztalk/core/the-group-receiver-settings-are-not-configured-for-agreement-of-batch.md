---
title: "Les paramètres de destinataire de groupe ne sont pas configurés pour l’accord de lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57b205e9-aaab-43d1-b373-17d206957814
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ea41ad5c8de88e446a86745b57ff282d5b90af5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-group-receiver-settings-are-not-configured-for-agreement-of-batch"></a>Les paramètres de destinataire de groupe ne sont pas configurés pour l'accord de lot.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|GroupReceiverNotSelected|  
|Texte du message|Les paramètres de destinataire de groupe ne sont pas configurés pour l'accord de lot {0}. Ils doivent être configurés pour permettre le traitement par lot.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique qu'une condition sur deux possibles est vérifiée :  
  
-   L'orchestration du traitement par lot n'a pas pu valider un élément de lot reçu, car le champ UNB1.1 (pour un échange EDIFACT) qui contient la syntaxe d'encodage n'était pas défini.  
  
-   L'orchestration du traitement par lot n'a pas pu créer les paramètres d'enveloppe de l'élément de lot, car les propriétés de l'en-tête n'étaient pas complètes (propriétés ISA, GS et ST pour un échange X12  ou propriétés UNA, UNB, UNG  et UNH pour un échange EDIFACT).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
-   Si l'orchestration du traitement par lot n'a pas pu valider un élément de lot reçu parce que la syntaxe d'encodage n'était pas définie, définissez celle-ci pour le champ UNB1.1 sur la page Définition du segment UNB de la boîte de dialogue Propriétés EDI.  
  
-   Si l'orchestration du traitement par lot n'a pas pu créer les paramètres d'enveloppe de l'élément de lot parce que les propriétés de l'en-tête n'étaient pas complètes, assurez-vous que les propriétés ISA, GS et ST pour un échange X12  (ou les propriétés UNA, UNB, UNG  et UNH pour un échange EDIFACT) sont définies.