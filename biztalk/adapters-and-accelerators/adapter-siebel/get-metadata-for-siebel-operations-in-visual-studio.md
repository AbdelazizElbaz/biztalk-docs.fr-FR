---
title: Obtenir les métadonnées pour les opérations Siebel dans Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving for Siebel operations in Visual Studio
ms.assetid: 63643942-6497-4891-ad7d-34b1df9acbc1
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30935631052adf4c455e730c476104b54a6a352b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-for-siebel-operations-in-visual-studio"></a>Obtenir les métadonnées pour les opérations Siebel dans Visual Studio
Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] fournit deux [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants que vous pouvez utiliser pour vous aider à développer des solutions à l’aide de l’adaptateur.  
  
-   Le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] est disponible dans les projets BizTalk Server. Vous utilisez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer des schémas de message (XSD) pour les opérations que vous souhaitez cibler dans votre solution BizTalk. Pour plus d’informations sur le développement de solutions avec BizTalk Server, consultez [BizTalk de développer les applications à l’aide de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md).
  
-   Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] est disponible dans les projets de programmation non-BizTalk. Vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer une classe de client WCF ou d’une interface de rappel de service WCF lorsque vous développez des solutions à l’aide du modèle de service WCF. Pour plus d’informations sur le développement de solutions avec le modèle de service WCF, consultez [Siebel de développer les applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md).  
  
 Ces deux [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants simplifient le développement par :  
  
-   En fournissant une interface de Microsoft Windows par le biais duquel vous pouvez parcourir et rechercher pour les opérations que vous souhaitez utiliser dans votre solution.  
  
-   La récupération des métadonnées exposées par l’adaptateur pour ces opérations de la cible.  
  
-   Conversion de ces métadonnées, exprimé sous forme d’un document Web Services Description Language (WSDL) par l’adaptateur, dans un formulaire que vous pouvez utiliser dans votre solution (schémas de message XSD pour les projets BizTalk ou d’une représentation d’objet .NET d’un contrat de service WCF modèle de service) et son ajout à votre projet.  
  
 Cette section fournit des instructions sur l’utilisation de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  

  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications Siebel](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)