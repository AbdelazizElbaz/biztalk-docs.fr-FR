---
title: "Bases de données de Services de mise à jour des références à la Notification BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Notification Services Application database [BAM], restoring
- Notification Services Application database [BAM], updating references
- restoring, BAM
- NS$instance_name service Notification Services Application database [BAM], NS$instance_name service
- restoring [BAM], updating references
- BAM, restoring
- restoring [BAM], Notification Services Application database
- restoring [BAM], NS$instance_name service
ms.assetid: b007fdc2-2e74-4eef-b4c3-43689e9f2180
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 394a002fedaffbb9c67fa4b0ae0229215e6d8efa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-references-to-the-bam-notification-services-databases"></a><span data-ttu-id="d5fb0-102">Mise à jour des références aux bases de données des services de notification BAM</span><span class="sxs-lookup"><span data-stu-id="d5fb0-102">How to Update References to the BAM Notification Services Databases</span></span>
<span data-ttu-id="d5fb0-103">Après avoir effectué les étapes nécessaires pour restaurer les bases de données des services de notification BAM (Business Activity Monitoring) sur le système de destination, vous devez réenregistrer les services de notification sur tous les ordinateurs du groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui exécutent des services de notification (NSservice.exe).</span><span class="sxs-lookup"><span data-stu-id="d5fb0-103">After you perform the steps necessary to restore the Business Activity Monitoring (BAM) Notification Services databases to the destination system, you must re-register the Notification Service on all computers in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group that are running Notification Services (NSservice.exe).</span></span> <span data-ttu-id="d5fb0-104">Cela permet aux services de notification de se connecter aux bases de données dans leur nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-104">This enables Notification Services to connect to the databases in their new location.</span></span>  
  
 <span data-ttu-id="d5fb0-105">L'enregistrement d'une instance des services de notification crée le service NS$instance_name, crée des compteurs de performance sur le serveur local, et ajoute des informations au Registre.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-105">Registering an instance of Notification Services creates the NS$instance_name service, creates performance counters on the local server, and adds information to the registry.</span></span> <span data-ttu-id="d5fb0-106">Vous devez enregistrer l'instance sur les serveurs suivants :</span><span class="sxs-lookup"><span data-stu-id="d5fb0-106">You must register the instance on the following servers:</span></span>  
  
-   <span data-ttu-id="d5fb0-107">Chaque serveur exécutant le service NS $ instance_name.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-107">Each server that runs the NS$instance_name service.</span></span> <span data-ttu-id="d5fb0-108">Le service exécute les composants hôte, générateur et distributeur du fournisseur d'événements.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-108">The service runs the event provider host, generator, and distributor components.</span></span> <span data-ttu-id="d5fb0-109">Pour les configurations mises à l'échelle, le service s'exécute sur plusieurs serveurs.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-109">For scaled-out configurations, the service runs on multiple servers.</span></span>  
  
-   <span data-ttu-id="d5fb0-110">Chaque serveur exécutant une application de gestion des abonnements.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-110">Each server that runs a subscription management application.</span></span> <span data-ttu-id="d5fb0-111">Si l'application de gestion des abonnements est exécutée sur un serveur dédié, ne créez pas le service NS$instance_name lors de l'enregistrement de l'instance.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-111">If the subscription management application runs on its own server, do not create the NS$instance_name service when registering the instance.</span></span>  
  
-   <span data-ttu-id="d5fb0-112">Chaque serveur exécutant un fournisseur d'événements indépendant.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-112">Each server that runs an independent event provider.</span></span> <span data-ttu-id="d5fb0-113">Si le fournisseur d'événements indépendant est exécuté sur un serveur dédié ou sur le serveur de base de données, ne créez pas le service NS$instance_name lors de l'enregistrement de l'instance.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-113">If the independent event provider runs on its own server or the database server, do not create the NS$instance_name service when registering the instance.</span></span>  
  
 <span data-ttu-id="d5fb0-114">Si le serveur de base de données n'exécute pas également l'instance des services de notification ou les composants du client, n'enregistrez pas l'instance sur ce serveur.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-114">If the database server does not also run the Notification Services instance or the client components, do not register the instance on this server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d5fb0-115">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d5fb0-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="d5fb0-116">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-116">You must be logged on as a member of the Administrators group to perform this procedure.</span></span>  
  
