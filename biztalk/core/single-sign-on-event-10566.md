---
title: "Single Sign-On : Événement 10566 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7bd140b-5503-40f8-bf5d-604fa763989e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dec463e417ce7ab1a409f7660427d2f6882ea325
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10566"></a>Single Sign-On : Événement 10566
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10566|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_CANNOT_UPDATE_APP_FLAGS|  
|Texte du message|Il est impossible de mettre à jour certains des indicateurs spécifiés pour cette application. Ils seront ignorés.%r<br /><br /> Nom de l’application : %1 %r<br /><br /> Masque d’indicateur de spécifié : %2|  
  
## <a name="explanation"></a>Explication  
 Certains indicateurs d'une application ne peuvent pas être modifiés. (Par exemple, il n'est pas autorisé de modifier le type Individuel d'une application en type Groupe.) Les indicateurs pour cette application sont spécifiés dans le texte d'avertissement.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Aucune action de l'utilisateur n'est requise.