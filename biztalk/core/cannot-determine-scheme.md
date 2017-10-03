---
title: "Impossible de déterminer le schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cc6e50b-33f5-4a88-b35d-075fdf8d79b2
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82731b0712ac880936e074005c01eab7945b4add
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cannot-determine-scheme"></a>Impossible de déterminer le schéma
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible de déterminer le schéma ; indiquez une liaison valide.|  
  
## <a name="explanation"></a>Explication  
 L'élément de liaison de transport spécifié ne possède aucun schéma.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Sélectionnez une liaison valide et vérifiez que l'élément de liaison de transport possède un schéma valide. Si vous utilisez une liaison personnalisée, veillez à ce qu'un élément de liaison de transport valide soit spécifié.  
  
 Pour plus d’informations, consultez les ressources suivantes dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide :  
  
-   [Configuration de l’adaptateur WCF-Custom](../core/configuring-the-wcf-custom-adapter.md)