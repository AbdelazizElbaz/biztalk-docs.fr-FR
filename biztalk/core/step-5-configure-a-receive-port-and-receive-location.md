---
title: "Étape 5 : Configurer un Port de réception et l’emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43fc8d12-5fde-4ddf-a7f0-770f078ba66b
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8ec436657aefaceb71207d37808936aa6eaa1a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-configure-a-receive-port-and-receive-location"></a><span data-ttu-id="817d7-102">Étape 5 : Configurer un Port de réception et l’emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="817d7-102">Step 5: Configure a Receive Port and Receive Location</span></span>
<span data-ttu-id="817d7-103">![L’étape 5 de 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")</span><span class="sxs-lookup"><span data-stu-id="817d7-103">![Step 5 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")</span></span>  
  
 <span data-ttu-id="817d7-104">Cette étape permet de configurer un port et un emplacement de réception pour recevoir un message 850 dans le dossier créé pour le tiers Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="817d7-104">In this step you configure a receive port and receive location for receiving the 850 message in the folder set up for the Fabrikam party.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="817d7-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="817d7-105">Prerequisites</span></span>  
 <span data-ttu-id="817d7-106">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="817d7-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-a-receive-port-and-receive-location-for-receiving-the-850-message"></a><span data-ttu-id="817d7-107">Pour configurer un port et un emplacement de réception permettant de recevoir un message 850</span><span class="sxs-lookup"><span data-stu-id="817d7-107">To configure a receive port and receive location for receiving the 850 message</span></span>  
  
1.  <span data-ttu-id="817d7-108">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, puis **BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="817d7-108">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and then **BizTalk Application 1**.</span></span> <span data-ttu-id="817d7-109">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="817d7-109">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2.  <span data-ttu-id="817d7-110">Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , saisissez `ReceiveEDI_fromTHEM_A`.</span><span class="sxs-lookup"><span data-stu-id="817d7-110">In the Receive Port Properties dialog box, in the **Name** field, enter `ReceiveEDI_fromTHEM_A`.</span></span>  
  
3.  <span data-ttu-id="817d7-111">Cliquez sur **emplacements de réception** dans l’arborescence de la console, puis cliquez sur **nouveau** dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="817d7-111">Click **Receive Locations** in the console tree, and then click **New** in the right-hand pane.</span></span>  
  
4.  <span data-ttu-id="817d7-112">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , saisissez `fromTHEM_4010_850`.</span><span class="sxs-lookup"><span data-stu-id="817d7-112">In the **Receive Location Properties** dialog box, in the **Name** field, enter `fromTHEM_4010_850`.</span></span>  
  
5.  <span data-ttu-id="817d7-113">Pour **Type**, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="817d7-113">For **Type**, select **FILE**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="817d7-114">Le type de transport de l'emplacement de réception est FILE, car le message test est un fichier plat envoyé dans un dossier.</span><span class="sxs-lookup"><span data-stu-id="817d7-114">The transport type of the receive location is FILE because the test message is a flat file delivered into a folder.</span></span>  
  
6.  <span data-ttu-id="817d7-115">Dans le **propriétés du Transport FILE** boîte de dialogue, cliquez sur le **Parcourir** situé en regard du **dossier de réception** champ.</span><span class="sxs-lookup"><span data-stu-id="817d7-115">In the **FILE Transport Properties** dialog box, click the **Browse** button next to the **Receive folder** field.</span></span> <span data-ttu-id="817d7-116">Dans le **rechercher un dossier** boîte de dialogue, accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\fromTHEM, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="817d7-116">In the **Browse for Folder** dialog box, move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\fromTHEM, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="817d7-117">Dans le **propriétés du Transport FILE** boîte de dialogue, choisissez le **masque de fichier** à  **\*.txt** et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="817d7-117">In the **FILE Transport Properties** dialog box, change the **File mask** to **\*.txt** and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="817d7-118">Le masque de fichier est défini sur *.txt, car le message test d'entrée est un fichier texte, à savoir SamplePO.txt.</span><span class="sxs-lookup"><span data-stu-id="817d7-118">The file mask is set to *.txt because the input test message is a text file, SamplePO.txt.</span></span>  
  
