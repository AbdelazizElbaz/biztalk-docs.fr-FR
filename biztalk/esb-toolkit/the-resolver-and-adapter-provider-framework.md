---
title: "Le programme de résolution et l’infrastructure d’adaptateurs fournisseur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb7ea42e-b32c-40a8-b36b-c349f56f6edd
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b97eec38f868a6d1aa00684d92166bb2759a51d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="the-resolver-and-adapter-provider-framework"></a><span data-ttu-id="e48df-102">Le programme de résolution et l’infrastructure d’adaptateurs fournisseur</span><span class="sxs-lookup"><span data-stu-id="e48df-102">The Resolver and Adapter Provider Framework</span></span>
<span data-ttu-id="e48df-103">Le programme de résolution et l’infrastructure d’adaptateurs fournisseur prend en charge la résolution de point de terminaison, de transformation et d’itinéraire et le routage.</span><span class="sxs-lookup"><span data-stu-id="e48df-103">The Resolver and Adapter Provider Framework supports itinerary, transformation, and endpoint resolution and routing.</span></span> <span data-ttu-id="e48df-104">L’infrastructure peut résoudre les points de terminaison et définir les propriétés de l’adaptateur de sortie dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="e48df-104">The framework can dynamically resolve endpoints and set outbound adapter properties.</span></span> <span data-ttu-id="e48df-105">Après un programme de résolution composant résout un point de terminaison (par exemple, à l’aide de Universal Description, Discovery and Integration [UDDI] pour rechercher un point de terminaison de service Web sortants), un composant du fournisseur d’adaptateur définit des propriétés spécifiques du serveur BizTalk inscrit cartes.</span><span class="sxs-lookup"><span data-stu-id="e48df-105">After a resolver component resolves an endpoint (for example, using Universal Description, Discovery, and Integration [UDDI] to look up an outbound Web service endpoint), an adapter provider component sets specific properties of registered BizTalk Server adapters.</span></span> <span data-ttu-id="e48df-106">Par exemple, le fournisseur de l’adaptateur WCF-BasicHttp est chargé de définir les propriétés de contexte pour le point de terminaison URI qui utilisera l’adaptateur BizTalk spécifique ; le message spécifiques à BizTalk le fournisseur de l’adaptateur FTP est chargé de définir les propriétés spécifiques à l’adaptateur FTP.</span><span class="sxs-lookup"><span data-stu-id="e48df-106">For example, the WCF-BasicHttp adapter provider is responsible for setting the BizTalk-specific message context properties for the endpoint URI that will use the specific BizTalk adapter; the FTP adapter provider is responsible for setting the properties specific to the FTP adapter.</span></span>  
  
 <span data-ttu-id="e48df-107">Un des objectifs de l’infrastructure de fournisseur de carte et de programme de résolution sont prise en charge de résolution et de routage au niveau messagerie, sans exiger l’utilisation des orchestrations BizTalk, ou au niveau de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="e48df-107">One goal of the Resolver and Adapter Provider Framework is to support resolution and routing at either the messaging level, without requiring the use of BizTalk orchestrations, or at the orchestration level.</span></span> <span data-ttu-id="e48df-108">Dans les deux cas, le framework enfichable fournit le développement, le déploiement et l’inscription de nouveaux programmes de résolution et les fournisseurs de carte.</span><span class="sxs-lookup"><span data-stu-id="e48df-108">In both cases, the pluggable framework provides easy development, deployment, and registration of new resolvers and adapter providers.</span></span> <span data-ttu-id="e48df-109">Tous les fournisseurs de carte et les programmes de résolution implémentent des interfaces bien définies et sont chargées à la demande à l’aide de l’inscription dans les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="e48df-109">All resolvers and adapter providers implement well-defined interfaces and are demand-loaded at run time through registration in the configuration files.</span></span>  
  
 <span data-ttu-id="e48df-110">Les composants de pipeline le répartiteur d’ESB et le désassemblage de répartiteur ESB utilisent le programme de résolution et l’infrastructure d’adaptateurs fournisseur en passant la chaîne de connexion à partir de la feuille de route en-tête SOAP ou la configuration de pipeline pour le Gestionnaire de programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="e48df-110">Both the ESB Dispatcher and ESB Dispatcher Disassemble pipeline components use the Resolver and Adapter Provider Framework by passing the connection string from either the itinerary SOAP header or the pipeline configuration to the Resolver Manager.</span></span>  
  
 <span data-ttu-id="e48df-111">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] configuration contient les détails d’inscrits tous les programmes de résolution et les fournisseurs de carte.</span><span class="sxs-lookup"><span data-stu-id="e48df-111">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] configuration contains details of all registered resolvers and adapter providers.</span></span> <span data-ttu-id="e48df-112">Au moment de l’exécution, les gestionnaires de programme de résolution et les gestionnaires d’adaptateur lire les détails des programmes de résolution inscrits et des fournisseurs de carte à partir des fichiers de configuration, charger les assemblys appropriées et les stocker dans un cache de niveau hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e48df-112">At run time, the resolver managers and adapter managers read details of the registered resolvers and adapter providers from the configuration files, load the appropriate assemblies, and store them in a BizTalk host–level cache.</span></span> <span data-ttu-id="e48df-113">Cette technique de mise en cache supprime la nécessité de répétées lors de la lecture des fichiers de configuration et le chargement des assemblys pour chaque message envoyé.</span><span class="sxs-lookup"><span data-stu-id="e48df-113">This caching technique removes the requirement for repeated reading of configuration files and loading of assemblies for every submitted message.</span></span>  
  
 <span data-ttu-id="e48df-114">Pour plus d’informations sur la façon dont le programme de résolution et l’infrastructure d’adaptateurs fournisseur fonctionne et comment vous pouvez l’étendre en créant des programmes de résolution personnalisés et les fournisseurs de carte, consultez [modification et l’extension de BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).</span><span class="sxs-lookup"><span data-stu-id="e48df-114">For more information about how the Resolver and Adapter Provider Framework works and how you can extend it by creating custom resolvers and adapter providers, see [Modifying and Extending the BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).</span></span>  
  
