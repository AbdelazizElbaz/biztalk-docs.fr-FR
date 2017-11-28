---
title: "Créer des artefacts de l’envoi d’adaptateur TIBCO Rendezvous | Documents Microsoft"
description: "Créer un port d’envoi, de configurer les propriétés de transport pour envoyer des messages à TIBCO Rendezvous à partir de BizTalk"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad996c4f-e6ed-4582-a768-0cb1ad25b1d8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed6d03885423582c2657c9cb624c63f26ce1c6f3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="create-tibco-rendezvous-send-handlers"></a><span data-ttu-id="d6e77-103">Créer des gestionnaires d’envoi TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="d6e77-103">Create TIBCO Rendezvous Send Handlers</span></span>
<span data-ttu-id="d6e77-104">Cette section décrit la création d'un schéma pour utiliser TIBCO Rendezvous dans une orchestration BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d6e77-104">This section explains how to create a schema to use TIBCO Rendezvous in a BizTalk Server orchestration.</span></span>  
  
## <a name="create-a-send-port"></a><span data-ttu-id="d6e77-105">Créer un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="d6e77-105">Create a send port</span></span>
  
1.  <span data-ttu-id="d6e77-106">Dans **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez votre application.</span><span class="sxs-lookup"><span data-stu-id="d6e77-106">In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand your application.</span></span>  
  
2.  <span data-ttu-id="d6e77-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="d6e77-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="d6e77-108">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d6e77-108">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="d6e77-109">Tapez un nom pour le port d’envoi, par exemple, `SendToTIBCORV`.</span><span class="sxs-lookup"><span data-stu-id="d6e77-109">Type a name for the send port, for example, `SendToTIBCORV`.</span></span>  
  
    2.  <span data-ttu-id="d6e77-110">À partir de la **Type** la liste déroulante, sélectionnez **TIBCO Rendezvous**.</span><span class="sxs-lookup"><span data-stu-id="d6e77-110">From the **Type** drop-down list, select **TIBCO Rendezvous**.</span></span>  
  
    3.  <span data-ttu-id="d6e77-111">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="d6e77-111">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="d6e77-112">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="d6e77-112">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  <span data-ttu-id="d6e77-113">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="d6e77-113">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  

        > [!NOTE]
        > <span data-ttu-id="d6e77-114">L’adaptateur Microsoft BizTalk pour TIBCO Rendezvous requiert que vous sélectionnez pipeline XMLTransmit pour l’envoi et le pipeline XMLReceive de réception.</span><span class="sxs-lookup"><span data-stu-id="d6e77-114">Microsoft BizTalk Adapter for TIBCO Rendezvous requires that you select XMLTransmit pipeline for send, and XMLReceive pipeline for receive.</span></span>
        
    6.  <span data-ttu-id="d6e77-115">Cliquez sur **configurer** pour configurer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="d6e77-115">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="d6e77-116">Dans le **propriétés du Transport TIBCO Rendezvous** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d6e77-116">In the **TIBCO Rendezvous Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="d6e77-117">Saisissez les propriétés.</span><span class="sxs-lookup"><span data-stu-id="d6e77-117">Enter the properties.</span></span>  
  
         <span data-ttu-id="d6e77-118">Il n'est pas nécessaire de définir les informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="d6e77-118">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="d6e77-119">Dans la liste, sélectionnez l'application SSO associée que vous avez créée pour représenter le système TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="d6e77-119">In the list, select the SSO affiliate application you created to represent the TIBCO Rendezvous system.</span></span>  
  
    3.  <span data-ttu-id="d6e77-120">Pour **utiliser SSO**, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="d6e77-120">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="d6e77-121">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d6e77-121">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="d6e77-122">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d6e77-122">Click **OK**.</span></span>  

