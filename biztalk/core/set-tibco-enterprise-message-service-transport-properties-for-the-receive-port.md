---
title: "Définition des propriétés du Transport TIBCO Enterprise Message Service pour le Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive ports, setting transport properties
- transport properties, setting for receive port
- setting transport properties, receive port
ms.assetid: bccddf84-d92e-469f-aa6f-4234c91a0be9
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d94229364e3bed8faaf1407603f17db76c70e6bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-tibco-enterprise-message-service-transport-properties-for-the-receive-port"></a><span data-ttu-id="2e8ef-102">Configuration des propriétés de transport de l'adaptateur TIBCO Enterprise Message Service pour le port de réception</span><span class="sxs-lookup"><span data-stu-id="2e8ef-102">Setting TIBCO Enterprise Message Service Transport Properties for the Receive Port</span></span>
<span data-ttu-id="2e8ef-103">Emplacement de réception pour un système d’exploitation TIBCO Enterprise Message System (EMS) le **URL** et **cible Namespace** au système TIBCO EMS sont les seules valeurs de configuration requises.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-103">For a TIBCO Enterprise Message System (EMS) receive location, the **URL** and **Target Namespace** to the TIBCO EMS System are the only configuration values required.</span></span>  
  
### <a name="to-specify-tibco-ems-transport-properties"></a><span data-ttu-id="2e8ef-104">Pour spécifier les propriétés du transport TIBCO EMS</span><span class="sxs-lookup"><span data-stu-id="2e8ef-104">To specify TIBCO EMS transport properties</span></span>  
  
1.  <span data-ttu-id="2e8ef-105">Développez le **définition système** et entrez les informations requises pour la connexion au serveur TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-105">Expand the **System Definition** and enter all required information for connection to the TIBCO EMS server.</span></span>  
  
2.  <span data-ttu-id="2e8ef-106">Développez **gestion des messages** et entrez les informations requises.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-106">Expand **Message Handling** and enter all required information.</span></span>  
  
    |<span data-ttu-id="2e8ef-107">Paramètre</span><span class="sxs-lookup"><span data-stu-id="2e8ef-107">Parameter</span></span>|<span data-ttu-id="2e8ef-108"> Description</span><span class="sxs-lookup"><span data-stu-id="2e8ef-108">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="2e8ef-109">**Sélecteur de message**</span><span class="sxs-lookup"><span data-stu-id="2e8ef-109">**Message Selector**</span></span>|<span data-ttu-id="2e8ef-110">Les messages ne sont reçus que si cette chaîne renvoie True avec le message dans la destination.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-110">Messages are received only if this string evaluates to True with the message in the destination.</span></span><br /><br /> <span data-ttu-id="2e8ef-111">Permet au port de réception de ne récupérer que les messages qui contiennent des propriétés d'en-tête correspondant à l'expression décrite dans ce champ.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-111">Allows the receive port to retrieve only messages that contain header properties that match the expression described in this field.</span></span><br /><br /> <span data-ttu-id="2e8ef-112">La syntaxe des sélecteurs de message est basée sur un sous-ensemble de la syntaxe d'expression conditionnelle SQL92.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-112">The syntax of message selectors is based on a subset of the SQL92 conditional expression syntax.</span></span> <span data-ttu-id="2e8ef-113">Cette syntaxe est décrite en détail dans le guide de l'utilisateur de TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-113">The syntax is fully described in the TIBCO EMS users guide.</span></span><br /><br /> <span data-ttu-id="2e8ef-114">Par exemple, si un message contient un nom de propriété d'en-tête NewsType, un port de réception ne peut récupérer que ceux dont le type est Sports ou Éditorial.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-114">For example, if a message contains a header property name NewsType, a receive port can retrieve only those that are of type Sports or Editorial.</span></span>|  
    |<span data-ttu-id="2e8ef-115">**Nombre de tentatives**</span><span class="sxs-lookup"><span data-stu-id="2e8ef-115">**Retry Count**</span></span>|<span data-ttu-id="2e8ef-116">Nombre de tentatives du transport.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-116">The retry count for the transport.</span></span> <span data-ttu-id="2e8ef-117">Valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-117">Default value is 0.</span></span>|  
    |<span data-ttu-id="2e8ef-118">**Intervalle avant nouvelle tentative**</span><span class="sxs-lookup"><span data-stu-id="2e8ef-118">**Retry Interval**</span></span>|<span data-ttu-id="2e8ef-119">Délai d'attente avant que l'adaptateur fasse une nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-119">The period of time the adapter waits before initiating a retry.</span></span> <span data-ttu-id="2e8ef-120">La valeur par défaut est de cinq minutes.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-120">Default value is five minutes.</span></span>|  
  
