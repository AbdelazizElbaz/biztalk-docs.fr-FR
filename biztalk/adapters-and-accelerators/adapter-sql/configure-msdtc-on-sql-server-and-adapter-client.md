---
title: Configurer MSDTC sur le client de SQL Server et de carte | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c87f455-a8c4-4169-bf18-695926136df1
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf519044dc28d417d85682189dd4a52585310ac0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-msdtc-on-sql-server-and-adapter-client"></a><span data-ttu-id="1a286-102">Configurer MSDTC sur un client SQL Server et de la carte</span><span class="sxs-lookup"><span data-stu-id="1a286-102">Configure MSDTC on SQL Server and adapter client</span></span>
<span data-ttu-id="1a286-103">Les opérations effectuées sur l’utilisation de SQL Server le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] (via [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le modèle de service WCF ou le modèle de canal WCF) peut être effectuée dans une étendue de transaction.</span><span class="sxs-lookup"><span data-stu-id="1a286-103">The operations performed on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] (through [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the WCF service model, or the WCF channel model) can be performed within a transaction scope.</span></span> <span data-ttu-id="1a286-104">Si le programme client possède plusieurs ressources de transaction dans le cadre de la même transaction, la transaction obtient élevés au rang d’une transaction MSDTC.</span><span class="sxs-lookup"><span data-stu-id="1a286-104">If the client program has more than one transactional resource as part of the same transaction, the transaction gets elevated to an MSDTC transaction.</span></span> <span data-ttu-id="1a286-105">Pour activer la carte effectuer des opérations dans l’étendue d’une transaction MSDTC, vous devez configurer MSDTC à la fois sur l’ordinateur exécutant le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] et SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1a286-105">To enable the adapter to perform operations within the scope of an MSDTC transaction, you must configure MSDTC both on the computer running the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] and SQL Server.</span></span> <span data-ttu-id="1a286-106">En outre, vous devez ajouter MSDTC à la liste des exceptions du pare-feu Windows.</span><span class="sxs-lookup"><span data-stu-id="1a286-106">Also, you must add MSDTC to the exceptions list of Windows Firewall.</span></span> <span data-ttu-id="1a286-107">Cette section fournit des informations sur comment effectuer ces tâches sur les ordinateurs exécutant le client de l’adaptateur et le SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1a286-107">This section provides information about how to perform these tasks on computers running the adapter client and SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a286-108">Exécution d’opérations sur l’utilisation de SQL Server [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] toujours implique deux ressources, l’adaptateur de la connexion à SQL Server et de la boîte de Message BizTalk résidant sur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1a286-108">Performing operations on SQL Server using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] always involves two resources—the adapter connecting to SQL Server and the BizTalk Message Box residing on SQL Server.</span></span> <span data-ttu-id="1a286-109">Par conséquent, toutes les opérations effectuées à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] sont effectuées dans l’étendue d’une transaction MSDTC.</span><span class="sxs-lookup"><span data-stu-id="1a286-109">Hence, all operations performed using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] are performed within the scope of an MSDTC transaction.</span></span> <span data-ttu-id="1a286-110">Par conséquent, pour utiliser le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez toujours activer MSDTC.</span><span class="sxs-lookup"><span data-stu-id="1a286-110">So, to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must always enable MSDTC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a286-111">Pour les opérations où le client de carte n’écrit pas toutes les données à la base de données SQL Server, tel qu’une opération Select, vous pouvez la charge supplémentaire d’effectuer les opérations à l’intérieur d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="1a286-111">For operations where the adapter client does not write any data to the SQL Server database, such as a Select operation, you might not want the additional overhead of performing the operations inside a transaction.</span></span> <span data-ttu-id="1a286-112">Dans ce cas, vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour effectuer des opérations sans un contexte transactionnel en définissant le **UseAmbientTransaction** liaison de propriété **false**.</span><span class="sxs-lookup"><span data-stu-id="1a286-112">In such cases, you can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to perform operations without a transactional context by setting the **UseAmbientTransaction** binding property to **false**.</span></span> <span data-ttu-id="1a286-113">Pour plus d’informations sur la propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="1a286-113">For more information about the binding property, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="1a286-114">Dans ce cas, il est inutile de configurer MSDTC ainsi.</span><span class="sxs-lookup"><span data-stu-id="1a286-114">In such cases, you do not need to configure MSDTC as well.</span></span>  
  
## <a name="configure-msdtc"></a><span data-ttu-id="1a286-115">Configurer MSDTC</span><span class="sxs-lookup"><span data-stu-id="1a286-115">Configure MSDTC</span></span>  
  
1.  <span data-ttu-id="1a286-116">Ouvrez **Services de composants**.</span><span class="sxs-lookup"><span data-stu-id="1a286-116">Open **Component Services**.</span></span>  

    <span data-ttu-id="1a286-117">Ou, **le Gestionnaire de serveur**, sélectionnez **outils**, puis sélectionnez **Services de composants**.</span><span class="sxs-lookup"><span data-stu-id="1a286-117">Or, In **Server Manager**, select **Tools**, and then select **Component Services**.</span></span>  
  
