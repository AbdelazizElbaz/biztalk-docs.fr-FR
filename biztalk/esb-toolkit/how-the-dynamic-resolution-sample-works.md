---
title: Fonctionne de l’exemple de résolution dynamique | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7789316d-f2c4-4018-a8e8-dd9359f1664f
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe7d7b473482c432c8e3ae9ca48cab414a9e9573
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="how-the-dynamic-resolution-sample-works"></a><span data-ttu-id="9f873-102">Fonctionne de l’exemple de résolution dynamique</span><span class="sxs-lookup"><span data-stu-id="9f873-102">How the Dynamic Resolution Sample Works</span></span>
<span data-ttu-id="9f873-103">L’exemple de résolution dynamique utilise le composant de pipeline désassembleur de répartiteur ESB pour tous les exemples de messagerie décrits dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="9f873-103">The Dynamic Resolution sample uses the ESB Dispatcher Disassembler pipeline component for all the messaging examples described in the previous section.</span></span>  
  
 <span data-ttu-id="9f873-104">Pour les scénarios de messagerie unidirectionnels, l’exemple résout le point de terminaison à l’aide de la méthode statique, BRE ou programme de résolution de XPATH et transmet les requêtes du protocole de fichier au fichier, FTP ou MQSeries.</span><span class="sxs-lookup"><span data-stu-id="9f873-104">For one-way messaging scenarios, the example resolves the endpoint using the STATIC, BRE, or XPATH Resolver and brokers the protocol from FILE to FILE, FTP, or MQSeries.</span></span>  
  
 <span data-ttu-id="9f873-105">Pour les scénarios de messagerie bidirectionnelles, l’exemple résout le point de terminaison à l’aide de la méthode statique, BRE, UDDI ou programme de résolution de XPATH et transmet les requêtes du protocole SOAP à partir de SOAP ou WCF-BasicHttp.</span><span class="sxs-lookup"><span data-stu-id="9f873-105">For two-way messaging scenarios, the example resolves the endpoint using the STATIC, BRE, UDDI, or XPATH Resolver and brokers the protocol from SOAP to either SOAP or WCF-BasicHttp.</span></span> <span data-ttu-id="9f873-106">En outre, les exemples résoudre et exécutent des mappages de Microsoft BizTalk à l’aide du résolveur BRE, qui utilise des faits contenues dans les propriétés de contexte de message et le corps du message pour déterminer le résultat de la résolution.</span><span class="sxs-lookup"><span data-stu-id="9f873-106">In addition, the examples resolve and execute Microsoft BizTalk maps using the BRE Resolver, which uses facts contained in the message context properties and the message body to determine the resolution result.</span></span>  
  
 <span data-ttu-id="9f873-107">Le résultat du processus de résolution est que tous les exemples bidirectionnelles envoyer son message à l’architecture ESB. Service Web de CanadianServices à http://localhost/ESB.CanadianServices/SubmitPOService.asmx.</span><span class="sxs-lookup"><span data-stu-id="9f873-107">The result of the resolution process is that all the two-way examples submit their message to the ESB.CanadianServices Web service located at http://localhost/ESB.CanadianServices/SubmitPOService.asmx.</span></span> <span data-ttu-id="9f873-108">En outre, en fonction du résultat de la résolution, l’exemple exécute la **submitOrder** ou **submitPurchase** action.</span><span class="sxs-lookup"><span data-stu-id="9f873-108">In addition, depending on the resolution result, the example executes either the **submitOrder** or the **submitPurchase** action.</span></span> <span data-ttu-id="9f873-109">En outre, le composant de pipeline désassembleur de répartiteur ESB exécute dynamiquement un mappage BizTalk, selon le texte spécifié ou l’action exécutée.</span><span class="sxs-lookup"><span data-stu-id="9f873-109">Additionally, the ESB Dispatcher Disassembler pipeline component dynamically executes a BizTalk map, depending on the specified or the resolved action.</span></span>  
  
 <span data-ttu-id="9f873-110">La figure 1 illustre que les pipelines configurés pour le DynamicResolutionReqResp_SOAP l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="9f873-110">Figure 1 shows the configured pipelines for the DynamicResolutionReqResp_SOAP receive location.</span></span>  
  
 <span data-ttu-id="9f873-111">![Pipelines de résolution dynamique](../esb-toolkit/media/ch6-dynamicresolutionpipelines.gif "§ 6-DynamicResolutionPipelines")</span><span class="sxs-lookup"><span data-stu-id="9f873-111">![Dynamic Resolution Pipelines](../esb-toolkit/media/ch6-dynamicresolutionpipelines.gif "Ch6-DynamicResolutionPipelines")</span></span>  
  
 <span data-ttu-id="9f873-112">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="9f873-112">**Figure 1**</span></span>  
  
 <span data-ttu-id="9f873-113">**Les pipelines configurées de la DynamicResolutionReqResp_SOAP réception de l’application d’exemple de résolution dynamique**</span><span class="sxs-lookup"><span data-stu-id="9f873-113">**The configured pipelines of the DynamicResolutionReqResp_SOAP receive location of the Dynamic Resolution sample application**</span></span>  
  
 <span data-ttu-id="9f873-114">La figure 2 illustre les propriétés de chaque instance du composant ESBReceiveXML qui utilise le désassembleur de répartiteur ESB.</span><span class="sxs-lookup"><span data-stu-id="9f873-114">Figure 2 shows the per-instance properties of the ESBReceiveXML component that uses the ESB Dispatcher Disassembler.</span></span>  
  
 <span data-ttu-id="9f873-115">![Résolution dynamique de réception XML](../esb-toolkit/media/ch6-dynamicresolutionreceivexml.gif "§ 6-DynamicResolutionReceiveXML")</span><span class="sxs-lookup"><span data-stu-id="9f873-115">![Dynamic Resolution Receive XML](../esb-toolkit/media/ch6-dynamicresolutionreceivexml.gif "Ch6-DynamicResolutionReceiveXML")</span></span>  
  
 <span data-ttu-id="9f873-116">**Figure 2**</span><span class="sxs-lookup"><span data-stu-id="9f873-116">**Figure 2**</span></span>  
  
 <span data-ttu-id="9f873-117">**Les propriétés de chaque instance pour les composants dans le pipeline ESBReceiveXML de l’application d’exemple de résolution dynamique**</span><span class="sxs-lookup"><span data-stu-id="9f873-117">**The per-instance properties for the components in the ESBReceiveXML pipeline of the Dynamic Resolution sample application**</span></span>  
  
 <span data-ttu-id="9f873-118">Les propriétés suivantes sont présentées dans la Figure 2 :</span><span class="sxs-lookup"><span data-stu-id="9f873-118">The following properties are shown in Figure 2:</span></span>  
  
