---
title: "Listes de vérification opérationnelle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c308a876-9872-43b3-a1fb-76e81396612f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87da295129a4cb90ecf643cd06eb18ac3e6aa18e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operational-readiness-checklists"></a>Listes de vérification de disponibilité opérationnelle
Les listes de vérification opérationnelle contient des recommandations dont vous devez tenir compte et les tâches que vous devez effectuer avant de déployer une solution BizTalk en production. Ces listes de vérification incluent des informations sur la configuration des logiciels requis, accroître la disponibilité, analyse le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement et les procédures de test.  
  
 Étant donné que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] conserve les dépendances sur afin de nombreuses autres technologies Microsoft, vous devez effectuer les tâches pour chaque technologie pour vous assurer que votre production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement s’exécute correctement.  
  
## <a name="typical-prerequisite-software"></a>Logiciels requis par défaut  
 Logiciels requis pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] plate-forme d’application inclut généralement les produits suivants :  
  
-   Le système d’exploitation Windows  
  
-   [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]SP1 ou[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)](pour les besoins du développement, pas au moment de l’exécution)  
  
## <a name="additional-components"></a>Composants supplémentaires  
 Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] plate-forme d’application peut également exiger de plusieurs composants logiciels suivants :  
  
-   Internet Information Services (IIS)  
  
-   Windows SharePoint® Services 2010  
  
-   SharePoint Foundation 2010  
  
-   Microsoft Office SharePoint Server 2007 Service Pack 1 (SP1) (MOSS)  
  
-   Windows SharePoint Services 3.0 avec SP1 ou SP2  
  
-   Microsoft Office Excel 2010 ou 2007  
  
    > [!NOTE]  
    >  [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]prend en charge uniquement la version 32 bits de Microsoft Office 2010.  
  
-   SQL Server 2005 Notification Services  
  
-   SQLXML 4.0 avec Service Pack 1  
  
-   .NET framework 1.0  
  
-   .NET Framework 2.0  
  
-   .NET framework 3.0  
  
-   Microsoft .NET Framework 4 et .net Framework 3.5 Service Pack 1 (SP1)  
  
-   Composants non Microsoft pour activer la fonctionnalité pour certaines [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cartes.  
  
 Pour plus d’informations sur les logiciels de dépendance est requis pour les fonctionnalités spécifiques de la plate-forme d’application BizTalk pour les différentes versions de système d’exploitation Windows, consultez la section « Matrice des dépendances des fonctionnalités » dans le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] installation et mise à niveau du guide pour la version de système d’exploitation Windows spécifique. Le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] guides d’installation et de mise à niveau sont disponibles à [http://go.microsoft.com/fwlink/?LinkID=152913](http://go.microsoft.com/fwlink/?LinkID=152913).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Liste de vérification : Mise en route avec BizTalk Server](http://msdn.microsoft.com/library/37d265cd-c393-46ac-ac21-129a1511359b)  
  
-   [Liste de vérification : Configuration de Windows Server](../technical-guides/checklist-configuring-windows-server.md)  
  
-   [Liste de vérification : Configuration d’Internet Information Services](../technical-guides/checklist-configuring-internet-information-services.md)  
  
-   [Liste de vérification : Configuration de SQL Server](~/technical-guides/checklist-configuring-sql-server.md)  
  
-   [Liste de vérification : Configuration de BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)  
  
-   [Liste de vérification : Offrant une haute disponibilité avec une tolérance de panne ou l’équilibrage de charge](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)  
  
-   [Liste de vérification : Accroître la disponibilité avec la récupération d’urgence](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)  
  
-   [Liste de vérification : Analyse opérationnelle](../technical-guides/checklist-monitoring-operational-readiness.md)  
  
-   [Liste de vérification : Gestion et résolution des problèmes de bases de données BizTalk Server](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)  
  
-   [Liste de vérification : Test opérationnelle](../technical-guides/checklist-testing-operational-readiness.md)