2.  <span data-ttu-id="1a286-118">Développez **Services de composants**, développez **ordinateurs**, développez **poste**, développez **Distributed Transaction Coordinator**, avec le bouton droit **DTC Local**, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1a286-118">Expand **Component Services**, expand **Computers**, expand **My Computer**, expand **Distributed Transaction Coordinator**, right-click **Local DTC**, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="1a286-119">Sélectionnez l'onglet **Sécurité** . Dans cet onglet, sélectionnez tous les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1a286-119">Select the **Security** tab. In this tab, select all of the following:</span></span> 

  - <span data-ttu-id="1a286-120">**Accès DTC réseau**</span><span class="sxs-lookup"><span data-stu-id="1a286-120">**Network DTC Access**</span></span>
  - <span data-ttu-id="1a286-121">**Autoriser les Clients distants**</span><span class="sxs-lookup"><span data-stu-id="1a286-121">**Allow Remote Clients**</span></span> 
  - <span data-ttu-id="1a286-122">**Autoriser les transactions entrantes**</span><span class="sxs-lookup"><span data-stu-id="1a286-122">**Allow Inbound**</span></span> 
  - <span data-ttu-id="1a286-123">**Autoriser les transactions sortantes**</span><span class="sxs-lookup"><span data-stu-id="1a286-123">**Allow Outbound**</span></span> 
  - <span data-ttu-id="1a286-124">**Aucun Authetnication requis**</span><span class="sxs-lookup"><span data-stu-id="1a286-124">**No Authetnication Required**</span></span>
  
4.  <span data-ttu-id="1a286-125">Sélectionnez **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="1a286-125">Select **OK** to save your changes.</span></span>  
  
5.  <span data-ttu-id="1a286-126">Si vous êtes invité à redémarrer le service MSDTC, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="1a286-126">If prompted to restarted the MSDTC service, select **Yes**.</span></span> <span data-ttu-id="1a286-127">Une fois que le service MSDTC est redémarré, fermez les propriétés et la console MMC Services de composants.</span><span class="sxs-lookup"><span data-stu-id="1a286-127">After the MSDTC service is restarted, close the properties and the Component Services MMC.</span></span> 
  
## <a name="add-msdtc-to-windows-firewall-exceptions-list"></a><span data-ttu-id="1a286-128">Ajouter de MSDTC à la liste des exceptions du pare-feu Windows</span><span class="sxs-lookup"><span data-stu-id="1a286-128">Add MSDTC to Windows Firewall exceptions list</span></span>  

> [!TIP] 
>  <span data-ttu-id="1a286-129">Microsoft Distributed ordre Coordinator (MSDTC) peut déjà être autorisé dans votre pare-feu.</span><span class="sxs-lookup"><span data-stu-id="1a286-129">Microsoft Distributed Tansaction Coordinator (MSDTC) may already be allowed in your firewall.</span></span> <span data-ttu-id="1a286-130">Dans ce cas, il est répertorié comme une règle de trafic entrant.</span><span class="sxs-lookup"><span data-stu-id="1a286-130">If so, it is listed as an Inbound Rule.</span></span> <span data-ttu-id="1a286-131">S’il n’est pas répertorié, utilisez cette section pour autoriser le MSDTC.</span><span class="sxs-lookup"><span data-stu-id="1a286-131">If it's not listed, use this section to allow MSDTC.</span></span> 

1.  <span data-ttu-id="1a286-132">Ouvrez **pare-feu Windows**, puis sélectionnez **paramètres avancés** sur la gauche.</span><span class="sxs-lookup"><span data-stu-id="1a286-132">Open **Windows Firewall**, and select **Advanced Settings** on the left.</span></span>  

    <span data-ttu-id="1a286-133">Ou, **le Gestionnaire de serveur**, sélectionnez **outils**, puis sélectionnez **pare-feu Windows avec fonctions avancées de sécurité**.</span><span class="sxs-lookup"><span data-stu-id="1a286-133">Or, In **Server Manager**, select **Tools**, and then select **Windows Firewall with Advanced Security**.</span></span>  
  
2.  <span data-ttu-id="1a286-134">Bouton droit sur **règles de trafic entrant**, puis sélectionnez **nouvelle règle**.</span><span class="sxs-lookup"><span data-stu-id="1a286-134">Right click **Inbound Rules**, and select **New Rule**.</span></span>  
  
3.  <span data-ttu-id="1a286-135">Dans l’Assistant :</span><span class="sxs-lookup"><span data-stu-id="1a286-135">In the wizard:</span></span> 

    1. <span data-ttu-id="1a286-136">Sélectionnez **programme**, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="1a286-136">Select **Program**, and select **Next**.</span></span> 
    2. <span data-ttu-id="1a286-137">Définir le **chemin d’accès du programme** à `%SystemRoot%\system32\msdtc.exe`, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="1a286-137">Set the **program path** to `%SystemRoot%\system32\msdtc.exe`, and select **Next**.</span></span>  
    3. <span data-ttu-id="1a286-138">**Autoriser la connexion**, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="1a286-138">**Allow the connection**, and select **Next**.</span></span>
    4. <span data-ttu-id="1a286-139">Sélectionnez **domaine**, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="1a286-139">Select **Domain**, and select **Next**.</span></span>
    5. <span data-ttu-id="1a286-140">Entrez un nom quelconque, tel que `MSDTC for Oracle EBS`, puis sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="1a286-140">Enter any name, such as `MSDTC for Oracle EBS`, and select **Finish**.</span></span>
  
5.  <span data-ttu-id="1a286-141">Terminez l’Assistant et fermer le pare-feu Windows.</span><span class="sxs-lookup"><span data-stu-id="1a286-141">Complete the wizard, and close Windows Firewall.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="1a286-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a286-142">See Also</span></span>  
[<span data-ttu-id="1a286-143">Développer vos applications SQL</span><span class="sxs-lookup"><span data-stu-id="1a286-143">Develop your SQL applications</span></span>](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)