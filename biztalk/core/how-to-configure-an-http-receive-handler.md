---
title: "Pour configurer les Gestionnaire de réception HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions, receive handlers
- configuring [HTTP adapters], permissions
- HTTP adapters, receive handlers
- receive handlers, permissions
- configuring [HTTP adapters], receive handlers
- permissions, HTTP adapters
- receive handlers, HTTP adapters
- HTTP adapters, permissions
ms.assetid: c295489e-dbbb-44f7-bddb-d3cdfe302cf5
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0380804039d45efbe3db06b6fc072a3afb8b6b48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-http-receive-handler"></a><span data-ttu-id="a4a93-102">Pour configurer les Gestionnaire de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="a4a93-102">How to Configure an HTTP Receive Handler</span></span>
<span data-ttu-id="a4a93-103">La procédure suivante permet de configurer les propriétés d'un gestionnaire de réception HTTP.</span><span class="sxs-lookup"><span data-stu-id="a4a93-103">Use the following procedure to configure the properties for an HTTP receive handler.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4a93-104">Un seul gestionnaire de réception peut être associé à chaque hôte.</span><span class="sxs-lookup"><span data-stu-id="a4a93-104">Each host can have only one receive handler associated with it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4a93-105">L'adaptateur de réception HTTP est exécuté dans le contexte d'une instance d'hôte BizTalk isolé.</span><span class="sxs-lookup"><span data-stu-id="a4a93-105">The HTTP receive adapter runs in the context of a BizTalk Isolated Host instance.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a4a93-106">Lors de l'utilisation des gestionnaires d'adaptateur HTTP ou SOAP, il est recommandé d'installer les instances d'hôte pour ces gestionnaires sur des ordinateurs Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4a93-106">When using HTTP or SOAP adapter handlers, it is recommended that you install the host instances for these handlers on Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] computers.</span></span>  
  
### <a name="to-configure-the-general-properties-for-an-http-receive-handler"></a><span data-ttu-id="a4a93-107">Pour configurer les propriétés générales d'un gestionnaire de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="a4a93-107">To configure the general properties for an HTTP receive handler</span></span>  
  
1.  <span data-ttu-id="a4a93-108">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez **Cartes**.</span><span class="sxs-lookup"><span data-stu-id="a4a93-108">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="a4a93-109">Dans la liste développée des adaptateurs, cliquez sur **HTTP,** dans le volet droit, cliquez sur le Gestionnaire de réception que vous souhaitez configurer, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a4a93-109">In the expanded adapter list, click **HTTP,** in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a4a93-110">Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte avec lequel associer le Gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="a4a93-110">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.</span></span>  
  
4.  <span data-ttu-id="a4a93-111">Cliquez sur **propriétés** pour accéder à la **taille du lot** Gestionnaire de réception de propriété pour le protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="a4a93-111">Click **Properties** to access the **Batch size** property for the HTTP receive handler.</span></span>  
  
5.  <span data-ttu-id="a4a93-112">Entrez une valeur comprise entre 1 et 256, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a4a93-112">Enter a value from 1 to 256 and click **OK**.</span></span>  
  
6.  <span data-ttu-id="a4a93-113">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a4a93-113">Click **OK**.</span></span>  
  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="a4a93-114"> est conçu pour traiter efficacement les lots de messages, pas pour traiter un message unique très rapidement.</span><span class="sxs-lookup"><span data-stu-id="a4a93-114"> is designed to process batches of messages effectively and not to process a single message very quickly.</span></span> <span data-ttu-id="a4a93-115">Aussi, si ce gestionnaire de réception doit être utilisé par des emplacements de réception de requête-réponse/bidirectionnels, vous pouvez réduire la latence en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="a4a93-115">So if this receive handler is going to be used for two way/request-response receive locations then you can minimize latency by following these steps:</span></span>  
  
-   <span data-ttu-id="a4a93-116">Définir le **taille du lot** propriété à une valeur de 1.</span><span class="sxs-lookup"><span data-stu-id="a4a93-116">Set the **Batch size** property to a value of 1.</span></span>  
  
-   <span data-ttu-id="a4a93-117">Réduire le **MaxReceiveInterval** valeur à partir de la valeur par défaut de 500 à une valeur inférieure à 100 pour le **messagerie isolée, XLANG/s,** et **messagerie In-Process** service classes.</span><span class="sxs-lookup"><span data-stu-id="a4a93-117">Reduce the **MaxReceiveInterval** value from the default value of 500 to a value less than 100 for the **Messaging Isolated, XLANG/s,** and **Messaging In-Process** service classes.</span></span>  <span data-ttu-id="a4a93-118">Modifications du **adm_ServiceClass** table de la base de données de gestion BizTalk qui contienne un enregistrement pour chacun de ces types de service.</span><span class="sxs-lookup"><span data-stu-id="a4a93-118">Changes are made the **adm_ServiceClass** table of the BizTalk Management database, which contains one record for each of these service types.</span></span>  <span data-ttu-id="a4a93-119">Soyez prudent lorsque vous modifiez ce paramètre, car il s’agit d’une modification de l’échelle du type de service.</span><span class="sxs-lookup"><span data-stu-id="a4a93-119">Use caution when changing this setting because this is a service-type-wide change.</span></span> <span data-ttu-id="a4a93-120">Ce paramètre spécifie l'intervalle d'interrogation maximal (en millisecondes) auquel l'agent des messages [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] interroge la base de données MessageBox de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] afin de récupérer des messages.</span><span class="sxs-lookup"><span data-stu-id="a4a93-120">This setting specifies the maximum polling interval (in milliseconds) at which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] messaging agent polls the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Messagebox database for messages.</span></span>  <span data-ttu-id="a4a93-121">Il est également utilisé par le contrôleur de limitation pour décider si la limitation des messages est requise sous certaines conditions de charge.</span><span class="sxs-lookup"><span data-stu-id="a4a93-121">It also is used by the throttle controller to decide whether message throttling is needed under certain load conditions.</span></span> <span data-ttu-id="a4a93-122">Dans l'affirmative, le contrôleur de limitation augmente de façon incrémentielle l'intervalle de distribution des messages sur la base des conditions de forte charge sur le système.</span><span class="sxs-lookup"><span data-stu-id="a4a93-122">If needed, the throttling controller will incrementally delay the message dispatch interval based upon stress conditions on the system.</span></span> <span data-ttu-id="a4a93-123">Ce paramètre n'est pas utilisé dans un système à débit élevé.</span><span class="sxs-lookup"><span data-stu-id="a4a93-123">In a high throughput system, this setting will not be used.</span></span>  <span data-ttu-id="a4a93-124">Une fois que ces valeurs sont utilisées, l'intervalle passe de la valeur MaxReceiveInteral/10 à la valeur MaxReceiveInterval de façon dynamique.</span><span class="sxs-lookup"><span data-stu-id="a4a93-124">Once this values is used, however, the time interval will dynamically change between MaxReceiveInteral/10 and MaxReceiveInterval.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a4a93-125">Modifier ce paramètre affecte tous les ordinateurs hôtes qui sont créés avec un **Type d’hôte** de **isolé**.</span><span class="sxs-lookup"><span data-stu-id="a4a93-125">Changing this setting affects all hosts that are created with a **Host Type** of **Isolated**.</span></span>  
  
