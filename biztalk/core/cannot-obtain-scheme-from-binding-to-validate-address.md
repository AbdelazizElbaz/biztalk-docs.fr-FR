---
title: "Impossible d’obtenir le schéma à partir de la liaison pour valider l’adresse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b002084a-63ae-4685-8ce3-88cc6489e19e
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c952e967a391011bbd887513d58e426d90d325a1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cannot-obtain-scheme-from-binding-to-validate-address"></a>Impossible d'obtenir le schéma à partir de la liaison pour valider l'adresse
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible d'obtenir le schéma à partir de la liaison pour valider l'adresse.|  
  
## <a name="explanation"></a>Explication  
 L'élément de liaison de transport spécifié ne possède aucun schéma.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez que l'élément de liaison de transport est valide ou possède un schéma valide. Si vous utilisez une liaison personnalisée, veillez à ce qu'un élément de liaison de transport valide soit spécifié.  
  
 Pour plus d’informations, consultez les ressources suivantes dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide :  
  
-   [Configuration de l’adaptateur WCF-Custom](../core/configuring-the-wcf-custom-adapter.md)