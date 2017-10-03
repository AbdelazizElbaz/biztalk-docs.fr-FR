---
title: "Single Sign-On : Événement 10818 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ad54646-4285-42e5-a270-d56935742a95
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be2c40fa5da46f5045b55c815be9f6f8048cda67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10818"></a>Single Sign-On : Événement 10818
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10818|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_AMBIGUOUS_SYNC_FIELDS|  
|Texte du message|L'application doit inclure deux champs ou un seul champ doit être marqué pour la synchronisation.|  
  
## <a name="explanation"></a>Explication  
 S'il y a plus de deux champs, un seul doit être marqué pour la synchronisation des mots de passe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour remédier à cette situation, vous devez supprimer l'application et la recréer afin qu'elle soit conforme à ces instructions.