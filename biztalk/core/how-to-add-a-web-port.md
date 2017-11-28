---
title: "L’ajout d’un Port Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web ports, creating
- creating, Web ports
ms.assetid: da94d98e-10ca-437a-ba34-7aa6efc68f3d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42e9853755788aa29d3ca7506829dcd6bdfed53d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-web-port"></a><span data-ttu-id="3ccd5-102">Ajout d'un port Web</span><span class="sxs-lookup"><span data-stu-id="3ccd5-102">How to Add a Web Port</span></span>
<span data-ttu-id="3ccd5-103">L'ajout d'un port Web sur la surface d'un port s'effectue dans le Concepteur d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-103">You add a Web port on the port surface in Orchestration Designer.</span></span> <span data-ttu-id="3ccd5-104">Contrairement aux autres ports configurés, les ports Web prennent en charge une combinaison d'opérations de requête (unidirectionnelles) et de requête-réponse (bidirectionnelles).</span><span class="sxs-lookup"><span data-stu-id="3ccd5-104">Unlike other configured ports, Web ports support a mixture of request (one-way) and request/response (two-way) operations.</span></span> <span data-ttu-id="3ccd5-105">Chaque opération au niveau du port Web représente une méthode Web.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-105">Each operation in the Web port represents a Web method.</span></span> <span data-ttu-id="3ccd5-106">Si la méthode Web contient *d’entrée* et *sortie* paramètres, BizTalk crée une opération de demande/réponse.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-106">If the Web method contains *input* and *output* parameters, BizTalk creates a request/response operation.</span></span> <span data-ttu-id="3ccd5-107">Si le service Web contient uniquement un *d’entrée* paramètre, BizTalk crée uniquement une opération unidirectionnelle.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-107">If the Web service contains only an *input* parameter, BizTalk only creates a one-way operation.</span></span>  
  
### <a name="to-add-a-web-port"></a><span data-ttu-id="3ccd5-108">Pour ajouter un port Web</span><span class="sxs-lookup"><span data-stu-id="3ccd5-108">To add a Web port</span></span>  
  
1.  <span data-ttu-id="3ccd5-109">Dans le Concepteur d’Orchestration, avec une orchestration est ouverte, cliquez sur la surface du port, puis sélectionnez **nouveau Port configuré**.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-109">In Orchestration Designer, with an orchestration open, right-click the port surface, and then select **New Configured Port**.</span></span>  
  
2.  <span data-ttu-id="3ccd5-110">Dans la page **Bienvenue dans l'Assistant Configuration du port** , cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-110">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="3ccd5-111">Sur le **propriétés de Port** page, dans le **nom** zone de texte, tapez un nom pour le port, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-111">On the **Port Properties** page, in the **Name** text box, type a name for the port, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="3ccd5-112">Dans le **sélectionner un Type de Port** , sélectionnez **utiliser un Type de Port existant**.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-112">In the **Select a Port Type** page, select **Use an existing Port Type**.</span></span>  
  
5.  <span data-ttu-id="3ccd5-113">Dans le **Types de ports disponibles** , développez le **Types de ports Web** nœud et sélectionnez le site Web type qui correspond au service Web ajouté de port, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-113">In the **Available Port Types** box, expand the **Web Port Types** node and select the Web port type that corresponds to the added Web service, and then click **Next**.</span></span>  
  
     <span data-ttu-id="3ccd5-114">L’illustration suivante montre le **sélectionner un Type de Port** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-114">The following figure shows the **Select a Port Type** dialog box.</span></span>  
  
     ![](../core/media/ebiz-prog-ws-addwebport.gif "ebiz_prog_ws_addwebport")  
  
6.  <span data-ttu-id="3ccd5-115">Dans le **liaison de Port** page, dans le **liaison de Port** liste déroulante, sélectionnez **spécifier maintenant**.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-115">In the **Port Binding** page, in the **Port binding** drop down box, select **Specify now**.</span></span> <span data-ttu-id="3ccd5-116">BizTalk place automatiquement les valeurs du service Web référencé dans l'URI, le transport et le pipeline d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-116">BizTalk automatically places the values from the referenced Web service in the URI, transport, and receive and send pipelines.</span></span> <span data-ttu-id="3ccd5-117">Il exploite ces valeurs pour créer le port d'envoi lors du déploiement de votre projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-117">BizTalk uses these values to create the send port when you deploy your BizTalk project.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3ccd5-118">La méthode d'authentification par défaut pour le port d'envoi est l'authentification anonyme.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-118">The default authentication method for the send port is anonymous access.</span></span> <span data-ttu-id="3ccd5-119">Si un service Web demande une autre méthode d'authentification ou de chiffrement, vous devez modifier la configuration de manière à fournir les informations d'identification utilisateur appropriées ou utiliser SSL (Secure Sockets Layer) pour exécuter les services Web.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-119">If the Web service requires a different authentication or encryption method, you must change the configuration to supply the appropriate user credentials or Secure Sockets Layer (SSL) to run Web services.</span></span> <span data-ttu-id="3ccd5-120">Pour plus d’informations, consultez [: adaptateur d’envoi SOAP](../core/soap-send-adapter.md) et [exemple TMA : adaptateurs HTTP et SOAP](../core/sample-tma-http-and-soap-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="3ccd5-120">For more information, see [SOAP Send Adapter](../core/soap-send-adapter.md) and [Sample TMA: HTTP and SOAP Adapters](../core/sample-tma-http-and-soap-adapters.md).</span></span>  
  
7.  <span data-ttu-id="3ccd5-121">Cliquez sur **suivant**, puis **Terminer** pour terminer l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="3ccd5-121">Click **Next**, and then **Finish** to complete the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ccd5-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ccd5-122">See Also</span></span>  
 <span data-ttu-id="3ccd5-123">[Comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="3ccd5-123">[How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md) </span></span>  
 [<span data-ttu-id="3ccd5-124">Création de Ports Web</span><span class="sxs-lookup"><span data-stu-id="3ccd5-124">Creating Web Ports</span></span>](../core/creating-web-ports.md)