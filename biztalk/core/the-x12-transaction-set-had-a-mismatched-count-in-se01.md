---
title: "Le X12 informatisé comportait un nombre incompatible dans SE01 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a90079f5-5939-40b6-9756-d7943240c125
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41539f0492f90d3f7276b0d80af28c568593ef4f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-x12-transaction-set-had-a-mismatched-count-in-se01"></a>Le document informatisé X12 présentait un nombre incompatible dans SE01
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12StSeCountMismatch|  
|Texte du message|Le document informatisé X12 présentait un nombre incompatible dans SE01. SE01 était {0}, alors qu’elle aurait dû être {{1}. Il a été corrigé.|  
  
## <a name="explanation"></a>Explication  
 Cet avertissement indique que le nombre spécifié dans le code de fin du document informatisé (champ SE01) ne correspond pas au nombre de segments dans le document informatisé de l'échange. Le pipeline d'envoi corrige le nombre dans le champ SE01 et publie l'avertissement.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Aucune action n'est nécessaire.