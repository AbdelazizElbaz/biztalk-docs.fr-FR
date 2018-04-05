---
title: Comment créer un Port de réception | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.procedure.createreceiveport
helpviewer_keywords:
- receive ports, creating
- managing [receive ports], creating
- creating, receive ports
ms.assetid: 23fae441-be80-4759-b3d6-74787a40e65b
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdecbc36962d3e4e45d35171747ff4c450959a83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-receive-port"></a><span data-ttu-id="55b96-102">Comment créer un Port de réception</span><span class="sxs-lookup"><span data-stu-id="55b96-102">How to Create a Receive Port</span></span>
<span data-ttu-id="55b96-103">La présente rubrique explique comment créer un port de réception à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="55b96-103">This topic describes how to use the BizTalk Server Administration console to create a receive port.</span></span> <span data-ttu-id="55b96-104">Un port de réception est groupe logique d'emplacements de réception similaires grâce auquel les services interagissent avec les partenaires externes en recevant des données.</span><span class="sxs-lookup"><span data-stu-id="55b96-104">A receive port is a logical grouping of similar receive locations through which services interact with external partners by receiving data.</span></span>  
  
 <span data-ttu-id="55b96-105">Vous pouvez créer les types de ports de réception suivants :</span><span class="sxs-lookup"><span data-stu-id="55b96-105">You can create the following types of receive ports:</span></span>  
  
-   <span data-ttu-id="55b96-106">Unidirectionnel : utilisé pour les applications qui déposent un message et n'attendent pas de réponse synchrone</span><span class="sxs-lookup"><span data-stu-id="55b96-106">One-way — used for applications that drop off a message and do not wait synchronously for a reply</span></span>  
  