## <a name="set-the-transport-properties"></a><span data-ttu-id="d6e77-123">Définir les propriétés de transport</span><span class="sxs-lookup"><span data-stu-id="d6e77-123">Set the transport properties</span></span>
<span data-ttu-id="d6e77-124">La boîte de dialogue Propriétés du transport TIBCO Rendezvous est utilisée pour l'exécution.</span><span class="sxs-lookup"><span data-stu-id="d6e77-124">The TIBCO Rendezvous Transport property is used for run time.</span></span> <span data-ttu-id="d6e77-125">Dans le **propriétés du Transport**, vous définissez les paramètres de connexion qui identifient le domaine TIBCO Rendezvous où vous souhaitez publier les messages générés.</span><span class="sxs-lookup"><span data-stu-id="d6e77-125">In the **Transport Properties**, you set the connection parameters that identify the TIBCO Rendezvous domain where you want to publish the generated messages.</span></span>  
  
 
1.  <span data-ttu-id="d6e77-126">Sur le **propriétés du Transport TIBCO Rendezvous** écran, développez **propriétés d’expéditeur certifié** et entrez les informations suivantes.</span><span class="sxs-lookup"><span data-stu-id="d6e77-126">On the **TIBCO Rendezvous Transport Properties** screen, expand **Certified Sender Properties** and enter the following information.</span></span>  
  
     ![](../core/media/sadp-tibcoren-transs.gif "SAdp_TibcoRen_Transs")  
  
    |<span data-ttu-id="d6e77-127">Utiliser</span><span class="sxs-lookup"><span data-stu-id="d6e77-127">Use this</span></span>|<span data-ttu-id="d6e77-128">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="d6e77-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d6e77-129">**Nom de comptabilité**</span><span class="sxs-lookup"><span data-stu-id="d6e77-129">**Ledger name**</span></span>|<span data-ttu-id="d6e77-130">Par défaut, cette option n'est pas renseignée.</span><span class="sxs-lookup"><span data-stu-id="d6e77-130">Default value is blank.</span></span> <span data-ttu-id="d6e77-131">Nom du fichier de comptabilité à utiliser pour la remise des messages certifiés persistants.</span><span class="sxs-lookup"><span data-stu-id="d6e77-131">Ledger file name to use for persistent certified message delivery.</span></span> <span data-ttu-id="d6e77-132">Utilisez des lecteurs locaux uniquement.</span><span class="sxs-lookup"><span data-stu-id="d6e77-132">Use local drives only.</span></span>|  
    |<span data-ttu-id="d6e77-133">**Nom réutilisable**</span><span class="sxs-lookup"><span data-stu-id="d6e77-133">**Reusable name**</span></span>|<span data-ttu-id="d6e77-134">Par défaut, cette option n'est pas renseignée.</span><span class="sxs-lookup"><span data-stu-id="d6e77-134">Default value is blank.</span></span> <span data-ttu-id="d6e77-135">Nom de destinataire réutilisable à utiliser pour la remise des messages certifiés.</span><span class="sxs-lookup"><span data-stu-id="d6e77-135">Reusable correspondent name to use for certified message delivery.</span></span> <span data-ttu-id="d6e77-136">Le nom doit être unique parmi les noms de destinataires de messages certifiés sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="d6e77-136">The name must be unique among all certified message correspondent names on the network.</span></span>|  
  
2.  <span data-ttu-id="d6e77-137">Développez **informations d’identification** et entrez les informations suivantes pour la connexion au serveur.</span><span class="sxs-lookup"><span data-stu-id="d6e77-137">Expand **Credentials** and enter the following information for connection to the server.</span></span>  
  
    |<span data-ttu-id="d6e77-138">Utiliser</span><span class="sxs-lookup"><span data-stu-id="d6e77-138">Use this</span></span>|<span data-ttu-id="d6e77-139">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="d6e77-139">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d6e77-140">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="d6e77-140">**Password**</span></span>|<span data-ttu-id="d6e77-141">Par défaut, cette option n'est pas renseignée.</span><span class="sxs-lookup"><span data-stu-id="d6e77-141">Default value is blank.</span></span> <span data-ttu-id="d6e77-142">Mot de passe de connexion à un démon TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="d6e77-142">Password for login to a Tibco Rendezvous daemon.</span></span>|  
    |<span data-ttu-id="d6e77-143">**Nom d'utilisateur**</span><span class="sxs-lookup"><span data-stu-id="d6e77-143">**User name**</span></span>|<span data-ttu-id="d6e77-144">Par défaut, cette option n'est pas renseignée.</span><span class="sxs-lookup"><span data-stu-id="d6e77-144">Default value is blank.</span></span> <span data-ttu-id="d6e77-145">Nom d'utilisateur du démon TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="d6e77-145">User name for Tibco Rendezvous daemon.</span></span>|  
  