-   <span data-ttu-id="9f873-119">**Activé**.</span><span class="sxs-lookup"><span data-stu-id="9f873-119">**Enabled**.</span></span> <span data-ttu-id="9f873-120">Cette propriété détermine si le pipeline est actif.</span><span class="sxs-lookup"><span data-stu-id="9f873-120">This property determines whether the pipeline is active.</span></span> <span data-ttu-id="9f873-121">Si la valeur est **False**, messages passent sans traitement.</span><span class="sxs-lookup"><span data-stu-id="9f873-121">If this is set to **False**, messages pass through without processing.</span></span>  
  
-   <span data-ttu-id="9f873-122">**Point de terminaison**.</span><span class="sxs-lookup"><span data-stu-id="9f873-122">**Endpoint**.</span></span> <span data-ttu-id="9f873-123">Cette propriété est la chaîne de connexion utilisée pour déterminer le programme de résolution à charger, et spécifie la configuration de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="9f873-123">This property is the connection string used to determine which resolver to load, and it specifies the endpoint configuration.</span></span>  
  
-   <span data-ttu-id="9f873-124">**MapName**.</span><span class="sxs-lookup"><span data-stu-id="9f873-124">**MapName**.</span></span> <span data-ttu-id="9f873-125">Cette propriété est la chaîne de connexion utilisée pour déterminer le programme de résolution pour charger et le mappage BizTalk à exécuter.</span><span class="sxs-lookup"><span data-stu-id="9f873-125">This property is the connection string used to determine which resolver to load and which BizTalk map to execute.</span></span> <span data-ttu-id="9f873-126">Il peut être le nom qualifié complet d’un mappage au lieu d’une chaîne de connexion du programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="9f873-126">It can be the fully qualified name of a map instead of a resolver connection string.</span></span>  
  
