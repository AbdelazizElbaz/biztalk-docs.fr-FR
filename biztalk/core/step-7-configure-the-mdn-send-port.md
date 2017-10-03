---
title: "Étape 7 : Configurer le Port d’envoi MDN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 983033ac-9d32-47c8-9bb8-b4161bcdf183
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0f70df6846553e2d64711f33e8c5a0b0e4d2cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-configure-the-mdn-send-port"></a><span data-ttu-id="b24de-102">Étape 7 : Configurer le Port d’envoi MDN</span><span class="sxs-lookup"><span data-stu-id="b24de-102">Step 7: Configure the MDN Send Port</span></span>
<span data-ttu-id="b24de-103">![Étape 7 11](../core/media/tut-step7-of-11.gif "Tut_Step7_of_11")</span><span class="sxs-lookup"><span data-stu-id="b24de-103">![Step 7 of 11](../core/media/tut-step7-of-11.gif "Tut_Step7_of_11")</span></span>  
  
 <span data-ttu-id="b24de-104">Dans cette étape, vous définissez un port d’envoi dynamique pour envoyer un MDN asynchrone à le \\dossier _MDNToFabrikam.</span><span class="sxs-lookup"><span data-stu-id="b24de-104">In this step, you set up a dynamic send port to send an asynchronous MDN to the \\_MDNToFabrikam folder.</span></span> <span data-ttu-id="b24de-105">Ce port d'envoi fait appel au pipeline d'envoi AS2Send pour générer la réponse MDN sortante.</span><span class="sxs-lookup"><span data-stu-id="b24de-105">This send port uses the AS2Send send pipeline to generate the outgoing MDN response.</span></span> <span data-ttu-id="b24de-106">Dans la mesure où il s’agit d’un port d’envoi dynamique, il utilisera l’adresse dans la ligne Receipt-Delivery-Option dans l’en-tête du message pour router le message vers le \\dossier _MDNToFabrikam.</span><span class="sxs-lookup"><span data-stu-id="b24de-106">Since this is a dynamic send port, it will use the address in the Receipt-Delivery-Option line in the header of the message to route the message to the \\_MDNToFabrikam folder.</span></span> <span data-ttu-id="b24de-107">Cette adresse pointe vers le répertoire virtuel Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="b24de-107">That address is the Fabrikam virtual directory.</span></span> <span data-ttu-id="b24de-108">Le fichier Default.aspx.cs associé à ce répertoire virtuel permet de créer le MDN avec une extension .msg, puis de l'envoyer dans le dossier de destination (lequel est également spécifié à la ligne Receipt-Delivery-Option).</span><span class="sxs-lookup"><span data-stu-id="b24de-108">The Default.aspx.cs file associated with that virtual directory builds the MDN with an .msg extension, and sends the file to the destination folder (which is also specified in Receipt-Delivery-Option).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b24de-109">Vous pouvez également configurer l'accord de manière à envoyer le MDN à une autre adresse en remplaçant les paramètres du message par ceux de l'accord.</span><span class="sxs-lookup"><span data-stu-id="b24de-109">You can also configure the agreement to send the MDN to another address, by overriding the message settings with the agreement settings.</span></span> <span data-ttu-id="b24de-110">Pour plus d'informations, consultez</span><span class="sxs-lookup"><span data-stu-id="b24de-110">For more information, see</span></span>  
  
 <span data-ttu-id="b24de-111">Dans cet exemple, le MDN est envoyé à l'aide d'un port d'envoi dynamique ; vous pouvez toutefois utiliser un port d'envoi statique afin d'envoyer le MDN à une adresse statique.</span><span class="sxs-lookup"><span data-stu-id="b24de-111">In this example the MDN is sent using a dynamic send port; however you can also use a static send port to send the MDN to a static address.</span></span> <span data-ttu-id="b24de-112">Pour plus d’informations, consultez [configuration d’un Port d’envoi statique pour les MDN asynchrones via AS2](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md) et [configuration d’un Port d’envoi dynamique pour les MDN asynchrones via AS2](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md).</span><span class="sxs-lookup"><span data-stu-id="b24de-112">For more information, see [Configuring a Static Send Port for Asynchronous MDNs over AS2](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md) and [Configuring a Dynamic Send Port for Asynchronous MDNs over AS2](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b24de-113">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b24de-113">Prerequisites</span></span>  
 <span data-ttu-id="b24de-114">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b24de-114">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-create-the-sendasyncmdn-send-port"></a><span data-ttu-id="b24de-115">Pour créer le port d'envoi Send_Async_MDN</span><span class="sxs-lookup"><span data-stu-id="b24de-115">To create the Send_Async_MDN send port</span></span>  
  
