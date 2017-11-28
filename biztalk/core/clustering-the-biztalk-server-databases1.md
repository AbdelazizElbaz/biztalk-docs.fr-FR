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
# <a name="clustering-the-biztalk-server-databases"></a><span data-ttu-id="7a209-102">Mise en cluster des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7a209-102">Clustering the BizTalk Server Databases</span></span>
<span data-ttu-id="7a209-103">Cette section fournit des instructions sur le déploiement d'une solution Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hautement disponible.</span><span class="sxs-lookup"><span data-stu-id="7a209-103">This section provides guidelines for deploying a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution with high availability.</span></span> <span data-ttu-id="7a209-104">Si les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deviennent indisponibles, l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne fonctionne pas correctement.</span><span class="sxs-lookup"><span data-stu-id="7a209-104">If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases become unavailable, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment will not function correctly.</span></span> <span data-ttu-id="7a209-105">Pour fournir une haute disponibilité, vous pouvez créer un cluster Microsoft SQL Server pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des bases de données, comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="7a209-105">To provide high availability, you can create a Microsoft SQL Server cluster for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="7a209-106">![Niveau de base de données BizTalk Server](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")</span><span class="sxs-lookup"><span data-stu-id="7a209-106">![BizTalk Server Database Tier](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")</span></span>  
  
 <span data-ttu-id="7a209-107">Pour fournir une haute disponibilité pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, vous devez disposer au moins deux ordinateurs qui exécutent SQL Server et une baie de disques partagée pour une utilisation par un Cluster de basculement Windows Server.</span><span class="sxs-lookup"><span data-stu-id="7a209-107">To provide high availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, you must have at least two computers that are running SQL Server and a shared disk array for use by a  Windows Server Failover Cluster.</span></span>  
  
## <a name="procedures-for-clustering-the-databases"></a><span data-ttu-id="7a209-108">Procédures de mise en cluster des bases de données</span><span class="sxs-lookup"><span data-stu-id="7a209-108">Procedures for Clustering the Databases</span></span>  
  
#### <a name="before-you-start"></a><span data-ttu-id="7a209-109">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="7a209-109">Before you start</span></span>  
  
1.  <span data-ttu-id="7a209-110">Lorsque vous créez les groupes de domaine pour l'environnement BizTalk Server, vous devez également créer des groupes globaux de domaine Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7a209-110">When you create the domain groups for your BizTalk Server environment, you must create Active Directory domain global groups.</span></span>  
  
2.  <span data-ttu-id="7a209-111">Vous devez configurer le cluster SQL Server avant d'installer et de configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a209-111">Configure the SQL Server cluster before you install and configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="7a209-112">Pour plus d’informations sur les clusters SQL Server, consultez [toujours sur Failover Cluster Instances](https://technet.microsoft.com/library/ms189134.aspx).</span><span class="sxs-lookup"><span data-stu-id="7a209-112">For more information about clustering SQL Server, see [Always On Failover Cluster Instances](https://technet.microsoft.com/library/ms189134.aspx).</span></span>  
  
3.  <span data-ttu-id="7a209-113">Si vous envisagez de mettre également en cluster le serveur de secret principal, configurez-le en premier.</span><span class="sxs-lookup"><span data-stu-id="7a209-113">If you are also clustering the master secret server, configure that server first.</span></span> <span data-ttu-id="7a209-114">Pour plus d’informations sur la haute disponibilité pour Enterprise Single Sign-On, consultez [haute disponibilité pour Enterprise Single Sign-On](../core/high-availability-for-enterprise-single-sign-on.md).</span><span class="sxs-lookup"><span data-stu-id="7a209-114">For more information about high availability for Enterprise Single Sign-On, see [High Availability for Enterprise Single Sign-On](../core/high-availability-for-enterprise-single-sign-on.md).</span></span>  
  
#### <a name="to-run-the-biztalk-server-configuration-wizard"></a><span data-ttu-id="7a209-115">Pour exécuter l'Assistant Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7a209-115">To run the BizTalk Server Configuration Wizard</span></span>  
  
1.  <span data-ttu-id="7a209-116">Installez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un serveur d'exécution.</span><span class="sxs-lookup"><span data-stu-id="7a209-116">Install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a runtime server.</span></span>  
  
2.  <span data-ttu-id="7a209-117">Lancez le programme de configuration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7a209-117">Launch the BizTalk Configuration Program.</span></span> <span data-ttu-id="7a209-118">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Configuration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="7a209-118">Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.</span></span>  
  
3.  <span data-ttu-id="7a209-119">Suivez les étapes de [importer et exporter une Configuration de BizTalk Server](../install-and-config-guides/import-and-export-biztalk-server-configuration.md) pour appliquer une configuration personnalisée.</span><span class="sxs-lookup"><span data-stu-id="7a209-119">Follow the steps in [Import and Export BizTalk Server Configuration](../install-and-config-guides/import-and-export-biztalk-server-configuration.md) to apply a custom configuration.</span></span> <span data-ttu-id="7a209-120">Pour spécifier le cluster SQL Server pour les bases de données BizTalk, entrez le nom du cluster SQL Server dans le **bases de données** boîte de dialogue du programme de configuration, comme décrit dans la **bases de données Édition** section de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="7a209-120">To specify the SQL Server cluster for the BizTalk databases, enter the name of the SQL Server cluster in the **Databases** dialog of the configuration program as described in the **Editing Databases** section of this topic.</span></span>  
  
4.  <span data-ttu-id="7a209-121">Terminez la configuration de BizTalk Server en suivant les instructions de [configurer BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="7a209-121">Complete the BizTalk Server configuration by following the instructions in [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a209-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a209-122">See Also</span></span>  
 [<span data-ttu-id="7a209-123">Création d’un environnement hautement disponible BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7a209-123">Creating a Highly Available BizTalk Server Environment</span></span>](../core/creating-a-highly-available-biztalk-server-environment.md)