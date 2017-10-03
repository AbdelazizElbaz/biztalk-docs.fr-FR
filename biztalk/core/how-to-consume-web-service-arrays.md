---
title: Comment utiliser les tableaux de Service Web | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP adapters, Web services
- Web services, arrays
- orchestrations, Web services
- orchestrations, Web ports
ms.assetid: 29ecaaed-aa8a-4cf9-a7c8-4b0d6dd412ac
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e78f12405c9c331a888a268d39e2a1520c84fdc8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-consume-web-service-arrays"></a><span data-ttu-id="820e7-102">Utilisation des tableaux de service Web</span><span class="sxs-lookup"><span data-stu-id="820e7-102">How to Consume Web Service Arrays</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="820e7-103"> permet d'utiliser les tableaux exposés dans les services Web à partir d'une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="820e7-103"> provides the ability to consume arrays that are exposed in Web services from a BizTalk Orchestration.</span></span>  
  
 <span data-ttu-id="820e7-104">**Pour configurer une Orchestration pour utiliser un tableau exposé dans un service Web :**</span><span class="sxs-lookup"><span data-stu-id="820e7-104">**To configure an Orchestration to consume an array exposed in a Web service:**</span></span>  
  
 <span data-ttu-id="820e7-105">Déterminez l'URL du service Web qui expose des tableaux.</span><span class="sxs-lookup"><span data-stu-id="820e7-105">Determine the URL for the Web service that exposes arrays.</span></span> <span data-ttu-id="820e7-106">Il s'agit généralement d'une page Web asmx qui répertorie les opérations prises en charge par le service Web.</span><span class="sxs-lookup"><span data-stu-id="820e7-106">This is typically an asmx Web page that lists the operations supported by the Web service.</span></span> <span data-ttu-id="820e7-107">Par exemple : http://localhost/ArrayWS/ArraySvc.asmx.</span><span class="sxs-lookup"><span data-stu-id="820e7-107">For example: http://localhost/ArrayWS/ArraySvc.asmx.</span></span>  
  
1.  <span data-ttu-id="820e7-108">Ajoutez une référence Web à cette URL dans le projet Visual Studio qui contient votre orchestration :</span><span class="sxs-lookup"><span data-stu-id="820e7-108">Add a Web reference to this URL in the Visual Studio project that contains your orchestration:</span></span>  
  
    -   <span data-ttu-id="820e7-109">Dans l’Explorateur de solutions, cliquez sur **références**, puis cliquez sur **ajouter une référence de Service**.</span><span class="sxs-lookup"><span data-stu-id="820e7-109">In the Solution Explorer, right-click **References**, and click **Add Service Reference**.</span></span>  
  
    -   <span data-ttu-id="820e7-110">Dans le **ajouter une référence de Service** boîte de dialogue, cliquez sur **avancé**.</span><span class="sxs-lookup"><span data-stu-id="820e7-110">In the **Add Service Reference** dialog box, click **Advanced**.</span></span>  
  
    -   <span data-ttu-id="820e7-111">Dans le **paramètres de référence de Service** boîte de dialogue, cliquez sur **ajouter une référence Web** dans les **compatibilité** section.</span><span class="sxs-lookup"><span data-stu-id="820e7-111">In the **Service Reference Settings** dialog box, click **Add Web Reference** in the **Compatibility** section.</span></span>  
  
    -   <span data-ttu-id="820e7-112">Dans le **ajouter une référence Web** boîte de dialogue, entrez l’URL du service Web dans le **URL** zone de texte, puis cliquez sur **accédez**.</span><span class="sxs-lookup"><span data-stu-id="820e7-112">In the **Add Web Reference** dialog box, enter the URL for the Web service into the **URL** text box and then click **Go**.</span></span>  
  
    -   <span data-ttu-id="820e7-113">Entrez un nom pour la référence Web dans le **nom de référence Web** zone de texte et cliquez sur le **ajouter une référence** bouton.</span><span class="sxs-lookup"><span data-stu-id="820e7-113">Enter a name for the Web reference into the **Web reference name** text box and click the **Add Reference** button.</span></span>  
  
    -   <span data-ttu-id="820e7-114">La référence Web s’affiche sous **références Web** dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="820e7-114">The Web reference will appear under **Web References** in the Solution Explorer.</span></span>  
  
        > [!TIP]
        >  <span data-ttu-id="820e7-115">Une fois que vous avez ajouté au projet, une référence Web le **ajouter une référence Web** commande est directement disponible lorsque vous cliquez sur le nom du projet ou **références** ou **lesréférencesWeb**.</span><span class="sxs-lookup"><span data-stu-id="820e7-115">Once you have a Web reference added to the project, the **Add Web Reference** command is directly available when you right-click the project name or **References** or **Web References**.</span></span>  
  
