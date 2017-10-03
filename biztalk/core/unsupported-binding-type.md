---
title: Non pris en charge de type de liaison | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5556a7d7-f092-4f69-9561-88f51ac46cc9
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98d156f22b5e903cd704dc109f98435203bd6ba8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unsupported-binding-type"></a>Type de liaison non pris en charge
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Type de liaison non pris en charge|  
  
## <a name="explanation"></a>Explication  
 La liaison MsmqIntegration choisie n'est pas prise en charge par l'adaptateur WCF.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Utilisez l'adaptateur WCF NetMsmq. Si des messages MSMQ natifs doivent être échangés, utilisez l'adaptateur MSMQ BizTalk.  
  
 Pour plus d'informations sur la configuration des adaptateurs, consultez la ressource suivante :  
  
-   [Configuration de l’adaptateur WCF-NetMsmq](../core/configuring-the-wcf-netmsmq-adapter.md)