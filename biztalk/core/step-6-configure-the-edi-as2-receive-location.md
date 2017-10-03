---
title: "Étape 6 : Configurer EDI-AS2 emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 167f8ba2-d38b-4088-863b-2bd90c2a12a2
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bbf1fce88301960a28c19fa20c9996282ce4619
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-configure-the-edi-as2-receive-location"></a><span data-ttu-id="03b59-102">Étape 6 : Configurer EDI-AS2 emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="03b59-102">Step 6: Configure the EDI-AS2 Receive Location</span></span>
<span data-ttu-id="03b59-103">![Étape 6 sur 11](../core/media/tut-step6-of-11.gif "Tut_Step6_of_11")</span><span class="sxs-lookup"><span data-stu-id="03b59-103">![Step 6 of 11](../core/media/tut-step6-of-11.gif "Tut_Step6_of_11")</span></span>  
  
 <span data-ttu-id="03b59-104">Au cours de cette étape, vous allez configurer un emplacement de réception unidirectionnel qui reçoit le message EDI du tiers Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="03b59-104">In this step, you set up a one-way receive location that receives the EDI message from the Fabrikam party.</span></span> <span data-ttu-id="03b59-105">Cet emplacement de réception utilise le pipeline de réception AS2EdiReceive pour traiter le message EDI/AS2 entrant.</span><span class="sxs-lookup"><span data-stu-id="03b59-105">This receive location uses the AS2EdiReceive receive pipeline to process the incoming EDI/AS2 message.</span></span> <span data-ttu-id="03b59-106">Le message est envoyé vers l'emplacement de réception par l'application sender.exe via le répertoire virtuel Contoso à l'aide de l'extension ISAPI BTSHTTPReceive.dll.</span><span class="sxs-lookup"><span data-stu-id="03b59-106">The message will be sent to the receive location by the sender.exe application through the Contoso virtual directory using the BTSHTTPReceive.dll ISAPI extension.</span></span>  
  
 <span data-ttu-id="03b59-107">Dans ce didacticiel, vous allez configurer un port d'envoi dynamique pour envoyer la réponse MDN de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="03b59-107">In this tutorial, you will set up a dynamic send port to send the MDN response asynchronously.</span></span> <span data-ttu-id="03b59-108">Dans ce scénario, un seul port de réception unidirectionnel est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="03b59-108">In this scenario, only a one-way receive port is required.</span></span> <span data-ttu-id="03b59-109">Vous pouvez toutefois également modifier l'exécutable Sender.exe pour envoyer un message AS2 spécifiant un MDN synchrone.</span><span class="sxs-lookup"><span data-stu-id="03b59-109">However, you could also change Sender.exe to send an AS2 message specifying a synchronous MDN.</span></span> <span data-ttu-id="03b59-110">Vous devrez alors créer un port de réception de requête-réponse bidirectionnel pour renvoyer le MDN.</span><span class="sxs-lookup"><span data-stu-id="03b59-110">You would then have to create a two-way request response receive port to return the MDN.</span></span> <span data-ttu-id="03b59-111">Pour plus d’informations, consultez la section « pour tester la solution » de [procédure pas à pas (AS2) : réception d’EDI via AS2 avec un MDN synchrone](../core/walkthrough-as2-receiving-edi-over-as2-with-a-synchronous-mdn.md).</span><span class="sxs-lookup"><span data-stu-id="03b59-111">For more information, see the "To test the solution" section of [Walkthrough (AS2): Receiving EDI over AS2 with a Synchronous MDN](../core/walkthrough-as2-receiving-edi-over-as2-with-a-synchronous-mdn.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="03b59-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="03b59-112">Prerequisites</span></span>  
 <span data-ttu-id="03b59-113">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03b59-113">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-create-the-biztalk-http-receive-location"></a><span data-ttu-id="03b59-114">Pour créer l'emplacement de réception HTTP BizTalk</span><span class="sxs-lookup"><span data-stu-id="03b59-114">To create the BizTalk HTTP receive location</span></span>  
  
1.  <span data-ttu-id="03b59-115">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, sous le nœud BizTalk Application 1, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="03b59-115">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the BizTalk Application 1 node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2.  <span data-ttu-id="03b59-116">Nommez le port de réception **Receive_AS2**.</span><span class="sxs-lookup"><span data-stu-id="03b59-116">Name the receive port as **Receive_AS2**.</span></span>  
  
3.  <span data-ttu-id="03b59-117">Cliquez sur **emplacements de réception** dans l’arborescence de la console, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="03b59-117">Click **Receive Locations** in the console tree, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="03b59-118">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, le nom de votre emplacement de réception **Receive_AS2**, sélectionnez **HTTP** pour **Type**, puis Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="03b59-118">In the **Receive Location Properties** dialog box, name your receive location **Receive_AS2**, select **HTTP** for **Type**, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="03b59-119">Dans le **propriétés du Transport HTTP** boîte de dialogue, entrez **/Contoso/BTSHTTPReceive.dll** pour **répertoire virtuel assorti de l’extension ISAPI**.</span><span class="sxs-lookup"><span data-stu-id="03b59-119">In the **HTTP Transport Properties** dialog box, enter **/Contoso/BTSHTTPReceive.dll** for **Virtual directory plus ISAPI extension**.</span></span> <span data-ttu-id="03b59-120">Désactivez **un descripteur de corrélation de retour en cas de réussite** et sélectionnez **suspendre les requêtes ayant échoué**.</span><span class="sxs-lookup"><span data-stu-id="03b59-120">Clear **Return correlation handle on success** and select **Suspend failed requests**.</span></span> <span data-ttu-id="03b59-121">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="03b59-121">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="03b59-122">Sélectionnez **AS2EdiReceive** pour le **Pipeline de réception**.</span><span class="sxs-lookup"><span data-stu-id="03b59-122">Select **AS2EdiReceive** for the **Receive Pipeline**.</span></span> <span data-ttu-id="03b59-123">Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="03b59-123">Click **OK**, and then click **OK** again.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="03b59-124">Le pipeline de réception AS2EdiReceive effectue le décodage AS2 et le désassemblage EDI.</span><span class="sxs-lookup"><span data-stu-id="03b59-124">The AS2EdiReceive receive pipeline performs AS2 decoding and EDI disassembly.</span></span>  
  
7.  <span data-ttu-id="03b59-125">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur **emplacements de réception** sous le nœud BizTalk Application 1, avec le bouton droit **Receive_AS2**, puis cliquez sur **activer** .</span><span class="sxs-lookup"><span data-stu-id="03b59-125">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click **Receive Locations** under the BizTalk Application 1 node, right-click **Receive_AS2**, and then click **Enable**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="03b59-126">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="03b59-126">Next Steps</span></span>  
 <span data-ttu-id="03b59-127">Configurer le port d’envoi (**Send_Asynch_MDN**) port d’envoi pour renvoyer le MDN asynchrone à Fabrikam, comme décrit dans [étape 7 : configurer le Port d’envoi MDN](../core/step-7-configure-the-mdn-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="03b59-127">You configure the send port (**Send_Asynch_MDN**) send port to send the asynchronous MDN back to Fabrikam, as described in [Step 7: Configure the MDN Send Port](../core/step-7-configure-the-mdn-send-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03b59-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03b59-128">See Also</span></span>  
 <span data-ttu-id="03b59-129">[Réception des Messages AS2 par BizTalk Server](../core/how-biztalk-server-receives-as2-messages.md) </span><span class="sxs-lookup"><span data-stu-id="03b59-129">[How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md) </span></span>  
 [<span data-ttu-id="03b59-130">Configuration d’un Port de réception des Messages via AS2</span><span class="sxs-lookup"><span data-stu-id="03b59-130">Configuring a Receive Port for Messages over AS2</span></span>](../core/configuring-a-receive-port-for-messages-over-as2.md)