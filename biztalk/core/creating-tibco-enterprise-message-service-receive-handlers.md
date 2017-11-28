---
title: "Créer TIBCO EMS artefacts de réception | Documents Microsoft"
description: "Créer le port de réception et définissez les propriétés de transport à utiliser l’adaptateur TIBCO Enterprise Message Service dans BizTalk Server"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1307e3c-0237-4f19-a642-58e694fe95d0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf5810dc012c7aa5dcc2fbdfcecd9d59d066ced7
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="create-tibco-ems-receive-artifacts"></a><span data-ttu-id="9d9c5-103">Créer TIBCO EMS reçoivent des artefacts</span><span class="sxs-lookup"><span data-stu-id="9d9c5-103">Create TIBCO EMS receive artifacts</span></span>

## <a name="overview"></a><span data-ttu-id="9d9c5-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="9d9c5-104">Overview</span></span>
<span data-ttu-id="9d9c5-105">Le récepteur TIBCO Enterprise Message Service est un service de port d'écoute qui enregistre une file d'attente ou une rubrique particulière et reçoit les messages associés.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-105">TIBCO Enterprise Message Service receiver is a listener service that registers a particular Queue or Topic and receives the relative messages.</span></span> <span data-ttu-id="9d9c5-106">L'adaptateur BizTalk pour TIBCO Enterprise Message Service s'enregistre d'abord auprès de TIBCO Enterprise Message Service en ouvrant une nouvelle session, puis il continue l'interrogation pour recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-106">BizTalk Adapter for TIBCO Enterprise Message Service first registers with TIBCO Enterprise Message Service by opening a new session, and then it continues polling to receive messages..</span></span> <span data-ttu-id="9d9c5-107">Cette section décrit la configuration du port de réception pour la connexion à TIBCO Enterprise Message Service et l'utilisation d'un fichier XML dans votre orchestration pour interagir avec TIBCO EMS lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-107">This section explains how to set the receive port to connect to TIBCO Enterprise Message Service and how to include XML in your orchestration to interact with TIBCO EMS at run time.</span></span>  

## <a name="create-a-receive-port"></a><span data-ttu-id="9d9c5-108">Créer un port de réception</span><span class="sxs-lookup"><span data-stu-id="9d9c5-108">Create a receive port</span></span>  
  
1.  <span data-ttu-id="9d9c5-109">Dans la Console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis développez votre application.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-109">In the BizTalk Server Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand your application.</span></span>  
  
2.  <span data-ttu-id="9d9c5-110">Avec le bouton droit **Ports de réception**, sélectionnez **nouveau**, puis cliquez sur **Ports de réception unidirectionnels**.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-110">Right-click **Receive Ports**, select **New**, and then click **One-way Receive Ports**.</span></span>  
  
3.  <span data-ttu-id="9d9c5-111">Dans le **propriétés du Port de réception** fenêtre, dans le **général** page, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9d9c5-111">In the **Receive Port Properties** window, on the **General** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="9d9c5-112">Dans le **nom** , tapez `ReceiveFromTIBCOEMS`.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-112">In the **Name** field, type `ReceiveFromTIBCOEMS`.</span></span>  
  
    2.  <span data-ttu-id="9d9c5-113">Dans le **authentification** zone de groupe, spécifiez le traitement des messages lors de l’utilisation de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-113">In the **Authentication** group box, specify how messages are handled when using authentication.</span></span>  
  
    3.  <span data-ttu-id="9d9c5-114">Sélectionnez le **activer le routage pour les messages ayant échoué** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-114">Select the **Enable routing for failed messages** checkbox.</span></span>  
  
4.  <span data-ttu-id="9d9c5-115">Sur le **emplacements de réception** page, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9d9c5-115">On the **Receive Locations** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="9d9c5-116">Cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-116">Click **New**.</span></span>  
  
    2.  <span data-ttu-id="9d9c5-117">Dans le **emplacements de réception** fenêtre, dans le **général** , tapez le **nom** l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-117">In the **Receive Locations** window, on the **General** page, type the **Name** of the receive location.</span></span>  
  
    3.  <span data-ttu-id="9d9c5-118">À partir de la **Type** liste déroulante, sélectionnez le type de transport et à partir de la **Gestionnaire de réception** liste déroulante, sélectionnez l’adresse de transport.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-118">From the **Type** drop-down list, select the transport type, and from the **Receive handler** drop-down list, select the transport address.</span></span>  
  
    4.  <span data-ttu-id="9d9c5-119">À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-119">From the **Receive pipeline** drop-down list, select the receive pipeline.</span></span>  
  
    5.  <span data-ttu-id="9d9c5-120">Sur le **planification** page, sélectionnez le **date de début** et **date de fin** pour restreindre la réception des documents.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-120">On the **Schedule** page, select the **Start date** and the **End date** to restrict receiving documents.</span></span>  
  
    6.  <span data-ttu-id="9d9c5-121">Sélectionnez le **activer la fenêtre de service** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-121">Select the **Enable service window** checkbox.</span></span>  
  
    7.  <span data-ttu-id="9d9c5-122">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-122">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="9d9c5-123">Sur le **mappages entrants** , sélectionnez les mappages entrants pour transformer les documents sur le port sélectionné.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-123">On the **Inbound Maps** page, select the inbound maps for transforming documents on the selected port.</span></span>  
  
