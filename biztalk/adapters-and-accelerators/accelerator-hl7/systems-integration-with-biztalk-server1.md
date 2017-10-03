---
title: "Intégration des systèmes avec BizTalk Serveur1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system integration
- BizTalk Server, tools
- business processes, automating
- BTAHL7, BizTalk Server
- BizTalk Server
- BizTalk Server, business process automation
- BizTalk Server, messages
- BizTalk Server, system integration
ms.assetid: 8f66a4fc-186c-415f-a7ed-31f620f0495f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13eba7a4a799803340d2757bd39c3e5e9844603e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="systems-integration-with-biztalk-server"></a>Intégration des systèmes avec BizTalk Server
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] est un serveur d’intégration conçu pour les applications de commerce électronique. Il repose sur le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsWinSvrNoVersion](../../includes/btswinsvrnoversion-md.md)] plateforme du système, y compris [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Windows Server 2008, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)], et [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]et s’appuie sur les fonctionnalités de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[vs2012](../../includes/vs2012-md.md)]. Cette pile de technologies fournit une gamme de fonctionnalités pour le développement, l’implémentation, de fonctionnement et maintenance de votre solution.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]fournit les services d’intégration suivants que vous pouvez utiliser conjointement avec [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]). Pour plus d’informations sur [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] integration services, consultez [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
## <a name="message-integration"></a>Intégration de message  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]s’intègre à différentes entités (services, des partenaires commerciaux, fournisseurs et ainsi de suite) par l’automatisation de l’échange de messages. Il utilise Extensible Markup Language (XML) comme un protocole de communication commun. Il utilise des schémas de définition de schéma XML (XSD) pour décrire et valider les messages et XSLT (XSL Transformations) pour transformer des données à partir d’un message à un autre.  
  
 Le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] moteur d’intégration achemine les messages d’un emplacement à un autre. Elle propose un modèle de serveur de publication/abonné qui permet à un service publier un document et une autre pour vous abonner à ce dernier. Le service d’abonnement peut s’abonner au message sans le service de publication soit consciente. Cela permet une gestion efficace des organisations partenaires, en remplaçant des communications point à point avec une disposition flexible hub/spoke.  
  
## <a name="business-process-automation"></a>Automatisation des processus  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]automatise et intègre des processus d’entreprise à l’aide d’une carte de processus appelée une orchestration pour lier un ensemble d’actions distinctes, connexes dans un seul processus. En créant une orchestration, vous pouvez lier des étapes basées sur l’échange de données et l’analyse, telles que les boucles de réception, le message envoyé, décisions, des messages et autres opérations. Une orchestration vous permet de créer un processus d’entreprise qui s’exécutent automatiquement lorsqu’un événement se produit.  
  
 À l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous pouvez modifier dynamiquement un processus basé sur des règles d’entreprise. Cela vous donne la possibilité de modifier les actions effectuées dans un processus orchestré en fonction des règles d’entreprise. Un exemple est limitant le processus d’approbation pour les commandes de facturation pour ces commandes sur un certain seuil.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]vous permet également d’inclure des actions humaines dans les orchestrations automatisées, via les Services HWS.  
  
## <a name="integration-of-heterogeneous-systems"></a>Intégration de systèmes hétérogènes  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]peut intégrer des systèmes informatiques dans un environnement hétérogène dans lequel les systèmes transmettent des données dans différents protocoles de communication. Il le fait à l’aide des adaptateurs pour se connecter à des systèmes utilisant différents protocoles. Il prend en charge l’utilisation des adaptateurs de fichier, FTP, HTTP, SMTP, SOAP et SQL. Vous pouvez créer des adaptateurs personnalisés à l’aide de l’infrastructure d’adaptateurs BizTalk.  
  
## <a name="role-based-tools"></a>Outils basés sur le rôle  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]est un environnement de développement et d’exécution dans lequel les développeurs, les professionnels de l’informatique et les professionnels de l’entreprise collaborent pour créer, mettre en œuvre, fonctionnent, mettre à jour et personnaliser le système. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]chacun de ces rôles offre les outils adaptées à leur utilisation.  
  
 Pour plus d’informations, consultez [produit basé sur un rôle](../../adapters-and-accelerators/accelerator-hl7/a-role-based-product1.md), et [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
## <a name="see-also"></a>Voir aussi  
 [BizTalk Accelerator pour HL7 ajoutée à BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/what-biztalk-accelerator-for-hl7-adds-to-biztalk-server.md)