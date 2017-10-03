---
title: "Le message ne peut pas être acheminé à l’orchestration de traitement par lot, comme le type de codage n’a pas pu être déterminé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d2ee38d-22c0-4fcf-bb68-b2ef00088c4c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe5054f53f779274c9b25f2751fdcb9d85545560
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-message-cannot-be-routed-to-the-batching-orchestration-as-the-encoding-type-could-not-be-determined"></a>Le message ne peut pas être acheminé à l'orchestration de traitement par lots, car le type de codage n'a pu être déterminé
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|UnknownEncodingType|  
|Texte du message|Le message ne peut pas être acheminé à l'orchestration de traitement par lots, car le type de codage n'a pu être déterminé. Pour que le message puisse être traité par lots, le type de codage ne doit être ni X12 ni EDIFACT.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique qu'un élément par lot autre que de type EDI n'a pas été acheminé à l'instance d'orchestration par lot, même si le document informatisé correspond aux critères de filtre pour le traitement par lot. Le document informatisé n'a pas pu être acheminé à l'instance d'orchestration par lot, car la propriété de contexte EDI.EncodingType n'a pas été promue avec une valeur 0 pour X12 ou 1 pour EDIFACT. Cette erreur s'est produite lorsque l'élément par lot a été acheminé par le composant de pipeline BatchMarker à l'orchestration de routage, mais l'élément par lot autre que de type EDI n'était pas converti par un mappage en un message EDI. Par conséquent, l'orchestration de routage n'a pas pu déterminer le type de codage depuis les en-têtes EDI.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, vérifiez que le message autre que de type EDI est converti par un mappage en un message EDI avant d'être acheminé à l'orchestration de routage. Vous devez aussi inclure un composant de pipeline personnalisé (avec le composant BatchMarker) ou une orchestration personnalisée pour traiter l'élément par lot n'étant pas de type EDI. Pour plus d'informations, consultez la rubrique « Assemblage d'un échange EDI par lot » dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].