## <a name="supported-resolution-mechanisms-resolvers"></a><span data-ttu-id="e48df-115">Mécanismes de résolution prise en charge (résolution)</span><span class="sxs-lookup"><span data-stu-id="e48df-115">Supported Resolution Mechanisms (Resolvers)</span></span>  
 <span data-ttu-id="e48df-116">BizTalk ESB Toolkit inclut les programmes de résolution suivants : **statique, UDDI, UDDI3, XPATH, BRE, BRI, itinéraire, itinéraire statique** et **LDAP**.</span><span class="sxs-lookup"><span data-stu-id="e48df-116">The BizTalk ESB Toolkit includes the following resolvers: **STATIC, UDDI, UDDI3, XPATH, BRE, BRI, ITINERARY, ITINERARY-STATIC** and **LDAP**.</span></span>  
  
 <span data-ttu-id="e48df-117">Chaîne de connexion d’un programme de résolution est toujours constitué d’un **moniker** (tel que **BRE**) suivi de « :\\\\» et les détails de connexion ou le traitement.</span><span class="sxs-lookup"><span data-stu-id="e48df-117">A resolver's connection string always consists of a **moniker** (such as **BRE**) followed by ":\\\\" and the connection or processing details.</span></span> <span data-ttu-id="e48df-118">Le moniker correspond à la définition de la résolution associée dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e48df-118">The moniker matches the definition of the associated resolver in the configuration file.</span></span> <span data-ttu-id="e48df-119">Les propriétés associées à chaque chaîne de connexion sont uniques, et toutes les propriétés ne sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="e48df-119">The properties associated with each connection string are unique, and not all properties are required.</span></span> <span data-ttu-id="e48df-120">Vous trouverez le schéma pour chacun des programmes de résolution dans l’architecture ESB. Resolvers.Schemas projet.</span><span class="sxs-lookup"><span data-stu-id="e48df-120">The schema for each of the resolvers can be found in the ESB.Resolvers.Schemas project.</span></span>  
  
 <span data-ttu-id="e48df-121">Voici quelques exemples de chaînes de connexion :</span><span class="sxs-lookup"><span data-stu-id="e48df-121">The following are examples of connection strings:</span></span>  
  