1.  <span data-ttu-id="b24de-116">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, sous le nœud BizTalk Application 1, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **dynamique Port d’envoi unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="b24de-116">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the BizTalk Application 1 node, right-click **Send Ports**, point to **New**, and then click **Dynamic One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="b24de-117">Dans le **propriétés de Port d’envoi** boîte de dialogue, nommez le port d’envoi **Send_Async_MDN**.</span><span class="sxs-lookup"><span data-stu-id="b24de-117">In the **Send Port Properties** dialog box, name the send port as **Send_Async_MDN**.</span></span>  
  
3.  <span data-ttu-id="b24de-118">Sélectionnez **AS2Send** pour **pipeline d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="b24de-118">Select **AS2Send** for **Send pipeline**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b24de-119">Le pipeline AS2Send est utilisé, car aucun traitement EDI n'est requis pour le MDN.</span><span class="sxs-lookup"><span data-stu-id="b24de-119">The AS2Send pipeline is used because no EDI processing is required for the MDN.</span></span>  
  
4.  <span data-ttu-id="b24de-120">Cliquez sur **filtres** dans l’arborescence de la console.</span><span class="sxs-lookup"><span data-stu-id="b24de-120">Click **Filters** in the console tree.</span></span> <span data-ttu-id="b24de-121">Dans le volet filtres, sélectionnez **EdiIntAS.IsAS2AsynchronousMdn** pour **propriété**,  **==**  pour **opérateur**, entrez **True** pour **valeur**.</span><span class="sxs-lookup"><span data-stu-id="b24de-121">In the Filters pane, select **EdiIntAS.IsAS2AsynchronousMdn** for **Property**, **==** for **Operator**, and enter **True** for **Value**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b24de-122">Ce filtre garantit que le port d'envoi dynamique récupère uniquement les MDN asynchrones dans MessageBox.</span><span class="sxs-lookup"><span data-stu-id="b24de-122">This filter ensures that the dynamic send port only picks up asynchronous MDNs from the MessageBox.</span></span>  
  
5.  <span data-ttu-id="b24de-123">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b24de-123">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="b24de-124">Dans le **Ports d’envoi** volet de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit **Send_Async_MDN**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="b24de-124">In the **Send Ports** pane of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **Send_Async_MDN**, and then click **Start**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b24de-125">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b24de-125">Next Steps</span></span>  
 <span data-ttu-id="b24de-126">Configurer le port d’envoi (**Send_Async_997**) pour envoyer le 997 accusé de réception vers Fabrikam, comme décrit dans [étape 8 : configurer le Port d’envoi 997](../core/step-8-configure-the-997-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="b24de-126">You configure the send port (**Send_Async_997**) to send the 997 acknowledgement back to Fabrikam, as described in [Step 8: Configure the 997 Send Port](../core/step-8-configure-the-997-send-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b24de-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b24de-127">See Also</span></span>  
 <span data-ttu-id="b24de-128">[Envoi des Messages AS2 par BizTalk Server](../core/how-biztalk-server-sends-as2-messages.md) </span><span class="sxs-lookup"><span data-stu-id="b24de-128">[How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md) </span></span>  
 <span data-ttu-id="b24de-129">[Configuration d’un Port d’envoi statique pour les MDN asynchrones via AS2](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md) </span><span class="sxs-lookup"><span data-stu-id="b24de-129">[Configuring a Static Send Port for Asynchronous MDNs over AS2](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md) </span></span>  
 [<span data-ttu-id="b24de-130">Configuration d’un Port d’envoi dynamique pour les Messages via AS2</span><span class="sxs-lookup"><span data-stu-id="b24de-130">Configuring a Dynamic Send Port for Messages over AS2</span></span>](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md)