-   <span data-ttu-id="9f873-127">**Valider**.</span><span class="sxs-lookup"><span data-stu-id="9f873-127">**Validate**.</span></span> <span data-ttu-id="9f873-128">Lorsque la valeur **True** (paramètre par défaut), le désassembleur de répartiteur ESB composant fait en sorte que le service de Transformation d’ESB pour valider le message source par rapport au schéma source défini dans le plan est résoudre et les exécuter.</span><span class="sxs-lookup"><span data-stu-id="9f873-128">When set to **True** (the default setting), the ESB Dispatcher Disassembler component instructs the ESB Transformation service to validate the source message against the source schema defined in the map that is will resolve and execute.</span></span>  
  
 <span data-ttu-id="9f873-129">Figure 3 illustre les propriétés de chaque instance du composant ESBSendPassthrough qui utilise le répartiteur ESB.</span><span class="sxs-lookup"><span data-stu-id="9f873-129">Figure 3 shows the per-instance properties of the ESBSendPassthrough component that uses the ESB Dispatcher.</span></span>  
  
 <span data-ttu-id="9f873-130">![Résolution dynamique d’envoi Passthrough](../esb-toolkit/media/ch6-dynamicresolutionsendpassthrough.gif "§ 6-DynamicResolutionSendPassthrough")</span><span class="sxs-lookup"><span data-stu-id="9f873-130">![Dynamic Resolution Send Passthrough](../esb-toolkit/media/ch6-dynamicresolutionsendpassthrough.gif "Ch6-DynamicResolutionSendPassthrough")</span></span>  
  
 <span data-ttu-id="9f873-131">**Figure 3**</span><span class="sxs-lookup"><span data-stu-id="9f873-131">**Figure 3**</span></span>  
  
 <span data-ttu-id="9f873-132">**Les propriétés de chaque instance pour les composants dans le pipeline ESBSendPassthrough de l’application d’exemple de résolution dynamique**</span><span class="sxs-lookup"><span data-stu-id="9f873-132">**The per-instance properties for the components in the ESBSendPassthrough pipeline of the Dynamic Resolution sample application**</span></span>  
  
 <span data-ttu-id="9f873-133">Les propriétés suivantes sont présentées dans la Figure 3 :</span><span class="sxs-lookup"><span data-stu-id="9f873-133">The following properties are shown in Figure 3:</span></span>  
  
-   <span data-ttu-id="9f873-134">**Activé**.</span><span class="sxs-lookup"><span data-stu-id="9f873-134">**Enabled**.</span></span> <span data-ttu-id="9f873-135">Cette propriété détermine si le pipeline est actif.</span><span class="sxs-lookup"><span data-stu-id="9f873-135">This property determines whether the pipeline is active.</span></span> <span data-ttu-id="9f873-136">Si la valeur est **False**, messages passent sans traitement.</span><span class="sxs-lookup"><span data-stu-id="9f873-136">If this is set to **False**, messages pass through without processing.</span></span>  
  
-   <span data-ttu-id="9f873-137">**Point de terminaison**.</span><span class="sxs-lookup"><span data-stu-id="9f873-137">**Endpoint**.</span></span> <span data-ttu-id="9f873-138">Cette propriété est la chaîne de connexion utilisée pour déterminer le programme de résolution de chargement et la configuration de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="9f873-138">This property is the connection string used to determine which resolver to load and the end-point configuration.</span></span>  
  
-   <span data-ttu-id="9f873-139">**MapName**.</span><span class="sxs-lookup"><span data-stu-id="9f873-139">**MapName**.</span></span> <span data-ttu-id="9f873-140">Cette propriété est la chaîne de connexion utilisée pour déterminer le programme de résolution pour charger et le mappage BizTalk à exécuter.</span><span class="sxs-lookup"><span data-stu-id="9f873-140">This property is the connection string used to determine which resolver to load and which BizTalk map to execute.</span></span> <span data-ttu-id="9f873-141">Un nom qualifié complet d’un mappage peut être utilisé à la place la chaîne de connexion d’un programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="9f873-141">A fully qualified name of a map can be used in place of a resolver's connection string.</span></span>  
  
-   <span data-ttu-id="9f873-142">**Valider**.</span><span class="sxs-lookup"><span data-stu-id="9f873-142">**Validate**.</span></span> <span data-ttu-id="9f873-143">Lorsque la valeur **True** (paramètre par défaut), le désassembleur de répartiteur ESB composant fait en sorte que le service de Transformation d’ESB pour valider le message source par rapport au schéma source défini dans le plan est résoudre et les exécuter.</span><span class="sxs-lookup"><span data-stu-id="9f873-143">When set to **True** (the default setting), the ESB Dispatcher Disassembler component instructs the ESB Transformation service to validate the source message against the source schema defined in the map that is will resolve and execute.</span></span>