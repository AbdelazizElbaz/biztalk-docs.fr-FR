---
title: "Étape 2 : Configurer un Port d’envoi WCF-WebHttp bidirectionnel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bcab296-7921-4df4-abcc-eea78cc827e8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f355275f9480cfa13f3a15bcc6522fbe7ec83b8c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-a-two-way-wcf-webhttp-send-port"></a><span data-ttu-id="de082-102">Étape 2 : Configurer un Port d’envoi WCF-WebHttp bidirectionnel</span><span class="sxs-lookup"><span data-stu-id="de082-102">Step 2: Configure a Two-way WCF-WebHttp Send Port</span></span>
<span data-ttu-id="de082-103">Dans cette étape, vous configurez un texte bidirectionnel **WCF-WebHttp** port d’envoi pour appeler l’URL de ressource REST pour récupérer des retards dans les planifications des transporteurs aériens américains.</span><span class="sxs-lookup"><span data-stu-id="de082-103">In this step you configure a two-way **WCF-WebHttp** send port to invoke the REST resource URL to retrieve delays in the US air carriers’ schedules.</span></span>  
  
### <a name="to-configure-wcf-webhttp-send-port"></a><span data-ttu-id="de082-104">Pour configurer le port d’envoi WCF-WebHttp</span><span class="sxs-lookup"><span data-stu-id="de082-104">To configure WCF-WebHttp send port</span></span>  
  
1.  <span data-ttu-id="de082-105">À partir de la Console Administration de BizTalk Server, sous la **BizTalk Application 1** nœud, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **statique Port d’envoi de sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="de082-105">From BizTalk Server Administration Console, under the **BizTalk Application 1** node, right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
2.  <span data-ttu-id="de082-106">Sous l'onglet **Général** , effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="de082-106">On the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="de082-107">Utiliser</span><span class="sxs-lookup"><span data-stu-id="de082-107">Use this</span></span>|<span data-ttu-id="de082-108">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="de082-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="de082-109">**Nom**</span><span class="sxs-lookup"><span data-stu-id="de082-109">**Name**</span></span>|<span data-ttu-id="de082-110">Type **SendPortRESTAzureMarketPlace**.</span><span class="sxs-lookup"><span data-stu-id="de082-110">Type **SendPortRESTAzureMarketPlace**.</span></span>|  
    |<span data-ttu-id="de082-111">**Type**</span><span class="sxs-lookup"><span data-stu-id="de082-111">**Type**</span></span>|<span data-ttu-id="de082-112">Sélectionnez **WCF-WebHttp**.</span><span class="sxs-lookup"><span data-stu-id="de082-112">Select **WCF-WebHttp**.</span></span>|  
    |<span data-ttu-id="de082-113">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="de082-113">**Send handler**</span></span>|<span data-ttu-id="de082-114">Sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="de082-114">Select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="de082-115">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="de082-115">**Send pipeline**</span></span>|<span data-ttu-id="de082-116">Sélectionnez **PassThruTransmit**.</span><span class="sxs-lookup"><span data-stu-id="de082-116">Select **PassThruTransmit**.</span></span>|  
    |<span data-ttu-id="de082-117">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="de082-117">**Receive pipeline**</span></span>|<span data-ttu-id="de082-118">Sélectionnez **PassThruReceive**.</span><span class="sxs-lookup"><span data-stu-id="de082-118">Select **PassThruReceive**.</span></span>|  
  
     <span data-ttu-id="de082-119">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="de082-119">Click **Configure**.</span></span>  
  
