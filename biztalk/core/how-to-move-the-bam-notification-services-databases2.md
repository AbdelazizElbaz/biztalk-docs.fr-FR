---
title: "Le déplacement de Notification BAM Services Databases2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Notification Services Application database [BAM]
- Notification Services Instance database [BAM]
- migrating, Notification Services database [BAM]
ms.assetid: 4b7f3397-65c9-4c71-8374-8764f4c2e2e3
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 639a326878cd425a951581711c08a0a53127035b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-bam-notification-services-databases"></a><span data-ttu-id="ae934-102">Déplacement des bases de données des services de notification BAM</span><span class="sxs-lookup"><span data-stu-id="ae934-102">How to Move the BAM Notification Services Databases</span></span>
<span data-ttu-id="ae934-103">Cette procédure vous permet de déplacer les bases de données des services de notification BAM vers un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="ae934-103">You can use this procedure to move the BAM Notification Services databases to another server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae934-104">Vous devez déplacer la base de données d'application (BAMAlertsApplication) et la base de données d'instance (BAMAlertsNSMain) des services de notification BAM ensemble.</span><span class="sxs-lookup"><span data-stu-id="ae934-104">You must move the BAM Notification Services Application (BAMAlertsApplication) database and BAM Notification Services Instance (BAMAlertsNSMain) database together.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ae934-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ae934-105">Prerequisites</span></span>  
 <span data-ttu-id="ae934-106">Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ae934-106">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-move-the-bam-notification-services-databases"></a><span data-ttu-id="ae934-107">Pour déplacer les bases de données des services de notification BAM</span><span class="sxs-lookup"><span data-stu-id="ae934-107">To move the BAM Notification Services databases</span></span>  
  
1.  <span data-ttu-id="ae934-108">Obtenez une copie du fichier .xml utilisé pour restaurer BAM :</span><span class="sxs-lookup"><span data-stu-id="ae934-108">Get a copy of the .xml file used for restoring BAM:</span></span>  
  
    1.  <span data-ttu-id="ae934-109">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ae934-109">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="ae934-110">À l'invite de commandes, accédez au répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="ae934-110">At the command prompt, navigate to the following directory:</span></span>  
  
         <span data-ttu-id="ae934-111">**%SystemDrive%\Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\Tracking** </span><span class="sxs-lookup"><span data-stu-id="ae934-111">**%SystemDrive%\Program Files\Microsoft**  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\Tracking**</span></span>  
  
    3.  <span data-ttu-id="ae934-112">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="ae934-112">At the command prompt, type:</span></span>  
  
        ```  
        Bm.exe get-config –filename:BAMConfiguration.xml  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="ae934-113">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="ae934-113">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
2.  <span data-ttu-id="ae934-114">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="ae934-114">At the command prompt, type:</span></span>  
  
    ```  
    Net stop NS$BamAlerts  
    ```  
  
3.  <span data-ttu-id="ae934-115">Suivez les instructions de la documentation en ligne de SQL Server pour sauvegarder la base de données sur l'ancien serveur.</span><span class="sxs-lookup"><span data-stu-id="ae934-115">Follow the instructions in SQL Server Books Online on how to back up the database on the old server.</span></span>  
  
4.  <span data-ttu-id="ae934-116">Copiez les bases de données des services de notification BAM sur le nouveau serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ae934-116">Copy the BAM Notification Services databases to the new SQL server.</span></span>  
  
5.  <span data-ttu-id="ae934-117">Suivez les instructions de la documentation en ligne de SQL Server pour restaurer la base de données sur le nouveau serveur.</span><span class="sxs-lookup"><span data-stu-id="ae934-117">Follow the instructions in SQL Server Books Online on how to restore the database on the new server.</span></span>  
  
6.  <span data-ttu-id="ae934-118">Modifiez le fichier BAMConfiguration.xml et définissez le nom du serveur dans la section Alert DeploymentUnit sur le nom du nouveau serveur.</span><span class="sxs-lookup"><span data-stu-id="ae934-118">Edit the BAMConfiguration.xml file and change the ServerName in the Alert DeploymentUnit section to the new server name.</span></span>  
  
7.  <span data-ttu-id="ae934-119">Enregistrez le fichier BAMConfiguration.xml, puis fermez-le.</span><span class="sxs-lookup"><span data-stu-id="ae934-119">Save and close the BAMConfiguration.xml file.</span></span>  
  
8.  <span data-ttu-id="ae934-120">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ae934-120">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="ae934-121">À l'invite de commandes, accédez au répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="ae934-121">At the command prompt, navigate to the following directory:</span></span>  
  
     <span data-ttu-id="ae934-122">**%SystemDrive%\Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\Tracking** </span><span class="sxs-lookup"><span data-stu-id="ae934-122">**%SystemDrive%\Program Files\Microsoft**  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\Tracking**</span></span>  
  
10. <span data-ttu-id="ae934-123">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="ae934-123">At the command prompt, type:</span></span>  
  
    ```  
    bm.exe update-config -FileName:BAMConfiguration.xml  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="ae934-124">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="ae934-124">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
11. <span data-ttu-id="ae934-125">Mettez à jour les références aux bases de données des services de notification BAM.</span><span class="sxs-lookup"><span data-stu-id="ae934-125">Update references to the BAM Notification Services databases.</span></span> <span data-ttu-id="ae934-126">Pour plus d’informations, consultez [comment la mise à jour des références aux bases de données Services de Notification BAM](../core/how-to-update-references-to-the-bam-notification-services-databases.md).</span><span class="sxs-lookup"><span data-stu-id="ae934-126">For more information, see [How to Update References to the BAM Notification Services Databases](../core/how-to-update-references-to-the-bam-notification-services-databases.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae934-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae934-127">See Also</span></span>  
 [<span data-ttu-id="ae934-128">Déplacement de bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="ae934-128">Moving BizTalk Server Databases</span></span>](../core/moving-biztalk-server-databases.md)