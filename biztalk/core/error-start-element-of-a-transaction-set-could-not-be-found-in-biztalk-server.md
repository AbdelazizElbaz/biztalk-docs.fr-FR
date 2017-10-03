---
title: "Erreur rencontrée après le traitement de Transaction Set(s), car il est impossible de trouver l’élément de début d’un document informatisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5380aee-1632-4cdf-98a1-aff87574ce4f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 224b08046d1733aa8426909d7dddac4b10e48c8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-after-processing-transaction-sets-because-the-start-element-of-a-transaction-set-could-not-be-found"></a>Erreur rencontrée après le traitement de document(s) informatisé(s) car l'élément de départ d'un document informatisé n'a pas pu être trouvé
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|InvalidEfactBiboXmlFormat|  
|Texte du message|Erreur rencontrée après le traitement de {0} document(s) informatisé(s). L'élément de départ d'un document informatisé n'a pas pu être trouvé.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI n'a pas pu traiter un document informatisé entrant, car le pipeline de réception n'a pas réussi à trouver l'en-tête ST ou UNH.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, contactez l'expéditeur de l'échange et demandez-lui de s'assurer que le document informatisé erroné commence par un segment ST01 ou UNH1.