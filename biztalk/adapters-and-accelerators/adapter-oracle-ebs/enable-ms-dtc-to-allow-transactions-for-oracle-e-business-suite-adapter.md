---
title: "Activez Microsoft distribuée transaction coordinator autoriser les transactions pour Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 634538e5-7292-4b3f-85b0-c6db86d0dbd2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0597c050e1531d71a62af04fe6c825653076297c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enable-ms-distributed-transaction-coordinator-to-allow-transactions-for-oracle-e-business-suite"></a><span data-ttu-id="db01e-102">Activez Microsoft distribuée transaction coordinator autoriser les transactions pour Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="db01e-102">Enable MS distributed transaction coordinator to allow transactions for Oracle E-Business Suite</span></span>
<span data-ttu-id="db01e-103">Configurer MSDTC avant de commencer la création d’applications qui utilisent le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db01e-103">Configure MSDTC before you start creating applications that use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
<span data-ttu-id="db01e-104">Les opérations effectuées sur Oracle E-Business Suite à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] (via [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le modèle de service WCF ou le modèle de canal WCF) peut être effectuée dans une étendue de transaction.</span><span class="sxs-lookup"><span data-stu-id="db01e-104">The operations performed on Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] (through [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the WCF service model, or the WCF channel model) can be performed within a transaction scope.</span></span> <span data-ttu-id="db01e-105">Si le programme client possède plusieurs ressources de transaction dans le cadre de la même transaction, la transaction obtient élevés au rang d’une transaction MSDTC.</span><span class="sxs-lookup"><span data-stu-id="db01e-105">If the client program has more than one transactional resource as part of the same transaction, the transaction gets elevated to an MSDTC transaction.</span></span> <span data-ttu-id="db01e-106">Pour activer la carte effectuer des opérations dans l’étendue d’une transaction MSDTC, configurez MSDTC sur l’ordinateur exécutant le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]et à Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="db01e-106">To enable the adapter to perform operations within the scope of an MSDTC transaction, configure MSDTC on the computer running the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], and on the Oracle E-Business Suite.</span></span> <span data-ttu-id="db01e-107">En outre, ajoutez MSDTC à la liste des exceptions dans votre pare-feu, qui peut être le pare-feu Windows.</span><span class="sxs-lookup"><span data-stu-id="db01e-107">Also, add MSDTC to the exceptions list in your firewall, which may be the built-in Windows Firewall.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="db01e-108">Les étapes pour configurer MSDTC varient pour les différents systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="db01e-108">The steps to configure MSDTC vary for different operating systems.</span></span> <span data-ttu-id="db01e-109">Les étapes répertoriées dans cette rubrique s’appliquent à des systèmes d’exploitation Windows Server et clients Windows.</span><span class="sxs-lookup"><span data-stu-id="db01e-109">The steps listed in this topic apply to Windows client and Windows Server operating systems.</span></span>  
  
## <a name="configure-msdtc"></a><span data-ttu-id="db01e-110">Configurer MSDTC</span><span class="sxs-lookup"><span data-stu-id="db01e-110">Configure MSDTC</span></span>  
  
1.  <span data-ttu-id="db01e-111">Ouvrez **Services de composants**.</span><span class="sxs-lookup"><span data-stu-id="db01e-111">Open **Component Services**.</span></span>  

    <span data-ttu-id="db01e-112">Ou, **le Gestionnaire de serveur**, sélectionnez **outils**, puis sélectionnez **Services de composants**.</span><span class="sxs-lookup"><span data-stu-id="db01e-112">Or, In **Server Manager**, select **Tools**, and then select **Component Services**.</span></span>  
  
2.  <span data-ttu-id="db01e-113">Développez **Services de composants**, développez **ordinateurs**, développez **poste**, développez **Distributed Transaction Coordinator**, avec le bouton droit **DTC Local**, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="db01e-113">Expand **Component Services**, expand **Computers**, expand **My Computer**, expand **Distributed Transaction Coordinator**, right-click **Local DTC**, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="db01e-114">Sélectionnez l'onglet **Sécurité** . Dans cet onglet, sélectionnez tous les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="db01e-114">Select the **Security** tab. In this tab, select all of the following:</span></span> 

  - <span data-ttu-id="db01e-115">**Accès DTC réseau**</span><span class="sxs-lookup"><span data-stu-id="db01e-115">**Network DTC Access**</span></span>
  - <span data-ttu-id="db01e-116">**Autoriser les Clients distants**</span><span class="sxs-lookup"><span data-stu-id="db01e-116">**Allow Remote Clients**</span></span> 
  - <span data-ttu-id="db01e-117">**Autoriser les transactions entrantes**</span><span class="sxs-lookup"><span data-stu-id="db01e-117">**Allow Inbound**</span></span> 
  - <span data-ttu-id="db01e-118">**Autoriser les transactions sortantes**</span><span class="sxs-lookup"><span data-stu-id="db01e-118">**Allow Outbound**</span></span> 
  - <span data-ttu-id="db01e-119">**Aucun Authetnication requis**</span><span class="sxs-lookup"><span data-stu-id="db01e-119">**No Authetnication Required**</span></span>
  
