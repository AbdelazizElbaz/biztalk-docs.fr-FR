---
title: "Single Sign-On : Événement 10671 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06c5564f-6412-4e83-9bec-03264e992ebe
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db44ecfd9980db445d3a611e4992f4b3961b3548
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10671"></a>Single Sign-On : Événement 10671
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10671|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_INFO_EXTERNAL_MAPPING_CONFLICT_ALLOWED|  
|Texte du message|La modification d'un mot de passe Windows entraîne la modification de plusieurs comptes au sein du même système externe.%r<br /><br /> Cette opération est autorisée car l'adaptateur pour ce système externe est configurée de sorte à ne pas autoriser les conflits de mappage.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Compte Windows : %3 %r<br /><br /> Compte externe 1 : %4 %r<br /><br /> Compte externe 2 : %5|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'informations indique que la modification d'un mot de passe Windows entraîne la modification de plusieurs comptes au sein du même système externe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
-   Aucune action utilisateur n’est nécessaire.  
  
## <a name="more-info"></a>En savoir plus
  
-   **Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)