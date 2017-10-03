---
title: "L'échange comportait une erreur structurelle. Dernier groupe structurellement valide était d’ID : | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd62855b-ecc6-4cfd-be9c-0025348eb841
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 565a4865455cabef3cd53988d601a89ecf1549e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-had-structural-error-last-structurally-valid-functional-group-id-was"></a>L'échange comportait une erreur structurelle. Le dernier ID de groupe structurellement valide était :
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12InterchangeStructuralErrorAfter1stGroup|  
|Texte du message|L’échange avec l’id '{0}', id d’expéditeur « {{1} », id de récepteur « {{2} » comportait une erreur structurelle. Dernier ID de groupe structurellement valide était '{3}'|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange X12 entrant, car une erreur structurelle s'est produite dans l'échange après le groupe fonctionnel indiqué. Cela peut être survenu avec un échange qui a été conservé, avec des documents informatisés suspendus sur l’erreur. Par conséquent, les documents informatisés qui incluaient l'erreur ont été suspendus et les autres documents informatisés ont été traités dans le cadre du lot conservé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, demandez à l'expéditeur de corriger l'erreur structurelle, puis de renvoyer l'échange.