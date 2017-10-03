---
title: "Single Sign-On : Événement 10673 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa1d572a-1e9f-496e-a219-852e7d9228d5
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8068d7ec43cc07dfd76b21dc749ca062226e49f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10673"></a>Single Sign-On : Événement 10673
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10673|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_INFO_WINDOWS_MAPPING_CONFLICT_ALLOWED|  
|Texte du message|Le changement d'un mot de passe externe entraînera des modifications au niveau de plusieurs comptes Windows.%r<br /><br /> Cette opération est autorisée car l'adaptateur pour ce système externe est configurée de sorte à ne pas autoriser les conflits de mappage.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Compte externe : %3 %r<br /><br /> Compte Windows 1 : %4 %r<br /><br /> Le compte Windows 2 : %5|  
  
## <a name="explanation"></a>Explication  
 Cette information indique qu'un changement de mot de passe entraînera des modifications au niveau de plusieurs comptes Windows.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
-   Aucune action utilisateur n’est nécessaire.  
  
## <a name="more-info"></a>En savoir plus
  
-   [Comment administrer la synchronisation de mot de passe](../core/how-to-administer-password-synchronization.md)  
  
-   **Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)