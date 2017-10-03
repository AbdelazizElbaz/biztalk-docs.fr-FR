---
title: "Développer des applications d’Oracle E-Business Suite à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75bb6de1-e11a-4377-af13-e1cb954aaf3f
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e99dfa0c69500b86fe086ce0daa81e3ffb62857d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-oracle-e-business-suite-applications-using-the-wcf-channel-model"></a>Développer des applications d’Oracle E-Business Suite à l’aide du modèle de canal WCF
Vous pouvez utiliser la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de canal pour consommer le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] en envoyant des messages XML directement sur une instance de canal créée avec la liaison de Oracle eBusiness Suite.  
  
 L’un des avantages de l’utilisation du modèle de canal WCF en utilisant les classes fortement typées et les méthodes qui l’expose de modèle de service WCF est que le modèle de canal fournit un contrôle plus précis sur les opérations que vous effectuez sur Oracle E-Business Suite. Ce contrôle vient du fait que dans le modèle de canal WCF, vous contrôlez directement le contenu des messages que vous envoyez sur le canal.  
  
 Dans certains scénarios, ce niveau supplémentaire de contrôle peut être utile. Par exemple, lorsque vous utilisez le modèle de canal WCF pour effectuer une opération de mise à jour sur une table, vous pouvez sélectivement mettre à jour colonnes dans les lignes de la cible en omettant les colonnes à partir du modèle de mise à jour que vous passez dans le message. Seules les colonnes qui sont nécessaires sont celles avec « nillable = false » dans le WSDL. La méthode de mise à jour exposée par un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client utilise un paramètre d’enregistrement de fortement typé pour le modèle qui inclut toutes les colonnes dans le schéma de table.  
  
 Les rubriques de cette section expliquent comment effectuer des opérations sur les [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] en utilisant le modèle de canal WCF.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Vue d’ensemble du modèle de canal WCF avec l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md)  
  
-   [Créer un canal à l’aide d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-channel-using-oracle-e-business-suite.md)
  
-   [Exécuter une opération d’insertion sur une table d’interface dans Oracle E-Business Suite à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-ebs/insert-on-an-interface-table-in-oracle-ebs-using-the-wcf-channel-model.md)  
  
-   [Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT avec le modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement-with-the-wcf-channel-model.md)
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)