---
title: "Obtenir les métadonnées pour les opérations Oracle E-Business Suite dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87d7f731-cd0f-4970-a3cd-072f09312989
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97ef4cc308979718f306958d0da1bb1eceaebaf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-for-oracle-e-business-suite-operations-in-visual-studio"></a>Obtenir les métadonnées pour les opérations Oracle E-Business Suite dans Visual Studio
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] fournit trois [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants que vous pouvez utiliser pour vous aider à développer des solutions à l’aide de l’adaptateur :  
  
-   [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]  
  
-   [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]  
  
-   [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]  
  
 Clients de l’adaptateur doivent utiliser ces composants pour se connecter à Oracle E-Business Suite, puis générer des métadonnées pour les opérations à effectuer. Tous ces [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants simplifient le développement par :  
  
-   En fournissant une interface de Microsoft Windows par le biais duquel vous pouvez parcourir et rechercher pour les opérations que vous souhaitez utiliser dans votre solution.  
  
-   La récupération des métadonnées exposées par l’adaptateur pour ces opérations de la cible.  
  
-   Conversion de ces métadonnées, exprimé sous forme d’un document Web Services Description Language (WSDL) par l’adaptateur, dans un formulaire que vous pouvez utiliser dans votre solution (schémas de message XSD pour les projets BizTalk ou d’une représentation d’objet .NET d’un contrat de service WCF modèle de service) et son ajout à votre projet.  
  
 Cette section fournit des instructions sur l’utilisation de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
> [!NOTE]
>  Si vous avez créé une solution à l’aide de l’adaptateur sur une version particulière d’Oracle E-Business Suite et que vous souhaitez maintenant déployer la solution sur une autre version d’Oracle E-Business Suite vous devez tester la solution avant de le déployer. Vous risquez de rencontrer des problèmes lors du déploiement de la solution sur une autre version d’Oracle E-Business Suite, car les métadonnées de l’objet sous-jacent peuvent être différente. Pour résoudre ce problème, vous devez régénérer les métadonnées à l’aide de la carte sur la même version d’Oracle E-Business Suite sur lequel vous prévoyez de déployer la solution.  
  
