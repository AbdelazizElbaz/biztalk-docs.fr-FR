---
title: Les Services Web sur Internet et les Services WCF de publication | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7553608-f57a-470e-91d4-75504b3fd52b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38ee916aaa5e158160f2096b0ba9b2678dd6b8d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-internet-facing-web-services-and-wcf-services"></a>Publication de Services Web exposés à Internet et les Services WCF
Vous pouvez utiliser plusieurs approches pour la publication [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services Web et les services WCF à Internet :  
  
-   Utilisez les règles de proxy inverse dans un réseau de périmètre (également appelé DMZ, zone démilitarisée et sous-réseau filtré).  
  
-   Placer les ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui permettent de publier les services Web ou les services WCF dans le domaine de réseau de périmètre.  
  
-   Utilisez [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] cloud des fonctionnalités d’activation pour publier les services Web ou les services WCF sous la forme d’un point de terminaison de relais Azure AppFabric Service Bus.  
  
## <a name="using-a-reverse-proxy"></a>À l’aide d’un Proxy inverse  
 Il s’agit de l’approche traditionnelle pour la publication [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services Web et les services WCF. À l’aide des règles de proxy inverse dans le réseau de périmètre évite la nécessité de disposer de serveurs BizTalk Server situés dans le réseau de périmètre. Les règles de proxy inverse pour transférer simplement les demandes HTTP et SOAP à partir du réseau de périmètre vers les ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans le domaine de l’intranet.  
  
 Pour plus d’informations sur l’utilisation d’un proxy inverse, consultez les rubriques suivantes dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] aider à :  
  
-   [« Exemple d’Architecture : adaptateurs HTTP et SOAP «](http://go.microsoft.com/fwlink/?LinkId=153339) (http://go.microsoft.com/fwlink/?LinkId=153339).  
  
-   [« Exemples de menaces : adaptateurs HTTP et SOAP «](http://go.microsoft.com/fwlink/?LinkId=153340) (http://go.microsoft.com/fwlink/?LinkId=153340).  
  
-   [« Large Distributed Architecture »](http://go.microsoft.com/fwlink/?LinkId=153341) (http://go.microsoft.com/fwlink/?LinkId=153341).  
  
## <a name="using-computers-running-biztalk-server-in-the-perimeter-network"></a>À l’aide des ordinateurs exécutant BizTalk Server dans le réseau de périmètre  
 Cela n’est pas la meilleure approche pour la publication [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services ou des services WCF à Internet, car elle requiert des ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] se trouve dans le réseau de périmètre. Toutefois, lorsqu’un proxy inverse n’est pas disponible dans le réseau de périmètre, vous pouvez utiliser cette approche.  
  
 Cette approche, le domaine de réseau de périmètre pour l’inscrire dans une approbation à sens unique avec le domaine de l’intranet (mais le domaine de l’intranet n’approuve pas le domaine de réseau de périmètre). Les pools de l’application IIS qui hébergent que les services Web ou les services WCF dans le domaine de réseau de périmètre doivent être en cours d’exécution sous un compte de domaine intranet qui se trouve dans le groupe de domaine « Utilisateurs d’hôtes isolés BizTalk ». Ainsi, le pool d’applications les droits requis pour publier des messages à le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données MessageBox.  
  
 Vous devez ouvrir des ports spécifiques dans le pare-feu pour tenir compte de cela. Pour plus d’informations sur les ports requis, consultez [« Ports pour le recevoir et envoyer des serveurs »](http://go.microsoft.com/fwlink/?LinkId=153342) (http://go.microsoft.com/fwlink/?LinkId=153342) dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.  
  
## <a name="exposing-biztalk-applications-on-the-cloud-using-appfabric-connect-for-services"></a>Exposer les Applications BizTalk sur le Cloud à l’aide d’AppFabric Connect pour les Services  
 Consultez l’article [exposer les Applications BizTalk sur le Cloud à l’aide d’AppFabric Connect pour les Services](http://go.microsoft.com/fwlink/?LinkID=204700) (http://go.microsoft.com/fwlink/?LinkID=204700) pour plus d’informations sur des Applications BizTalk exposer en tant que Services WCF sur le cloud.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification de la publication Web Services1](../technical-guides/planning-for-publishing-web-services1.md)