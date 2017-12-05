---
title: "Comment faire pour désactiver le suivi Global | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eae3059a-cbdd-47c4-84cd-edfb5480b9fa
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c143d19e6071ca4f9ce488ae936082db86dc84dc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-turn-off-global-tracking"></a><span data-ttu-id="c0306-102">Désactivation du suivi global</span><span class="sxs-lookup"><span data-stu-id="c0306-102">How to Turn Off Global Tracking</span></span>
<span data-ttu-id="c0306-103">Par défaut, le suivi global est activé lorsque vous installez BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c0306-103">By default, global tracking is enabled when you install BizTalk Server.</span></span> <span data-ttu-id="c0306-104">La taille de la base de données des suivis BizTalk (BizTalkDTADb) croît à mesure que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite des données sur votre système.</span><span class="sxs-lookup"><span data-stu-id="c0306-104">The BizTalk Tracking (BizTalkDTADb) database grows in size as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes data on your system.</span></span> <span data-ttu-id="c0306-105">Si la taille de cette base de données affecte les performances du disque, vous pouvez en purger les données.</span><span class="sxs-lookup"><span data-stu-id="c0306-105">If the size of the BizTalk Tracking database causes poor disk performance, you can purge the data from the Tracking database.</span></span> <span data-ttu-id="c0306-106">Si vous rencontrez des problèmes de performances qui sont momentanément résolus par une purge de la base de données de suivi BizTalk, et que vous souhaitez configurer BizTalk de sorte que les informations de suivi ne soient plus collectées, vous pouvez envisager de désactiver le suivi global.</span><span class="sxs-lookup"><span data-stu-id="c0306-106">If you are having performance issues that are momentarily addressed by purging the BizTalk tracking database, and you want to configure BizTalk to no longer collect tracking information, you may want to consider turning off global tracking.</span></span>  
  
 <span data-ttu-id="c0306-107">Il est important de comprendre que le fait de désactiver le suivi global entraîne également la désactivation des intercepteurs de suivi de l'ensemble du groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0306-107">It is important to understand that turning off global tracking disables the tracking interceptors for the entire [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.</span></span> <span data-ttu-id="c0306-108">Cela signifie que BizTalk ne suivra pas les événements dans les tables de suivi.</span><span class="sxs-lookup"><span data-stu-id="c0306-108">This means that BizTalk will not track events in its tracking tables.</span></span> <span data-ttu-id="c0306-109">Vous pouvez aussi désactiver le suivi des événements de manière individuelle.</span><span class="sxs-lookup"><span data-stu-id="c0306-109">Alternatively, you can turn off tracking for individual events.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0306-110">Si vous utilisez l'analyse BAM, vous devez conserver un hôte de suivi dédié, même si vous désactivez le suivi global,</span><span class="sxs-lookup"><span data-stu-id="c0306-110">If you are using Business Activity Monitoring (BAM), you should maintain a dedicated tracking host, even if you disable global tracking.</span></span> <span data-ttu-id="c0306-111">car les événements BAM utilisent le service TDDS (Tracking Data Decode Service).</span><span class="sxs-lookup"><span data-stu-id="c0306-111">This is because BAM events use the Tracking Data Decode Service (TDDS).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c0306-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="c0306-112">Prerequisites</span></span>  
 <span data-ttu-id="c0306-113">Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c0306-113">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-turn-off-global-tracking-sql-server-2008"></a><span data-ttu-id="c0306-114">Pour désactiver le suivi global (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="c0306-114">To turn off global tracking (SQL Server 2008)</span></span>  
  
1.  <span data-ttu-id="c0306-115">Sur le serveur SQL qui héberge la base de données des suivis BizTalk (BizTalkDTADb), cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur  **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="c0306-115">On the SQL server that hosts the BizTalk Tracking (BizTalkDTADb) database, click **Start**, click **Programs**, click **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="c0306-116">Dans le **se connecter au serveur** boîte de dialogue, vérifiez le nom du serveur et l’authentification, puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="c0306-116">In the **Connect to Server** dialog box, verify the server name and authentication, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="c0306-117">Dans Microsoft SQL Server Management Studio, dans **l’Explorateur d’objets**, développez \< *nom de l’ordinateur*\>, développez **bases de données**, développez  **BizTalkMgmtDb**, développez **Tables**, avec le bouton droit **adm_Group**, puis cliquez sur **ouvrir la Table**.</span><span class="sxs-lookup"><span data-stu-id="c0306-117">In Microsoft SQL Server Management Studio, in **Object Explorer**, expand \<*computer name*\>, expand **Databases**, expand **BizTalkMgmtDb**, expand **Tables**, right-click **adm_Group**, and then click **Open Table**.</span></span>  
  
4.  <span data-ttu-id="c0306-118">Dans la visionneuse de table, faites défiler horizontalement jusqu'à ce que vous trouviez **GlobalTrackingOption**.</span><span class="sxs-lookup"><span data-stu-id="c0306-118">In the table viewer, scroll horizontally until you find **GlobalTrackingOption**.</span></span>  
  
5.  <span data-ttu-id="c0306-119">Dans le **GlobalTrackingOption** colonne, modifiez la valeur 1 en 0 pour désactiver cette fonctionnalité et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="c0306-119">In the **GlobalTrackingOption** column, change the value from 1 to 0, to turn off this feature, and then press ENTER.</span></span>  
  
6.  <span data-ttu-id="c0306-120">Fermez Microsoft SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="c0306-120">Close Microsoft SQL Server Management Studio.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c0306-121">Vous devez redémarrer vos hôtes BizTalk pour que ce changement prenne effet.</span><span class="sxs-lookup"><span data-stu-id="c0306-121">You must restart your BizTalk hosts for the change to take effect.</span></span>  
  
7.  <span data-ttu-id="c0306-122">Cliquez sur **Démarrer**, cliquez sur **programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="c0306-122">Click **Start**, click **Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
8.  <span data-ttu-id="c0306-123">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur  **Instances de l’hôte**.</span><span class="sxs-lookup"><span data-stu-id="c0306-123">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Host Instances**.</span></span>  
  
9. <span data-ttu-id="c0306-124">Dans le volet de détails, cliquez sur chaque ordinateur hôte, puis cliquez sur **redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="c0306-124">In the details pane, right-click each host, and then click **Restart**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0306-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0306-125">See Also</span></span>  
 <span data-ttu-id="c0306-126">[Archivage et la purge de la base de données de suivi de BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="c0306-126">[Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md) </span></span>  
 <span data-ttu-id="c0306-127">[Purge des données de la base de données de suivi de BizTalk](../core/how-to-purge-data-from-the-biztalk-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="c0306-127">[How to Purge Data from the BizTalk Tracking Database](../core/how-to-purge-data-from-the-biztalk-tracking-database.md) </span></span>  
 [<span data-ttu-id="c0306-128">Purge manuelle des données à partir de la base de données de suivi BizTalk</span><span class="sxs-lookup"><span data-stu-id="c0306-128">How to Manually Purge Data from the BizTalk Tracking Database</span></span>](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)