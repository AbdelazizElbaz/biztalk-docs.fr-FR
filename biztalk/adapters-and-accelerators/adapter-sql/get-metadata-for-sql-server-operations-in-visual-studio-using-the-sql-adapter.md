---
title: "Obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a7ac720-e573-4564-8d15-8212a815f1f7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec993dd308abf0f364eb73f6f35d48d618d6807e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter"></a>Obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] fournit trois [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] les composants que vous pouvez utiliser pour vous aider à développer des solutions à l’aide de l’adaptateur, le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]. Les clients de l’adaptateur doivent utiliser ces composants pour se connecter à SQL Server et générer ensuite des métadonnées pour les opérations à effectuer.  
  
 Tous ces [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants simplifient le développement par :  
  
-   En fournissant une interface de Microsoft Windows par le biais duquel vous pouvez parcourir et rechercher pour les opérations que vous souhaitez utiliser dans votre solution.  
  
-   La récupération des métadonnées exposées par l’adaptateur pour ces opérations de la cible.  
  
-   Conversion de ces métadonnées, exprimé sous forme d’un document Web Services Description Language (WSDL) par l’adaptateur, dans un formulaire que vous pouvez utiliser dans votre solution (schémas de message XSD pour les projets BizTalk ou d’une représentation d’objet .NET d’un contrat de service WCF modèle de service) et son ajout à votre projet.  
  
 Cette section fournit des instructions sur l’utilisation de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
