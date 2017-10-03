---
title: "Purge manuelle des données à partir de la base de données MessageBox dans un environnement de Test | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 398991a9-344a-487a-a817-dfc97d48ebe6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4a6d5f8b232e31a140ee4786b87d2bb270505f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manually-purge-data-from-the-messagebox-database-in-a-test-environment"></a><span data-ttu-id="1c2df-102">Purge manuelle des données de la base de données MessageBox dans un environnement de test</span><span class="sxs-lookup"><span data-stu-id="1c2df-102">How to Manually Purge Data from the MessageBox Database in a Test Environment</span></span>
<span data-ttu-id="1c2df-103">Lors de l'exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement de développement ou de test, les données stockées dans la base de données MessageBox ne sont généralement pas des données actives critiques et peuvent donc être supprimées.</span><span class="sxs-lookup"><span data-stu-id="1c2df-103">When running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a development or test environment, data that is stored in the MessageBox database is not usually business critical "live" data and therefore may be deleted.</span></span> <span data-ttu-id="1c2df-104">Dans ces scénarios, vous pouvez avoir besoin d'une méthode rapide pour purger les données de la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="1c2df-104">In these scenarios, you may need a "quick and dirty" method for purging data from the MessageBox database.</span></span> <span data-ttu-id="1c2df-105">Suivez les procédures de cette rubrique pour purger manuellement les données de la base de données MessageBox à l'aide de la procédure stockée bts_CleanupMsgbox.</span><span class="sxs-lookup"><span data-stu-id="1c2df-105">Follow the procedures in this topic to manually purge data from the MessageBox database using the bts_CleanupMsgbox stored procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c2df-106">Vous devez uniquement effectuer ces opérations dans un environnement de test.</span><span class="sxs-lookup"><span data-stu-id="1c2df-106">You should only perform these steps in a test environment.</span></span> <span data-ttu-id="1c2df-107">La purge manuelle de la base de données MessageBox de BizTalk dans un environnement de production n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="1c2df-107">Manually purging the BizTalk MessageBox database in a production environment is not supported.</span></span>  
  
### <a name="to-stop-biztalk-services"></a><span data-ttu-id="1c2df-108">Pour arrêter les services BizTalk</span><span class="sxs-lookup"><span data-stu-id="1c2df-108">To stop BizTalk services</span></span>  
  
1.  <span data-ttu-id="1c2df-109">Arrêtez les instances du service BizTalk à partir de la console Services.</span><span class="sxs-lookup"><span data-stu-id="1c2df-109">Stop any instances of the BizTalk service from the Services console.</span></span>  
  
2.  <span data-ttu-id="1c2df-110">Si vous exécutez des adaptateurs dans des hôtes isolés (par exemple, HTTP, SOAP ou WCF), redémarrez IIS en exécutant IISRESET dans une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="1c2df-110">If you are running any adapters in isolated hosts (for example HTTP, SOAP, or WCF), restart IIS by running the IISRESET from a command prompt.</span></span>  
  
3.  <span data-ttu-id="1c2df-111">Arrêtez les adaptateurs isolés personnalisés en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="1c2df-111">Shut down any custom Isolated Adapters that are running.</span></span>  
  
### <a name="to-create-and-execute-the-btscleanupmsgbox-stored-procedure-using-sql-server-2008"></a><span data-ttu-id="1c2df-112">Pour créer et exécuter la procédure stockée bts_CleanupMsgbox à l'aide de SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="1c2df-112">To create and execute the bts_CleanupMsgbox stored procedure using SQL Server 2008</span></span>  
  
1.  <span data-ttu-id="1c2df-113">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="1c2df-113">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="1c2df-114">Dans le **se connecter à SQL Server** boîte de dialogue, sélectionnez le serveur SQL server et la méthode d’authentification appropriée, puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="1c2df-114">In the **Connect to SQL Server** dialog box, select the SQL server and the appropriate authentication method, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="1c2df-115">Dans le **bases de données disponibles** liste déroulante, sélectionnez la base de données BizTalk Messagebox (**BizTalkMsgBoxDB** par défaut).</span><span class="sxs-lookup"><span data-stu-id="1c2df-115">In the **Available databases** drop-down list, select the BizTalk Messagebox database (**BizTalkMsgBoxDB** by default).</span></span>  
  
4.  <span data-ttu-id="1c2df-116">Cliquez sur le **nouvelle requête** icône dans la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="1c2df-116">Click the **New Query** icon on the toolbar.</span></span>  
  
