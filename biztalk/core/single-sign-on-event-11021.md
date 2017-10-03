---
title: "Single Sign-On : Événement 11021 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70b987aa-8097-4243-a25b-f1cc12c5bc6a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1e246ac3d0bbab4e991b17c091567b4b59131b4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11021"></a>Single Sign-On : Événement 11021
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11021|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_INFO_EXTERNAL_TO_EXTERNAL_MAPPING_CONFLICT_ALLOWED|  
|Texte du message|La modification d'un mot de passe externe entraînera la modification d'un autre compte externe.%r<br /><br /> Cette opération est autorisée car l'adaptateur pour ce système externe est configurée de sorte à ne pas autoriser les conflits de mappage.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Compte Windows : %3 %r<br /><br /> Compte externe 1 : %4 %r<br /><br /> Compte externe 2 : %5|  
  
## <a name="explanation"></a>Explication  
 Ce message d'information indique que la modification d'un mot de passe externe entraînera la modification d'un autre compte externe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vous devez vérifier immédiatement que vous aviez connaissance de cette modification et l'aviez autorisée. Dans ce cas, aucune action n'est requise. Sinon, déterminez où le changement a été initié et confirmez qu'il s'agissait d'un emplacement sûr au sein du système. 