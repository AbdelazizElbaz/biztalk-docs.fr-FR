---
title: "Problèmes connus avec l’adaptateur SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3229d73-170d-42b7-bab9-12ae5f2d0fa7
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 671510c6901fc399580ab73018e67eadc86f7212
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-soap-adapter"></a><span data-ttu-id="8e18b-102">Problèmes connus avec l'adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="8e18b-102">Known Issues with the SOAP Adapter</span></span>
<span data-ttu-id="8e18b-103">Cette section contient des informations qui peuvent vous permettre d'éviter certaines erreurs.</span><span class="sxs-lookup"><span data-stu-id="8e18b-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="8e18b-104">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="8e18b-104">Known Issues</span></span>  
  
#### <a name="the-soap-adapter-experiences-poor-performance-or-generates-errors-under-load"></a><span data-ttu-id="8e18b-105">L'adaptateur SOAP rencontre des problèmes de performances ou génère des erreurs en conditions de charge</span><span class="sxs-lookup"><span data-stu-id="8e18b-105">The SOAP Adapter experiences poor performance or generates errors under load</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="8e18b-106">Problème</span><span class="sxs-lookup"><span data-stu-id="8e18b-106">Problem</span></span>  
 <span data-ttu-id="8e18b-107">L'adaptateur SOAP rencontre des problèmes de performances ou génère des erreurs en conditions de charge</span><span class="sxs-lookup"><span data-stu-id="8e18b-107">The SOAP Adapter experiences poor performance or generates errors under load</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="8e18b-108">Cause</span><span class="sxs-lookup"><span data-stu-id="8e18b-108">Cause</span></span>  
 <span data-ttu-id="8e18b-109">Ce problème survient car les options de configuration par défaut de l'adaptateur SOAP ou des composants de dépendances qui ont un impact sur l'adaptateur SOAP ne sont pas configurés pour les performances en cas de charge.</span><span class="sxs-lookup"><span data-stu-id="8e18b-109">This problem occurs because the default configuration options for the SOAP adapter or for dependency components that affect the SOAP adapter are not tuned for performance under load.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="8e18b-110">Résolution</span><span class="sxs-lookup"><span data-stu-id="8e18b-110">Resolution</span></span>  
 <span data-ttu-id="8e18b-111">Pour résoudre ce problème, modifiez les options de configuration de l’adaptateur SOAP ou des composants de dépendance décrites dans la rubrique [les paramètres de Configuration qui affectent les performances carte](../core/configuration-parameters-that-affect-adapter-performance.md).</span><span class="sxs-lookup"><span data-stu-id="8e18b-111">To resolve this problem modify the configuration options for the SOAP adapter or for the dependency components described in the topic [Configuration Parameters that Affect Adapter Performance](../core/configuration-parameters-that-affect-adapter-performance.md).</span></span>  
  
#### <a name="the-mimesmime-encoder-and-decoder-pipeline-components-cannot-encode-and-decode-data-processed-by-the-soap-adapter"></a><span data-ttu-id="8e18b-112">Les composants de pipeline Encodeur et Décodeur MIME/SMIME ne peuvent ni coder ni décoder les données traitées par l'adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="8e18b-112">The MIME/SMIME encoder and decoder pipeline components cannot encode and decode data processed by the SOAP adapter</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="8e18b-113">Problème</span><span class="sxs-lookup"><span data-stu-id="8e18b-113">Problem</span></span>  
 <span data-ttu-id="8e18b-114">Les composants de pipeline Encodeur et Décodeur MIME/SMIME ne peuvent ni coder ni décoder les données traitées par l'adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="8e18b-114">The MIME/SMIME encoder and decoder pipeline components cannot encode and decode data processed by the SOAP adapter</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="8e18b-115">Cause</span><span class="sxs-lookup"><span data-stu-id="8e18b-115">Cause</span></span>  
 <span data-ttu-id="8e18b-116">Ce problème se produit car l'adaptateur SOAP assemble et désassemble les messages SOAP dans l'étape du processus le concernant.</span><span class="sxs-lookup"><span data-stu-id="8e18b-116">This problem occurs because the SOAP adapter assembles and disassembles the SOAP messages in the adapter stage of the process.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="8e18b-117">Résolution</span><span class="sxs-lookup"><span data-stu-id="8e18b-117">Resolution</span></span>  
 <span data-ttu-id="8e18b-118">Pour résoudre ce problème, utilisez SSL (Secure Sockets Layer) pour sécuriser les communications de codage des messages traités par l'adaptateur SOAP.</span><span class="sxs-lookup"><span data-stu-id="8e18b-118">To resolve this problem, Use Secure Sockets Layer (SSL) to secure communications to encode messages processed by the SOAP adapter.</span></span> <span data-ttu-id="8e18b-119">Sur le côté envoi, utilisez le **empreinte de certificat Client** propriété dans la page de propriétés de l’adaptateur SOAP pour effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="8e18b-119">On the send side, use the **Client Certificate Thumbprint** property in the SOAP adapter properties page to achieve this.</span></span> <span data-ttu-id="8e18b-120">Au niveau de la réception, vous devez configurer le répertoire virtuel qui héberge le service Web BizTalk pour les communications SSL sécurisées.</span><span class="sxs-lookup"><span data-stu-id="8e18b-120">On the receive side, you must configure the virtual directory that hosts the BizTalk Web Service for SSL secure communications.</span></span>  
  