-   <span data-ttu-id="e48df-122">**STATIQUE**</span><span class="sxs-lookup"><span data-stu-id="e48df-122">**STATIC**</span></span>  
  
     <span data-ttu-id="e48df-123">STATIQUE :\\\TransportType= ;</span><span class="sxs-lookup"><span data-stu-id="e48df-123">STATIC:\\\TransportType=;</span></span>  
  
     <span data-ttu-id="e48df-124">TransportLocation = http://localhost/ESB.CanadianServices/SubmitPOService.asmx;</span><span class="sxs-lookup"><span data-stu-id="e48df-124">TransportLocation=http://localhost/ESB.CanadianServices/SubmitPOService.asmx;</span></span>  
  
     <span data-ttu-id="e48df-125">Action = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-125">Action=;</span></span>  
  
     <span data-ttu-id="e48df-126">EndPointConfig = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-126">EndPointConfig=;</span></span>  
  
     <span data-ttu-id="e48df-127">JaxRpcResponse = false ;</span><span class="sxs-lookup"><span data-stu-id="e48df-127">JaxRpcResponse=false;</span></span>  
  
     <span data-ttu-id="e48df-128">MessageExchangePattern = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-128">MessageExchangePattern=;</span></span>  
  
     <span data-ttu-id="e48df-129">TargetNamespace = http://globalbank.esb.dynamicresolution.com/canadianservices/;</span><span class="sxs-lookup"><span data-stu-id="e48df-129">TargetNamespace=http://globalbank.esb.dynamicresolution.com/canadianservices/;</span></span>  
  
     <span data-ttu-id="e48df-130">TransformType = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-130">TransformType=;</span></span>  
  
-   <span data-ttu-id="e48df-131">**UDDI**</span><span class="sxs-lookup"><span data-stu-id="e48df-131">**UDDI**</span></span>  
  
     <span data-ttu-id="e48df-132">UDDI :\\\serverUrl= http://localhost : 9901/rmengine ;</span><span class="sxs-lookup"><span data-stu-id="e48df-132">UDDI:\\\serverUrl=http://localhost:9901/rmengine;</span></span>  
  
     <span data-ttu-id="e48df-133">serviceName = OrderPurchaseWebService ;</span><span class="sxs-lookup"><span data-stu-id="e48df-133">serviceName=OrderPurchaseWebService;</span></span>  
  
     <span data-ttu-id="e48df-134">serviceProvider = ESB pratiques de Microsoft</span><span class="sxs-lookup"><span data-stu-id="e48df-134">serviceProvider=Microsoft Practices ESB</span></span>  
  