-   <span data-ttu-id="55b96-107">Requête-réponse : utilisé avec les applications qui exigent une réponse à un message</span><span class="sxs-lookup"><span data-stu-id="55b96-107">Request-response — used with applications that require a response to a message</span></span>  
  
 <span data-ttu-id="55b96-108">En plus de la configuration décrite dans cette rubrique, vous pouvez également spécifier des options de suivi pour les messages traités par un port de réception, comme décrit dans [comment configurer le suivi pour un Port de réception](../core/how-to-configure-tracking-for-a-receive-port.md).</span><span class="sxs-lookup"><span data-stu-id="55b96-108">In addition to the configuration described in this topic, you can also specify tracking options for the messages handled by a receive port, as described in [How to Configure Tracking for a Receive Port](../core/how-to-configure-tracking-for-a-receive-port.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55b96-109">Si vous créez un port de réception sur un ordinateur distant alors que le réseau DTC n'est pas activé sur cet ordinateur, vous devrez redémarrer l'ordinateur distant une fois le port de réception créé.</span><span class="sxs-lookup"><span data-stu-id="55b96-109">If you are creating a receive port on a remote computer and that computer does not have network DTC enabled, you will have to reboot the remote computer after creating the receive port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="55b96-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="55b96-110">Prerequisites</span></span>  
 <span data-ttu-id="55b96-111">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="55b96-111">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="55b96-112">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="55b96-112">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-create-a-receive-port"></a><span data-ttu-id="55b96-113">Pour créer un port de réception</span><span class="sxs-lookup"><span data-stu-id="55b96-113">To create a receive port</span></span>  
  
1.  <span data-ttu-id="55b96-114">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="55b96-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="55b96-115">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk pour laquelle créer un port de réception.</span><span class="sxs-lookup"><span data-stu-id="55b96-115">In the console tree, expand the BizTalk group and the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="55b96-116">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel** ou **Receive Port requête-réponse**, en fonction pour le type de port que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="55b96-116">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port** or **Request Response Receive Port**, according to the type of port you want to create.</span></span>  
  
4.  <span data-ttu-id="55b96-117">Dans le **propriétés du Port de réception** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="55b96-117">In the **Receive Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="55b96-118">Utiliser</span><span class="sxs-lookup"><span data-stu-id="55b96-118">Use this</span></span>|<span data-ttu-id="55b96-119">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="55b96-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="55b96-120">**Nom**</span><span class="sxs-lookup"><span data-stu-id="55b96-120">**Name**</span></span>|<span data-ttu-id="55b96-121">Taper le nom du port.</span><span class="sxs-lookup"><span data-stu-id="55b96-121">Type the name of the port.</span></span>|  
    |<span data-ttu-id="55b96-122">**Aucune authentification**</span><span class="sxs-lookup"><span data-stu-id="55b96-122">**No authentication**</span></span>|<span data-ttu-id="55b96-123">Cliquer sur cette option pour désactiver l'authentification.</span><span class="sxs-lookup"><span data-stu-id="55b96-123">Click this option to disable authentication.</span></span> <span data-ttu-id="55b96-124">Il s'agit du paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="55b96-124">This is the default.</span></span>|  
    |<span data-ttu-id="55b96-125">**Supprimer les messages si l’authentification échoue**</span><span class="sxs-lookup"><span data-stu-id="55b96-125">**Drop messages if authentication fails**</span></span>|<span data-ttu-id="55b96-126">Cliquez sur cette option pour activer l’authentification, mais abandonner les messages non authentifiés.</span><span class="sxs-lookup"><span data-stu-id="55b96-126">Click this option to enable authentication but to drop unauthenticated messages.</span></span>|  
    |<span data-ttu-id="55b96-127">**Conserver les messages si l’authentification échoue**</span><span class="sxs-lookup"><span data-stu-id="55b96-127">**Keep messages if authentication fails**</span></span>|<span data-ttu-id="55b96-128">Activer l'authentification et conserver les messages non authentifiés.</span><span class="sxs-lookup"><span data-stu-id="55b96-128">Click this option to enable authentication and keep unauthenticated messages.</span></span>|  
    |<span data-ttu-id="55b96-129">**Activer le routage des messages ayant échoué**</span><span class="sxs-lookup"><span data-stu-id="55b96-129">**Enable routing for failed messages**</span></span>|<span data-ttu-id="55b96-130">Activer cette case à cocher pour lancer une tentative d'acheminement des messages dont le traitement a échoué vers une application abonnée (un autre port de réception ou une planification d'orchestration).</span><span class="sxs-lookup"><span data-stu-id="55b96-130">Select this check box to attempt to route any message that fails processing to a subscribing application (such as another receive port or orchestration schedule).</span></span> <span data-ttu-id="55b96-131">Désactiver la case à cocher pour interrompre les messages ayant échoué et générer un accusé de réception négatif (NACK).</span><span class="sxs-lookup"><span data-stu-id="55b96-131">Clear the check box to suspend failed messages and generate a negative acknowledgment (NACK).</span></span> <span data-ttu-id="55b96-132">Par défaut, cette case à cocher est désactivée.</span><span class="sxs-lookup"><span data-stu-id="55b96-132">The default value is cleared.</span></span> <span data-ttu-id="55b96-133">Pour plus d’informations, consultez [comment activer le routage de Messages a échoué pour un Port de réception](../core/how-to-enable-routing-for-failed-messages-for-a-receive-port.md).</span><span class="sxs-lookup"><span data-stu-id="55b96-133">For more information, see [How to Enable Routing for Failed Messages for a Receive Port](../core/how-to-enable-routing-for-failed-messages-for-a-receive-port.md).</span></span>|  
  
5.  <span data-ttu-id="55b96-134">Dans le volet gauche, cliquez sur **emplacements de réception**, puis créez un emplacement de réception pour ce port de réception.</span><span class="sxs-lookup"><span data-stu-id="55b96-134">In the left pane, click **Receive Locations**, and create a new receive location for this receive port.</span></span> <span data-ttu-id="55b96-135">Pour obtenir des instructions, consultez [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).</span><span class="sxs-lookup"><span data-stu-id="55b96-135">For instructions, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).</span></span>  
  
