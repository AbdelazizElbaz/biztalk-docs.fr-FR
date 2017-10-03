---
title: "Impossible de fusionner les opérations en raison d’une collision de nom | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81ddb8b7-6f7e-420c-b7c3-921c0e305326
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8f884b4eea6be64f1d1575b157805703d12cee3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cannot-merge-operations-due-to-name-collision"></a>Impossible de fusionner l'opération en raison d'une collision de noms
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible de fusionner l'opération « {0} » en raison d'une collision de noms. Toutes les opérations d'un service Web doivent avoir des noms uniques.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que le nom ou le nom d'opération de deux ports en cours de fusion sont identiques.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 À l'aide de l'Assistant Configuration du port, vérifiez que tous les ports en cours de fusion portent différents noms ou sont associés à des opérations différentes.  
  
 Pour plus d'informations sur la configuration des ports, consultez la ressource suivante dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md)