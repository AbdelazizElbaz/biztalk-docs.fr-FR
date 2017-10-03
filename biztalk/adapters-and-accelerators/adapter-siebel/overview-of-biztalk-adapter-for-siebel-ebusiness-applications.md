---
title: "Vue d’ensemble de l’adaptateur BizTalk pour Siebel eBusiness Applications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overview, adapter
- adapter, overview of
- adapter, overview
ms.assetid: 41ab7d42-7096-45ef-9763-a5ccf88eb652
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efcc3a90f7025a5f396cd778676f5f3152bc7657
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-biztalk-adapter-for-siebel-ebusiness-applications"></a>Vue d’ensemble de l’adaptateur BizTalk pour Siebel eBusiness Applications
Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] expose le système Siebel comme service WCF. Les clients de carte peuvent effectuer des opérations sur le système Siebel en échangeant des messages SOAP avec l’adaptateur. L’adaptateur utilise le message WCF et appelle approprié au système Siebel pour effectuer l’opération. L’adaptateur renvoie la réponse à partir du système Siebel au client sous la forme des messages SOAP.  
  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] des métadonnées de surfaces d’artefacts Siebel (composants d’entreprise, services d’entreprise) qui décrivent la structure d’un protocole SOAP du message sous la forme de WSDL. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] utilise le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] et [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour permettre aux clients d’adaptateur récupérer des métadonnées pour les opérations et génère des artefacts de programmation qui peuvent être utilisés dans votre solution de programmation.  
  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] utilise le contrôle de données Siebel COM d’accéder au système Siebel. Le contrôle de données Siebel COM est fourni avec le client Siebel Web. Par conséquent, assurez-vous que le client Siebel Web est installé sur le même ordinateur que le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Vous pouvez utiliser la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] pour communiquer avec le système Siebel comme suit :  
  
-   En développant des applications BizTalk. Consultez [développement d’Applications de BizTalk Server](../../core/developing-biztalk-server-applications.md).
  
-   À l’aide du modèle de service WCF. Consultez [développer des Applications Siebel à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md).  
  
-   À l’aide du modèle de canal WCF. Reportez-vous à développer des Applications de base de données Oracle à l’aide du modèle de canal WCF[Entrez la description du lien ici](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment l’adaptateur effectue la connexion à un système Siebel ?](https://msdn.microsoft.com/library/cc185212(v=bts.10).aspx)  
  
-   [Quels sont les métadonnées Siebel aire de conception d’adaptateur ?](https://msdn.microsoft.com/library/cc185267(v=bts.10).aspx)  
  
-   [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)  
  
-   [Autres fonctionnalités prises en charge par l’adaptateur](https://msdn.microsoft.com/library/cc185252(v=bts.10).aspx) 
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)