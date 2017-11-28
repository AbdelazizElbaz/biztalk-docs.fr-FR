---
title: "L’utilisation de Web Services dans un scénario de messagerie seule | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66873959-5b1b-4d9b-ad19-f083670420b8
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ac3e87d54ab7babed8be6b4d81267d22d8ac319
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-consume-web-services-in-a-messaging-only-scenario"></a><span data-ttu-id="d3a03-102">Utilisation des services Web dans un scénario de messagerie seule</span><span class="sxs-lookup"><span data-stu-id="d3a03-102">How to Consume Web Services in a Messaging Only Scenario</span></span>
<span data-ttu-id="d3a03-103">Une nouvelle amélioration apportée à l'adaptateur SOAP réside dans la capacité à appeler les services Web dans un scénario de messagerie seule à l'aide de ports d'envoi de routage basé sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="d3a03-103">One of the new enhancements for the SOAP adapter is ability to call Web services in a messaging only scenario by using content-based routing send ports.</span></span> <span data-ttu-id="d3a03-104">Cette fonctionnalité permet d'utiliser des services Web sans créer d'orchestrations.</span><span class="sxs-lookup"><span data-stu-id="d3a03-104">This feature makes it possible to consume Web services without creating orchestrations.</span></span> <span data-ttu-id="d3a03-105">Elle offre également de meilleures performances dans l'utilisation des services Web, car les messages ne sont pas transmis via les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="d3a03-105">It also provides better performance to consume Web services because messages do not pass through orchestrations.</span></span>  
  
 <span data-ttu-id="d3a03-106">Pour utiliser des services Web dans un scénario de messagerie seule, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d3a03-106">To consume Web services in a messaging only scenario, do the following:</span></span>  
  
-   <span data-ttu-id="d3a03-107">Créez une bibliothèque proxy et des schémas XML pour l'appel de services Web.</span><span class="sxs-lookup"><span data-stu-id="d3a03-107">Create a proxy library and XML schemas for invoking Web services</span></span>  
  
-   <span data-ttu-id="d3a03-108">Configurez un port d'envoi et un emplacement de réception pour l'utilisation d'un service Web.</span><span class="sxs-lookup"><span data-stu-id="d3a03-108">Configure a send port and receive location for consuming a Web service</span></span>  
  
### <a name="to-create-a-proxy-library-and-xml-schemas-for-invoking-web-services"></a><span data-ttu-id="d3a03-109">Pour créer une bibliothèque proxy et des schémas XML pour l'appel de services Web</span><span class="sxs-lookup"><span data-stu-id="d3a03-109">To create a proxy library and XML schemas for invoking Web services</span></span>  
  
1.  <span data-ttu-id="d3a03-110">Déterminez l'URL du service Web.</span><span class="sxs-lookup"><span data-stu-id="d3a03-110">Determine the URL for the Web service.</span></span>  
  
