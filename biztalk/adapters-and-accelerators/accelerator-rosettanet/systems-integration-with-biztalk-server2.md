---
title: "Intégration des systèmes avec BizTalk Server2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system integration
- tools, BizTalk Server
- BizTalk Server, tools
- BizTalk Server, about BizTalk Server
- BizTalk Server, business processes
- messages, BizTalk Server
- BizTalk Server, messages
- BizTalk Server, system integration
- business processes, BizTalk Server
ms.assetid: 5ba3dda1-efdb-4a2b-bb3a-825d76696f15
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8729c6a197ce9ff6fe63f5d20499705fba3b258d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="systems-integration-with-biztalk-server"></a>Intégration des systèmes avec BizTalk Server
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server est un serveur d’intégration conçu pour les applications de commerce électronique. Il repose sur le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsWinSvrNoVersion](../../includes/btswinsvrnoversion-md.md)] plateforme du système, y compris [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsWinSvrNoVersion](../../includes/btswinsvrnoversion-md.md)]® 2008, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 2008 R2/2008 SP1, et [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] SharePoint® Services et tire profit du fonctionnalités de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Cette pile de technologies fournit une gamme de fonctionnalités pour le développement, l’implémentation, de fonctionnement et maintenance de votre solution.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]fournit les services d’intégration suivants que vous pouvez utiliser conjointement avec [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]. Pour plus d’informations sur [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] integration services, consultez [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] aide.  
  
## <a name="message-integration"></a>Intégration de message  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]s’intègre à différentes entités (services, les partenaires commerciaux, fournisseurs) grâce à l’automatisation de l’échange de messages. XML est utilisé comme un protocole de communication commun. Il utilise des schémas de définition de schéma XML (XSD) pour décrire et valider les messages et XSLT (XSL Transformations) pour transformer des données à partir d’un message à un autre.  
  
 Le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] moteur d’intégration achemine les messages d’un emplacement à un autre. Elle propose un modèle de serveur de publication/abonné qui permet à un service publier un document et une autre pour vous abonner à ce dernier. Le service d’abonnement peut s’abonner au message sans le service de publication soit consciente. Cela permet une gestion efficace des organisations partenaires, en remplaçant des communications point à point avec une disposition flexible hub/spoke.  
  
## <a name="business-process-automation"></a>Automatisation des processus  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]automatise et intègre des processus d’entreprise à l’aide d’une carte de processus appelée une orchestration pour lier un ensemble d’actions distinctes, connexes dans un seul processus. En créant une orchestration, vous pouvez lier des étapes basées sur l’échange de données et l’analyse, telles que les boucles de réception, le message envoyé, décisions, des messages et autres opérations. Avec une orchestration, vous pouvez créer un processus d’entreprise qui s’exécutent automatiquement lorsqu’un événement se produit.  
  
 À l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous pouvez modifier dynamiquement un processus basé sur des règles d’entreprise. Cela vous donne la possibilité de modifier les actions effectuées dans un processus orchestré en fonction des règles d’entreprise. Un exemple est limitant le processus d’approbation pour les commandes de facturation pour ces commandes sur un certain seuil.  
  
 À l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous pouvez inclure des actions humaines dans les orchestrations automatisées via les Services HWS. Pour plus d’informations, consultez « Human Workflow Services (HWS) » dans [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] aide.  
  
## <a name="integration-of-heterogeneous-systems"></a>Intégration de systèmes hétérogènes  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]peut intégrer des systèmes informatiques dans un environnement hétérogène dans lequel les systèmes transmettent des données dans différents protocoles de communication. Il le fait à l’aide des adaptateurs pour se connecter à des systèmes utilisant différents protocoles. Il prend en charge l’utilisation des adaptateurs de fichier, FTP, HTTP, SMTP, SOAP et SQL. Vous pouvez créer des adaptateurs personnalisés à l’aide de l’infrastructure d’adaptateurs BizTalk. Pour plus d’informations, consultez « Développement d’adaptateurs à l’aide de l’infrastructure d’adaptateurs » dans [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] aide.  
  
## <a name="role-based-tools"></a>Outils basés sur le rôle  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]est un environnement de développement et d’exécution dans lequel les développeurs, les professionnels de l’informatique et les professionnels de l’entreprise collaborent pour créer, mettre en œuvre, fonctionnent, mettre à jour et personnaliser le système. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]chacun de ces rôles offre les outils personnalisés pour leur utilisation.  
  
 Pour plus d’informations, consultez [A Role-Based produit &#91; RN3 &#93; ](../../adapters-and-accelerators/accelerator-rosettanet/a-role-based-product2.md), et [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] aide.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment BizTalk Server résout les besoins de l’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/how-biztalk-server-solves-the-business-need1.md)   
 [Ce qu’apporte BizTalk Accelerator pour RosettaNet à BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)