---
title: "Erreur rencontrée lors de l'analyse. L’échange Edifact comportait les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fa8f9d5-5b7c-47c9-96d3-77be280b78e9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4585966de7ecb410f8f46fa675fa4eae0c6715a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-parsing-the-edifact-interchange-had-the-following-errors"></a>Erreur rencontrée lors de l'analyse. L'échange Edifact comportait les erreurs suivantes
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EfactInterchangeReceiveError|  
|Texte du message|Erreur rencontrée lors de l'analyse. L’échange Edifact avec l’id '{0}', id d’expéditeur « {{1} », id de récepteur « {{2} » comporte les erreurs suivantes :|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception EDI a rencontré un problème lors de l'analyse d'un échange EDIFACT en raison des erreurs indiquées dans cet échange.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier celle-ci dans l'échange et déterminer la méthode de résolution dans l'aide du produit.