---
title: "Développer des applications BizTalk à l’aide de l’adaptateur Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf3374a2-2fca-4df4-a1b1-d11cdc05d393
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d201987490d9395b07d043c67fa50a31400fe7cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-biztalk-applications-using-the-oracle-e-business-suite-adapter"></a>Développer des applications BizTalk à l’aide de l’adaptateur Oracle E-Business Suite
Développement d’applications BizTalk implique la création d’un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]et à l’aide de la  **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]**  ou  **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]**  pour générer le schéma XML. Une fois que vous avez généré le schéma, vous pouvez utiliser le routage basé sur le contenu (CBR) ou créer des orchestrations BizTalk pour envoyer et recevoir des messages conformes au schéma généré.  
  
 CBR peut être utilisé dans les scénarios où les messages envoyés à Oracle E-Business Suite nécessitent un traitement intensif. Par exemple, si vous savez que les messages de réception de port de réception uniquement d’un certain type, vous pouvez ajouter un filtre au port d’envoi pour router les messages qui correspondent à l’expression de filtre pour le port d’envoi.  

## <a name="use-orchestration"></a>Utiliser l’orchestration  
 Dans les orchestrations BizTalk, vous créez envoi et ports de réception pour envoyer et recevoir des messages vers et depuis le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], qui à son tour envoie des messages à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. 
 
 Cette section fournit des informations sur l’utilisation des orchestrations BizTalk pour effectuer les tâches et les opérations sur Oracle E-Business Suite à l’aide du [!INCLUDE[adapteroraclebusinessshort_md](../../includes/adapteroraclebusinessshort-md.md)]. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] à son tour utilise le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], ce qui peut interagir avec une liaison WCF.  
  
> [!IMPORTANT]
>  Pour utiliser le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez toujours définir la **EnableBizTalkCompatibilityMode** liaison de propriété **True**. Pour connaître les étapes, consultez [configurer les propriétés de liaison pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md).  
  

  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)