3.  <span data-ttu-id="d6e77-146">Développez **paramètres généraux** et entrez les informations suivantes pour la connexion au serveur TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="d6e77-146">Expand **General Settings** and enter the following information for connection to the TIBCO Rendezvous server.</span></span>  
  
    |<span data-ttu-id="d6e77-147">Utiliser</span><span class="sxs-lookup"><span data-stu-id="d6e77-147">Use this</span></span>|<span data-ttu-id="d6e77-148">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="d6e77-148">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d6e77-149">**Numéro de Page de codes**</span><span class="sxs-lookup"><span data-stu-id="d6e77-149">**Code Page Number**</span></span>|<span data-ttu-id="d6e77-150">La valeur par défaut est 65001 (page de code du codage UTF-8).</span><span class="sxs-lookup"><span data-stu-id="d6e77-150">Default value is 65001 (code page for UTF-8 encoding).</span></span> <span data-ttu-id="d6e77-151">Il s'agit de la page de codes qu'utilise le Kit de développement logiciel (SDK) TIBCO Rendezvous pour le codage des chaînes.</span><span class="sxs-lookup"><span data-stu-id="d6e77-151">This is the code page that the TIBCO Rendezvous SDK uses for String encoding.</span></span>|  
    |<span data-ttu-id="d6e77-152">**Nom de l’objet par défaut**</span><span class="sxs-lookup"><span data-stu-id="d6e77-152">**Default Subject Name**</span></span>|<span data-ttu-id="d6e77-153">Valeur par défaut est vide.</span><span class="sxs-lookup"><span data-stu-id="d6e77-153">Default is empty.</span></span> <span data-ttu-id="d6e77-154">Le nom du sujet est défini dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="d6e77-154">The subject name is set in the orchestration.</span></span> <span data-ttu-id="d6e77-155">Si un port est utilisé pour un type de message, vous pouvez fournir un nom de sujet par défaut et indiquer simplement les orchestrations en évitant d'avoir à définir la propriété Nom du sujet.</span><span class="sxs-lookup"><span data-stu-id="d6e77-155">If a port is used for one message type, you can provide a default subject name, and you can simplify orchestrations by removing the need to set the Subject name property.</span></span>|  
    |<span data-ttu-id="d6e77-156">**Activer l’heure par lot**</span><span class="sxs-lookup"><span data-stu-id="d6e77-156">**Enable Time Batch**</span></span>|<span data-ttu-id="d6e77-157">La valeur par défaut est False.</span><span class="sxs-lookup"><span data-stu-id="d6e77-157">Default value is False.</span></span> <span data-ttu-id="d6e77-158">Fonctionnalité Activer/Désactiver l'heure par lot TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="d6e77-158">Enable/Disable TIBCO Rendezvous Time Batch feature.</span></span>|  
    |<span data-ttu-id="d6e77-159">**Mapper les types non pris en charge à la chaîne**</span><span class="sxs-lookup"><span data-stu-id="d6e77-159">**Map Unsupported types to string**</span></span>|<span data-ttu-id="d6e77-160">Valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="d6e77-160">Default value is True.</span></span> <span data-ttu-id="d6e77-161">Si la valeur est True, les types non pris en charge sont mappés si possible.</span><span class="sxs-lookup"><span data-stu-id="d6e77-161">If true, unsupported types are mapped to string if it is possible.</span></span> <span data-ttu-id="d6e77-162">Si la valeur est False, une erreur d'exécution est générée.</span><span class="sxs-lookup"><span data-stu-id="d6e77-162">If False, a run-time error is generated.</span></span>|  
    |<span data-ttu-id="d6e77-163">**Chemin d’accès aux données binaires, tels que les assemblys TIBCO Rendezvous**</span><span class="sxs-lookup"><span data-stu-id="d6e77-163">**Path to Binaries, such as TIBCO Rendezvous assemblies**</span></span>|<span data-ttu-id="d6e77-164">Fournissez ces informations si elles ne figurent pas dans la variable d'environnement PATH.</span><span class="sxs-lookup"><span data-stu-id="d6e77-164">Provide this information if it is not already in the PATH environment variable.</span></span>|  
    |<span data-ttu-id="d6e77-165">**Préserver l’ordre**</span><span class="sxs-lookup"><span data-stu-id="d6e77-165">**Preserver Order**</span></span>|<span data-ttu-id="d6e77-166">Valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="d6e77-166">Default value is True.</span></span> <span data-ttu-id="d6e77-167">Active la logique d'envoi de messages à TIBCO Rendezvous dans l'ordre dans lequel ils ont été reçus de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d6e77-167">Enables logic to send messages to TIBCO Rendezvous in the same order they were received from BizTalk Server.</span></span> <span data-ttu-id="d6e77-168">Ce paramètre force la publication des messages dans le même ordre, mais il ne signifie pas que les abonnés les reçoivent dans ce même ordre.</span><span class="sxs-lookup"><span data-stu-id="d6e77-168">This parameter forces publishing in the same order; it does not mean that subscribers receive them in the same order.</span></span>|  
    |<span data-ttu-id="d6e77-169">**Identificateur de Port d’envoi**</span><span class="sxs-lookup"><span data-stu-id="d6e77-169">**Send Port Identifier**</span></span>|<span data-ttu-id="d6e77-170">Cet identificateur apparaît dans les messages de journal associés à ce port.</span><span class="sxs-lookup"><span data-stu-id="d6e77-170">This identifier appears in log messages associated with this port.</span></span> <span data-ttu-id="d6e77-171">Il est fourni à titre informatif.</span><span class="sxs-lookup"><span data-stu-id="d6e77-171">It is provided as a convenience.</span></span>|  
  
