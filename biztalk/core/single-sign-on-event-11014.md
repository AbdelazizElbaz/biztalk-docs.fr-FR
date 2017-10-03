---
title: "Single Sign-On : Événement 11014 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71e4c9bd-8bda-46ca-9e76-f7b4fa033167
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 138a580122beb34b82f642dfa4d60aa6d422b445
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11014"></a>Single Sign-On : Événement 11014
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11014|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_ERROR_ACCESS_CHECK|  
|Texte du message|Échec du contrôle d'accès.%r<br /><br /> L’utilisateur client : %1\\%2 %r<br /><br /> Nom de l’application : %3 %r<br /><br /> Données supplémentaires : %4 %r<br /><br /> Code d’erreur : %5|  
  
## <a name="explanation"></a>Explication  
 Le contrôle d'accès a échoué pour le client et l'application indiqués.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Les autres informations doivent permettent de résoudre le problème. Pour éviter cette erreur à l'avenir, vous pouvez abaisser le niveau d'audit.