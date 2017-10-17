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
ms.openlocfilehash: f9e9297e5539fd95f316ebbf6239a5d017ec4ecf
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2017
---
# <a name="operational-readiness-checklists"></a>Listes de vérification de disponibilité opérationnelle
Les listes de vérification opérationnelle contient des recommandations dont vous devez tenir compte et les tâches que vous devez effectuer avant de déployer une solution BizTalk en production. Ces listes de vérification incluent des informations sur la configuration des logiciels requis, accroître la disponibilité, analyse le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement et les procédures de test.  
  
 Étant donné que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] conserve les dépendances sur afin de nombreuses autres technologies Microsoft, vous devez effectuer les tâches pour chaque technologie pour vous assurer que votre production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement s’exécute correctement.  
  
## <a name="typical-prerequisite-software"></a>Logiciels requis par défaut  
 Logiciels requis pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] plate-forme d’application inclut généralement les produits suivants :  
  
-   Le système d’exploitation Windows  
  
-   SQL Server 
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   Visual Studio (fins de développement, pas au moment de l’exécution)  
  
## <a name="additional-components"></a>Composants supplémentaires  
 Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] plate-forme d’application peut également exiger de plusieurs composants logiciels suivants :  
  
-   Internet Information Services (IIS)  
  
-   SharePoint
  
-   Microsoft Office Excel 
  
    > [!NOTE]  
    >  BizTalk Server prend en charge uniquement la version 32 bits de Microsoft Office.  
  
-   SQL Server
  
-   SQLXML 
  
-   .NET Framework 
  
-   Composants non Microsoft pour activer la fonctionnalité pour certaines [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cartes.  
  
 Pour plus d’informations sur les logiciels de dépendance est requis pour les fonctionnalités spécifiques de la plate-forme d’application BizTalk pour les différentes versions de système d’exploitation Windows, consultez [nouveautés, Installation, Configuration et la mise à niveau](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).
- 
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Liste de contrôle : Bien démarrer avec BizTalk Server](http://msdn.microsoft.com/library/37d265cd-c393-46ac-ac21-129a1511359b)  
  
-   [Liste de contrôle : Configuration de Windows Server](../technical-guides/checklist-configuring-windows-server.md)  
  
-   [Liste de contrôle : Configuration d’Internet Information Services](../technical-guides/checklist-configuring-internet-information-services.md)  
  
-   [Liste de contrôle : Configuration de SQL Server](~/technical-guides/checklist-configuring-sql-server.md)  
  
-   [Liste de contrôle : Configuration de BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)  
  
-   [Liste de contrôle : Mise en place de la haute disponibilité avec la tolérance de panne ou l’équilibrage de charge](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)  
  
-   [Liste de contrôle : Accroissement de la disponibilité avec la récupération d’urgence](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)  
  
-   [Liste de contrôle : Surveillance de la disponibilité opérationnelle](../technical-guides/checklist-monitoring-operational-readiness.md)  
  
-   [Liste de contrôle : Maintenance et résolution des problèmes des bases de données BizTalk Server](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)  
  
-   [Liste de contrôle : Test de la disponibilité opérationnelle](../technical-guides/checklist-testing-operational-readiness.md)