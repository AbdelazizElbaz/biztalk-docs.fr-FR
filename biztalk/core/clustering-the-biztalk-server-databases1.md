---
title: Clustering du Databases1 BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clustering, how to
- clustering, SQL Servers
- SQL Server, clustering
- BizTalk Server Configuration Wizard
- high availability, databases
- clustering, BizTalk Server Configuration Wizard
- clustering, databases
- clustering, prerequisites
ms.assetid: 9a1ed843-483b-4a56-961b-bc6801a07b64
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 983023ceb88618a540d922481c4cb185a076ae3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="clustering-the-biztalk-server-databases"></a>Mise en cluster des bases de données BizTalk Server
Cette section fournit des instructions sur le déploiement d'une solution Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hautement disponible. Si les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deviennent indisponibles, l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne fonctionne pas correctement. Pour fournir une haute disponibilité, vous pouvez créer un cluster Microsoft SQL Server pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des bases de données, comme indiqué dans l’illustration suivante.  
  
 ![Niveau de base de données BizTalk Server](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")  
  
 Pour fournir une haute disponibilité pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, vous devez disposer au moins deux ordinateurs qui exécutent SQL Server et une baie de disques partagée pour une utilisation par un Cluster de basculement Windows Server.  
  
## <a name="procedures-for-clustering-the-databases"></a>Procédures de mise en cluster des bases de données  
  
#### <a name="before-you-start"></a>Avant de commencer  
  
1.  Lorsque vous créez les groupes de domaine pour l'environnement BizTalk Server, vous devez également créer des groupes globaux de domaine Active Directory.  
  
2.  Vous devez configurer le cluster SQL Server avant d'installer et de configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur les clusters SQL Server, consultez [toujours sur Failover Cluster Instances](https://technet.microsoft.com/library/ms189134.aspx).  
  
3.  Si vous envisagez de mettre également en cluster le serveur de secret principal, configurez-le en premier. Pour plus d’informations sur la haute disponibilité pour Enterprise Single Sign-On, consultez [haute disponibilité pour Enterprise Single Sign-On](../core/high-availability-for-enterprise-single-sign-on.md).  
  
#### <a name="to-run-the-biztalk-server-configuration-wizard"></a>Pour exécuter l'Assistant Configuration de BizTalk Server  
  
1.  Installez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un serveur d'exécution.  
  
2.  Lancez le programme de configuration de BizTalk. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Configuration de BizTalk Server**.  
  
3.  Suivez les étapes de [importer et exporter une Configuration de BizTalk Server](../install-and-config-guides/import-and-export-biztalk-server-configuration.md) pour appliquer une configuration personnalisée. Pour spécifier le cluster SQL Server pour les bases de données BizTalk, entrez le nom du cluster SQL Server dans le **bases de données** boîte de dialogue du programme de configuration, comme décrit dans la **bases de données Édition** section de cette rubrique.  
  
4.  Terminez la configuration de BizTalk Server en suivant les instructions de [configurer BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un environnement hautement disponible BizTalk Server](../core/creating-a-highly-available-biztalk-server-environment.md)