---
title: "Gérer les versions d’adaptateur avec WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb596fdd-251c-4978-9f33-cf2883d281d8
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf8d5d13c37f683a118484c9c08fa90c13a95533
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-adapter-versioning-with-the-wcf-lob-adapter-sdk"></a>Gérer les versions d’adaptateur avec WCF LOB Adapter SDK
Après le déploiement initial des cartes et potentiellement plusieurs fois pendant leur durée de vie, adaptateurs (et les points de terminaison qu’ils exposent) peut-être être changé pour diverses raisons. Ces raisons sont modifier des besoins, spécifications informatiques ou problèmes liés à la ligne de système d’entreprise ou de l’adaptateur lui-même. Cette rubrique décrit les différentes stratégies pour gérer le contrôle de version pour les cartes qui sont écrits à l’aide de la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].  
  
## <a name="versioning-and-windows-communication-foundation"></a>Le contrôle de version et de Windows Communication Foundation  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] repose sur [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] et s’appuie sur son infrastructure d’échange de messages entre les systèmes. À l’aide des mécanismes qui [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] expose, vous pouvez la version des contrats de services et données. Pour plus d’informations, y compris les meilleures pratiques pour le contrôle de version de service, consultez [le Service de contrôle de version](http://go.microsoft.com/fwlink/?LinkId=85497) dans le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] référence en ligne. Pour plus d’informations, y compris les meilleures pratiques pour la version des contrats de données, consultez [contrôle de version de contrat de données](http://go.microsoft.com/fwlink/?LinkId=120177) dans le [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] référence en ligne.  
  
## <a name="versioning-scenarios"></a>Scénarios de contrôle de version  
 Il existe deux scénarios de contrôle de version principale :  
  
-   Une version de l’adaptateur prend en charge plusieurs versions du système cible.  
  
-   Deux ou plusieurs versions d’adaptateur prend en charge le même système ou deux ou plusieurs systèmes différents.  
  
 Vous devez également libérer une nouvelle version de votre carte si des mises à jour pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] affecte les fonctionnalités existantes.  
  
 Chacun de ces scénarios nécessite une stratégie de contrôle de version différents.  
  
> [!NOTE]
>  Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] n’applique pas les scénarios de contrôle de version spécifique. Il est laissé au développeur de déterminer la configuration requise pour un adaptateur de contrôle de version.  
  
### <a name="one-adapter-supports-multiple-versions-of-target-system"></a>Un adaptateur prend en charge plusieurs versions du système cible  
 Lorsque l’adaptateur prend en charge plusieurs versions du système cible, vous devez exposer une ou plusieurs propriétés de liaison qui peuvent être utilisées pour identifier la version souhaitée. Par exemple, un adaptateur peut prendre en charge plusieurs bibliothèques de communication fournis par le fabricant du système cible. À l’aide d’une propriété de liaison personnalisée nommée « LibraryVersion », le consommateur de l’adaptateur peut choisir la bibliothèque à utiliser en fonction de l’environnement de déploiement ou d’autres exigences.  
  
### <a name="two-or-more-adapters-support-one-version-of-target-system"></a>Deux ou plusieurs cartes prennent en charge une version du système cible  
 Dans ce cas, chaque adaptateur doit utiliser un schéma unique (ContosoV1 : / / et ContosoV2 : / /) et un nom unique de liaison (ContosoV1Binding et ContosoV2Binding). Fournisseurs doivent prendre en compte à l’aide de leur nom dans le schéma et le nom de liaison ainsi (par exemple, Microsoft.ContosoV1:// et Microsoft.ContosoV1Binding).  
  
### <a name="new-versions-of-the-wcf-lob-adapter-sdk"></a>Nouvelles versions de WCF LOB Adapter SDK  
 Lors de nouvelles versions de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] sont publiées, vous serez en mesure d’installer la nouvelle version sans avoir à recompiler votre adaptateur, étant donné que [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] versions sont être compatibles en amont. Toutefois, vous devez évaluer les nouvelles versions afin de déterminer s’il existe une modification de fonctionnalité qui dépend de votre carte, ou s’il existe de nouvelles fonctionnalités que votre adaptateur tireront parti d’implémentation.  
  
## <a name="see-also"></a>Voir aussi  
 [Recommandées de développement à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)