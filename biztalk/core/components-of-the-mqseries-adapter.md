---
title: "Composants de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, BizTalk component
- MQSeries adapters, components
- MQSeries components, MQSeries adapters
- BizTalk components
- MQSeries adapters, MQSeries component
ms.assetid: 923974cb-371d-47dc-99a7-2f7b93f60ada
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58726b6528af55da6554ff740208b3e03bdc806e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="components-of-the-mqseries-adapter"></a>Composants de l’adaptateur MQSeries
L'adaptateur MQSeries utilise deux composants pour simplifier le transfert de documents entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et MQSeries Server pour Windows.  
  
-   **Composant de BizTalk.** Installez ce composant sur le même ordinateur que Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ce composant communique avec BizTalk Server.  
  
-   **Composant MQSeries.** Installez ce composant sur le serveur MQSeries Server pour Windows. MQSeries Server pour Windows est exécuté sous [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. Ce composant (appelé MQSAgent) communique avec IBM MQSeries Server.  
  
    > [!NOTE]
    >  L'exécution du composant MQSAgent de l'adaptateur MQSeries est prise en charge sur MQSeries Server 5.3, CSD10 ou version ultérieure et WebSphere MQSeries Server 6.0 sous Windows.  
  
 La figure suivant illustre une utilisation typique de l'adaptateur.  
  
 ![Documenter le flux entre MQSeries Server et BizTalk](../core/media/bts-dev-mqadapterflow.gif "BTS_Dev_MQAdapterFlow")  
  
 L'adaptateur MQSeries est une solution de connectivité qui vous permet d'utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans une entreprise avec MQSeries comme norme de messagerie. Le développement de cette solution a été motivé, en partie, par les problématiques suivantes :  
  
-   répondre aux demandes des clients relatives à la simplification de l'installation et de la configuration, et à une solution de connectivité MQSeries ;  
  
-   prendre en charge les tailles de message jusqu'à 100 Mo ;  
  
-   assurer la prise en charge de MQSeries ;  
  
-   fournir une solution de connectivité Plug-and-Play pour les messages MQSeries à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 L'adaptateur MQSeries constitue un ajout important à la suite de services de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui fournit un ensemble d'écouteurs pour divers protocoles normalisés de communication. Les écouteurs associent un protocole (par exemple, HTTP, FTP ou MQSeries) à une relation commerciale d'intégration d'applications d'entreprise, interentreprises ou interapplications.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de l’adaptateur MQSeries](../core/mqseries-adapter-architecture.md)   
 [Nouveautés de l’adaptateur MQSeries ?](../core/what-is-the-mqseries-adapter.md)