8.  <span data-ttu-id="817d7-119">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Pipeline de réception** champ, sélectionnez **EdiReceive**.</span><span class="sxs-lookup"><span data-stu-id="817d7-119">In the **Receive Location Properties** dialog box, in the **Receive Pipeline** field, select **EdiReceive**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="817d7-120">Le pipeline de réception permettant de recevoir des échanges EDI, à l'exception de ceux envoyés via le transport AS2, est le pipeline EdiReceive.</span><span class="sxs-lookup"><span data-stu-id="817d7-120">The receive pipeline used to receive EDI interchanges, except for those delivered over the AS2 transport, is the EdiReceive pipeline.</span></span> <span data-ttu-id="817d7-121">(Le pipeline de réception AS2EdiReceive permet de recevoir des échanges EDI envoyés via le transport AS2.)</span><span class="sxs-lookup"><span data-stu-id="817d7-121">(The AS2EdiReceive receive pipeline is used to receive EDI interchanges delivered over the AS2 transport.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="817d7-122">Si EdiReceive ne figure pas dans la liste déroulante des pipelines de réception, cela signifie que votre application ne comporte peut-être pas de référence à l'application BizTalk EDI.</span><span class="sxs-lookup"><span data-stu-id="817d7-122">If EdiReceive is not listed in the drop-down list for receive pipeline, your application may not have a reference to the BizTalk EDI Application.</span></span> <span data-ttu-id="817d7-123">Pour ajouter la référence, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span><span class="sxs-lookup"><span data-stu-id="817d7-123">To add the reference, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  
  
9. <span data-ttu-id="817d7-124">Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="817d7-124">Click **OK**, and then click **OK** again.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="817d7-125">Le compte disposant des autorisations de connexion au service BizTalk doit également recevoir les autorisations d'accès total au dossier de réception associé à l'emplacement de réception fromTHEM_4010_850 ([!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\ProcessEDI_TestLocations\fromTHEM).</span><span class="sxs-lookup"><span data-stu-id="817d7-125">The account that has log-on privileges for the BizTalk service should also be granted full access permissions for the receive folder associated with the fromTHEM_4010_850 receive location ([!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\ProcessEDI_TestLocations\fromTHEM).</span></span> <span data-ttu-id="817d7-126">Si ce n'est pas le cas, un message d'erreur s'affichera lorsque vous tenterez d'activer l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="817d7-126">If not, you will receive an error when attempting to enable the receive location.</span></span> <span data-ttu-id="817d7-127">Pour modifier les autorisations d’accès au dossier de réception, accédez à l’onglet sécurité dans les **propriétés** boîte de dialogue pour ce dossier dans l’Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="817d7-127">To change the access permissions for the receive folder, go to the Security tab in the **Properties** dialog box for that folder in Windows Explorer.</span></span>  
  
10. <span data-ttu-id="817d7-128">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur **emplacements de réception**, avec le bouton droit **fromTHEM_4010_850**, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="817d7-128">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click **Receive Locations**, right-click **fromTHEM_4010_850**, and then click **Enable**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="817d7-129">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="817d7-129">Next Steps</span></span>  
 <span data-ttu-id="817d7-130">Configurer le port d’envoi (**toOrderSystem**) pour envoyer le message 850 à OrderSystem, comme décrit dans [étape 6 : configurer un Port d’envoi pour envoyer des données à votre organisation](../core/step-6-configure-a-send-port-to-send-data-to-your-organization.md).</span><span class="sxs-lookup"><span data-stu-id="817d7-130">You configure the send port (**toOrderSystem**) to send the 850 message to OrderSystem, as described in [Step 6: Configure a Send Port to Send Data to Your Organization](../core/step-6-configure-a-send-port-to-send-data-to-your-organization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="817d7-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="817d7-131">See Also</span></span>  
 [<span data-ttu-id="817d7-132">Configuration d’un Port pour recevoir des Messages EDI et les accusés de réception</span><span class="sxs-lookup"><span data-stu-id="817d7-132">Configuring a Port to Receive EDI Messages and Acknowledgments</span></span>](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md)