---
title: "Comment sélectionner une Source de données actives ou archivées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Management database, archived data
- Management database, real-time data
- HAT, real-time data
- archived data, Management database
- HAT, archived data
- real-time data, HAT
- real-time data, Management database
- archived data, HAT
ms.assetid: e2325823-22e1-4a1a-865b-15757b215b29
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7172a822a71e2b0d7dc621e6c1e11b055b723bd3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-select-a-live-or-archived-data-source"></a><span data-ttu-id="b3af2-102">Sélection d'une source de données actives ou archivées</span><span class="sxs-lookup"><span data-stu-id="b3af2-102">How to Select a Live or Archived Data Source</span></span>
<span data-ttu-id="b3af2-103">BizTalktracking permet d'accéder aux données archivées et actives.</span><span class="sxs-lookup"><span data-stu-id="b3af2-103">BizTalktracking enables you to access both archived and live data.</span></span> <span data-ttu-id="b3af2-104">Vous sélectionnez une source de données actives ou archivées à partir de la main **Administration de BizTalk Server** nœud Console d’Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b3af2-104">You select a live or archived data source from the main **BizTalk Server Administration** node BizTalk Server Administration Console.</span></span>  <span data-ttu-id="b3af2-105">La source employée par défaut est celle comprenant les données actives, extraites de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b3af2-105">The default source is live data, retrieved from the BizTalk Management database.</span></span> <span data-ttu-id="b3af2-106">Si vous choisissez de travailler sur les données archivées, vous devez sélectionner le ou les serveurs et la ou les bases de données appropriés à cet usage.</span><span class="sxs-lookup"><span data-stu-id="b3af2-106">If you choose to work with archived data, you must select the appropriate server/s and database/s with which to work.</span></span>  
  
-   <span data-ttu-id="b3af2-107">Les données archivées : l’analyse des données archivées permet à examiner les tendances dans votre entreprise et sur votre système, car vous pouvez en remontant jusqu'à nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b3af2-107">Archived data: Analyzing archived data enables you to examine trends both in your business and on your system, because you can look as far back as necessary.</span></span> <span data-ttu-id="b3af2-108">Si vous souhaitez consulter des données archivées, vous devez également sélectionner les bases de données et les serveurs SQL Server appropriés, qui contiennent lesdites données.</span><span class="sxs-lookup"><span data-stu-id="b3af2-108">If you select archived data, you must also select the appropriate SQL Servers and SQL databases that contain the archived data.</span></span>  
  
     <span data-ttu-id="b3af2-109">Données archivées sont désignées en sélectionnant **se connecter à une base de données de suivi existant...** .</span><span class="sxs-lookup"><span data-stu-id="b3af2-109">Archived data is designated by selecting **Connect to an existing tracking database…**.</span></span>  
  
-   <span data-ttu-id="b3af2-110">Données actives : analyse des données en direct permet de vous permettent de surveiller les orchestrations et pipelines, afin que vous puissiez identifier et résoudre des problèmes dans l’environnement d’intermédiaire ou de développement.</span><span class="sxs-lookup"><span data-stu-id="b3af2-110">Live data: Analyzing live data enables you to monitor orchestrations and pipelines, so that you can identify and fix problems in the development or staging environment.</span></span> <span data-ttu-id="b3af2-111">De même, elle permet de résoudre les problèmes apparaissant dans le système, par exemple de savoir pourquoi les messages sont suspendus.</span><span class="sxs-lookup"><span data-stu-id="b3af2-111">Monitoring live data also enables you to correct problems in your system, such as why messages are being suspended.</span></span>  
  
     <span data-ttu-id="b3af2-112">Données actives sont désignées en sélectionnant **se connecter à un groupe existant...** .</span><span class="sxs-lookup"><span data-stu-id="b3af2-112">Live data is designated by selecting **Connect to an existing group…**.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b3af2-113">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b3af2-113">Prerequisites</span></span>  
 <span data-ttu-id="b3af2-114">Vous devez être connecté en tant que membre du groupe opérateurs BizTalk Server pour effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="b3af2-114">You must be logged on as a member of the BizTalk Server Operators group to perform this procedure.</span></span>  
  
### <a name="to-select-live-data"></a><span data-ttu-id="b3af2-115">Pour sélectionner des données actives</span><span class="sxs-lookup"><span data-stu-id="b3af2-115">To select live data</span></span>  
  
1.  <span data-ttu-id="b3af2-116">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="b3af2-116">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b3af2-117">Cliquez sur le principal **Administration de BizTalk Server** nœud.</span><span class="sxs-lookup"><span data-stu-id="b3af2-117">Click the main  **BizTalk Server Administration** node.</span></span>  
  
3.  <span data-ttu-id="b3af2-118">Cliquez sur **se connecter à un groupe existant...**</span><span class="sxs-lookup"><span data-stu-id="b3af2-118">Click **Connect to an existing group…**</span></span>  
  
4.  <span data-ttu-id="b3af2-119">Dans le **nom SQL Server** , tapez le nom du serveur qui héberge la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b3af2-119">In the **SQL Server name** box, type the name of the server that hosts the BizTalk Management database.</span></span>  
  
5.  <span data-ttu-id="b3af2-120">Dans le **nom de la base de données** zone de liste déroulante, sélectionnez **BizTalkMgmtDb**.</span><span class="sxs-lookup"><span data-stu-id="b3af2-120">In the **Database name** drop-down list box, select **BizTalkMgmtDb**.</span></span>  
  
6.  <span data-ttu-id="b3af2-121">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b3af2-121">Click **OK**.</span></span>  
  
### <a name="to-select-archived-data"></a><span data-ttu-id="b3af2-122">Pour sélectionner des données archivées</span><span class="sxs-lookup"><span data-stu-id="b3af2-122">To select archived data</span></span>  
  
1.  <span data-ttu-id="b3af2-123">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="b3af2-123">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b3af2-124">Cliquez sur le principal **Administration de BizTalk Server** nœud.</span><span class="sxs-lookup"><span data-stu-id="b3af2-124">Click the main  **BizTalk Server Administration** node.</span></span>  
  
3.  <span data-ttu-id="b3af2-125">Cliquez sur **se connecter à une base de données de suivi existant...**</span><span class="sxs-lookup"><span data-stu-id="b3af2-125">Click **Connect to an existing tracking database…**</span></span>  
  
4.  <span data-ttu-id="b3af2-126">Dans le **nom SQL Server** , tapez le nom du serveur qui héberge la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b3af2-126">In the **SQL Server name** box, type the name of the server that hosts the BizTalk Management database.</span></span>  
  
5.  <span data-ttu-id="b3af2-127">Dans le **nom de la base de données** zone de liste déroulante, sélectionnez **BizTalkMgmtDb**.</span><span class="sxs-lookup"><span data-stu-id="b3af2-127">In the **Database name** drop-down list box, select **BizTalkMgmtDb**.</span></span>  
  
6.  <span data-ttu-id="b3af2-128">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b3af2-128">Click **OK**.</span></span>