---
title: "L'échange comportait une erreur structurelle. La partie située après l’erreur a été interrompue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9071825d-7b90-42bf-bcf9-2a15ae36086d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a028608e9843ee40c26bc7e8b158d97552a58163
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-had-structural-error-the-part-after-the-error-is-being-suspended"></a>L'échange comportait une erreur structurelle. La partie située après l'erreur a été interrompue
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EfactInterchangeStructuralError|  
|Texte du message|L’échange avec l’id '{0}', id d’expéditeur « {{1} », id de récepteur « {{2} » comportait une erreur structurelle. La partie située après que l’erreur a été interrompue, reportez-vous à la file d’attente pour plus d’informations|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange EDIFACT entrant car une erreur structurelle s'est produite dans l'échange. Cette erreur s'est produite avec un échange qui était conservé, avec des documents informatisés suspendus au moment de l'erreur. Par conséquent, les documents informatisés qui incluaient l'erreur ont été suspendus et les autres documents informatisés ont été traités dans le cadre du lot conservé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, demandez à l'expéditeur de corriger l'erreur structurelle, puis de renvoyer l'échange.