4.  <span data-ttu-id="db01e-120">Sélectionnez **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="db01e-120">Select **OK** to save your changes.</span></span>  
  
5.  <span data-ttu-id="db01e-121">Si vous êtes invité à redémarrer le service MSDTC, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="db01e-121">If prompted to restarted the MSDTC service, select **Yes**.</span></span> <span data-ttu-id="db01e-122">Une fois que le service MSDTC est redémarré, fermez les propriétés et la console MMC Services de composants.</span><span class="sxs-lookup"><span data-stu-id="db01e-122">After the MSDTC service is restarted, close the properties and the Component Services MMC.</span></span> 
  
## <a name="add-msdtc-to-windows-firewall-exceptions-list"></a><span data-ttu-id="db01e-123">Ajouter de MSDTC à la liste des exceptions du pare-feu Windows</span><span class="sxs-lookup"><span data-stu-id="db01e-123">Add MSDTC to Windows Firewall exceptions list</span></span>  

> [!TIP] 
>  <span data-ttu-id="db01e-124">Microsoft Distributed ordre Coordinator (MSDTC) peut déjà être autorisé dans votre pare-feu.</span><span class="sxs-lookup"><span data-stu-id="db01e-124">Microsoft Distributed Tansaction Coordinator (MSDTC) may already be allowed in your firewall.</span></span> <span data-ttu-id="db01e-125">Dans ce cas, il est répertorié comme une règle de trafic entrant.</span><span class="sxs-lookup"><span data-stu-id="db01e-125">If so, it is listed as an Inbound Rule.</span></span> <span data-ttu-id="db01e-126">S’il n’est pas répertorié, utilisez cette section pour autoriser le MSDTC.</span><span class="sxs-lookup"><span data-stu-id="db01e-126">If it's not listed, use this section to allow MSDTC.</span></span> 

1.  <span data-ttu-id="db01e-127">Ouvrez **pare-feu Windows**, puis sélectionnez **paramètres avancés** sur la gauche.</span><span class="sxs-lookup"><span data-stu-id="db01e-127">Open **Windows Firewall**, and select **Advanced Settings** on the left.</span></span>  

    <span data-ttu-id="db01e-128">Ou, **le Gestionnaire de serveur**, sélectionnez **outils**, puis sélectionnez **pare-feu Windows avec fonctions avancées de sécurité**.</span><span class="sxs-lookup"><span data-stu-id="db01e-128">Or, In **Server Manager**, select **Tools**, and then select **Windows Firewall with Advanced Security**.</span></span>  
  
2.  <span data-ttu-id="db01e-129">Bouton droit sur **règles de trafic entrant**, puis sélectionnez **nouvelle règle**.</span><span class="sxs-lookup"><span data-stu-id="db01e-129">Right click **Inbound Rules**, and select **New Rule**.</span></span>  
  
3.  <span data-ttu-id="db01e-130">Dans l’Assistant :</span><span class="sxs-lookup"><span data-stu-id="db01e-130">In the wizard:</span></span> 

    1. <span data-ttu-id="db01e-131">Sélectionnez **programme**, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="db01e-131">Select **Program**, and select **Next**.</span></span> 
    2. <span data-ttu-id="db01e-132">Définir le **chemin d’accès du programme** à `%SystemRoot%\system32\msdtc.exe`, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="db01e-132">Set the **program path** to `%SystemRoot%\system32\msdtc.exe`, and select **Next**.</span></span>  
    3. <span data-ttu-id="db01e-133">**Autoriser la connexion**, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="db01e-133">**Allow the connection**, and select **Next**.</span></span>
    4. <span data-ttu-id="db01e-134">Sélectionnez **domaine**, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="db01e-134">Select **Domain**, and select **Next**.</span></span>
    5. <span data-ttu-id="db01e-135">Entrez un nom quelconque, tel que `MSDTC for Oracle EBS`, puis sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="db01e-135">Enter any name, such as `MSDTC for Oracle EBS`, and select **Finish**.</span></span>
  
5.  <span data-ttu-id="db01e-136">Terminez l’Assistant et fermer le pare-feu Windows.</span><span class="sxs-lookup"><span data-stu-id="db01e-136">Complete the wizard, and close Windows Firewall.</span></span> 
  
## <a name="next"></a><span data-ttu-id="db01e-137">Suivant</span><span class="sxs-lookup"><span data-stu-id="db01e-137">Next</span></span> 
[<span data-ttu-id="db01e-138">Exemples de l’adaptateur Oracle eBusiness Suite</span><span class="sxs-lookup"><span data-stu-id="db01e-138">Samples for the Oracle EBS adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)