---
title: "Considérations relatives à la création de projets BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects, size
- map type name
- projects, naming conventions
- projects, planning
ms.assetid: f6c3dc71-105f-46af-9e6e-9a4c3b982d8c
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e9d05e07465d834f587f79d50f04bec18a89506
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-creating-biztalk-projects"></a>Considérations à prendre en compte lors de la création de projets BizTalk
Cette section fournit des informations à prendre en compte lors de la création de projets BizTalk à l’aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## <a name="avoid-compilation-errors-caused-by-projects-that-are-too-large"></a>Éviter les erreurs de compilation causées par des projets trop volumineux  
 Le compilateur [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] ne réussira pas la compilation d’un projet si elle donne lieu à un assembly supérieur à 75 Mo. Lorsque le compilateur atteint une contrainte de taille elle émet l’erreur irrécupérable CS0013 « erreur inattendue lors de l’écriture au fichier \<nom de fichier > » et s’arrêter.  
  
 Afin d’éviter ce problème, nous préconisons que les projets n’excèdent pas 10 Mo, sauf en cas de nécessité absolue. Pourquoi ?  
  
-   Les projets plus petits sont potentiellement plus simples à déployer en raison du nombre limité d’étapes de déploiement. Et ces étapes ont des chances d’être étroitement liées, par exemple, la gestion des remises des partenaires commerciaux ou la gestion des appels d'offres.  
  
-   Il est plus facile d’identifier les bogues, les problèmes de déploiement et autres lors de l’utilisation de projets plus petits. Repérer un bogue dans un projet comportant 140 schémas et de nombreux mappages et scripts personnalisés sera beaucoup plus difficile que dans un projet ne comprenant que 10 schémas et quelques mappages et scripts personnalisés.  
  
-   La division d’un gros projet en plus petits projets peut permettre de réduire la complexité. Les projets de plus petite taille sont plus faciles à gérer.  
  
-   La compilation des projets plus petits est plus rapide.  
  
-   La division d’un gros projet comportant de nombreux schémas non apparentés en projets plus petits avec des schémas étroitement liés peut améliorer les performances, Il s’agit, car seules certaines des assemblys seront chargé à la fois.  
  
## <a name="avoid-using-the-project-name-as-the-map-type-name"></a>Éviter d’utiliser le nom de projet comme nom de type de mappage  
 Lors de l’ajout d’un nouveau mappage à un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], n’utilisez pas le nom du projet comme nom de type. Dans ce cas, le compilateur génère une ou plusieurs erreurs semblables à « le nom de type \<nom >' n’existe pas dans le type ».  
  
 Pour modifier le nom de type pour un mappage à partir d’un projet BizTalk, cliquez sur la carte dans le volet Explorateur de solutions, puis vérifiez la propriété de nom de type dans le volet Propriétés. Si elle est identique, vous devez la modifier en veillant à changer les configurations associées.  
  
## <a name="visual-studio-team-system-support"></a>Prise en charge de Visual Studio Team System  
 Les projets BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] ne prennent pas directement en charge l'ensemble des composants de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Team System. Les composants de contrôle de code source de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Team System sont pris en charge pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. Visual Source Safe est également entièrement pris en charge pour le suivi et la gestion des versions des artefacts de projet BizTalk.