2.  <span data-ttu-id="d3a03-111">Ouvrir un **projet BizTalk Server vide** dans un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solution.</span><span class="sxs-lookup"><span data-stu-id="d3a03-111">Open an **Empty BizTalk Server Project** in a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solution.</span></span> <span data-ttu-id="d3a03-112">Pour plus d’informations sur la création d’un projet BizTalk Server, consultez [comment créer des projets BizTalk](../core/how-to-create-biztalk-projects.md).</span><span class="sxs-lookup"><span data-stu-id="d3a03-112">For more information about how to create a BizTalk Server project, see [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d3a03-113">Cette procédure pas à pas utilise un projet BizTalk Server pour permettre de générer les bibliothèques proxy et les schémas XML utilisés par le service Web.</span><span class="sxs-lookup"><span data-stu-id="d3a03-113">This walkthrough uses a BizTalk Server project to generate proxy libraries and XML schemas that the Web service uses.</span></span> <span data-ttu-id="d3a03-114">Vous pouvez également utiliser le Wsdl.exe et Xsd.exe dans le Kit de développement logiciel .NET Framework 4.0 dans le même but.</span><span class="sxs-lookup"><span data-stu-id="d3a03-114">You can also use the Wsdl.exe and Xsd.exe in the .NET Framework 4.0 SDK for the same purpose.</span></span>  
  
3.  <span data-ttu-id="d3a03-115">Dans l’Explorateur de solutions, cliquez sur le nom de projet BizTalk Server, puis cliquez sur **ajouter une référence de Service**.</span><span class="sxs-lookup"><span data-stu-id="d3a03-115">In Solution Explorer, right-click the BizTalk Server project name, and then click **Add Service Reference**.</span></span>  
  
4.  <span data-ttu-id="d3a03-116">Dans le **ajouter une référence de Service** boîte de dialogue, cliquez sur **avancé**.</span><span class="sxs-lookup"><span data-stu-id="d3a03-116">In the **Add Service Reference** dialog box, click **Advanced**.</span></span>  
  
5.  <span data-ttu-id="d3a03-117">Dans le **paramètres de référence de Service** boîte de dialogue, cliquez sur **ajouter une référence Web** dans les **compatibilité** section.</span><span class="sxs-lookup"><span data-stu-id="d3a03-117">In the **Service Reference Settings** dialog box, Click **Add Web Reference** in the **Compatibility** section.</span></span>  
  
6.  <span data-ttu-id="d3a03-118">Dans le **ajouter une référence Web** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d3a03-118">In the **Add Web Reference** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="d3a03-119">Dans le **URL** champ, tapez l’URL du service Web, puis cliquez sur **accédez**.</span><span class="sxs-lookup"><span data-stu-id="d3a03-119">In the **URL** field, type a Web service URL, and then click **Go**.</span></span>  
  
    2.  <span data-ttu-id="d3a03-120">Dans le **nom de référence Web** champ, tapez un nom pour l’espace de noms, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="d3a03-120">In the **Web reference name** field, type a name for the namespace, and then click **Add Reference**.</span></span>  
  
7.  <span data-ttu-id="d3a03-121">La référence Web s’affiche sous **références Web** nœud dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="d3a03-121">The Web reference will appear under **Web References** node in Solution Explorer.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d3a03-122">Une fois que vous avez ajouté à un projet BizTalk, une référence web le **ajouter une référence Web** commande est directement disponible lorsque vous cliquez sur le nom du projet ou **références** ou **lesréférencesWeb**.</span><span class="sxs-lookup"><span data-stu-id="d3a03-122">Once you have a web reference added to a BizTalk project, the **Add Web Reference** command is directly available when you right-click the project name or **References** or **Web References**.</span></span>  
  
8.  <span data-ttu-id="d3a03-123">Dans l’Explorateur de solutions, cliquez sur le nom du projet, puis cliquez sur **propriétés** pour lancer le Concepteur de projet.</span><span class="sxs-lookup"><span data-stu-id="d3a03-123">In Solution Explorer, right-click the project name, and then click **Properties** to launch the Project Designer.</span></span>  
  
9. <span data-ttu-id="d3a03-124">Dans le Concepteur de projets, cliquez sur le **signature** onglet.</span><span class="sxs-lookup"><span data-stu-id="d3a03-124">In the Project Designer, click the **Signing** tab.</span></span>  
  
10. <span data-ttu-id="d3a03-125">Sélectionnez **signer l’assembly** , cliquez sur la liste déroulante pour le **choisir un fichier de clé de nom fort**, puis cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="d3a03-125">Select **Sign the assembly** option, click the drop-down list for the **Choose a strong name key file**, and then click **Browse**.</span></span>  
  
11. <span data-ttu-id="d3a03-126">Recherchez et sélectionnez le fichier de clé d’assembly, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="d3a03-126">Browse and select the assembly key file, and then click **Open**.</span></span>  
  
12. <span data-ttu-id="d3a03-127">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="d3a03-127">In Solution Explorer, right-click the project name, and then click **Build**.</span></span>  
  
13. <span data-ttu-id="d3a03-128">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Déployer**.</span><span class="sxs-lookup"><span data-stu-id="d3a03-128">In Solution Explorer, right-click the project name, and then click **Deploy**.</span></span>  
  
### <a name="to-configure-a-send-port-and-receive-location-for-consuming-a-web-service"></a><span data-ttu-id="d3a03-129">Pour configurer un port d'envoi et un emplacement de réception pour l'utilisation d'un service Web</span><span class="sxs-lookup"><span data-stu-id="d3a03-129">To configure a send port and receive location for consuming a Web service</span></span>  
  
1.  <span data-ttu-id="d3a03-130">Dans la console Administration de BizTalk Server, créez un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="d3a03-130">In the BizTalk Server Administration console, create a send port.</span></span> <span data-ttu-id="d3a03-131">Pour plus d’informations, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md).</span><span class="sxs-lookup"><span data-stu-id="d3a03-131">For more information, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span> <span data-ttu-id="d3a03-132">Lors de la création d'un port d'envoi, sélectionnez le type de transport ou protocole de transport SOAP.</span><span class="sxs-lookup"><span data-stu-id="d3a03-132">When creating the send port, select SOAP as the transport type or transport protocol.</span></span>  
  
