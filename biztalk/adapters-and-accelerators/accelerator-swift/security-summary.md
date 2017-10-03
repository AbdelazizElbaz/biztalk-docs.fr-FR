---
title: "Résumé de la sécurité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security
ms.assetid: 357ebf63-a35e-4ce4-a754-be880946f9fc
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5d327de93941278b9b1dcecc9378183c6a2f77a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-summary"></a>Résumé de la sécurité
## <a name="overview"></a>Vue d'ensemble
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fournit des composants de développement et d’exécution pour faciliter les applications BizTalk qui fournissent des fonctionnalités de messagerie et d’automatisation de SWIFT. Les applications développées à l’aide de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] sont des applications BizTalk et qui sont sécurisés par natif [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)], [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]et IIS/ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] fonctionnalités de sécurité.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]protège la confidentialité des éléments du système à l’aide des protocoles et des normes des communications Internet chiffré de fait. Participants de la communication, les processus et les informations sont sécurisées à l’aide de certificats de signature, [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] l’authentification et Enterprise Single Sign-On. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]garantit également l’autorisation d’utilisation des ressources avec des mécanismes tels que [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] rôles et [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] l’authentification et la base de données MessageBox.  
  
 En plus de natif [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] fonctionnalités de sécurité, [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] définit et applique une sémantique de sécurité pour la création, de réparation, l’approbation et envoi des messages SWIFT par les utilisateurs professionnels. Cette sécurité au niveau utilisateur est appliquée à l’aide de [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] sur la station de travail et les certificats et les données intégrité vérification de l’utilisateur par les technologies de signature numérique [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] services d’exécution sur le serveur.  
  
 Ensemble, [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fournissent la plateforme, l’infrastructure et outils de conception, le développement et l’exécution de sécurisent SWIFT systèmes d’automatisation de la messagerie et de flux de travail.  
  
## <a name="more-information"></a>Informations complémentaires  
 Pour plus d’informations sur les meilleures pratiques de sécurité, consultez les rubriques suivantes :  
  
-   Centre de ressources de sécurité TechNet :  
  
     [http://go.Microsoft.com/fwlink/p/?LinkId=27741](http://go.microsoft.com/fwlink/p/?LinkId=27741)  
  

-   Guide de sécurité de Symantec montrant comment utiliser leurs outils pour implémenter les meilleures pratiques décrites dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Guide des opérations de sécurité pour [!INCLUDE[btsWin2kSvr](../../includes/btswin2ksvr-md.md)]:  
  
     [http://go.Microsoft.com/fwlink/p/?LinkId=28274](http://go.microsoft.com/fwlink/p/?LinkId=28274)  

  
-   Plus d’informations sur la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Service de Notification de sécurité :  
  
     [http://go.Microsoft.com/fwlink/p/?LinkId=27744](http://go.microsoft.com/fwlink/p/?LinkId=27744)  
  
  
## <a name="see-also"></a>Voir aussi  
[Runtime, la réparation de messages, la réponse FIN et la messagerie](../../adapters-and-accelerators/accelerator-swift/runtime-message-repair-fin-response-and-messaging.md)