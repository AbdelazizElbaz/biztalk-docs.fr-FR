---
title: "Comment déplacer la Database2 archives BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Archive database [BAM], migrating
- migrating, Archive database [BAM]
ms.assetid: 88b96dc2-8c9c-43f5-afb9-a937e05de36b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4398e155168a903d39f3fbd1c9fd8f1421862cc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-bam-archive-database"></a><span data-ttu-id="f629a-102">Déplacement de la base de données des archives BAM</span><span class="sxs-lookup"><span data-stu-id="f629a-102">How to Move the BAM Archive Database</span></span>
<span data-ttu-id="f629a-103">Cette procédure vous permet de déplacer la base de données des archives BAM vers un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="f629a-103">You can use this procedure to move the BAM Archive database to another server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f629a-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f629a-104">Prerequisites</span></span>  
 <span data-ttu-id="f629a-105">Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f629a-105">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-move-the-bam-archive-database"></a><span data-ttu-id="f629a-106">Pour déplacer la base de données des archives BAM</span><span class="sxs-lookup"><span data-stu-id="f629a-106">To move the BAM Archive database</span></span>  
  
1.  <span data-ttu-id="f629a-107">Obtenez une copie du fichier .xml utilisé pour restaurer BAM :</span><span class="sxs-lookup"><span data-stu-id="f629a-107">Get a copy of the .xml file used for restoring BAM:</span></span>  
  
    1.  <span data-ttu-id="f629a-108">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f629a-108">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="f629a-109">À l'invite de commandes, accédez au répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="f629a-109">At the command prompt, navigate to the following directory:</span></span>  
  
         [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="f629a-110">Tracking</span><span class="sxs-lookup"><span data-stu-id="f629a-110">Tracking</span></span>  
  
    3.  <span data-ttu-id="f629a-111">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="f629a-111">At the command prompt, type:</span></span>  
  
        ```  
        Bm.exe get-config –filename:BAMConfiguration.xml  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="f629a-112">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="f629a-112">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
2.  <span data-ttu-id="f629a-113">Suivez les instructions dans la documentation en ligne de SQL Server pour sauvegarder la base de données sur l'ancien serveur</span><span class="sxs-lookup"><span data-stu-id="f629a-113">Follow the instructions in SQL Server Books Online to back up the database on the old server.</span></span>  
  
3.  <span data-ttu-id="f629a-114">Copiez la base de données des archives BAM sur le nouveau serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f629a-114">Copy the BAM Archive database to the new SQL server.</span></span>  
  
4.  <span data-ttu-id="f629a-115">Suivez les instructions dans la documentation en ligne de SQL Server pour restaurer la base de données sur le nouveau serveur</span><span class="sxs-lookup"><span data-stu-id="f629a-115">Follow the instructions in SQL Server Books Online to restore the database on the new server.</span></span>  
  
5.  <span data-ttu-id="f629a-116">Modifiez le fichier BAMConfiguration.xml et définissez le nom du serveur dans la section ArchivingDatabase DeploymentUnit sur le nom du nouveau serveur.</span><span class="sxs-lookup"><span data-stu-id="f629a-116">Edit the BAMConfiguration.xml file and change the ServerName in the ArchivingDatabase DeploymentUnit section to the new server name.</span></span>  
  
6.  <span data-ttu-id="f629a-117">Enregistrez le fichier BAMConfiguration.xml, puis fermez-le.</span><span class="sxs-lookup"><span data-stu-id="f629a-117">Save and close the BAMConfiguration.xml file.</span></span>  
  
7.  <span data-ttu-id="f629a-118">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f629a-118">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="f629a-119">À l'invite de commandes, accédez au répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="f629a-119">At the command prompt, navigate to the following directory:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="f629a-120">Tracking</span><span class="sxs-lookup"><span data-stu-id="f629a-120">Tracking</span></span>  
  
9. <span data-ttu-id="f629a-121">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="f629a-121">At the command prompt, type:</span></span>  
  
    ```  
    bm.exe update-config -FileName:BAMConfiguration.xml  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f629a-122">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="f629a-122">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f629a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f629a-123">See Also</span></span>  
 [<span data-ttu-id="f629a-124">Déplacement de bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="f629a-124">Moving BizTalk Server Databases</span></span>](../core/moving-biztalk-server-databases.md)