2.  <span data-ttu-id="d3a03-133">Configurez le port d'envoi SOAP avec les paramètres suivants.</span><span class="sxs-lookup"><span data-stu-id="d3a03-133">Configure the SOAP send port with the following settings.</span></span> <span data-ttu-id="d3a03-134">Pour plus d’informations, consultez [comment configurer un Port d’envoi SOAP](../core/how-to-configure-a-soap-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="d3a03-134">For more information, see [How to Configure a SOAP Send Port](../core/how-to-configure-a-soap-send-port.md).</span></span>  
  
    |<span data-ttu-id="d3a03-135">Utiliser</span><span class="sxs-lookup"><span data-stu-id="d3a03-135">Use this</span></span>|<span data-ttu-id="d3a03-136">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="d3a03-136">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d3a03-137">**Les paramètres suivants**</span><span class="sxs-lookup"><span data-stu-id="d3a03-137">**The following settings**</span></span>|<span data-ttu-id="d3a03-138">Sélectionner cette option pour spécifier les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="d3a03-138">Select this option to specify the following properties.</span></span>|  
    |<span data-ttu-id="d3a03-139">**Nom de l’assembly**</span><span class="sxs-lookup"><span data-stu-id="d3a03-139">**Assembly name**</span></span>|<span data-ttu-id="d3a03-140">Sélectionner l'assembly créé dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="d3a03-140">Select the assembly created in the previous procedure.</span></span> <span data-ttu-id="d3a03-141">Le nom qualifié complet de l’assembly est écrit à l’adaptateur SOAP **AssemblyName** propriété.</span><span class="sxs-lookup"><span data-stu-id="d3a03-141">The fully qualified name of the assembly is written to the SOAP adapter **AssemblyName** property.</span></span>|  
    |<span data-ttu-id="d3a03-142">**Nom de type**</span><span class="sxs-lookup"><span data-stu-id="d3a03-142">**Type name**</span></span>|<span data-ttu-id="d3a03-143">Indiquez le nom de la classe contenant la méthode Web à appeler.</span><span class="sxs-lookup"><span data-stu-id="d3a03-143">Specify the name of the class that contains the Web method to be invoked.</span></span> <span data-ttu-id="d3a03-144">Le nom de type est écrit à l’adaptateur SOAP **TypeName** propriété.</span><span class="sxs-lookup"><span data-stu-id="d3a03-144">The type name is written to the SOAP adapter **TypeName** property.</span></span>|  
    |<span data-ttu-id="d3a03-145">**Nom de la méthode**</span><span class="sxs-lookup"><span data-stu-id="d3a03-145">**Method name**</span></span>|<span data-ttu-id="d3a03-146">Spécifier une des méthodes dans la zone de liste.</span><span class="sxs-lookup"><span data-stu-id="d3a03-146">Specify one of the methods in the list box.</span></span> <span data-ttu-id="d3a03-147">La méthode Web est écrit à l’adaptateur Soap **MethodName** propriété.</span><span class="sxs-lookup"><span data-stu-id="d3a03-147">The Web method is written to the Soap Adapter **MethodName** property.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="d3a03-148">Si vous souhaitez utiliser le routage basé sur le contenu, configurez le filtre du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="d3a03-148">If you want to use Content-Based Routing (CBR), configure the filter of the send port.</span></span> <span data-ttu-id="d3a03-149">Pour plus d’informations, consultez [comment configurer des filtres pour un Port d’envoi](../core/how-to-configure-filters-for-a-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="d3a03-149">For more information, see [How to Configure Filters for a Send Port](../core/how-to-configure-filters-for-a-send-port.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d3a03-150">S'il n'existe aucun abonné aux messages de réponse des services Web appelés, une erreur de défaillance du routage se produit.</span><span class="sxs-lookup"><span data-stu-id="d3a03-150">If there is no subscriber to the response messages from the invoked Web services, a routing failure error will occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a03-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3a03-151">See Also</span></span>  
 [<span data-ttu-id="d3a03-152">Utilisation de Services Web</span><span class="sxs-lookup"><span data-stu-id="d3a03-152">Consuming Web Services</span></span>](../core/consuming-web-services.md)