6.  <span data-ttu-id="55b96-136">Dans le volet gauche, cliquez sur **mappages entrants**, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="55b96-136">In the left pane, click **Inbound Maps**, and do the following:</span></span>  
  
    |<span data-ttu-id="55b96-137">Utiliser</span><span class="sxs-lookup"><span data-stu-id="55b96-137">Use this</span></span>|<span data-ttu-id="55b96-138">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="55b96-138">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="55b96-139">**Document source**</span><span class="sxs-lookup"><span data-stu-id="55b96-139">**Source Document**</span></span>|<span data-ttu-id="55b96-140">Sélectionner, dans la liste déroulante, le schéma source à utiliser avec ce port.</span><span class="sxs-lookup"><span data-stu-id="55b96-140">From the drop-down list, select the source schema to use with this port.</span></span>|  
    |<span data-ttu-id="55b96-141">**Carte**</span><span class="sxs-lookup"><span data-stu-id="55b96-141">**Map**</span></span>|<span data-ttu-id="55b96-142">Sélectionner, dans la liste déroulante, le mappage à associer à ce port.</span><span class="sxs-lookup"><span data-stu-id="55b96-142">From the drop-down list, select the map you want to associate with this port.</span></span>|  
    |<span data-ttu-id="55b96-143">**Document cible**</span><span class="sxs-lookup"><span data-stu-id="55b96-143">**Target Document**</span></span>|<span data-ttu-id="55b96-144">Sélectionner, dans la liste déroulante, le schéma de destination à utiliser avec ce port.</span><span class="sxs-lookup"><span data-stu-id="55b96-144">From the drop-down list, select the destination schema to use with this port.</span></span>|  
  
7.  <span data-ttu-id="55b96-145">Si vous créez une requête-réponse port de réception, puis dans le volet gauche, cliquez sur **mappages sortants**, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="55b96-145">If you are creating a request-response receive port, then in the left pane, click **Outbound Maps**, and do the following:</span></span>  
  
    |<span data-ttu-id="55b96-146">Utiliser</span><span class="sxs-lookup"><span data-stu-id="55b96-146">Use this</span></span>|<span data-ttu-id="55b96-147">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="55b96-147">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="55b96-148">**Document source**</span><span class="sxs-lookup"><span data-stu-id="55b96-148">**Source Document**</span></span>|<span data-ttu-id="55b96-149">Sélectionner, dans la liste déroulante, le schéma source à utiliser avec ce port.</span><span class="sxs-lookup"><span data-stu-id="55b96-149">From the drop-down list, select the source schema to use with this port.</span></span>|  
    |<span data-ttu-id="55b96-150">**Carte**</span><span class="sxs-lookup"><span data-stu-id="55b96-150">**Map**</span></span>|<span data-ttu-id="55b96-151">Sélectionner, dans la liste déroulante, le mappage à associer à ce port.</span><span class="sxs-lookup"><span data-stu-id="55b96-151">From the drop-down list, select the map you want to associate with this port.</span></span>|  
    |<span data-ttu-id="55b96-152">**Document cible**</span><span class="sxs-lookup"><span data-stu-id="55b96-152">**Target Document**</span></span>|<span data-ttu-id="55b96-153">Sélectionner, dans la liste déroulante, le schéma de destination à utiliser avec ce port.</span><span class="sxs-lookup"><span data-stu-id="55b96-153">From the drop-down list, select the destination schema to use with this port.</span></span>|  
  
8.  <span data-ttu-id="55b96-154">Une fois terminé de configurer le port de réception, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="55b96-154">When finished configuring the receive port, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55b96-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55b96-155">See Also</span></span>  
 [<span data-ttu-id="55b96-156">La gestion des Ports de réception</span><span class="sxs-lookup"><span data-stu-id="55b96-156">Managing Receive Ports</span></span>](../core/managing-receive-ports.md)