6.  <span data-ttu-id="9d9c5-124">Sur le **suivi** , sélectionnez le suivi des propriétés de message et le suivi des corps de message souhaité.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-124">On the **Tracking** page, select the desired tracking message bodies and tracking message properties.</span></span>  
  
7.  <span data-ttu-id="9d9c5-125">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-125">Click **OK**.</span></span>  

## <a name="set-the-receive-port-transport-properties"></a><span data-ttu-id="9d9c5-126">Définir des propriétés de port de la réception</span><span class="sxs-lookup"><span data-stu-id="9d9c5-126">Set the receive port transport properties</span></span>
<span data-ttu-id="9d9c5-127">Emplacement de réception pour un système d’exploitation TIBCO Enterprise Message System (EMS) le **URL** et **cible Namespace** au système TIBCO EMS sont les seules valeurs de configuration requises.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-127">For a TIBCO Enterprise Message System (EMS) receive location, the **URL** and **Target Namespace** to the TIBCO EMS System are the only configuration values required.</span></span>    
 
1.  <span data-ttu-id="9d9c5-128">Développez le **définition système** et entrez les informations requises pour la connexion au serveur TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-128">Expand the **System Definition** and enter all required information for connection to the TIBCO EMS server.</span></span>  
  
2.  <span data-ttu-id="9d9c5-129">Développez **gestion des messages** et entrez les informations requises.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-129">Expand **Message Handling** and enter all required information.</span></span>  
  
    |<span data-ttu-id="9d9c5-130">Paramètre</span><span class="sxs-lookup"><span data-stu-id="9d9c5-130">Parameter</span></span>|<span data-ttu-id="9d9c5-131"> Description</span><span class="sxs-lookup"><span data-stu-id="9d9c5-131">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="9d9c5-132">**Sélecteur de message**</span><span class="sxs-lookup"><span data-stu-id="9d9c5-132">**Message Selector**</span></span>|<span data-ttu-id="9d9c5-133">Les messages ne sont reçus que si cette chaîne renvoie True avec le message dans la destination.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-133">Messages are received only if this string evaluates to True with the message in the destination.</span></span><br /><br /> <span data-ttu-id="9d9c5-134">Permet au port de réception de ne récupérer que les messages qui contiennent des propriétés d'en-tête correspondant à l'expression décrite dans ce champ.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-134">Allows the receive port to retrieve only messages that contain header properties that match the expression described in this field.</span></span><br /><br /> <span data-ttu-id="9d9c5-135">La syntaxe des sélecteurs de message est basée sur un sous-ensemble de la syntaxe d'expression conditionnelle SQL92.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-135">The syntax of message selectors is based on a subset of the SQL92 conditional expression syntax.</span></span> <span data-ttu-id="9d9c5-136">Cette syntaxe est décrite en détail dans le guide de l'utilisateur de TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-136">The syntax is fully described in the TIBCO EMS users guide.</span></span><br /><br /> <span data-ttu-id="9d9c5-137">Par exemple, si un message contient un nom de propriété d'en-tête NewsType, un port de réception ne peut récupérer que ceux dont le type est Sports ou Éditorial.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-137">For example, if a message contains a header property name NewsType, a receive port can retrieve only those that are of type Sports or Editorial.</span></span>|  
    |<span data-ttu-id="9d9c5-138">**Nombre de tentatives**</span><span class="sxs-lookup"><span data-stu-id="9d9c5-138">**Retry Count**</span></span>|<span data-ttu-id="9d9c5-139">Nombre de tentatives du transport.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-139">The retry count for the transport.</span></span> <span data-ttu-id="9d9c5-140">Valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-140">Default value is 0.</span></span>|  
    |<span data-ttu-id="9d9c5-141">**Intervalle avant nouvelle tentative**</span><span class="sxs-lookup"><span data-stu-id="9d9c5-141">**Retry Interval**</span></span>|<span data-ttu-id="9d9c5-142">Délai d'attente avant que l'adaptateur fasse une nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-142">The period of time the adapter waits before initiating a retry.</span></span> <span data-ttu-id="9d9c5-143">La valeur par défaut est de cinq minutes.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-143">Default value is five minutes.</span></span>|  
  