3.  <span data-ttu-id="2e8ef-121">Développez le **définition de la connexion serveur** et entrez les informations requises.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-121">Expand the **Server Connection Definition** and enter all required information.</span></span>  
  
    |<span data-ttu-id="2e8ef-122">Paramètre</span><span class="sxs-lookup"><span data-stu-id="2e8ef-122">Parameter</span></span>|<span data-ttu-id="2e8ef-123"> Description</span><span class="sxs-lookup"><span data-stu-id="2e8ef-123">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="2e8ef-124">**Destination**</span><span class="sxs-lookup"><span data-stu-id="2e8ef-124">**Destination**</span></span>|<span data-ttu-id="2e8ef-125">Paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-125">Mandatory setting.</span></span> <span data-ttu-id="2e8ef-126">Définit le nom et le type de la destination.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-126">Defines the name and type of the destination.</span></span> <span data-ttu-id="2e8ef-127">Définit la file d'attente ou la rubrique au format suivant : File d'attente[nom.file.attente] ou Rubrique[nom.rubrique].</span><span class="sxs-lookup"><span data-stu-id="2e8ef-127">Defines the queue or topic with the following format: Queue[queue.name] or Topic[topic.name].</span></span>|  
    |<span data-ttu-id="2e8ef-128">**Numéro de port**</span><span class="sxs-lookup"><span data-stu-id="2e8ef-128">**Port Number**</span></span>|<span data-ttu-id="2e8ef-129">Port sur lequel le serveur TIBCO EMS écoute.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-129">Port on which the TIBCO EMS server listens.</span></span>|  
    |<span data-ttu-id="2e8ef-130">**Nom de serveur**</span><span class="sxs-lookup"><span data-stu-id="2e8ef-130">**Server Name**</span></span>|<span data-ttu-id="2e8ef-131">Paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-131">Mandatory setting.</span></span> <span data-ttu-id="2e8ef-132">Nom du système qui héberge le serveur TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-132">Name of the system hosting the TIBCO EMS server.</span></span>|  
  
4.  <span data-ttu-id="2e8ef-133">Indiquez les informations d'identification à l'aide de l'authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="2e8ef-133">Provide credentials using Single Sign-On (SSO).</span></span>  
  
     <span data-ttu-id="2e8ef-134">Vous pouvez utiliser deux méthodes pour accéder au système TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-134">There are two methods that you can use to access the TIBCO EMS system.</span></span> <span data-ttu-id="2e8ef-135">Vous pouvez utiliser les informations d’identification (paramètres nom et mot de passe d’utilisateur) ou l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-135">You can use Credentials (user name and password parameters) or Single Sign-On.</span></span>  
  
    -   <span data-ttu-id="2e8ef-136">Sélectionnez **Oui** dans **utiliser SSO** à utiliser l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-136">Select **Yes** in **Use SSO** to use Single Sign-On.</span></span>  
  
    -   <span data-ttu-id="2e8ef-137">Sélectionnez une application associée sur la liste.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-137">Select an affiliate application in the list.</span></span>  
  
         <span data-ttu-id="2e8ef-138">Une application associée (créée par les outils d'authentification unique de l'entreprise) représente une application telle que TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-138">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as TIBCO EMS.</span></span> <span data-ttu-id="2e8ef-139">L'adaptateur Microsoft BizTalk pour TIBCO EMS utilise les informations d'identification d'un utilisateur d'application.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-139">Microsoft BizTalk Adapter for TIBCO EMS uses the credentials of an application user.</span></span> <span data-ttu-id="2e8ef-140">Celles-ci sont extraites de la base de données SSO pour le système de serveur pour une application associée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-140">These credentials are retrieved from the SSO database for the server system for a specified affiliate application.</span></span>  
  
         <span data-ttu-id="2e8ef-141">Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications5.md).</span><span class="sxs-lookup"><span data-stu-id="2e8ef-141">For more information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).</span></span>  
  
5.  <span data-ttu-id="2e8ef-142">Développez **informations d’identification utilisateur** et entrez le **nom d’utilisateur** et **mot de passe** pour accéder au serveur TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-142">Expand **User Credentials** and enter the **User Name** and **Password** to access the TIBCO EMS server.</span></span>  
  
    |<span data-ttu-id="2e8ef-143">Paramètre</span><span class="sxs-lookup"><span data-stu-id="2e8ef-143">Parameter</span></span>|<span data-ttu-id="2e8ef-144"> Description</span><span class="sxs-lookup"><span data-stu-id="2e8ef-144">Description</span></span>|  
    |---------------|-----------------|  
    |`Password`|<span data-ttu-id="2e8ef-145">Le mot de passe qui est utilisé pour communiquer avec un démon TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-145">The user’s password that is used to communicate with a TIBCO EMS daemon.</span></span><br /><br /> <span data-ttu-id="2e8ef-146">Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour TIBCO EMS communiquer avec un démon TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-146">If you did not select **Use SSO**, you must set credential parameters for BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.</span></span>|  
    |`User Name`|<span data-ttu-id="2e8ef-147">Nom d’un utilisateur qui est utilisé pour communiquer avec un démon TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-147">Name of a user that is used to communicate with a TIBCO EMS daemon.</span></span><br /><br /> <span data-ttu-id="2e8ef-148">Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour TIBCO EMS communiquer avec un démon TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-148">If you did not select **Use SSO**, you must set credential parameters for BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.</span></span>|  
  
6.  <span data-ttu-id="2e8ef-149">Cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2e8ef-149">Click **Apply**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e8ef-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e8ef-150">See Also</span></span>  
 <span data-ttu-id="2e8ef-151">[Création de Ports d’envoi](../core/creating-send-ports1.md) </span><span class="sxs-lookup"><span data-stu-id="2e8ef-151">[Creating Send Ports](../core/creating-send-ports1.md) </span></span>  
 [<span data-ttu-id="2e8ef-152">Gestionnaires de réception TIBCO Enterprise Message Service de création</span><span class="sxs-lookup"><span data-stu-id="2e8ef-152">Creating TIBCO Enterprise Message Service Receive Handlers</span></span>](../core/creating-tibco-enterprise-message-service-receive-handlers.md)