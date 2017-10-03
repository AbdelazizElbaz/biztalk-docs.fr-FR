---
title: "Single Sign-On : Événement 11020 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa6a0d72-ece6-4094-9263-dbf69bb068c8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 444a61beec74a9d7141df79d05d8863cc10d6dc6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11020"></a>Single Sign-On : Événement 11020
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11020|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_INFO_WINDOWS_TO_WINDOWS_MAPPING_CONFLICT_ALLOWED|  
|Texte du message|La modification d'un mot de passe Windows entraînera la modification d'un autre compte Windows.%r<br /><br /> Cette opération est autorisée car l'adaptateur pour ce système externe est configurée de sorte à ne pas autoriser les conflits de mappage.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Compte externe : %3 %r<br /><br /> Compte Windows 1 : %4 %r<br /><br /> Le compte Windows 2 : %5|  
  
## <a name="explanation"></a>Explication  
 Ce message d'information indique que la modification d'un mot de passe Windows entraînera la modification d'un autre compte Windows.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vous devez vérifier immédiatement que vous aviez connaissance de cette modification et l'aviez autorisée. Dans ce cas, aucune action n'est requise. Sinon, déterminez où le changement a été initié et confirmez qu'il s'agissait d'un emplacement sûr au sein du système. 