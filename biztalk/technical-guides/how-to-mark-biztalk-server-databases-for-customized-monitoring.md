---
title: "Bases de données BizTalk Server de marque pour une analyse personnalisée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfbdc73d-a108-42ee-a5d8-401d5bfe5e7d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08807b1a365b84765221e3a71cb131d8c037fcf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-mark-biztalk-server-databases-for-customized-monitoring"></a><span data-ttu-id="fa183-102">Comment marquer les bases de données BizTalk Server pour une analyse personnalisée</span><span class="sxs-lookup"><span data-stu-id="fa183-102">How to Mark BizTalk Server Databases for Customized Monitoring</span></span>
<span data-ttu-id="fa183-103">Si vous avez installé Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Pack d’administration, vous pouvez personnaliser la façon dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sont analysées.</span><span class="sxs-lookup"><span data-stu-id="fa183-103">If you have installed the Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Pack, you can customize the way [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are monitored.</span></span> <span data-ttu-id="fa183-104">Cela garantit que le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Pack d’administration analyse les éléments suivants [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données :</span><span class="sxs-lookup"><span data-stu-id="fa183-104">This ensures that the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Pack monitors the following [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases:</span></span>  
  
-   <span data-ttu-id="fa183-105">Base de données des archives BAM (BAMArchive)</span><span class="sxs-lookup"><span data-stu-id="fa183-105">BAM Archive (BAMArchive) database</span></span>  
  
-   <span data-ttu-id="fa183-106">Base de données d'importation principale BAM (BAMPrimaryImport)</span><span class="sxs-lookup"><span data-stu-id="fa183-106">BAM Primary Import (BAMPrimaryImport) database</span></span>  
  
-   <span data-ttu-id="fa183-107">Base de données de schémas en étoile BAM (BAMStarSchema)</span><span class="sxs-lookup"><span data-stu-id="fa183-107">BAM Star Schema (BAMStarSchema) database</span></span>  
  
-   <span data-ttu-id="fa183-108">Base de données des suivis (BizTalkDTADb)</span><span class="sxs-lookup"><span data-stu-id="fa183-108">BizTalk Tracking (BizTalkDTADb) database</span></span>  
  
-   <span data-ttu-id="fa183-109">Base de données de gestion BizTalk (BizTalkMgmtDb)</span><span class="sxs-lookup"><span data-stu-id="fa183-109">BizTalk Management (BizTalkMgmtDb) database</span></span>  
  
-   <span data-ttu-id="fa183-110">Base de données MessageBox BizTalk (BizTalkMsgBoxDb)</span><span class="sxs-lookup"><span data-stu-id="fa183-110">BizTalk MessageBox (BizTalkMsgBoxDb) database</span></span>  
  
-   <span data-ttu-id="fa183-111">Base de données du moteur de règles (BizTalkRuleEngineDb)</span><span class="sxs-lookup"><span data-stu-id="fa183-111">Rule Engine (BizTalkRuleEngineDb) database</span></span>  
  
-   <span data-ttu-id="fa183-112">Base de données de l'authentification unique de l'entreprise (SSODB)</span><span class="sxs-lookup"><span data-stu-id="fa183-112">Enterprise Single Sign-On (SSODB) database</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa183-113">Vous devez être connecté en tant que membre du rôle opérateur avancé Operations Manager ou [!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)] groupe d’administration.</span><span class="sxs-lookup"><span data-stu-id="fa183-113">You must be logged on as a member of the Operations Manager Advanced Operator role or [!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)] Management Group.</span></span>  
  
### <a name="to-mark-biztalk-server-databases-for-customized-monitoring"></a><span data-ttu-id="fa183-114">Pour marquer les bases de données BizTalk Server pour personnaliser l’analyse</span><span class="sxs-lookup"><span data-stu-id="fa183-114">To mark BizTalk Server databases for customized monitoring</span></span>  
  
1.  <span data-ttu-id="fa183-115">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **System Center Operations Manager 2007**, puis cliquez sur **Console opérateur**.</span><span class="sxs-lookup"><span data-stu-id="fa183-115">Click **Start**, click **All Programs**, click **System Center Operations Manager 2007**, and then click **Operations Console**.</span></span>  
  
2.  <span data-ttu-id="fa183-116">Dans la console Opérateur, cliquez sur le **création** bouton.</span><span class="sxs-lookup"><span data-stu-id="fa183-116">In the Operations console, click the **Authoring** button.</span></span>  
  
3.  <span data-ttu-id="fa183-117">Dans le **création** volet, développez **objets du Pack d’administration**, puis cliquez sur **détections**.</span><span class="sxs-lookup"><span data-stu-id="fa183-117">In the **Authoring** pane, expand **Management Pack Objects**, and then click **Object Discoveries**.</span></span>  
  
4.  <span data-ttu-id="fa183-118">Pour localiser une détection pour SQL Server, dans la barre d’outils de la console Opérateur, cliquez sur **trouver**et dans le **recherchez** zone de texte Entrez **SQL 2008** à rechercher pour SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="fa183-118">To locate a discovery for SQL Server, on the Operations console toolbar click **Find**, and in the **Look for** text box enter **SQL 2008** to search for SQL Server 2008.</span></span>  
  
5.  <span data-ttu-id="fa183-119">Sous le **Type découvert : base de données SQL 2008** catégorie, sélectionnez **découvrir de bases de données pour un moteur de base de données**.</span><span class="sxs-lookup"><span data-stu-id="fa183-119">Under the **Discovered Type: SQL 2008 DB** category, select **Discover Databases for a Database Engine**.</span></span>  
  
6.  <span data-ttu-id="fa183-120">Dans la barre d’outils de la console Opérateur, cliquez sur **substitue** , puis pointez sur **remplacer la détection d’objets**.</span><span class="sxs-lookup"><span data-stu-id="fa183-120">On the Operations console toolbar, click **Overrides** and then point to **Override the Object Discovery**.</span></span> <span data-ttu-id="fa183-121">Vous pouvez choisir de remplacer la détection des objets d’un type spécifique ou pour tous les objets au sein d’un groupe.</span><span class="sxs-lookup"><span data-stu-id="fa183-121">You can choose to override the discovery for objects of a specific type or for all objects within a group.</span></span> <span data-ttu-id="fa183-122">Après avoir choisi le groupe du type d’objet à substituer, mais le **propriétés du remplacement** boîte de dialogue s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="fa183-122">After you choose which group of object type to override, the **Override Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fa183-123">Si le **substitue** bouton n’est pas disponible, assurez-vous que vous avez sélectionné un moniteur et non un objet conteneur dans le volet analyses.</span><span class="sxs-lookup"><span data-stu-id="fa183-123">If the **Overrides** button is not available, make sure you have selected a monitor and not a container object in the Monitors pane.</span></span>  
  
7.  <span data-ttu-id="fa183-124">Activez la case à cocher dans la **remplacer** colonne suivant pour le **liste d’exclusion** paramètre, puis, dans le **remplacer par la valeur** colonne, tapez le nom de la base de données que vous souhaitez exclure à partir de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="fa183-124">Select the check box in the **Override** column next to the **Exclude List** parameter, and in the **Override Value** column, type the name of the database that you want to exclude from monitoring.</span></span> <span data-ttu-id="fa183-125">Assurez-vous que le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] que vous souhaitez surveiller les bases de données ne sont pas répertoriées dans le **remplacer par la valeur** colonne.</span><span class="sxs-lookup"><span data-stu-id="fa183-125">Make sure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases that you want to monitor are not listed in the **Override Value** column.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="fa183-126">Vous pouvez utiliser les détections d’objets modifiés pour créer un pack d’administration.</span><span class="sxs-lookup"><span data-stu-id="fa183-126">You can use the modified object discoveries to create a new management pack.</span></span> <span data-ttu-id="fa183-127">En bas du volet, le **sélectionnez Pack d’administration de destination** liste déroulante affiche la valeur par défaut **Pack d’administration par défaut**.</span><span class="sxs-lookup"><span data-stu-id="fa183-127">At the bottom of the pane, the **Select destination management pack** drop-down shows a default value of **Default Management Pack**.</span></span> <span data-ttu-id="fa183-128">Cliquez sur **nouveau** pour créer un nouveau pack d’administration dans les détections d’objet modifié.</span><span class="sxs-lookup"><span data-stu-id="fa183-128">Click **New** to create a new management pack using the modified object discoveries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa183-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa183-129">See Also</span></span>  
 [<span data-ttu-id="fa183-130">Analyse des serveurs SQL</span><span class="sxs-lookup"><span data-stu-id="fa183-130">Monitoring SQL Servers</span></span>](../technical-guides/monitoring-sql-servers.md)