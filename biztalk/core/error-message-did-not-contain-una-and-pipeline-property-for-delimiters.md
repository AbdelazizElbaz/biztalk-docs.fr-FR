---
title: "Message ne contenait pas UNA et la propriété de pipeline pour les délimiteurs était d’un format incorrect | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b761d820-e09d-4949-bb41-da9e66054c60
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6310c96f897126a498772f2147a20c84f7e926a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-did-not-contain-una-and-pipeline-property-for-delimiters-was-incorrect-format"></a>Le message ne contenait pas UNA et la propriété de pipeline pour les délimiteurs était d'un format incorrect
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EfactDelimiterIncorrectFormat|  
|Texte du message|Le message ne contenait pas UNA et la propriété de pipeline pour les délimiteurs était d'un format incorrect '{0}'|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange EDIFACT entrant car il n'a pas pu déterminer les séparateurs requis pour le traiter. Cette erreur peut se produire si l'échange ne possède pas de segment UNA et que la propriété de pipeline EfactDelimiters ne définit pas les séparateurs de manière appropriée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
1.  Assurez-vous que l'échange possède un segment UNA qui définit les séparateurs pour l'échange, puis renvoyez l'échange.  
  
2.  Pour définir la propriété EfactDelimiters du pipeline d'envoi, ouvrez la console Administration de BizTalk Server, cliquez avec le bouton droit sur l'emplacement de réception qui recevra l'échange, cliquez sur Propriétés, puis sur les points de suspension pour le pipeline, puis entrez une chaîne contenant les valeurs des séparateurs.