3.  <span data-ttu-id="de082-120">À partir de la **propriétés du Transport WCF-WebHttp** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="de082-120">From the **WCF-WebHttp Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="de082-121">Sur le **général** onglet, pour **adresse (URI)**, entrez `https://api.datamarket.azure.com/oakleaf/US_Air_Carrier_Flight_Delays_Incr/`.</span><span class="sxs-lookup"><span data-stu-id="de082-121">On the **General** tab, for **Address (URI)**, enter `https://api.datamarket.azure.com/oakleaf/US_Air_Carrier_Flight_Delays_Incr/`.</span></span>  
  
    2.  <span data-ttu-id="de082-122">Sous l’onglet Général, pour **méthode HTTP et mappage d’URL**, entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="de082-122">On the General tab, for **HTTP Method and URL Mapping**, enter the following:</span></span>  
  
        ```  
        <BtsHttpUrlMapping>  
        <Operation Method="GET" Url="/On_Time_Performance" />  
        </BtsHttpUrlMapping>  
  
        ```  
  
         <span data-ttu-id="de082-123">Ici, **obtenir** est le verbe HTTP et **On_Time_Performance** est ajouté à l’URI de base pour construire une URL de ressource unique pour extraire les retards de vol.</span><span class="sxs-lookup"><span data-stu-id="de082-123">Here, **GET** is the HTTP verb and **On_Time_Performance** is appended to the base URI to construct a unique resource URL to retrieve flight delays.</span></span>  
         
         > [!TIP] 
         > <span data-ttu-id="de082-124">Dans le champ URL, tous les caractères XML spéciaux doivent être « échappés ».</span><span class="sxs-lookup"><span data-stu-id="de082-124">Within the URL field, any special XML characters must be "escaped".</span></span> <span data-ttu-id="de082-125">Cela garantit que les caractères XML spéciaux sont traitées et conservées par le port.</span><span class="sxs-lookup"><span data-stu-id="de082-125">This ensures that the special XML characters are processed, and preserved by the port.</span></span> <span data-ttu-id="de082-126">Par exemple, le `&` caractères spéciaux doivent être échappés en tant que `&amp;`.</span><span class="sxs-lookup"><span data-stu-id="de082-126">For example, the `&` special character must be escaped as `&amp;`.</span></span> 
           >
           ><span data-ttu-id="de082-127">De :`Url=”/Customer?{ID}& group=Location”`</span><span class="sxs-lookup"><span data-stu-id="de082-127">From: `Url=”/Customer?{ID}& group=Location”`</span></span>
           >
           >
           ><span data-ttu-id="de082-128">À :`Url=”/Customer?{ID}&amp;group=Location”`</span><span class="sxs-lookup"><span data-stu-id="de082-128">To: `Url=”/Customer?{ID}&amp;group=Location”`</span></span>
  
    3.  <span data-ttu-id="de082-129">Sur le **liaisons** onglet, pour le **taille de Message maximale reçus** , sélectionnez une valeur suffisamment élevée.</span><span class="sxs-lookup"><span data-stu-id="de082-129">On the **Bindings** tab, for the **Maximum Received Message Size** field, select a sufficiently large value.</span></span> <span data-ttu-id="de082-130">car généralement, le message de réponse contenant les informations sur le vol est relativement volumineux et risque de dépasser la taille des messages spécifiée par défaut.</span><span class="sxs-lookup"><span data-stu-id="de082-130">That’s because typically the response message containing the flight status is considerably large and might exceed the default message size specified.</span></span>  
  
    4.  <span data-ttu-id="de082-131">Sur le **sécurité** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="de082-131">On the **Security** tab, do the following:</span></span>  
  
        1.  <span data-ttu-id="de082-132">Pour le **mode de sécurité**, sélectionnez **Transport**.</span><span class="sxs-lookup"><span data-stu-id="de082-132">For the **Security mode**, select **Transport**.</span></span>  
  
        2.  <span data-ttu-id="de082-133">Pour **type d’informations d’identification du client du Transport**, sélectionnez **base**.</span><span class="sxs-lookup"><span data-stu-id="de082-133">For **Transport client credential type**, select **Basic**.</span></span>  
  
        3.  <span data-ttu-id="de082-134">Sous le **informations d’identification utilisateur** , cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="de082-134">Under the **User name credentials** box, click **Edit**.</span></span> <span data-ttu-id="de082-135">Dans le **informations d’identification Client** boîte de dialogue, sélectionnez **ne pas utiliser l’authentification unique sur**et entrez le nom d’utilisateur et un mot de passe que vous avez récupéré à partir de la **mon compte** onglet une fois que vous avez connecté à [Windows Azure Marketplace](http://go.microsoft.com/fwlink/p/?LinkId=257913).</span><span class="sxs-lookup"><span data-stu-id="de082-135">In the **Client Credentials** dialog box, select **Do no use Single-Sign On**, and enter the username and password that you retrieved from the **My Account** tab after you have logged into [Windows Azure Marketplace](http://go.microsoft.com/fwlink/p/?LinkId=257913).</span></span> <span data-ttu-id="de082-136">Les informations d’identification sont répertoriées par rapport à la **ID de client** (nom d’utilisateur) et **clé de compte primaire** les étiquettes (mot de passe).</span><span class="sxs-lookup"><span data-stu-id="de082-136">The credentials are listed against the **Customer ID** (user name) and **Primary Account Key** (password) labels.</span></span>  
  
        4.  <span data-ttu-id="de082-137">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="de082-137">Click **OK**.</span></span>  
  
    5.  <span data-ttu-id="de082-138">Sur le **Messages** onglet, pour **supprimer le corps en fonction de verbes**, spécifiez le verbe pour lequel vous souhaitez supprimer la charge du message de demande.</span><span class="sxs-lookup"><span data-stu-id="de082-138">On the **Messages** tab, for **Suppress Body for Verbs**, specify the verb for which you want to strip the message payload from the request message.</span></span> <span data-ttu-id="de082-139">Pour ce didacticiel, spécifiez `GET`.</span><span class="sxs-lookup"><span data-stu-id="de082-139">For this tutorial, specify this as `GET`.</span></span> <span data-ttu-id="de082-140">Voici pourquoi : un appel de méthode GET au point de terminaison REST des retards de vol transporteurs aériens américains ne nécessite pas une charge utile de message ; l’URL de ressource REST suffit récupérer les informations.</span><span class="sxs-lookup"><span data-stu-id="de082-140">Here’s why: A GET method call on the US Air Carrier flight delays REST endpoint does not require a message payload; the REST resource URL is sufficient to retrieve the information.</span></span> <span data-ttu-id="de082-141">Toutefois, pour déclencher le **WCF-WebHttp** port d’envoi qui effectue l’appel REST, vous déposez un message factice comportant un corps de message.</span><span class="sxs-lookup"><span data-stu-id="de082-141">However, to trigger the **WCF-WebHttp** send port that makes the REST call, you drop a dummy message that has some message body.</span></span> <span data-ttu-id="de082-142">Le port d’envoi ne doit pas envoyer ce message factice au point de terminaison REST, car, comme expliqué plus haut, le point de terminaison n’attend pas de charge de message.</span><span class="sxs-lookup"><span data-stu-id="de082-142">The send port must not send that dummy message to the REST endpoint because, as explained earlier, the endpoint does not expect a message payload.</span></span> <span data-ttu-id="de082-143">Par conséquent, avant d’appeler le point de terminaison REST, l’adaptateur supprime la charge utile de message du message factice uniquement pour les verbes que vous spécifiez dans le **supprimer le corps en fonction de verbes** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="de082-143">So, before invoking the REST endpoint, the adapter strips the message payload from the dummy message only for the verbs that you specify in the **Suppress Body for Verbs** text box.</span></span>  
  
    6.  <span data-ttu-id="de082-144">Cliquez sur **OK** jusqu'à ce que vous êtes dans la boîte de dialogue Propriétés de Port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="de082-144">Click **OK** until you are back on the Send Port Properties dialog box.</span></span> <span data-ttu-id="de082-145">Dans le volet gauche, cliquez sur **filtres**et spécifiez le filtre à utiliser tous les messages reçus via la réception du port que vous avez créé dans [étape 1 : configurer un emplacement de réception du fichier](../core/step-1-configure-a-file-receive-location.md).</span><span class="sxs-lookup"><span data-stu-id="de082-145">From the left pane, click **Filters**, and specify the filter to consume all messages that are received through the receive port you created in [Step 1: Configure a FILE Receive Location](../core/step-1-configure-a-file-receive-location.md).</span></span>  
  
        |||  
        |-|-|  
        |<span data-ttu-id="de082-146">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="de082-146">**Property**</span></span>|<span data-ttu-id="de082-147">La valeur **BTS. ReceivePortName**</span><span class="sxs-lookup"><span data-stu-id="de082-147">Set to **BTS.ReceivePortName**</span></span>|  
        |<span data-ttu-id="de082-148">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="de082-148">**Operator**</span></span>|<span data-ttu-id="de082-149">La valeur**==**</span><span class="sxs-lookup"><span data-stu-id="de082-149">Set to **==**</span></span>|  
        |<span data-ttu-id="de082-150">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="de082-150">**Value**</span></span>|<span data-ttu-id="de082-151">La valeur`ReceivePortRestAzureMarketPlace`</span><span class="sxs-lookup"><span data-stu-id="de082-151">Set to `ReceivePortRestAzureMarketPlace`</span></span>|  
  
    7.  <span data-ttu-id="de082-152">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="de082-152">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de082-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de082-153">See Also</span></span>  
 [<span data-ttu-id="de082-154">Didacticiel de 5 : Appeler une Interface REST à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="de082-154">Tutorial 5: Invoking a REST Interface Using BizTalk Server</span></span>](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)