---
title: "Erreur lors du chargement d’assembly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 600973e0-3142-455f-9afa-74430af31e38
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13be3acf6974565c86cc87b14ed58929553d5220
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-loading-assembly"></a>Erreur lors du chargement de l'assembly
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Cette erreur indique que l'emplacement n'est peut-être pas entièrement fiable s'il est situé sur un partage réseau. Vérifiez la stratégie de sécurité d'accès du code pour la zone. Il se peut que le fichier ne corresponde pas à un assembly .NET de BizTalk. Vérifiez l’assembly pour le [assembly : assembly BizTalk] attribut personnalisé. Il se peut que le fichier ne corresponde pas à un assembly .NET. Il peut s'agir d'un fichier .dll ou .exe qui inclut du code non géré|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que l'emplacement n'est peut-être pas entièrement fiable s'il est situé sur un partage réseau. Vérifiez la stratégie de sécurité d'accès du code pour la zone. Il se peut que le fichier ne corresponde pas à un assembly .NET de BizTalk. Vérifiez l’assembly pour le [*assembly : assembly BizTalk*] attribut personnalisé. Il se peut que le fichier ne corresponde pas à un assembly .NET. Il peut s'agir d'un fichier .dll ou exe qui inclut du code non géré.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Accordez un niveau Confiance totale à l'emplacement s'il provient d'une source fiable.  Vérifiez que le fichier .dll est un assembly .Net de BizTalk valide.