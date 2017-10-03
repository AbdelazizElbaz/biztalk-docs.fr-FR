---
title: "Erreur rencontrée lors de l'analyse. Le X12 échange comportait les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c1085d4-75ef-4f63-84c9-287a4a61274a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94b9907667a7f99c1ecf8c2dc326fe32e134abf3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-parsing-the-x12-interchange-had-the-following-errors"></a>Erreur rencontrée lors de l'analyse. L'échange X12 comportait les erreurs suivantes
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12InterchangeReceiveError|  
|Texte du message|Erreur rencontrée lors de l'analyse. Le X12 échange avec l’id '{0}' avec l’expéditeur id « {{1}', id de récepteur « {{2} » comporte les erreurs suivantes :|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI a rencontré une erreur lors de l'analyse d'un échange X12 entrant en raison des erreurs mentionnées dans l'échange.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier celle-ci dans l'échange et déterminer la méthode de résolution dans l'aide du produit.