#### <a name="the-default-appdomain-hosting-the-soap-adapter-gets-unloaded-causing-the-host-process-to-hang"></a><span data-ttu-id="8e18b-121">Le domaine d'application AppDomain par défaut hébergeant l'adaptateur SOAP est déchargé, ce qui provoque le blocage du processus hôte</span><span class="sxs-lookup"><span data-stu-id="8e18b-121">The default AppDomain hosting the SOAP adapter gets unloaded causing the host process to hang</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="8e18b-122">Problème</span><span class="sxs-lookup"><span data-stu-id="8e18b-122">Problem</span></span>  
 <span data-ttu-id="8e18b-123">Le processus hébergeant l'adaptateur SOAP se bloque, ce qui provoque le blocage de tous les autres services Web du processus.</span><span class="sxs-lookup"><span data-stu-id="8e18b-123">The process hosting the SOAP adapter hangs, causing all other Web services in the process to hang.</span></span> <span data-ttu-id="8e18b-124">Cela peut donner lieu à l'erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="8e18b-124">This may result in the following error:</span></span>  
  
 <span data-ttu-id="8e18b-125">Échec de l’exécution du pipeline de réponse : Source « Inconnu » : « inconnu » recevoir Port : "TwoWayLatencyLoopBack_RxPort » URI : « / /twowaylatencyrxsoap/twowaylatencyws.asmx » raison : tenté d’accéder à un AppDomain non chargé.</span><span class="sxs-lookup"><span data-stu-id="8e18b-125">There was a failure executing the response(send) pipeline: "Unknown " Source: "Unknown " Receive Port: TwoWayLatencyLoopBack_RxPort" URI: "/TwoWayLatencyRxSOAP/TwoWayLatencyWS.asmx" Reason: Attempted to access an unloaded AppDomain.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="8e18b-126">Cause</span><span class="sxs-lookup"><span data-stu-id="8e18b-126">Cause</span></span>  
 <span data-ttu-id="8e18b-127">L'adaptateur SOAP s'exécute dans l'espace de processus IIS.</span><span class="sxs-lookup"><span data-stu-id="8e18b-127">The SOAP adapter runs in the IIS process space.</span></span> <span data-ttu-id="8e18b-128">Si le pool d'applications AppPool de IIS contient plusieurs services Web, chacun d'entre eux dispose au final de son propre AppDomain.</span><span class="sxs-lookup"><span data-stu-id="8e18b-128">If more than one Web service exists in the IIS AppPool, then every Web service ends up having its own AppDomain.</span></span>  
  
 <span data-ttu-id="8e18b-129">Par défaut, tous les objets du moteur de messagerie sont créés dans le premier AppDomain (c'est-à-dire,.</span><span class="sxs-lookup"><span data-stu-id="8e18b-129">By default all messaging engine objects are created in the first AppDomain (that is,.</span></span> <span data-ttu-id="8e18b-130">le domaine d’application correspondant au premier service Web).</span><span class="sxs-lookup"><span data-stu-id="8e18b-130">the AppDomain corresponding to the first Web service).</span></span> <span data-ttu-id="8e18b-131">Si le premier service Web est inactif pendant une période prolongée, quelle qu'en soit la raison, IIS décharge le premier AppDomain.</span><span class="sxs-lookup"><span data-stu-id="8e18b-131">If the first Web service is inactive for an extended period of time for any reason, IIS unloads the first AppDomain.</span></span> <span data-ttu-id="8e18b-132">Dans ce cas, tous les services du processus d'hébergement deviennent inutilisables.</span><span class="sxs-lookup"><span data-stu-id="8e18b-132">When this happens, all services in the hosting process become unusable.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="8e18b-133">Résolution</span><span class="sxs-lookup"><span data-stu-id="8e18b-133">Resolution</span></span>  
 <span data-ttu-id="8e18b-134">Pour éviter le déchargement du domaine d’application AppDomain, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8e18b-134">To prevent the AppDomain from being unloaded, follow the procedure below:</span></span>  
  
1.  <span data-ttu-id="8e18b-135">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk Server** puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="8e18b-135">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Server** and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="8e18b-136">Dans **Console d’Administration de BizTalk Server**, Expand **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **hôtes**.</span><span class="sxs-lookup"><span data-stu-id="8e18b-136">In **BizTalk Server Administration Console**, Expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Hosts**.</span></span>  
  
3.  <span data-ttu-id="8e18b-137">Dans la liste des ordinateurs hôtes, cliquez sur l’hôte requis, puis cliquez sur **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="8e18b-137">From the list of Hosts, right-click the required host, and then click **Settings**.</span></span>  
  
4.  <span data-ttu-id="8e18b-138">Dans le **Panneau de configuration BizTalk**, vérifiez **domaine d’application par défaut pour un adaptateur isolé** sous **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="8e18b-138">In the **BizTalk Settings Dashboard**, check **Default application domain for isolated adapter** under **General** tab.</span></span>  
  
 <span data-ttu-id="8e18b-139">Ceci fait, les objets du moteur de messagerie BizTalk sont créés dans le domaine d'application AppDomain par défaut et non dans leur propre AppDomains.</span><span class="sxs-lookup"><span data-stu-id="8e18b-139">When you do this, the BizTalk Messaging Engine objects are created in the default AppDomain instead of in their own AppDomains.</span></span> <span data-ttu-id="8e18b-140">Le domaine d'application AppDomain par défaut n'étant jamais déchargé, ce problème ne se produit plus.</span><span class="sxs-lookup"><span data-stu-id="8e18b-140">Because the default AppDomain is never unloaded, the problem no longer occurs.</span></span>  
  
#### <a name="the-soap-adapter-fails-to-register"></a><span data-ttu-id="8e18b-141">Échec de l'inscription de l'adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="8e18b-141">The SOAP Adapter fails to register</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="8e18b-142">Problème</span><span class="sxs-lookup"><span data-stu-id="8e18b-142">Problem</span></span>  
 <span data-ttu-id="8e18b-143">L'erreur suivante peut se produire lorsque BizTalk Server tente d'inscrire l'adaptateur SOAP (ou HTTP).</span><span class="sxs-lookup"><span data-stu-id="8e18b-143">The following error may occur when BizTalk Server attempts to register the SOAP (or HTTP) adapter.</span></span>  
  
 <span data-ttu-id="8e18b-144">« Le moteur de messagerie n'a pas pu inscrire l'adaptateur "SOAP".</span><span class="sxs-lookup"><span data-stu-id="8e18b-144">"The Messaging Engine failed to register an adapter "SOAP".</span></span> <span data-ttu-id="8e18b-145">Détails : « inscription de différents types d’adaptateur dans le même processus n’est pas un scénario pris en charge.</span><span class="sxs-lookup"><span data-stu-id="8e18b-145">Details: "Registering multiple adapter types within the same process is not a supported scenario.</span></span> <span data-ttu-id="8e18b-146">Ainsi, les adaptateurs de réception HTTP et SOAP ne peuvent pas coexister dans le même processus. »</span><span class="sxs-lookup"><span data-stu-id="8e18b-146">For e.g. HTTP and SOAP receive adapters cannot co-exist in the same process".</span></span>  
  
 <span data-ttu-id="8e18b-147">Ou</span><span class="sxs-lookup"><span data-stu-id="8e18b-147">Or</span></span>  
  
 <span data-ttu-id="8e18b-148">« Le moteur de messagerie n'a pas pu inscrire l'adaptateur "HTTP".</span><span class="sxs-lookup"><span data-stu-id="8e18b-148">"The Messaging Engine failed to register an adapter "HTTP".</span></span> <span data-ttu-id="8e18b-149">Détails : « inscription de différents types d’adaptateur dans le même processus n’est pas un scénario pris en charge.</span><span class="sxs-lookup"><span data-stu-id="8e18b-149">Details: "Registering multiple adapter types within the same process is not a supported scenario.</span></span>  <span data-ttu-id="8e18b-150">Ainsi, les adaptateurs de réception HTTP et SOAP ne peuvent pas coexister dans le même processus. »</span><span class="sxs-lookup"><span data-stu-id="8e18b-150">For e.g. HTTP and SOAP receive adapters cannot co-exist in the same process".</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="8e18b-151">Cause</span><span class="sxs-lookup"><span data-stu-id="8e18b-151">Cause</span></span>  
 <span data-ttu-id="8e18b-152">Lors de l'exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] / IIS 6.x, les adaptateurs SOAP et HTTP ne peuvent pas s'exécuter dans le même espace de processus ou pool d'applications.</span><span class="sxs-lookup"><span data-stu-id="8e18b-152">When running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] / IIS 6.x, the SOAP and HTTP adapters cannot execute in the same process space or application pool.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="8e18b-153">Résolution</span><span class="sxs-lookup"><span data-stu-id="8e18b-153">Resolution</span></span>  
 <span data-ttu-id="8e18b-154">Si une installation requiert l'utilisation des adaptateurs SOAP et HTTP sur le même serveur Web, des pools d'applications distincts doivent être créés pour chaque adaptateur.</span><span class="sxs-lookup"><span data-stu-id="8e18b-154">If an installation requires using both the SOAP and HTTP adapters on the same Web server then separate application pools must be created for each adapter.</span></span>  <span data-ttu-id="8e18b-155">Une fois créés, les répertoires virtuels de chaque adaptateur sont chacun assignés à un pool d'applications différent.</span><span class="sxs-lookup"><span data-stu-id="8e18b-155">Once created, the virtual directories for each adapter are each assigned to a different application pool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e18b-156">Ce problème ne se produit pas sous Windows XP car, sous ce système d'exploitation, les adaptateurs SOAP et HTTP s'exécutent dans des espaces de processus différents sous IIS 5.x.</span><span class="sxs-lookup"><span data-stu-id="8e18b-156">This problem does not occur under Windows XP since under these operating systems, the SOAP and HTTP adapter run in different process spaces under IIS 5.x.</span></span>  <span data-ttu-id="8e18b-157">L'adaptateur SOAP s'exécute en tant qu'application ASP.Net dans le processus aspnet_wp.exe.</span><span class="sxs-lookup"><span data-stu-id="8e18b-157">The SOAP adapter runs as an ASP.Net application in the aspnet_wp.exe process.</span></span>  <span data-ttu-id="8e18b-158">L'adaptateur HTTP s'exécute dans l'espace de processus dédié de dllhost.exe.</span><span class="sxs-lookup"><span data-stu-id="8e18b-158">The HTTP adapter runs in the dedicated process space of dllhost.exe.</span></span>  <span data-ttu-id="8e18b-159">Les deux adaptateurs sont donc isolés l'un de l'autre, et peuvent donc s'exécuter sur le même serveur Web simultanément.</span><span class="sxs-lookup"><span data-stu-id="8e18b-159">Therefore both adapters are isolated from each other allowing them to run on the same Web server concurrently.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e18b-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e18b-160">See Also</span></span>  
 [<span data-ttu-id="8e18b-161">Dépannage de l’adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="8e18b-161">Troubleshooting the SOAP Adapter</span></span>](../core/troubleshooting-the-soap-adapter.md)