-   <span data-ttu-id="d5fb0-117">Le fournisseur d'alertes BAM pour les services de notification SQL doit être installé sur l'ordinateur sur lequel vous restaurez les bases de données des services de notification BAM.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-117">The Business Activity Monitoring (BAM) Alert Provider for SQL Notification Services must be installed on the computer where you are restoring the BAM Notification Services databases.</span></span>  
  
### <a name="to-update-references-to-the-bam-notification-services-databases-sql-server-2008-r2sp1"></a><span data-ttu-id="d5fb0-118">Pour mettre à jour les références aux bases de données des services de notification BAM (SQL Server 2008 R2/SP1)</span><span class="sxs-lookup"><span data-stu-id="d5fb0-118">To update references to the BAM Notification Services databases (SQL Server 2008 R2/SP1)</span></span>  
  
1.  <span data-ttu-id="d5fb0-119">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-119">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="d5fb0-120">À l'invite de commandes, accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Suivi.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-120">At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="d5fb0-121">Type : **bm.exe get-config –filename:config.xml**</span><span class="sxs-lookup"><span data-stu-id="d5fb0-121">Type: **bm.exe get-config –filename:config.xml**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d5fb0-122">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-122">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="d5fb0-123">Ouvrez le fichier xml créé à l'étape 2 pour obtenir la liste des ordinateurs sur lesquels vous devez réenregistrer les services de notification.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-123">Open the xml file created in step 2 to obtain the list of the computers on which you must re-register Notification Services.</span></span>  
  
     <span data-ttu-id="d5fb0-124">Les noms d’ordinateur sont répertoriés dans le  **\<nom de la propriété\= >**  paramètres dans le  **\<DeploymentUnit nom = « Alerte » >** section du code xml fichier :</span><span class="sxs-lookup"><span data-stu-id="d5fb0-124">The computer names are listed in the **\<Property Name\=>** parameters in the **\<DeploymentUnit Name="Alert">** section of the xml file:</span></span>  
  
    ```  
    -<DeploymentUnit Name="Alert">  
    <Property Name="GeneratorServerName" />  
    <Property Name="ProviderServerName" />  
    <Property Name="DistributorServerName" />  
      </DeploymentUnit>  
    ```  
  
5.  <span data-ttu-id="d5fb0-125">Sur chaque ordinateur répertorié dans le fichier xml, arrêtez le service NS, puis annulez l'enregistrement d'une instance de Notification Services :</span><span class="sxs-lookup"><span data-stu-id="d5fb0-125">On each computer listed in the xml file, stop the NS service and then unregister an instance of Notification Services:</span></span>  
  
    1.  <span data-ttu-id="d5fb0-126">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, cliquez sur **outils de Configuration**, puis cliquez sur **Invite de commandes des Services de notification**.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-126">Click **Start**, click **Programs**, click **Microsoft SQL Server 2008 R2**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.</span></span>  
  
    2.  <span data-ttu-id="d5fb0-127">À l’invite de commandes, tapez : **net stop NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="d5fb0-127">At the command prompt, type: **net stop NS$BamAlerts**</span></span>  
  
    3.  <span data-ttu-id="d5fb0-128">Pour annuler l'inscription de l'instance, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="d5fb0-128">Type the following command to unregister the instance:</span></span>  
  
         <span data-ttu-id="d5fb0-129">**NSControl unregister - name BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="d5fb0-129">**nscontrol unregister  -name BamAlerts**</span></span>  
  
         <span data-ttu-id="d5fb0-130">L'annulation de l'enregistrement d'une instance supprime les entrées de Registre, le service NS$instance_name (s'il est présent) et les compteurs de performance pour le service.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-130">Unregistering an instance removes the registry entries, removes the NS$instance_name service (if present), and deletes the performance counters for the service.</span></span>  
  