-   <span data-ttu-id="e48df-135">**XPATH**</span><span class="sxs-lookup"><span data-stu-id="e48df-135">**XPATH**</span></span>  
  
     <span data-ttu-id="e48df-136">\\\TransportType= ;</span><span class="sxs-lookup"><span data-stu-id="e48df-136">\\\TransportType=;</span></span>  
  
     <span data-ttu-id="e48df-137">TransportLocation = /*[local-name () = 'OrderDoc' et namespace-uri() = 'http://globalbank.esb.dynamicresolution.com/northamericanservices/'] /*[local-name () = 'ID' et namespace-uri() = 'http://globalbank.esb.dynamicresolution.com/northamericanservices/'] ;</span><span class="sxs-lookup"><span data-stu-id="e48df-137">TransportLocation=/*[local-name()='OrderDoc' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/']/*[local-name()='ID' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/'];</span></span>  
  
     <span data-ttu-id="e48df-138">Action = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-138">Action=;</span></span>  
  
     <span data-ttu-id="e48df-139">EndPointConfig = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-139">EndPointConfig=;</span></span>  
  
     <span data-ttu-id="e48df-140">JaxRpcResponse = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-140">JaxRpcResponse=;</span></span>  
  
     <span data-ttu-id="e48df-141">MessageExchangePattern = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-141">MessageExchangePattern=;</span></span>  
  
     <span data-ttu-id="e48df-142">TargetNamespace = /*[local-name () = 'OrderDoc' et namespace-uri() = 'http://globalbank.esb.dynamicresolution.com/northamericanservices/'] /*[local-name () = 'customerName' and namespace-uri () ='http : / / globalbank.ESB.dynamicresolution.com/northamericanservices/'] ;</span><span class="sxs-lookup"><span data-stu-id="e48df-142">TargetNamespace=/*[local-name()='OrderDoc' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/']/*[local-name()='customerName' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/'];</span></span>  
  
     <span data-ttu-id="e48df-143">TransformType = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-143">TransformType=;</span></span>  
  
-   <span data-ttu-id="e48df-144">**BRE**</span><span class="sxs-lookup"><span data-stu-id="e48df-144">**BRE**</span></span>  
  
     <span data-ttu-id="e48df-145">BRE :\\\policy=GetCanadaEndPoint ;</span><span class="sxs-lookup"><span data-stu-id="e48df-145">BRE:\\\policy=GetCanadaEndPoint;</span></span>  
  
     <span data-ttu-id="e48df-146">version = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-146">version=;</span></span>  
  
     <span data-ttu-id="e48df-147">useMsg = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-147">useMsg=;</span></span>  
  
-   <span data-ttu-id="e48df-148">**BRI**</span><span class="sxs-lookup"><span data-stu-id="e48df-148">**BRI**</span></span>  
  
     <span data-ttu-id="e48df-149">BRI :\\\policy=ResolveItinerary ;</span><span class="sxs-lookup"><span data-stu-id="e48df-149">BRI:\\\policy=ResolveItinerary;</span></span>  
  
     <span data-ttu-id="e48df-150">version = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-150">version=;</span></span>  
  
     <span data-ttu-id="e48df-151">useMsg = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-151">useMsg=;</span></span>  
  
-   <span data-ttu-id="e48df-152">**FEUILLE DE ROUTE**</span><span class="sxs-lookup"><span data-stu-id="e48df-152">**ITINERARY**</span></span>  
  
     <span data-ttu-id="e48df-153">ITINÉRAIRE :\\\name=TwoWayTestItinerary ;</span><span class="sxs-lookup"><span data-stu-id="e48df-153">ITINERARY:\\\name=TwoWayTestItinerary;</span></span>  
  
     <span data-ttu-id="e48df-154">version = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-154">version=;</span></span>  
  
-   <span data-ttu-id="e48df-155">**ITINÉRAIRE STATIQUE**</span><span class="sxs-lookup"><span data-stu-id="e48df-155">**ITINERARY-STATIC**</span></span>  
  
     <span data-ttu-id="e48df-156">ITINÉRAIRE statique :\\\name=TwoWayTestItinerary ;</span><span class="sxs-lookup"><span data-stu-id="e48df-156">ITINERARY-STATIC:\\\name=TwoWayTestItinerary;</span></span>  
  
     <span data-ttu-id="e48df-157">version = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-157">version=;</span></span>  
  
-   <span data-ttu-id="e48df-158">**LDAP**</span><span class="sxs-lookup"><span data-stu-id="e48df-158">**LDAP**</span></span>  
  
     <span data-ttu-id="e48df-159">LDAP :\\\TransportType=SMTP ;</span><span class="sxs-lookup"><span data-stu-id="e48df-159">LDAP:\\\TransportType=SMTP;</span></span>  
  
     <span data-ttu-id="e48df-160">TransportLocation = {message}</span><span class="sxs-lookup"><span data-stu-id="e48df-160">TransportLocation={mail}</span></span>  
  
     <span data-ttu-id="e48df-161">Filtre = (&amp;(objectClass = User) (&#124; (userPrincipalName =yourname@domain.com))) ;</span><span class="sxs-lookup"><span data-stu-id="e48df-161">Filter=(&amp;(objectClass=User)(&#124;(userPrincipalName=yourname@domain.com)));</span></span>  
  
     <span data-ttu-id="e48df-162">SearchRoot = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-162">SearchRoot=;</span></span>  
  
     <span data-ttu-id="e48df-163">SearchScope = sous-arborescence ;</span><span class="sxs-lookup"><span data-stu-id="e48df-163">SearchScope=Subtree;</span></span>  
  
     <span data-ttu-id="e48df-164">EndpointConfig = Subject = Message de Test d’itinéraire à la messagerie de {}&amp;</span><span class="sxs-lookup"><span data-stu-id="e48df-164">EndpointConfig=Subject=Itinerary Test Message to {mail}&amp;</span></span>  
  
     <span data-ttu-id="e48df-165">SMTPAuthenticate = 0&amp;</span><span class="sxs-lookup"><span data-stu-id="e48df-165">SMTPAuthenticate=0&amp;</span></span>  
  
     <span data-ttu-id="e48df-166">SMTPHost = 127.0.0.1&amp;</span><span class="sxs-lookup"><span data-stu-id="e48df-166">SMTPHost=127.0.0.1&amp;</span></span>  
  
     <span data-ttu-id="e48df-167">FROM =test@globalbank.com&amp;</span><span class="sxs-lookup"><span data-stu-id="e48df-167">From=test@globalbank.com&amp;</span></span>  
  
     <span data-ttu-id="e48df-168">DeliveryReceipt = false&amp;</span><span class="sxs-lookup"><span data-stu-id="e48df-168">DeliveryReceipt=false&amp;</span></span>  
  
     <span data-ttu-id="e48df-169">MessagePartsAttachments = 0&amp;</span><span class="sxs-lookup"><span data-stu-id="e48df-169">MessagePartsAttachments=0&amp;</span></span>  
  
     <span data-ttu-id="e48df-170">ReadReceipt = false ;</span><span class="sxs-lookup"><span data-stu-id="e48df-170">ReadReceipt=false;</span></span>  
  
     <span data-ttu-id="e48df-171">ThrowErrorIfNotFound = false ;</span><span class="sxs-lookup"><span data-stu-id="e48df-171">ThrowErrorIfNotFound=false;</span></span>  
  
     <span data-ttu-id="e48df-172">Action = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-172">Action=;</span></span>  
  
     <span data-ttu-id="e48df-173">JaxRpcResponse = false ;</span><span class="sxs-lookup"><span data-stu-id="e48df-173">JaxRpcResponse=false;</span></span>  
  
     <span data-ttu-id="e48df-174">MessageExchangePattern = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-174">MessageExchangePattern=;</span></span>  
  
     <span data-ttu-id="e48df-175">TargetNamespace = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-175">TargetNamespace=;</span></span>  
  
     <span data-ttu-id="e48df-176">TransformType = ;</span><span class="sxs-lookup"><span data-stu-id="e48df-176">TransformType=;</span></span>  
  
 <span data-ttu-id="e48df-177">Pas de tous les attributs dans la chaîne de connexion sont obligatoires.</span><span class="sxs-lookup"><span data-stu-id="e48df-177">Not all attributes in the connection string are mandatory.</span></span> <span data-ttu-id="e48df-178">En outre, **EndPointConfig** est un attribut spécial qui n’importe quel programme de résolution peut remplir et retourner.</span><span class="sxs-lookup"><span data-stu-id="e48df-178">In addition, **EndPointConfig** is a special attribute that any resolver can populate and return.</span></span> <span data-ttu-id="e48df-179">Si vous le souhaitez, le programme de résolution peut stocker les paires nom/valeur qui correspondent aux propriétés de contexte de l’adaptateur BizTalk spécifiques, lequel il peut, à son tour, écrire dans le contexte du message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e48df-179">Optionally, the resolver can store the name/value pairs that correspond to specific BizTalk Adapter Context properties, which it can, in turn, write to the context of the BizTalk message.</span></span>  
  
 <span data-ttu-id="e48df-180">Dans ce cas, le **ResolverDictionary** instance qui contient toutes les propriétés résolues retourné par le processus de résolution, puis passe au gestionnaire d’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="e48df-180">In this case, the **ResolverDictionary** instance that contains all the resolved properties returned from the resolution process then passes to the adapter manager.</span></span> <span data-ttu-id="e48df-181">Le Gestionnaire d’adaptateur transmet le dictionnaire pour le fournisseur de l’adaptateur spécifique qui définira le contexte de BizTalk spécifique à l’adaptateur et le point de terminaison spécifique de propriétés du message.</span><span class="sxs-lookup"><span data-stu-id="e48df-181">The adapter manager passes the dictionary to the specific adapter provider that will set all the adapter-specific and endpoint-specific BizTalk Context properties for the message.</span></span> <span data-ttu-id="e48df-182">Rechercher les programmes de résolution le **EndPointConfig** propriété, extraire les paires nom/valeur qui correspondent à leurs propriétés respectives de carte, puis définissez ces valeurs sur le message.</span><span class="sxs-lookup"><span data-stu-id="e48df-182">The resolvers look for the **EndPointConfig** property, extract the name/value pairs that correspond to their respective adapter properties, and then set these values on the message.</span></span>  
  
## <a name="supported-adapter-providers"></a><span data-ttu-id="e48df-183">Fournisseurs de carte pris en charge</span><span class="sxs-lookup"><span data-stu-id="e48df-183">Supported Adapter Providers</span></span>  
 <span data-ttu-id="e48df-184">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut les fournisseurs de carte intégrés suivants : **fichier, FTP, SMTP, MQSeries, WCF-BasicHttp, WCF-WSHttp,** et **WCF-Custom**.</span><span class="sxs-lookup"><span data-stu-id="e48df-184">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes the following built-in adapter providers: **FILE, FTP, SMTP,MQSeries, WCF-BasicHttp, WCF-WSHttp,** and **WCF-Custom**.</span></span> <span data-ttu-id="e48df-185">Le nom de chaque fournisseur de l’adaptateur est identique au nom de la carte associée (type de transport) dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e48df-185">The name of each adapter provider is identical to the name of the associated adapter (transport type) in BizTalk Server.</span></span>  
  
 <span data-ttu-id="e48df-186">Un avantage majeur de l’infrastructure de fournisseur de carte et de programme de résolution est que vous pouvez l’étendre en créant et en enregistrant vos propres programmes de résolution personnalisés pour résoudre les informations de point de terminaison et les fournisseurs d’adaptateur personnalisé pour définir des propriétés spécifiques d’adaptateurs BizTalk inscrits.</span><span class="sxs-lookup"><span data-stu-id="e48df-186">A major advantage of the Resolver and Adapter Provider Framework is that you can extend it by creating and registering your own custom resolvers to resolve endpoint information and custom adapter providers to set specific properties of registered BizTalk adapters.</span></span> <span data-ttu-id="e48df-187">Pour plus d’informations, consultez [modification et l’extension de BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).</span><span class="sxs-lookup"><span data-stu-id="e48df-187">For more information, see [Modifying and Extending the BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).</span></span>