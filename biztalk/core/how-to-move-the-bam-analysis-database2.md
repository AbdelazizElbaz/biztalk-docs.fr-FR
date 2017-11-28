---
title: "Comment déplacer la Database2 d’analyse BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migrating, Analysis database [BAM]
- Analysis database [BAM], migrating
ms.assetid: b0320273-4840-4573-bb82-bba95021535e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f9ae627dffd36ceca78e7da0b9e8e516845691a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-bam-analysis-database"></a><span data-ttu-id="70caa-102">Déplacement de la base de données d'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="70caa-102">How to Move the BAM Analysis Database</span></span>
<span data-ttu-id="70caa-103">Cette procédure vous permet de déplacer la base de données d'analyse BAM vers un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="70caa-103">You can use this procedure to move the BAM Analysis database to another server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="70caa-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="70caa-104">Prerequisites</span></span>  
 <span data-ttu-id="70caa-105">Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.</span><span class="sxs-lookup"><span data-stu-id="70caa-105">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-move-the-bam-analysis-database"></a><span data-ttu-id="70caa-106">Pour déplacer la base de données d'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="70caa-106">To move the BAM Analysis database</span></span>  
  
1.  <span data-ttu-id="70caa-107">Obtenez une copie du fichier .xml utilisé pour restaurer BAM :</span><span class="sxs-lookup"><span data-stu-id="70caa-107">Get a copy of the .xml file used for restoring BAM:</span></span>  
  
    1.  <span data-ttu-id="70caa-108">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="70caa-108">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="70caa-109">À l'invite de commandes, accédez au répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="70caa-109">At the command prompt, navigate to the following directory:</span></span>  
  
         [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="70caa-110">Tracking</span><span class="sxs-lookup"><span data-stu-id="70caa-110">Tracking</span></span>  
  
    3.  <span data-ttu-id="70caa-111">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="70caa-111">At the command prompt, type:</span></span>  
  
        ```  
        Bm.exe get-config –filename:BAMConfiguration.xml  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="70caa-112">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="70caa-112">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
2.  <span data-ttu-id="70caa-113">Suivez les instructions de la documentation en ligne de SQL Server pour sauvegarder la base de données sur l'ancien serveur.</span><span class="sxs-lookup"><span data-stu-id="70caa-113">Follow the instructions in SQL Server Books Online on how to back up the database on the old server.</span></span>  
  
3.  <span data-ttu-id="70caa-114">Copiez la base de données d'analyse BAM sur le nouveau serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="70caa-114">Copy the BAM Analysis database to the new SQL Server.</span></span>  
  
4.  <span data-ttu-id="70caa-115">Suivez les instructions de la documentation en ligne de SQL Server pour restaurer la base de données sur le nouveau serveur.</span><span class="sxs-lookup"><span data-stu-id="70caa-115">Follow the instructions in SQL Server Books Online on how to restore the database on the new server.</span></span>  
  
5.  <span data-ttu-id="70caa-116">Modifiez le fichier BAMConfiguration.xml et définissez le nom du serveur dans la section AnalysisDatabase DeploymentUnit sur le nom du nouveau serveur.</span><span class="sxs-lookup"><span data-stu-id="70caa-116">Edit the BAMConfiguration.xml file and change the ServerName in the AnalysisDatabase DeploymentUnit section to the new server name.</span></span>  
  
6.  <span data-ttu-id="70caa-117">Enregistrez le fichier BAMConfiguration.xml, puis fermez-le.</span><span class="sxs-lookup"><span data-stu-id="70caa-117">Save and close the BAMConfiguration.xml file.</span></span>  
  
7.  <span data-ttu-id="70caa-118">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="70caa-118">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="70caa-119">À l'invite de commandes, accédez au répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="70caa-119">At the command prompt, navigate to the following directory:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="70caa-120">Tracking</span><span class="sxs-lookup"><span data-stu-id="70caa-120">Tracking</span></span>  
  
9. <span data-ttu-id="70caa-121">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="70caa-121">At the command prompt, type:</span></span>  
  
    ```  
    bm.exe update-config -FileName:BAMConfiguration.xml  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="70caa-122">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="70caa-122">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70caa-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70caa-123">See Also</span></span>  
 [<span data-ttu-id="70caa-124">Déplacement de bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="70caa-124">Moving BizTalk Server Databases</span></span>](../core/moving-biztalk-server-databases.md)