5.  <span data-ttu-id="1c2df-117">Ouvrez le **msgbox_cleanup_logic.sql** fichier à partir de SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="1c2df-117">Open the **msgbox_cleanup_logic.sql** file from SQL Server Management Studio.</span></span> <span data-ttu-id="1c2df-118">Le fichier msgbox_cleanup_logic.sql est situé dans le répertoire [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\ de l'ordinateur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1c2df-118">The msgbox_cleanup_logic.sql file is located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\ directory of the BizTalk Server computer.</span></span>  
  
6.  <span data-ttu-id="1c2df-119">Cliquez sur le **exécuter la requête** icône dans la barre d’outils pour exécuter le script pour créer le bts_CleanupMsgbox de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="1c2df-119">Click the **Execute Query** icon on the toolbar to run the script to create the bts_CleanupMsgbox stored procedure.</span></span> <span data-ttu-id="1c2df-120">La procédure stockée bts_CleanupMsgbox peut ensuite être affichée dans la liste des procédures stockées en tant que dbo.bts_CleanupMsgbox.</span><span class="sxs-lookup"><span data-stu-id="1c2df-120">The bts_CleanupMsgbox stored procedure can then be viewed in the list of stored procedures as dbo.bts_CleanupMsgbox.</span></span>  
  
7.  <span data-ttu-id="1c2df-121">Cliquez sur le **nouvelle requête** icône dans la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="1c2df-121">Click the **New Query** icon on the toolbar.</span></span>  
  
8.  <span data-ttu-id="1c2df-122">Collez la commande suivante dans la fenêtre de la nouvelle requête :</span><span class="sxs-lookup"><span data-stu-id="1c2df-122">Paste the following command into the new query window:</span></span>  
  
    ```  
    exec bts_CleanupMsgbox  
    ```  
  
9. <span data-ttu-id="1c2df-123">Cliquez sur le **exécuter la requête** icône dans la barre d’outils pour exécuter le bts_CleanupMsgbox de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="1c2df-123">Click the **Execute Query** icon on the toolbar to run the bts_CleanupMsgbox stored procedure.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1c2df-124">N'exécutez pas la procédure stockée bts_CleanupMsgbox sur un serveur de production exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c2df-124">Do not run the bts_CleanupMsgbox stored procedure on a production server that is running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="1c2df-125">Vous devez uniquement exécuter la procédure stockée bts_CleanupMsgbox dans un environnement de test.</span><span class="sxs-lookup"><span data-stu-id="1c2df-125">You should only run the bts_CleanupMsgbox stored procedure in a test environment.</span></span> <span data-ttu-id="1c2df-126">L'exécution de la procédure stockée bts_CleanupMsgbox dans un environnement de production n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="1c2df-126">Running the bts_CleanupMsgbox stored procedure in a production environment is not supported.</span></span>  
  
10. <span data-ttu-id="1c2df-127">Redémarrez les services BizTalk si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="1c2df-127">Restart BizTalk services as needed.</span></span>  
  
## <a name="considerations-when-running-the-btscleanupmsgbox-stored-procedure"></a><span data-ttu-id="1c2df-128">Considérations relatives à l'exécution de la procédure stockée bts_CleanupMsgbox</span><span class="sxs-lookup"><span data-stu-id="1c2df-128">Considerations when running the bts_CleanupMsgbox stored procedure</span></span>  
 <span data-ttu-id="1c2df-129">Les considérations suivantes s'appliquent lors de l'exécution de la procédure stockée bts_CleanupMsgbox :</span><span class="sxs-lookup"><span data-stu-id="1c2df-129">The following considerations apply when running the bts_CleanupMsgbox stored procedure:</span></span>  
  
1.  <span data-ttu-id="1c2df-130">Si vous installez un correctif sur votre système de test qui met à jour les schémas de la base de données BizTalk, celui-ci peut remplacer la procédure stockée bts_CleanupMsgbox par une version vide de cette procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="1c2df-130">If you install a hot fix onto your test system that updates the BizTalk database schemas, the hot fix may overwrite the bts_CleanupMsgbox stored procedure with an empty version of this stored procedure.</span></span> <span data-ttu-id="1c2df-131">Dans ce cas, vous devez suivre les procédures présentées dans cette rubrique pour la recréer.</span><span class="sxs-lookup"><span data-stu-id="1c2df-131">In this case, you will need to follow the procedures outlined in this topic to recreate the bts_CleanupMsgbox stored procedure.</span></span>  
  
2.  <span data-ttu-id="1c2df-132">Si vous créez une base de données MessageBox, la procédure stockée bts_CleanupMsgbox est vide. Vous devez suivre les procédures présentées dans cette rubrique pour la recréer.</span><span class="sxs-lookup"><span data-stu-id="1c2df-132">If you create a new MessageBox database, the bts_CleanupMsgbox stored procedure will be empty and you will need to follow the procedures outlined in this topic to recreate the bts_CleanupMsgbox stored procedure.</span></span>  
  
3.  <span data-ttu-id="1c2df-133">Utilisation de la procédure stockée bts_CleanupMsgbox est **ne pas pris en charge** sur un système de production.</span><span class="sxs-lookup"><span data-stu-id="1c2df-133">Use of the bts_CleanupMsgbox stored procedure is **not supported** on a production system.</span></span> <span data-ttu-id="1c2df-134">Cette procédure stockée supprime toutes les données de votre base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="1c2df-134">This stored procedure will delete all of the data in your MessageBox database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c2df-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c2df-135">See Also</span></span>  
 [<span data-ttu-id="1c2df-136">Purge des données de la base de données de suivi de BizTalk</span><span class="sxs-lookup"><span data-stu-id="1c2df-136">How to Purge Data from the BizTalk Tracking Database</span></span>](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)