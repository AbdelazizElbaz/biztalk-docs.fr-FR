---
title: "Erreurs d’exécution WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5591bd4-aa15-4c7a-903e-fc73b880692f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97f4107ddf791b8d9fd152f2258cd3185f23498f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-run-time-errors"></a>Erreurs WCF au moment de l'exécution
Informations pour diagnostiquer et résoudre les événements d’exécution WCF.  
  
## <a name="wcf-service-host-restarted"></a>Hôte de service WCF redémarré
  
||Détails de l’erreur|  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0x1FB0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|BTS_I_WCF_SERVICE_HOST_RESTARTED|  
|Texte du message|0|  
  
## <a name="explanation"></a>Explication  
 Ce message permet à l'adaptateur WCF d'ajouter une entrée à caractère informatif au journal des événements alors que les API fournies pour les adaptateurs autorisent la création d'avertissements et d'erreurs, mais pas d'informations.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Lorsque le journal des événements a consigné un événement à caractère informatif, cela signifie que la récupération automatique a réussi. Aucune action supplémentaire n'est requise.