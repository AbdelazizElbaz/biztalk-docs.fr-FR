---
title: "Afficher les modèles d’échange de message pris en charge dans WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6662f17-b4f8-45fe-a22f-5d027dc9f2ff
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77fee95033e669bf584220461b330afbb9fd25b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="view-the-supported-message-exchange-patterns-in-the-wcf-lob-adapter-sdk"></a>Afficher les modèles d’échange de message pris en charge dans WCF LOB Adapter SDK
Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] prend en charge plusieurs modèles de messagerie pris en charge par sous-jacent [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] , y compris la demande-réponse et la communication unidirectionnelle. Différents transports prennent en charge les modèles de messagerie différents et ce qui affectent les types d’interactions qu’ils prennent en charge.  
  
 Les modèles répertoriés dans le tableau suivant sont gérées par le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  
  
|Motif| Description|  
|-------------|-----------------|  
|Unidirectionnel entrant|Les messages entrants sont reçus à partir du système métier- mais aucune réponse n’est attendue à partir de l’adaptateur.|  
|Requête-réponse entrante|Les messages entrants sont reçus à partir du système de métier qui attend une réponse appropriée à partir de l’adaptateur.|  
|Unidirectionnel sortant|Les messages sortants sont envoyés au système métier- mais aucune réponse n’est attendue à partir de l’adaptateur.|  
|Requête-réponse sortant|Les messages sortants sont envoyés au système métier-avec une réponse attendue de l’adaptateur.|  
|Session entrante|Les messages entrants sont reçus à partir du système de métier dans une session unique. Aucune réponse est attendue par le système de métier à partir de l’adaptateur.|  
|Session sortante|Les messages sortants sont envoyés au système métier-au sein d’une session unique. Aucune réponse n’est attendue à partir du système métier-par l’adaptateur.|  
  
 Le choix du modèle de message il sera demandé par la fonctionnalité de l’application cible.  
  
## <a name="planning-for-sessions"></a>Planification de Sessions  
 Un modèle de messagerie peut utiliser une session lorsqu’il souhaite s’assurer que tous les messages échangés entre l’adaptateur et le système métier-doivent être la partie de la même conversation. En général, les sessions sont utilisées lors de la garantie de remise est nécessaire, mais ils peuvent également être utilisés pour prendre en charge d’autres spécifications développeur d’adaptateurs peut avoir pour l’échange de messages.  
  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] s’appuie sur la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] pour la prise en charge de la session. Pour plus d’informations sur les sessions, consultez [Sessions, Instancing et concurrence](https://msdn.microsoft.com/library/ms731193.aspx). 
  
## <a name="see-also"></a>Voir aussi  
 [Planifier et concevoir un adaptateur à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)