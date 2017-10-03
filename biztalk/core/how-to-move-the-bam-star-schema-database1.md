---
title: "Comment déplacer la Database1 de schéma en étoile BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Star Schema database [BAM], migrating
- migrating, Star Schema database [BAM]
ms.assetid: b4a5f8fc-0dc4-4987-b96f-ecd49bd4dba3
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6661a9ae315988a5348198fa463e24ea508cf50f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-bam-star-schema-database"></a><span data-ttu-id="a9ecf-102">Déplacement de la base de données de schémas en étoile BAM</span><span class="sxs-lookup"><span data-stu-id="a9ecf-102">How to Move the BAM Star Schema Database</span></span>
<span data-ttu-id="a9ecf-103">Cette procédure vous permet de déplacer la base de données de schémas en étoile BAM vers un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-103">You can use this procedure to move the BAM Star Schema database to another server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a9ecf-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a9ecf-104">Prerequisites</span></span>  
 <span data-ttu-id="a9ecf-105">Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-105">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-move-the-bam-star-schema-database"></a><span data-ttu-id="a9ecf-106">Pour déplacer la base de données de schémas en étoile BAM</span><span class="sxs-lookup"><span data-stu-id="a9ecf-106">To move the BAM Star Schema database</span></span>  
  
1.  <span data-ttu-id="a9ecf-107">Obtenez une copie du fichier .xml utilisé pour restaurer BAM :</span><span class="sxs-lookup"><span data-stu-id="a9ecf-107">Get a copy of the .xml file used for restoring BAM:</span></span>  
  
    1.  <span data-ttu-id="a9ecf-108">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-108">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="a9ecf-109">À l'invite de commandes, accédez au répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="a9ecf-109">At the command prompt, navigate to the following directory:</span></span>  
  
         [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="a9ecf-110">Tracking</span><span class="sxs-lookup"><span data-stu-id="a9ecf-110">Tracking</span></span>  
  
    3.  <span data-ttu-id="a9ecf-111">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="a9ecf-111">At the command prompt, type:</span></span>  
  
        ```  
        Bm.exe get-config –filename:BAMConfiguration.xml  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="a9ecf-112">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-112">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
2.  <span data-ttu-id="a9ecf-113">Suivez les instructions de la documentation en ligne de SQL Server pour sauvegarder la base de données sur l'ancien serveur.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-113">Follow the instructions in SQL Server Books Online on how to back up the database on the old server.</span></span>  
  
3.  <span data-ttu-id="a9ecf-114">Copiez la base de données de schémas en étoile BAM sur le nouveau serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-114">Copy the BAM Star Schema database to the new SQL Server.</span></span>  
  
4.  <span data-ttu-id="a9ecf-115">Suivez les instructions de la documentation en ligne de SQL Server pour restaurer la base de données sur le nouveau serveur.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-115">Follow the instructions in SQL Server Books Online on how to restore the database on the new server.</span></span>  
  
5.  <span data-ttu-id="a9ecf-116">Modifiez le fichier BAMConfiguration.xml et définissez le nom du serveur dans la section StarSchemaDatabase DeploymentUnit sur le nom du nouveau serveur.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-116">Edit the BAMConfiguration.xml file and change the ServerName in the StarSchemaDatabase DeploymentUnit section to the new server name.</span></span>  
  
6.  <span data-ttu-id="a9ecf-117">Enregistrez le fichier BAMConfiguration.xml, puis fermez-le.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-117">Save and close the BAMConfiguration.xml file.</span></span>  
  
7.  <span data-ttu-id="a9ecf-118">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-118">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="a9ecf-119">À l'invite de commandes, accédez au répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="a9ecf-119">At the command prompt, navigate to the following directory:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="a9ecf-120">Tracking</span><span class="sxs-lookup"><span data-stu-id="a9ecf-120">Tracking</span></span>  
  
9. <span data-ttu-id="a9ecf-121">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="a9ecf-121">At the command prompt, type:</span></span>  
  
    ```  
    bm.exe update-config -FileName:BAMConfiguration.xml  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="a9ecf-122">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-122">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
10. <span data-ttu-id="a9ecf-123">Mettez à jour la connexion SQL 2 en modifiant le nom du serveur et celui de la base de données dans tous les lots DTS de l'analyse BAM dotés du préfixe « BAM_AN_ ». Pour cela, suivez la procédure ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="a9ecf-123">Update SQL Connection 2 to change the server and database name in all BAM analysis DTS packages, which are prefixed with "BAM_AN_", by following these steps:</span></span>  
  
    1.  <span data-ttu-id="a9ecf-124">Ouvrez le serveur hébergeant l'analyse BAM à l'aide de SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-124">Using SQL Server Management Studio, open the server hosting BAM.</span></span>  
  
    2.  <span data-ttu-id="a9ecf-125">Ouvrez le **Data Transformation Services** dossier.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-125">Open the **Data Transformation Services** folder.</span></span>  
  
    3.  <span data-ttu-id="a9ecf-126">Ouvrez le **lots locaux** dossier.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-126">Open the **Local Packages** folder.</span></span>  
  
    4.  <span data-ttu-id="a9ecf-127">Ouvrez le lot DTS, puis double-cliquez sur **connexion 2** pour ouvrir la connexion.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-127">Open the DTS package, and then double-click **Connection 2** to open the connection.</span></span>  
  
    5.  <span data-ttu-id="a9ecf-128">Dans la zone de liste déroulante, sélectionnez les nouveaux noms de serveur et de base de données.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-128">Select the new server and database name in the drop-down box.</span></span>  
  
11. <span data-ttu-id="a9ecf-129">Mettez à jour la source de données dans la base de données d'analyse BAM comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="a9ecf-129">Update the data source in the BAM Analysis database as follows:</span></span>  
  
    1.  <span data-ttu-id="a9ecf-130">À l'aide de SQL Server Analysis Manager, ouvrez le serveur hébergeant la base de données d'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-130">Using SQL Server Analysis Manager, open the server hosting the BAM Analysis database.</span></span>  
  
    2.  <span data-ttu-id="a9ecf-131">Ouvrez le **des Sources de données** dossier.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-131">Open the **Data Sources** folder.</span></span>  
  
    3.  <span data-ttu-id="a9ecf-132">Avec le bouton droit de la source de données pour le cube, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-132">Right-click the data source for the cube, and then click **Edit**.</span></span>  
  
    4.  <span data-ttu-id="a9ecf-133">Sur le **connexion** onglet, tapez le nouveau nom du serveur et le nom de base de données pour la base de données de schémas en étoile BAM, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9ecf-133">On the **Connection** tab, type the new server name and database name for the BAM Star Schema database, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ecf-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9ecf-134">See Also</span></span>  
 [<span data-ttu-id="a9ecf-135">Déplacement de bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a9ecf-135">Moving BizTalk Server Databases</span></span>](../core/moving-biztalk-server-databases.md)