---
title: "Fonctionnalités pour les clients de l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapter features
- features, of the adapter
ms.assetid: 11792629-a692-4378-b522-d33484ee8acb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f929b14415265c4ad9894a16b87294dccd4e906f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="features-for-siebel-adapter-clients"></a>Fonctionnalités pour les clients de l’adaptateur Siebel
Outre les fonctionnalités présentées dans toutes les rubriques de [vue d’ensemble de l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md), le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] fournit les fonctionnalités suivantes sont utiles pour les clients de la carte :  
  
-   **Prise en charge de la configuration des cartes à l’aide des propriétés de liaison**. Les clients de l’adaptateur peuvent configurer le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] en spécifiant certaines propriétés de liaison lors de la génération de métadonnées. Pour plus d’informations, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
-   **Prise en charge des valeurs null pour les paramètres de l’opération**. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] permet aux clients d’adaptateur fournir des valeurs null pour les paramètres d’opération objet métier à l’aide de l’attribut « nillable » XSD. L’adaptateur ne transmet pas de champs avec des valeurs null dans le système Siebel.  
  
-   **Prise en charge pour la diffusion en continu de données XML**. Les clients de l’adaptateur peuvent diffuser des données depuis ou vers le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] à l’aide de la **XMLReader** ou **XMLWriter** interfaces.  
  
-   **Prise en charge pour les ports dynamiques dans BizTalk Server**. Via BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] prend en charge un port dynamique qui active le routage dynamique de messages de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] basée sur les propriétés de contexte de message. Pour plus d’informations, consultez [configuration des ports dynamiques avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/configure-dynamic-ports-with-the-siebel-adapter.md).  
  
-   **Prise en charge pour le versioning de messages**. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] prend en charge le contrôle de version de message. Cela permet la prise en charge pour les schémas de message différents dans les futures versions de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [prise en charge du Versioning de Message](../../adapters-and-accelerators/adapter-siebel/message-versioning-support2.md).  
  
-   **Prise en charge pour les compteurs de performance**. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] prend en charge les compteurs de performances basée sur WCF qui permet aux clients de l’adaptateur. Pour plus d’informations sur les compteurs de performance, consultez [utiliser des compteurs de performances avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/use-performance-counters-with-the-siebel-adapter.md).  
  
    > [!NOTE]
    >  Cette fonctionnalité ne fournit pas de compatibilité descendante avec les versions précédentes de la carte.  
  
-   **Prise en charge pour l’encodage des noms d’élément XML**. Le[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] présente des entités à partir d’applications d’entreprise en tant que noms d’éléments XML. Des traits de soulignement sont les caractères spéciaux seulement qui peuvent être inclus dans les noms d’élément. Par conséquent, des traits de soulignement sont utilisés pour encoder les noms d’éléments avec des caractères spéciaux. Par exemple, `emp$name` est encodé à `emp_x0024_name`.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)