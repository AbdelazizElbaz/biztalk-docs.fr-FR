---
title: "Le document informatisé Edifact comportait un nombre incompatible dans UNT01 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2859274-78e8-4e16-92b7-c143da6da421
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 180abe338441917afa6691400a02a42e88026052
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-edifact-transaction-set-had-a-mismatched-count-in-unt01"></a>Le document informatisé EDIFACT comportait un nombre incompatible dans UNT01
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EfactUnhUntCountMismatch|  
|Texte du message|Le document informatisé EDIFACT comportait un nombre incompatible dans UNT01. UNT01 était {0}, alors qu’elle aurait dû être {{1}. Il a été corrigé.|  
  
## <a name="explanation"></a>Explication  
 Cet avertissement indique que le champ UNT01, qui représente le nombre de segments, ne correspond pas au nombre de segments du document informatisé. La valeur de UNT01 a été soit modifiée soit corrompue ou des segments ont été ajoutés ou supprimés après le calcul de ce nombre. Le pipeline d'envoi a rétabli le champ UNT01 sur le nombre de segments correct, puis il a renvoyé l'échange.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Aucune action utilisateur n’est nécessaire.