2.  <span data-ttu-id="820e7-116">Ajouter un port Web à votre orchestration :</span><span class="sxs-lookup"><span data-stu-id="820e7-116">Add a Web port to your orchestration:</span></span>  
  
    -   <span data-ttu-id="820e7-117">Faites glisser un **Port** met en évidence la forme à partir de la boîte à outils à un de port dans le Concepteur d’Orchestration pour lancer le **Assistant Configuration du Port**.</span><span class="sxs-lookup"><span data-stu-id="820e7-117">Drag a **Port** shape from the toolbox to one of the port surfaces in the Orchestration Designer to launch the **Port Configuration Wizard**.</span></span> <span data-ttu-id="820e7-118">Cliquez sur le **suivant** situé dans le **Assistant Configuration du Port** pour afficher les **propriétés de Port** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="820e7-118">Click the **Next** button in the **Port Configuration Wizard** to display the **Port Properties** dialog.</span></span>  
  
    -   <span data-ttu-id="820e7-119">Entrez une valeur dans la **nom** zone de texte pour identifier le port, puis cliquez sur le **suivant** bouton pour afficher la **sélectionner un Type de Port** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="820e7-119">Enter a value into the **Name** text box to identify the port, and click the **Next** button to display the **Select a Port Type** dialog.</span></span>  
  
    -   <span data-ttu-id="820e7-120">Sélectionnez l’option de **utiliser un Type de Port existant**, sélectionnez le Port Web type qui correspond au site Web référence ajoutée, puis cliquez sur le **suivant** bouton pour afficher la **deliaisondePort**boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="820e7-120">Select the option to **Use an existing Port Type**, select the Web Port type that corresponds to the Web reference you added, and click the **Next** button to display the **Port Binding** dialog.</span></span>  
  
    -   <span data-ttu-id="820e7-121">Dans le **liaison de Port** boîte de dialogue Sélectionnez la **liaison de Port** , puis cliquez sur le **suivant** , puis cliquez sur le **Terminer** bouton.</span><span class="sxs-lookup"><span data-stu-id="820e7-121">In the **Port Binding** dialog select the appropriate **Port binding** option and click the **Next** button, then click the **Finish** button.</span></span> <span data-ttu-id="820e7-122">Vous devez maintenant avoir un port Web affiché dans le Concepteur d’Orchestration qui inclut les opérations prises en charge par le service Web.</span><span class="sxs-lookup"><span data-stu-id="820e7-122">You should now have a Web port displayed in the Orchestration Designer that includes the operations supported by the Web service.</span></span>  
  