6.  <span data-ttu-id="d5fb0-131">Réenregistrez le service de notification :</span><span class="sxs-lookup"><span data-stu-id="d5fb0-131">Re-register the Notification Service:</span></span>  
  
    1.  <span data-ttu-id="d5fb0-132">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, cliquez sur **outils de Configuration**, puis cliquez sur **Invite de commandes des Services de notification**.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-132">Click **Start**, click **Programs**, click **Microsoft SQL Server 2008 R2**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.</span></span>  
  
    2.  <span data-ttu-id="d5fb0-133">À l’invite de commandes, tapez : **nscontrol register - name BamAlerts-server**  *\<nom_serveur >***-service - serviceusername «**  *\<ServiceUserName >***« - servicepassword »***\<ServicePassword >***»**</span><span class="sxs-lookup"><span data-stu-id="d5fb0-133">At the command prompt, type: **nscontrol register -name BamAlerts -server** *\<ServerName>***-service -serviceusername "***\<ServiceUserName>***" -servicepassword "***\<ServicePassword>***"**</span></span>  
  
         <span data-ttu-id="d5fb0-134">Cette commande permet à Notification Services de se connecter à la base de données appropriée (ces informations sont conservées par nscontrol dans le registre de l'ordinateur du service).</span><span class="sxs-lookup"><span data-stu-id="d5fb0-134">This enables Notification Services to log on to the correct database (this information is maintained in the registry of the service machine by nscontrol).</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="d5fb0-135">N’oubliez pas d’utiliser le nouveau serveur de bases de données des Services de Notification dans le **-server** option lors de la réinscription du service.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-135">Remember to use the new Notification Services databases server in the **-server** option when re-registering the service.</span></span> <span data-ttu-id="d5fb0-136">Par ailleurs, vous devez conserver le même nom d'utilisateur pour le nouveau service Notification Services.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-136">In addition, you should use the same user name for the new Notification Services service as the old one.</span></span>  
  
7.  <span data-ttu-id="d5fb0-137">Sur l’ordinateur qui héberge le portail BAM, cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, cliquez sur **outils de Configuration**, puis cliquez sur **invite de commandes de Notification Services**.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-137">On the computer that hosts the BAM portal, click **Start**, click **Programs**, click **Microsoft SQL Server 2008 R2**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.</span></span>  
  
8.  <span data-ttu-id="d5fb0-138">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="d5fb0-138">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="d5fb0-139">**net stop NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="d5fb0-139">**net stop NS$BamAlerts**</span></span>  
  
9. <span data-ttu-id="d5fb0-140">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="d5fb0-140">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="d5fb0-141">**NSControl unregister - name BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="d5fb0-141">**nscontrol unregister  -name BamAlerts**</span></span>  
  
10. <span data-ttu-id="d5fb0-142">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="d5fb0-142">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="d5fb0-143">**NSControl register - nom***\<BamAlerts >***-server**  *\<NotificationServicesDatabaseServer >* </span><span class="sxs-lookup"><span data-stu-id="d5fb0-143">**nscontrol register  -name**  *\<BamAlerts>*  **-server** *\<NotificationServicesDatabaseServer>*</span></span>  
  
11. <span data-ttu-id="d5fb0-144">À l’invite de commandes, tapez : **net start NS$ BamAlerts**.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-144">At the command prompt, type: **net start NS$BamAlerts**.</span></span>  
  
12. <span data-ttu-id="d5fb0-145">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-145">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="d5fb0-146">À l'invite de commandes, accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Suivi.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-146">At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
14. <span data-ttu-id="d5fb0-147">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="d5fb0-147">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="d5fb0-148">**BM.exe update-config –FileName:config.xml**</span><span class="sxs-lookup"><span data-stu-id="d5fb0-148">**bm.exe update-config –FileName:config.xml**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d5fb0-149">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="d5fb0-149">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5fb0-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5fb0-150">See Also</span></span>  
 [<span data-ttu-id="d5fb0-151">Sauvegarde et restauration BAM</span><span class="sxs-lookup"><span data-stu-id="d5fb0-151">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)