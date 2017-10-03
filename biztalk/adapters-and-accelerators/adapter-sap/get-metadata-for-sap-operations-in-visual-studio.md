---
title: "Obtenir les métadonnées pour les opérations de SAP dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata, retrieving for SAP operations in Visual Studio
ms.assetid: 1be5934a-a5d4-4734-8bea-fb8274f59c71
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5c786ea9b1acbc3ed88c79187725697ce279ea5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-for-sap-operations-in-visual-studio"></a>Obtenir les métadonnées pour les opérations de SAP dans Visual Studio
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] fournit deux [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] les composants que vous pouvez utiliser pour vous aider à développer des solutions à l’aide de l’adaptateur, le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Les clients de l’adaptateur doivent utiliser ces composants pour se connecter à un système SAP et générer ensuite les métadonnées pour les artefacts SAP qu’ils veulent appeler.  
  
 Tous ces [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants simplifient le développement par :  
  
-   En fournissant une interface de Microsoft Windows par le biais duquel vous pouvez parcourir et rechercher pour les opérations que vous souhaitez utiliser dans votre solution.  
  
-   La récupération des métadonnées exposées par l’adaptateur pour ces opérations de la cible.  
  
-   Conversion de ces métadonnées, exprimé sous forme d’un document Web Services Description Language (WSDL) par l’adaptateur, dans un formulaire que vous pouvez utiliser dans votre solution (schémas de message XSD pour les projets BizTalk ou d’une représentation d’objet .NET d’un contrat de service WCF modèle de service) et son ajout à votre projet.  
  
 Cette section fournit des instructions sur l’utilisation de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
 
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications SAP](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)