3.  <span data-ttu-id="820e7-123">Ajouter **envoyer** et **réception** formes à votre Orchestration comme il convient :</span><span class="sxs-lookup"><span data-stu-id="820e7-123">Add **Send** and **Receive** shapes to your Orchestration as appropriate:</span></span>  
  
    -   <span data-ttu-id="820e7-124">Faites glisser un **envoyer** forme à partir de la boîte à outils vers une ligne de connexion dans l’aire du Concepteur d’Orchestration pour configurer l’orchestration pour envoyer un message de demande au port Web.</span><span class="sxs-lookup"><span data-stu-id="820e7-124">Drag a **Send** shape from the toolbox to a connecting line in the Orchestration Designer surface to configure the orchestration to send a request message to the Web port.</span></span> <span data-ttu-id="820e7-125">Si vous vous connectez le **envoyer** forme une du port Web demandent des connecteurs de message, BizTalk crée automatiquement un message du type approprié à utiliser lors de l’envoi d’un message de demande à ce port.</span><span class="sxs-lookup"><span data-stu-id="820e7-125">If you connect the **Send** shape to one of the Web port request message connectors, BizTalk will automatically create a message of the appropriate type to be used when sending a request message to this port.</span></span>  
  
    -   <span data-ttu-id="820e7-126">Faites glisser un **réception** forme à partir de la boîte à outils vers une ligne de connexion dans l’aire du Concepteur d’Orchestration pour configurer l’orchestration pour recevoir un message de réponse du port Web.</span><span class="sxs-lookup"><span data-stu-id="820e7-126">Drag a **Receive** shape from the toolbox to a connecting line in the Orchestration Designer surface to configure the orchestration to receive a response message from the Web port.</span></span> <span data-ttu-id="820e7-127">Si vous vous connectez le **réception** forme à un des connecteurs de message de réponse de port Web, BizTalk crée automatiquement un message du type approprié à utiliser lors de la réception d’un message de réponse à partir de ce port.</span><span class="sxs-lookup"><span data-stu-id="820e7-127">If you connect the **Receive** shape to one of the Web port response message connectors, BizTalk will automatically create a message of the appropriate type to be used when receiving a response message from this port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="820e7-128">L'adaptateur SOAP permet d'envoyer des messages à un service Web ou d'en recevoir d'un service Web.</span><span class="sxs-lookup"><span data-stu-id="820e7-128">Use the SOAP Adapter to send messages to or receive messages from a Web service.</span></span> <span data-ttu-id="820e7-129">Pour plus d’informations sur la configuration de l’adaptateur SOAP, consultez [configuration de l’adaptateur SOAP](../core/configuring-the-soap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="820e7-129">For more information about configuring the SOAP Adapter see [Configuring the SOAP Adapter](../core/configuring-the-soap-adapter.md).</span></span>  
  
 <span data-ttu-id="820e7-130">Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] moteur d’Orchestration fournit la prise en charge pour les deux une consommation de tableaux et en escalier exposés par les services Web.</span><span class="sxs-lookup"><span data-stu-id="820e7-130">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Orchestration Engine provides support for consuming both one dimensional and jagged arrays that are exposed by Web services.</span></span> <span data-ttu-id="820e7-131">Si vous ajoutez une référence Web à un service Web qui expose des tableaux, le Concepteur d'orchestration génère un type de message Web qui décrit le tableau.</span><span class="sxs-lookup"><span data-stu-id="820e7-131">If you add a Web reference to a Web service that exposes arrays, the Orchestration Designer will generate a Web message type that describes the array.</span></span> <span data-ttu-id="820e7-132">Vous pouvez alors envoyer et recevoir des messages de ce type comme n'importe quel autre message.</span><span class="sxs-lookup"><span data-stu-id="820e7-132">You can then send and receive messages of this type like any other message.</span></span> <span data-ttu-id="820e7-133">BizTalk Server ne limite pas l'envoi de messages Web contenant des tableaux aux seuls ports Web.</span><span class="sxs-lookup"><span data-stu-id="820e7-133">BizTalk Server does not limit the sending of Web messages containing arrays to only Web ports.</span></span>  
  
 <span data-ttu-id="820e7-134">Pour obtenir un exemple d’utilisation des tableaux de service Web, consultez l’exemple du Kit de développement logiciel « Consume Web Services » et « Utilisation de Services Web with Array Parameters » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span><span class="sxs-lookup"><span data-stu-id="820e7-134">For an example of consuming Web service arrays, see the SDK sample "Consume Web Services" and "Consuming Web Services with Array Parameters" at [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="820e7-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="820e7-135">See Also</span></span>  
 [<span data-ttu-id="820e7-136">À l’aide de Messages dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="820e7-136">Using Messages in Orchestrations</span></span>](../core/using-messages-in-orchestrations.md)