---
title: "Comment déterminer et définir des rôles d’écriture d’événements pour les activités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73bfe8ff-167a-4bf0-ab87-3926290d52d8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc9fa663d395fc36205e137da374f17cb9470521
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-determine-and-set-event-writer-roles-for-activities"></a><span data-ttu-id="e33b6-102">Choix et définition des rôles d'écriture d'événement pour les activités</span><span class="sxs-lookup"><span data-stu-id="e33b6-102">How to Determine and Set Event Writer Roles for Activities</span></span>
<span data-ttu-id="e33b6-103">L'analyse BAM propose deux modes de sécurité pour l'écriture d'événements sur les activités.</span><span class="sxs-lookup"><span data-stu-id="e33b6-103">BAM provides two modes of security when writing events on activities.</span></span> <span data-ttu-id="e33b6-104">Vous pouvez accorder des autorisations d'écriture d'événements sur des activités particulières ou sur toutes les activités déployées.</span><span class="sxs-lookup"><span data-stu-id="e33b6-104">You can grant permissions to write events on individual activities or you can grant permissions to write events on all deployed activities.</span></span>  
  
 <span data-ttu-id="e33b6-105">La sécurité au niveau de l'activité est assurée par les rôles d'écriture d'événement pour les activités créés lorsque vous déployez une définition BAM.</span><span class="sxs-lookup"><span data-stu-id="e33b6-105">Activity-level security is provided by activity event writer roles that are created when you deploy a BAM definition.</span></span> <span data-ttu-id="e33b6-106">Par exemple, si vous déployez une définition pour une activité intitulée CreditCard, BAM crée un rôle d'écriture d'événement nommé bam_CreditCard_EventWriter.</span><span class="sxs-lookup"><span data-stu-id="e33b6-106">For example, if you deploy a definition for an activity named CreditCard, BAM creates an event writer role named bam_CreditCard_EventWriter.</span></span> <span data-ttu-id="e33b6-107">Ce rôle dispose des autorisations nécessaires pour écrire les événements liés à cette activité.</span><span class="sxs-lookup"><span data-stu-id="e33b6-107">This role has permissions to write events for the activity.</span></span> <span data-ttu-id="e33b6-108">Pour accorder à un utilisateur les autorisations d'écritures des événements pour cette activité, vous ajoutez l'utilisateur à ce rôle.</span><span class="sxs-lookup"><span data-stu-id="e33b6-108">To grant a user permissions to write events for the activity, you add the user to the role.</span></span>  
  
 <span data-ttu-id="e33b6-109">Vous pouvez également accorder aux utilisateurs des droits d’écrire eve2nts toutes les activités en les ajoutant au super rôle BAM_EVENT_WRITER, qui est autorisé à écrire à toutes les activités.</span><span class="sxs-lookup"><span data-stu-id="e33b6-109">Alternatively, you can grant users rights to write eve2nts to all activities by adding them to the super role BAM_EVENT_WRITER, which has permissions to write to all activities.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e33b6-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e33b6-110">Prerequisites</span></span>  
 <span data-ttu-id="e33b6-111">Pour pouvoir effectuer cette procédure, vous devez disposer des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e33b6-111">To perform this procedure, you must have the following:</span></span>  
  
-   <span data-ttu-id="e33b6-112">une connexion à la base BAMPrimaryImportDb sur laquelle l'activité est déployée ;</span><span class="sxs-lookup"><span data-stu-id="e33b6-112">A connection to BAMPrimaryImportDb on which the activity is deployed.</span></span>  
  
-   <span data-ttu-id="e33b6-113">des autorisations DBO sur la base de données.</span><span class="sxs-lookup"><span data-stu-id="e33b6-113">DBO permissions on the database.</span></span>  
  
### <a name="to-add-a-user-to-an-event-writer-role"></a><span data-ttu-id="e33b6-114">Pour ajouter un utilisateur à un rôle d'écriture d'événements</span><span class="sxs-lookup"><span data-stu-id="e33b6-114">To add a user to an event writer role</span></span>  
  
1.  <span data-ttu-id="e33b6-115">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="e33b6-115">Click **Start**, point to **All Programs**, click **Microsoft SQL Server 2008**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="e33b6-116">Dans le **se connecter à SQL Server** boîte de dialogue, sélectionnez le serveur SQL Server et la méthode d’authentification appropriée, puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="e33b6-116">In the **Connect to SQL Server** dialog box, select the SQL Server and the appropriate authentication method, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="e33b6-117">Dans le **l’Explorateur d’objets** volet développez **bases de données**, puis sélectionnez la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="e33b6-117">In the **Object Explorer** pane expand **Databases**, and then select the BAM Primary Import database.</span></span>  
  