4.  <span data-ttu-id="d6e77-172">Développez **Transport Rendezvous** et entrez les informations de connexion au serveur TIBCO Rendezvous, cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d6e77-172">Expand **Rendezvous Transport** and enter the information for connection to the TIBCO Rendezvous server, click **Apply**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d6e77-173">Vous devez définir les paramètres de connexion de l'adaptateur Microsoft BizTalk pour accéder à TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="d6e77-173">You must set connection parameters for Microsoft BizTalk Adapter for TIBCO Rendezvous to access TIBCO Rendezvous.</span></span>  
  
    |<span data-ttu-id="d6e77-174">Utiliser</span><span class="sxs-lookup"><span data-stu-id="d6e77-174">Use this</span></span>|<span data-ttu-id="d6e77-175">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="d6e77-175">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d6e77-176">**Démon**</span><span class="sxs-lookup"><span data-stu-id="d6e77-176">**Daemon**</span></span>|<span data-ttu-id="d6e77-177">Valeur par défaut est vide.</span><span class="sxs-lookup"><span data-stu-id="d6e77-177">Default is empty.</span></span><br /><br /> <span data-ttu-id="d6e77-178">Paramètre Daemon du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="d6e77-178">Rendezvous Transport Daemon parameter.</span></span>|  
    |<span data-ttu-id="d6e77-179">**Réseau**</span><span class="sxs-lookup"><span data-stu-id="d6e77-179">**Network**</span></span>|<span data-ttu-id="d6e77-180">Valeur par défaut est vide.</span><span class="sxs-lookup"><span data-stu-id="d6e77-180">Default is empty.</span></span><br /><br /> <span data-ttu-id="d6e77-181">Paramètre Réseau du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="d6e77-181">Rendezvous Transport Network parameter.</span></span>|  
    |<span data-ttu-id="d6e77-182">**Service**</span><span class="sxs-lookup"><span data-stu-id="d6e77-182">**Service**</span></span>|<span data-ttu-id="d6e77-183">Valeur par défaut est vide.</span><span class="sxs-lookup"><span data-stu-id="d6e77-183">Default is empty.</span></span><br /><br /> <span data-ttu-id="d6e77-184">Paramètre Service du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="d6e77-184">Rendezvous Transport Service parameter.</span></span>|  
  
