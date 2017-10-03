---
title: "Administration à l’aide du portail de gestion ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 478d1dcc-e9b2-443b-be98-5b7545322401
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 351d06df4d6384607564778c4b86d8c509379488
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="administration-using-the-esb-management-portal"></a>Administration à l’aide du portail de gestion ESB
Le portail de gestion ESB inclus dans le cadre de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], est un exemple de site qui illustre l’utilisation de mesures et les possibilités qui existent pour l’extension de BizTalk ESB Toolkit. Le portail fournit un point de départ à partir duquel vous pouvez générer votre propre portail personnalisé.  
  
 Le portail de gestion ESB est également un outil hautement compatible et utile qui peut aider à optimiser l’utilisation et l’efficacité du système de gestion d’exception ESB. En outre, le portail fournit une interface utilisateur pour un serveur de Registre Universal Description, Discovery and Integration (UDDI) sous-jacent et des fonctionnalités de configuration graphique des fonctionnalités telles que l’audit, affichage des informations d’historique, configuration alertes et notifications et en permettant aux utilisateurs à s’abonner aux alertes qui indiquent des erreurs qui se produisent dans les applications d’ESB.  
  
 Cette section décrit les tâches courantes que vous pouvez accomplir à l’aide du portail de gestion ESB, notamment les suivantes :  
  
-   [Utilisation des Exceptions et les Messages d’erreur](../esb-toolkit/working-with-exceptions-and-fault-messages.md)  
  
-   [Configuration des alertes, Notifications et abonnements](../esb-toolkit/configuring-alerts-notifications-and-subscriptions.md)  
  
-   [Affichage et gestion de l’audit et historique](../esb-toolkit/viewing-and-managing-auditing-and-history.md)  
  
-   [Analyse de tendances de panne à l’aide de graphiques et rapports](../esb-toolkit/analyzing-fault-trends-using-charts-and-reports.md)  
  
-   [Affichage et la publication des inscriptions UDDI](../esb-toolkit/viewing-and-publishing-uddi-registrations.md)  
  
> [!NOTE]
>  Pour obtenir une description détaillée des fonctionnalités du portail de gestion ESB individuelles, consultez [référence de fonctionnalité de portail de gestion ESB](../esb-toolkit/esb-management-portal-feature-reference.md).  
  
## <a name="esb-portal-technologies"></a>Technologies de portail ESB  
 Le portail de gestion ESB tire parti des technologies suivantes :  
  
-   [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)] 
  
-   ASP.NET
  
-   [Enterprise Library](http://go.microsoft.com/fwlink/?LinkId=188292) ([http://go.microsoft.com/fwlink/?LinkId=188292](http://go.microsoft.com/fwlink/?LinkId=188292)). Le portail de gestion ESB utilise les assemblys de bibliothèque d’entreprise suivants :  
  
    -   **Microsoft.Practices.EnterpriseLibrary.Caching**  
  
    -   **Microsoft.Practices.EnterpriseLibrary.Common**  
  
    -   **Microsoft.Practices.EnterpriseLibrary.Data**  
  
    -   **Microsoft.Practices.EnterpriseLibrary.ExceptionHandling**  
  
    -   **Microsoft.Practices.EnterpriseLibrary.ExceptionHandling.Logging**  
  
    -   **Microsoft.Practices.EnterpriseLibrary.Logging**  
  
    -   **Microsoft.Practices.EnterpriseLibrary.ObjectBuilder2**  
  
    -   **Microsoft.Practices.EnterpriseLibrary.Validation**  
  
    -   Microsoft.Practices.Unity  
  
-   [Contrôle de graphique Microsoft](http://go.microsoft.com/fwlink/?LinkId=188293) (http://go.microsoft.com/fwlink/?LinkId=188293) pour Microsoft .NET Framework 4  
  
Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] suivi métrique étend uniquement pour le suivi des pannes pour le système de gestion d’exception.