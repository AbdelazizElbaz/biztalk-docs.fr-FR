---
title: "Impossible d’accéder à l’accord à l’aide de destinataire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 470325f4-abc4-40bb-9109-9ffc73b496df
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f41b126ca0ebb96716f21381d2e1681ea59bd414
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-access-agreement-using-receiver-identity"></a>Impossible d'accéder à l'accord avec l'id de destinataire
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|UnableToLocateAS2PartyByPartyNameError|  
|Texte du message|Impossible d’accéder à l’accord à l’aide de destinataire : {0}|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que le pipeline d'envoi n'a pas pu déterminer le tiers pour un message AS2 sortant, car il n'est pas parvenu à mettre en correspondance la propriété de contexte AS2To du message sortant ou la propriété AS2To dans la propriété de contexte Http.UserHttpHeaders avec le nom du tiers dans la propriété AS2-To de la page Tiers considéré comme récepteur des messages AS2 dans la boîte de dialogue Propriétés AS2.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, définissez la propriété AS2-To de la page Tiers considéré comme récepteur des messages AS2 dans la boîte de dialogue Propriétés AS2 sur le nom de tiers approprié associé au message AS2 en erreur.