3.  <span data-ttu-id="9d9c5-144">Développez le **définition de la connexion serveur** et entrez les informations requises.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-144">Expand the **Server Connection Definition** and enter all required information.</span></span>  
  
    |<span data-ttu-id="9d9c5-145">Paramètre</span><span class="sxs-lookup"><span data-stu-id="9d9c5-145">Parameter</span></span>|<span data-ttu-id="9d9c5-146"> Description</span><span class="sxs-lookup"><span data-stu-id="9d9c5-146">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="9d9c5-147">**Destination**</span><span class="sxs-lookup"><span data-stu-id="9d9c5-147">**Destination**</span></span>|<span data-ttu-id="9d9c5-148">Paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-148">Mandatory setting.</span></span> <span data-ttu-id="9d9c5-149">Définit le nom et le type de la destination.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-149">Defines the name and type of the destination.</span></span> <span data-ttu-id="9d9c5-150">Définit la file d'attente ou la rubrique au format suivant : File d'attente[nom.file.attente] ou Rubrique[nom.rubrique].</span><span class="sxs-lookup"><span data-stu-id="9d9c5-150">Defines the queue or topic with the following format: Queue[queue.name] or Topic[topic.name].</span></span>|  
    |<span data-ttu-id="9d9c5-151">**Numéro de port**</span><span class="sxs-lookup"><span data-stu-id="9d9c5-151">**Port Number**</span></span>|<span data-ttu-id="9d9c5-152">Port sur lequel le serveur TIBCO EMS écoute.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-152">Port on which the TIBCO EMS server listens.</span></span>|  
    |<span data-ttu-id="9d9c5-153">**Nom de serveur**</span><span class="sxs-lookup"><span data-stu-id="9d9c5-153">**Server Name**</span></span>|<span data-ttu-id="9d9c5-154">Paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-154">Mandatory setting.</span></span> <span data-ttu-id="9d9c5-155">Nom du système qui héberge le serveur TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-155">Name of the system hosting the TIBCO EMS server.</span></span>|  
  
4.  <span data-ttu-id="9d9c5-156">Indiquez les informations d'identification à l'aide de l'authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="9d9c5-156">Provide credentials using Single Sign-On (SSO).</span></span>  
  
     <span data-ttu-id="9d9c5-157">Vous pouvez utiliser deux méthodes pour accéder au système TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-157">There are two methods that you can use to access the TIBCO EMS system.</span></span> <span data-ttu-id="9d9c5-158">Vous pouvez utiliser les informations d’identification (paramètres nom et mot de passe d’utilisateur) ou l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-158">You can use Credentials (user name and password parameters) or Single Sign-On.</span></span>  
  
    -   <span data-ttu-id="9d9c5-159">Sélectionnez **Oui** dans **utiliser SSO** à utiliser l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-159">Select **Yes** in **Use SSO** to use Single Sign-On.</span></span>  
  
    -   <span data-ttu-id="9d9c5-160">Sélectionnez une application associée sur la liste.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-160">Select an affiliate application in the list.</span></span>  
  
         <span data-ttu-id="9d9c5-161">Une application associée (créée par les outils d'authentification unique de l'entreprise) représente une application telle que TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-161">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as TIBCO EMS.</span></span> <span data-ttu-id="9d9c5-162">L'adaptateur Microsoft BizTalk pour TIBCO EMS utilise les informations d'identification d'un utilisateur d'application.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-162">Microsoft BizTalk Adapter for TIBCO EMS uses the credentials of an application user.</span></span> <span data-ttu-id="9d9c5-163">Celles-ci sont extraites de la base de données SSO pour le système de serveur pour une application associée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-163">These credentials are retrieved from the SSO database for the server system for a specified affiliate application.</span></span>  
  
         <span data-ttu-id="9d9c5-164">Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications5.md).</span><span class="sxs-lookup"><span data-stu-id="9d9c5-164">For more information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).</span></span>  
  
5.  <span data-ttu-id="9d9c5-165">Développez **informations d’identification utilisateur** et entrez le **nom d’utilisateur** et **mot de passe** pour accéder au serveur TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-165">Expand **User Credentials** and enter the **User Name** and **Password** to access the TIBCO EMS server.</span></span>  
  
    |<span data-ttu-id="9d9c5-166">Paramètre</span><span class="sxs-lookup"><span data-stu-id="9d9c5-166">Parameter</span></span>|<span data-ttu-id="9d9c5-167"> Description</span><span class="sxs-lookup"><span data-stu-id="9d9c5-167">Description</span></span>|  
    |---------------|-----------------|  
    |`Password`|<span data-ttu-id="9d9c5-168">Le mot de passe qui est utilisé pour communiquer avec un démon TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-168">The user’s password that is used to communicate with a TIBCO EMS daemon.</span></span><br /><br /> <span data-ttu-id="9d9c5-169">Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour TIBCO EMS communiquer avec un démon TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-169">If you did not select **Use SSO**, you must set credential parameters for BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.</span></span>|  
    |`User Name`|<span data-ttu-id="9d9c5-170">Nom d’un utilisateur qui est utilisé pour communiquer avec un démon TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-170">Name of a user that is used to communicate with a TIBCO EMS daemon.</span></span><br /><br /> <span data-ttu-id="9d9c5-171">Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour TIBCO EMS communiquer avec un démon TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-171">If you did not select **Use SSO**, you must set credential parameters for BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.</span></span>|  
  
6.  <span data-ttu-id="9d9c5-172">Cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9d9c5-172">Click **Apply**, and then click **OK**.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="9d9c5-173">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="9d9c5-173">Next steps</span></span>
[<span data-ttu-id="9d9c5-174">Propriétés de contexte de message TIBCO EMS</span><span class="sxs-lookup"><span data-stu-id="9d9c5-174">TIBCO EMS message context properties</span></span>](../core/message-context-properties-in-biztalk-server.md)