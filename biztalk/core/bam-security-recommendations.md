---
title: "Recommandations de sécurité BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, BAM
- managing [BAM], security
- BAM, security
ms.assetid: 73613123-c1ed-477a-9f5c-342b2573c975
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f26cd3051dd296cc2849cb9c8ba7f8aa1d7ac6a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-security-recommendations"></a><span data-ttu-id="930f5-102">Recommandations de sécurité pour les services BAM</span><span class="sxs-lookup"><span data-stu-id="930f5-102">BAM Security Recommendations</span></span>
<span data-ttu-id="930f5-103">Il est recommandé de respecter les informations suivantes pour la sécurisation et le déploiement de l'analyse BAM dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="930f5-103">We recommend that you follow these guidelines for securing and deploying BAM in your environment:</span></span>  
  
-   <span data-ttu-id="930f5-104">Si vous utilisez [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)], l'ordinateur d'administration doit disposer des logiciels suivants pour déployer l'analyse BAM :</span><span class="sxs-lookup"><span data-stu-id="930f5-104">If you are using [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)], the administration computer must have the following software installed to deploy BAM:</span></span>  
  
    -   [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]  
  
    -   <span data-ttu-id="930f5-105">outils clients [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)] ;</span><span class="sxs-lookup"><span data-stu-id="930f5-105">[!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)] client tools</span></span>  
  
    -   [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]<span data-ttu-id="930f5-106">Integration Services</span><span class="sxs-lookup"><span data-stu-id="930f5-106"> Integration Services</span></span>  
  
    -   [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]<span data-ttu-id="930f5-107"> Analysis Services ;</span><span class="sxs-lookup"><span data-stu-id="930f5-107"> Analysis Services</span></span>  
  
    -   [!INCLUDE[SQLServer2005_SP3_long](../includes/sqlserver2005-sp3-long-md.md)]<span data-ttu-id="930f5-108">, si vous allez utiliser les alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="930f5-108">, if you will be using BAM alerts</span></span>  
  
        > [!NOTE]
        >  [!INCLUDE[SQLServer2005_SP3_short](../includes/sqlserver2005-sp3-short-md.md)]<span data-ttu-id="930f5-109"> inclut [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Services pour [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="930f5-109"> contains [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Services for [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="930f5-110">Le contexte utilisateur d'exécution du lot DTS d'analyse doit être un membre du rôle [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] db_owner associé aux bases de données d'importation principale BAM et de schémas en étoile BAM.</span><span class="sxs-lookup"><span data-stu-id="930f5-110">The user context under which the analysis DTS package runs must be a member of the db_owner [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] role of the BAM Primary Import and BAM Star Schema databases.</span></span> <span data-ttu-id="930f5-111">De plus, le compte de service sous lequel Analysis Services est exécuté doit être un administrateur OLAP et avoir un rôle db_owner associé à la base de données de schémas en étoile BAM.</span><span class="sxs-lookup"><span data-stu-id="930f5-111">In addition, the service account under which Analysis Services runs must be an OLAP administrator and must be a db_owner of the BAM Star Schema database.</span></span> <span data-ttu-id="930f5-112">Pour plus d’informations, consultez le site Web de support technique et de Microsoft Help à [http://go.microsoft.com/fwlink/?LinkId=22781](http://go.microsoft.com/fwlink/?LinkId=22781).</span><span class="sxs-lookup"><span data-stu-id="930f5-112">For more information, see the Microsoft Help and Support Web site at [http://go.microsoft.com/fwlink/?LinkId=22781](http://go.microsoft.com/fwlink/?LinkId=22781).</span></span>  
  
-   <span data-ttu-id="930f5-113">Plusieurs utilisateurs ont besoin d’accéder aux données actives et archivées : commerciaux, les gestionnaires des activités et autres.</span><span class="sxs-lookup"><span data-stu-id="930f5-113">Multiple users need access to the live and archived data: salespeople, business managers, and others.</span></span> <span data-ttu-id="930f5-114">Ces utilisateurs doivent disposer de comptes dans le domaine des bases de données d'importation principale BAM et d'analyse BAM (domaine d'entreprise) mais leurs comptes n'ont pas besoin d'avoir accès aux ressources BizTalk.</span><span class="sxs-lookup"><span data-stu-id="930f5-114">These users must have domain accounts in the domain where the BAM Primary Import and BAM Analysis databases are (corporate domain), but their accounts do not need to have access to BizTalk resources.</span></span>  
  
-   <span data-ttu-id="930f5-115">Pour les utilisateurs à accéder à des affichages de données BAM, vous devez utiliser l’utilitaire de gestion BAM (BM.exe) pour accorder les autorisations requises pour les vues et les utilisateurs doivent disposer de connexions SQL.</span><span class="sxs-lookup"><span data-stu-id="930f5-115">For users to access views of the BAM data, you must use the BAM management utility (BM.exe) to grant the users permissions to the views, and the users must have SQL logins.</span></span> <span data-ttu-id="930f5-116">Pour plus d’informations sur l’utilitaire de gestion BAM, consultez [utilitaire de gestion BAM](../core/bam-management-utility.md).</span><span class="sxs-lookup"><span data-stu-id="930f5-116">For more information about the BAM management utility, see [BAM Management Utility](../core/bam-management-utility.md).</span></span>  
  
-   <span data-ttu-id="930f5-117">Pour ajouter des utilisateurs aux rôles qui ont accès aux cubes dans la base de données analyse BAM, vous devez disposer d’un ordinateur d’administration dans le même domaine que les bases de données BAM.</span><span class="sxs-lookup"><span data-stu-id="930f5-117">To add users to roles that have access to the cubes in the BAM Analysis database, you must have an administration computer in the same domain as the BAM databases.</span></span>  
  
-   <span data-ttu-id="930f5-118">La personne qui administre BAM doit avoir un rôle db_owner associé aux bases de données d'importation principale BAM, de schémas en étoile et d'archives BAM.</span><span class="sxs-lookup"><span data-stu-id="930f5-118">The person administering BAM must be db_owner for the BAM Primary Import, Star Schema, and BAM Archive databases.</span></span> <span data-ttu-id="930f5-119">Cette personne doit également être un administrateur OLAP de la base de données analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="930f5-119">That person must also be an OLAP administrator for the BAM Analysis database.</span></span>  
  
-   <span data-ttu-id="930f5-120">Si vous déployez des classeurs Microsoft Office Excel (fichiers .xls), l'application Excel doit être installée sur l'ordinateur d'administration.</span><span class="sxs-lookup"><span data-stu-id="930f5-120">If you are deploying Microsoft Office Excel workbooks (.xls files), Excel must be installed on the administration computer.</span></span> <span data-ttu-id="930f5-121">Avant de déployer un classeur, ouvrez-le et assurez-vous que le niveau de sécurité des macros est élevé et qu'aucun avertissement ne s'affiche.</span><span class="sxs-lookup"><span data-stu-id="930f5-121">Before you deploy a workbook, open it and ensure that the macro security is set to high, and that there are no warnings.</span></span>  
  
-   <span data-ttu-id="930f5-122">S'il n'est pas nécessaire de distribuer aux utilisateurs des classeurs Excel BAM associés à des données réelles, il est recommandé de déployer les classeurs à l'aide de fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="930f5-122">If there is no business need to distribute to the users BAM Excel workbooks that connect to the real data, we recommend that you deploy the workbooks by using XML files.</span></span> <span data-ttu-id="930f5-123">Il n'est ainsi pas nécessaire d'installer Excel sur l'ordinateur d'administration, ni de vérifier le niveau de sécurité des macros.</span><span class="sxs-lookup"><span data-stu-id="930f5-123">This eliminates the need to install Excel on the administration computer, and the need to verify the macro security level.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="930f5-124">Lorsque vous supprimez les autorisations d’un utilisateur sur une vue, vous devez également mettre à supprimer tous les abonnements aux alertes que l’utilisateur a défini.</span><span class="sxs-lookup"><span data-stu-id="930f5-124">When you remove a user's permissions on a view, you must also remember to eliminate any subscriptions to alerts that the user has set.</span></span> <span data-ttu-id="930f5-125">Pour plus d’informations sur la suppression d’abonnés d’une alerte, consultez [comment supprimer les abonnés d’une alerte](../core/how-to-remove-subscribers-from-an-alert.md).</span><span class="sxs-lookup"><span data-stu-id="930f5-125">For more information about removing subscribers from an alert, see [How to Remove Subscribers from an Alert](../core/how-to-remove-subscribers-from-an-alert.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="930f5-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="930f5-126">See Also</span></span>  
 <span data-ttu-id="930f5-127">[Autorisations de sécurité minimales](../core/minimum-security-user-rights.md) </span><span class="sxs-lookup"><span data-stu-id="930f5-127">[Minimum Security User Rights](../core/minimum-security-user-rights.md) </span></span>  
 [<span data-ttu-id="930f5-128">Recommandations de sécurité pour un déploiement BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="930f5-128">Security Recommendations for a BizTalk Server Deployment</span></span>](../core/security-recommendations-for-a-biztalk-server-deployment.md)