-   <span data-ttu-id="a4a93-126">Redémarrez le ou les pools d'applications IIS associés aux fonctions de réception HTTP que vous avez configurées.</span><span class="sxs-lookup"><span data-stu-id="a4a93-126">Restart the IIS Application Pool(s) associated with any HTTP receive functions that you have configured.</span></span>  
  
 <span data-ttu-id="a4a93-127">Le compte d’ouverture de session pour le **BizTalkServerIsolatedHost** instance d’hôte doit disposer de lecture et d’écriture pour l’ou les répertoires temporaires pour compiler de façon dynamique les fichiers de code-behind utilisés par le protocole HTTP receive, fonction.</span><span class="sxs-lookup"><span data-stu-id="a4a93-127">The logon account for the **BizTalkServerIsolatedHost** host instance must have Read and Write permissions to the temp directory or directories to dynamically compile the code-behind files used by the HTTP receive function.</span></span> <span data-ttu-id="a4a93-128">La procédure suivante permet d'octroyer ces autorisations.</span><span class="sxs-lookup"><span data-stu-id="a4a93-128">Use the following procedure to grant permissions.</span></span>  
  
### <a name="to-grant-the-account-for-the-biztalkserverisolatedhost-host-instance-read-and-write-permissions-to-the-temp-directory-of-your-biztalk-server"></a><span data-ttu-id="a4a93-129">Pour octroyer les autorisations de lecture et d'écriture sur le répertoire temporaire de votre serveur BizTalk Server au compte de l'instance de l'hôte BizTalkServerIsolatedHost</span><span class="sxs-lookup"><span data-stu-id="a4a93-129">To grant the account for the BizTalkServerIsolatedHost host instance Read and Write permissions to the temp directory of your BizTalk server</span></span>  
  
1.  <span data-ttu-id="a4a93-130">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **CMD**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="a4a93-130">Click **Start**, click **Run**, type **CMD**, and press ENTER.</span></span>  
  
2.  <span data-ttu-id="a4a93-131">À l’invite de commandes, tapez **définir TEMP** et appuyez sur ENTRÉE pour afficher le répertoire associé à la **TEMP** variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="a4a93-131">At the command prompt, type **set TEMP** and press ENTER to display the directory associated with the **TEMP** environment variable.</span></span>  
  
3.  <span data-ttu-id="a4a93-132">À l’invite de commandes, tapez **set TMP** et appuyez sur ENTRÉE pour afficher le répertoire associé à la **TMP** variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="a4a93-132">At the command prompt, type **set TMP** and press ENTER to display the directory associated with the **TMP** environment variable.</span></span>  
  
 <span data-ttu-id="a4a93-133">Accordez au compte qui est spécifié comme compte d’ouverture de session pour le **BizTalkServerIsolatedHost** héberger une instance en lecture et écriture pour l’ou les répertoires associés le **TEMP** et  **TMP** variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="a4a93-133">Grant the account that is specified as the logon account for the **BizTalkServerIsolatedHost** host instance Read and Write permissions to the directory or directories associated with the **TEMP** and **TMP** environment variables.</span></span> <span data-ttu-id="a4a93-134">Pour déterminer le compte d’ouverture de session pour le **BizTalkServerIsolatedHost** de l’instance, dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez  **Groupe BizTalk**, développez **paramètres de plateforme**, développez **Instances d’hôte**, avec le bouton droit le **BizTalkServerIsolatedHost** hôte l’instance dans le volet droit, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a4a93-134">To determine the logon account for the **BizTalkServerIsolatedHost** instance, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, expand **Host Instances**, right-click the **BizTalkServerIsolatedHost** host instance in the right pane, and then click **Properties**.</span></span> <span data-ttu-id="a4a93-135">Le compte d’ouverture de session utilisé pour l’instance d’hôte est répertorié en regard du **ouverture de session** étiquette.</span><span class="sxs-lookup"><span data-stu-id="a4a93-135">The logon account used for the host instance is listed next to the **Logon** label.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a93-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4a93-136">See Also</span></span>  
 [<span data-ttu-id="a4a93-137">Configuration de l’adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="a4a93-137">Configuring the HTTP Adapter</span></span>](../core/configuring-the-http-adapter.md)