5.  <span data-ttu-id="d6e77-185">Indiquez les informations d'identification à l'aide de l'authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="d6e77-185">Provide credentials using Single Sign-On (SSO).</span></span>  
  
     <span data-ttu-id="d6e77-186">Vous pouvez utiliser deux méthodes pour accéder au système TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="d6e77-186">There are two methods that you can use to access the TIBCO Rendezvous system.</span></span> <span data-ttu-id="d6e77-187">Vous pouvez utiliser les informations d'identification (paramètres Nom d'utilisateur et Mot de passe) ou l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="d6e77-187">You can use Credentials (User Name and Password parameters) or Single Sign-On.</span></span>  
  
    1.  <span data-ttu-id="d6e77-188">Sélectionnez **Oui** dans les **utiliser SSO** à utiliser l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="d6e77-188">Select **Yes** in the **Use SSO** to use Single Sign-On.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="d6e77-189">Consultez [sécurité](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md) pour plus d’informations sur la façon de configurer l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="d6e77-189">See [Security](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md) for information about how to set up SSO.</span></span>  
  
    2.  <span data-ttu-id="d6e77-190">Sélectionnez une application associée dans la liste.</span><span class="sxs-lookup"><span data-stu-id="d6e77-190">Select an affiliate application from the list.</span></span>  
  
         <span data-ttu-id="d6e77-191">Une application associée (créée par les outils d'authentification unique de l'entreprise) représente une application telle que TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="d6e77-191">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as TIBCO Rendezvous.</span></span> <span data-ttu-id="d6e77-192">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous utilise les informations d'identification d'un utilisateur de l'application.</span><span class="sxs-lookup"><span data-stu-id="d6e77-192">Microsoft BizTalk Adapter for TIBCO Rendezvous uses the credentials of an application user.</span></span> <span data-ttu-id="d6e77-193">Celles-ci sont extraites de la base de données SSO pour le système de serveur pour une application associée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d6e77-193">These credentials are retrieved from the SSO database for the server system for a specified affiliate application.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="d6e77-194">Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications1.md).</span><span class="sxs-lookup"><span data-stu-id="d6e77-194">For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications1.md).</span></span>  
  
6.  <span data-ttu-id="d6e77-195">Cliquez sur **appliquer**, puis cliquez sur **OK** après avoir entré toutes les informations requises pour accepter les informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="d6e77-195">Click **Apply**, and then click **OK** after providing all required information to accept the connection information.</span></span>  
  
     <span data-ttu-id="d6e77-196">Vous devez définir les paramètres de connexion pour l’adaptateur BizTalk pour TIBCO Rendezvous pour accéder à TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="d6e77-196">You must set connection parameters for BizTalk Adapter for TIBCO Rendezvous to access TIBCO Rendezvous .</span></span>  


## <a name="next-steps"></a><span data-ttu-id="d6e77-197">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="d6e77-197">Next steps</span></span>
  
-   [<span data-ttu-id="d6e77-198">Utilisation des ports d’envoi TIBCO Rendezvous à partir de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d6e77-198">Using TIBCO Rendezvous Send Ports from BizTalk Server</span></span>](../core/using-tibco-rendezvous-send-ports-from-biztalk-server.md)  
  
-   [<span data-ttu-id="d6e77-199">Mappage de types de données pour les gestionnaires d’envoi dans TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="d6e77-199">Data Type Mapping for Send Handlers in TIBCO Rendezvous</span></span>](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md)  
  
-   [<span data-ttu-id="d6e77-200">Propriétés de contexte de message BizTalk Server (gestionnaires d’envoi)</span><span class="sxs-lookup"><span data-stu-id="d6e77-200">BizTalk Server Message Context Properties (Send Handlers)</span></span>](../core/biztalk-server-message-context-properties-send-handlers.md)