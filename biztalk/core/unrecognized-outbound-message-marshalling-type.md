---
title: Conversion de type du message sortant non reconnu | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e675112b-12f3-47ff-95f7-ce1a05db120e
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3928bde0d81a4fe22b7c16af41c3a4b6d5c7121c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unrecognized-outbound-message-marshalling-type"></a>Type de conversion du message sortant non reconnu
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Type de conversion du message sortant non reconnu ; UseBodyElement ou UseTemplate attendu|  
  
## <a name="explanation"></a>Explication  
 La propriété .OutboundBodyLocation WCF est définie sur une autre valeur que UseBodyElement ou UseTemplate, dans un composant de pipeline personnalisé ou une orchestration.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Définissez la propriété WCF.OutboundBodyLocation sur une valeur valide. Les valeurs valides sont « UseBodyElement » ou « UseTemplate ». Vous devez les modifier dans le code.   
Pour plus d’informations sur les messages sortants, consultez les ressources suivantes dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide :  
  
-   [Configuration des Ports d’envoi dynamiques à l’aide des propriétés de contexte des adaptateurs WCF](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)  
  
-   [Configuration des adaptateurs WCF](../core/configuring-the-wcf-adapters.md)