4.  <span data-ttu-id="e33b6-118">Cliquez sur le **nouvelle requête** icône dans la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="e33b6-118">Click the **New Query** icon on the toolbar.</span></span>  
  
5.  <span data-ttu-id="e33b6-119">Dans la fenêtre de requête, copiez et collez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e33b6-119">Copy the following commands and paste them into the Query Window.</span></span> <span data-ttu-id="e33b6-120">Remplacez les chaînes domain name, user name et activity name par les valeurs appropriées.</span><span class="sxs-lookup"><span data-stu-id="e33b6-120">Replace the domain name, user name, and activity name placeholders with the appropriate values.</span></span>  
  
    ```  
    EXEC sp_grantlogin '<domain name>\<user name>’  
    EXEC sp_grantdbaccess '<domain name>\<user name>', 'ActivityLogin'  
    EXEC sp_addrolemember 'bam_<activity name>_EventWriter', 'SpecialLogin'  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e33b6-121">Les noms de rôle respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="e33b6-121">Role names are case-sensitive.</span></span> <span data-ttu-id="e33b6-122">Les noms d'activité également, ce qui implique qu'ils doivent respecter la casse utilisée lors du déploiement de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e33b6-122">Activity names are also case-sensitive, that is, they must match the case used when deploying the activity.</span></span>  
  
6.  <span data-ttu-id="e33b6-123">Cliquez sur le **Execute** icône sur la barre d’outils ou appuyez sur F5 pour exécuter les commandes.</span><span class="sxs-lookup"><span data-stu-id="e33b6-123">Click the **Execute** icon on the toolbar or press F5 to run the commands.</span></span>  
  
### <a name="to-add-a-user-to-an-event-writer-super-role"></a><span data-ttu-id="e33b6-124">Pour ajouter un utilisateur à un super rôle d'écriture d'événements</span><span class="sxs-lookup"><span data-stu-id="e33b6-124">To add a user to an event writer super role</span></span>  
  
1.  <span data-ttu-id="e33b6-125">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="e33b6-125">Click **Start**, point to **All Programs**, click **Microsoft SQL Server 2008**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="e33b6-126">Dans le **se connecter à SQL Server** boîte de dialogue, sélectionnez le serveur SQL Server et la méthode d’authentification appropriée, puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="e33b6-126">In the **Connect to SQL Server** dialog box, select the SQL Server and the appropriate authentication method, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="e33b6-127">Dans le **l’Explorateur d’objets** volet développez **bases de données**, puis sélectionnez la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="e33b6-127">In the **Object Explorer** pane expand **Databases**, and then select the BAM Primary Import database.</span></span>  
  
4.  <span data-ttu-id="e33b6-128">Cliquez sur le **nouvelle requête** icône dans la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="e33b6-128">Click the **New Query** icon on the toolbar.</span></span>  
  
5.  <span data-ttu-id="e33b6-129">Dans la fenêtre de requête, copiez et collez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e33b6-129">Copy the following commands and paste them into the Query Window.</span></span> <span data-ttu-id="e33b6-130">Remplacez les chaînes domain name et user name par les valeurs appropriées.</span><span class="sxs-lookup"><span data-stu-id="e33b6-130">Replace the domain name and user name with the appropriate values.</span></span>  
  
    ```  
    EXEC sp_grantlogin '<domain name>\<user name>’  
    EXEC sp_grantdbaccess '<domain name>\<user name>', 'ActivityLogin'  
    EXEC sp_addrolemember 'BAM_EVENT_WRITER', 'SpecialLogin'  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e33b6-131">Les noms de rôle respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="e33b6-131">Role names are case sensitive.</span></span> <span data-ttu-id="e33b6-132">Vous devez spécifier le rôle d'écriture d'événements tel qu'il a été défini.</span><span class="sxs-lookup"><span data-stu-id="e33b6-132">You must specify the event writer role as specified.</span></span>  
  
6.  <span data-ttu-id="e33b6-133">Cliquez sur le **Execute** icône sur la barre d’outils ou appuyez sur F5 pour exécuter les commandes.</span><span class="sxs-lookup"><span data-stu-id="e33b6-133">Click the **Execute** icon on the toolbar or press F5 to run the commands.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e33b6-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e33b6-134">See Also</span></span>  
 [<span data-ttu-id="e33b6-135">Gestion de la sécurité de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="e33b6-135">Managing BAM Security</span></span>](../core/managing-bam-security.md)