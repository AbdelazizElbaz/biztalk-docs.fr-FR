---
title: "Comment configurer BizTalk Server pour l’envoi des Messages signés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be86fbb3-de80-4d9f-bcf0-c61347704229
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ef71f5c11d6c1a000369644b822aa9f4d4ef792
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-for-sending-signed-messages"></a><span data-ttu-id="27d1b-102">Configuration de BizTalk Server pour envoyer des messages signés</span><span class="sxs-lookup"><span data-stu-id="27d1b-102">How to Configure BizTalk Server for Sending Signed Messages</span></span>
<span data-ttu-id="27d1b-103">La procédure suivante présente les étapes à suivre afin de configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l'envoi de messages signés.</span><span class="sxs-lookup"><span data-stu-id="27d1b-103">The following procedure lists the steps that you have to follow to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send signed messages.</span></span>  
  
-   <span data-ttu-id="27d1b-104">Pour créer un pipeline afin d'envoyer des messages signés</span><span class="sxs-lookup"><span data-stu-id="27d1b-104">To create a pipeline to send signed messages</span></span>  
  
-   <span data-ttu-id="27d1b-105">Configuration du port d'envoi pour l'envoi de messages signés</span><span class="sxs-lookup"><span data-stu-id="27d1b-105">To configure the send port for sending signed messages</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="27d1b-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="27d1b-106">Prerequisites</span></span>  
 <span data-ttu-id="27d1b-107">Avant de configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s pour envoyer des messages signés, vous devez effectuer les étapes de [comment installer les certificats pour les Signatures numériques](../core/how-to-install-the-certificates-for-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="27d1b-107">Before configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s for sending signed messages, you must perform the steps in [How to install the Certificates for Digital Signatures](../core/how-to-install-the-certificates-for-digital-signatures.md).</span></span>  
  
### <a name="to-create-a-pipeline-to-send-signed-messages"></a><span data-ttu-id="27d1b-108">Pour créer un pipeline afin d'envoyer des messages signés</span><span class="sxs-lookup"><span data-stu-id="27d1b-108">To create a pipeline to send signed messages</span></span>  
  
1.  <span data-ttu-id="27d1b-109">Dans l'Explorateur de solutions de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], sélectionnez le projet dans lequel créer le pipeline.</span><span class="sxs-lookup"><span data-stu-id="27d1b-109">In Solution Explorer in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], select the project in which you want to create the pipeline.</span></span>  
  
    1.  <span data-ttu-id="27d1b-110">Sur le **fichier** menu, cliquez sur **ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="27d1b-110">On the **File** menu, click **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="27d1b-111">Dans le **ajouter un nouvel élément** boîte de dialogue, développez les éléments de projet BizTalk, cliquez sur **fichiers de Pipeline**, puis cliquez sur le **Pipeline d’envoi** modèle.</span><span class="sxs-lookup"><span data-stu-id="27d1b-111">In the **Add New Item** dialog box, expand BizTalk Project Items, click **Pipeline Files**, and then click the **Send Pipeline** template.</span></span>  
  
    3.  <span data-ttu-id="27d1b-112">Dans le **nom** , tapez un nom pour le pipeline.</span><span class="sxs-lookup"><span data-stu-id="27d1b-112">In the **Name** field, type a name for the pipeline.</span></span>  
  
    4.  <span data-ttu-id="27d1b-113">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="27d1b-113">Click **Add**.</span></span>  
  
         <span data-ttu-id="27d1b-114">Le nouveau pipeline apparaît dans l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="27d1b-114">The new pipeline appears in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="27d1b-115">Faites glisser le composant de pipeline Encodeur MIME/SMIME dans l'étape Encoder d'un pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="27d1b-115">Drag the MIME/SMIME Encoder pipeline component into the Encode stage of a receive pipeline.</span></span>  
  
     <span data-ttu-id="27d1b-116">![MIME &#47; Composant de pipeline encodeur SMIME](../core/media/bts-dev-mimesmimeencoder.gif "BTS_DEV_MIMESMIMEEncoder")</span><span class="sxs-lookup"><span data-stu-id="27d1b-116">![MIME&#47;SMIME Encoder pipeline component](../core/media/bts-dev-mimesmimeencoder.gif "BTS_DEV_MIMESMIMEEncoder")</span></span>  
  
3.  <span data-ttu-id="27d1b-117">Dans la fenêtre Propriétés, configurez le composant de pipeline Encodeur MIME/SMIME **le type de Signature** propriété **ClearSign**ou **BlobSign**.</span><span class="sxs-lookup"><span data-stu-id="27d1b-117">In the Properties window, configure the MIME/SMIME Encoder pipeline component **Signature type** property to **ClearSign**or **BlobSign**.</span></span> <span data-ttu-id="27d1b-118">Pour plus d’informations sur la **activer le chiffrement** propriété, consultez [comment configurer le composant de Pipeline encodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="27d1b-118">For more information about the **Enable encryption** property, see [How to Configure the MIME-SMIME Encoder Pipeline Component](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="27d1b-119">Si vous utilisez également le chiffrement, vous pouvez uniquement sélectionner **BlobSign**.</span><span class="sxs-lookup"><span data-stu-id="27d1b-119">If you are also using encryption, you can only select **BlobSign**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27d1b-120">Vous pouvez configurer les propriétés du composant du pipeline d'envoi à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] après le déploiement du pipeline dans un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="27d1b-120">You can configure the send pipeline component properties using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console after the pipeline has been deployed into a BizTalk group.</span></span> <span data-ttu-id="27d1b-121">Pour plus d’informations, consultez [comment configurer des propriétés de Pipeline par Instance pour un Port d’envoi](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="27d1b-121">For more information, see [How to Configure Per-Instance Pipeline Properties for a Send Port](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27d1b-122">Le composant de pipeline Encodeur MIME/SMIME effectue à la fois le chiffrement et les opérations de signature numérique (lorsqu'il est configuré pour exécuter ces deux fonctions).</span><span class="sxs-lookup"><span data-stu-id="27d1b-122">The MIME/SMIME Encoder pipeline component performs both encryption and digital signing (when configured to perform both functions).</span></span> <span data-ttu-id="27d1b-123">Par conséquent, si vous configurez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour envoyer des messages chiffrés et signés, vous pouvez utiliser le même pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="27d1b-123">Therefore, if you are configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send encrypted and signed messages, you can use the same send pipeline.</span></span> <span data-ttu-id="27d1b-124">En d'autres termes, il est inutile que vous créiez des pipelines distincts pour les opérations de chiffrement et de signature numérique.</span><span class="sxs-lookup"><span data-stu-id="27d1b-124">In other words, you do not have to create separate pipelines for encryption and digital signing.</span></span>  
  
4.  <span data-ttu-id="27d1b-125">Construisez et déployez le pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="27d1b-125">Build and deploy the send pipeline.</span></span>  
  
### <a name="to-configure-the-send-port-for-sending-signed-messages"></a><span data-ttu-id="27d1b-126">Configuration du port d'envoi pour l'envoi de messages signés</span><span class="sxs-lookup"><span data-stu-id="27d1b-126">To configure the send port for sending signed messages</span></span>  
  
1.  <span data-ttu-id="27d1b-127">Ajoutez l'assembly BizTalk créé dans la procédure précédente à l'application BizTalk en incluant les emplacements de réception afin d'envoyer des messages signés.</span><span class="sxs-lookup"><span data-stu-id="27d1b-127">Add the BizTalk assembly that you created in previous procedure to the BizTalk Application including the receive locations to sending signed messages.</span></span> <span data-ttu-id="27d1b-128">Pour plus d’informations sur l’ajout d’assemblys BizTalk, consultez [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="27d1b-128">For more information about how to add BizTalk assemblies, see [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
2.  <span data-ttu-id="27d1b-129">Configurez le port d'envoi de l'application BizTalk avec le pipeline d'envoi créé dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="27d1b-129">Configure the send port in the BizTalk Application with the send pipeline that you created in previous procedure.</span></span> <span data-ttu-id="27d1b-130">Pour plus d’informations sur la configuration des ports d’envoi, consultez [création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md).</span><span class="sxs-lookup"><span data-stu-id="27d1b-130">For more information about how to configure send ports, see [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md).</span></span>  
  
3.  <span data-ttu-id="27d1b-131">Configurer le groupe BizTalk avec le certificat de signature que vous avez installé dans [comment installer les certificats pour les Signatures numériques](../core/how-to-install-the-certificates-for-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="27d1b-131">Configure the BizTalk group with the signing certificate that you installed in [How to install the Certificates for Digital Signatures](../core/how-to-install-the-certificates-for-digital-signatures.md).</span></span> <span data-ttu-id="27d1b-132">Pour savoir comment configurer un groupe BizTalk, consultez [comment modifier les propriétés de groupe](../core/how-to-modify-group-properties.md).</span><span class="sxs-lookup"><span data-stu-id="27d1b-132">For more information how to configure a BizTalk group, see [How to Modify Group Properties](../core/how-to-modify-group-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d1b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27d1b-133">See Also</span></span>  
 <span data-ttu-id="27d1b-134">[Comment configurer BizTalk Server pour la réception des Messages signés](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md) </span><span class="sxs-lookup"><span data-stu-id="27d1b-134">[How to Configure BizTalk Server for Receiving Signed Messages](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md) </span></span>  
 <span data-ttu-id="27d1b-135">[Certificats utilisés par BizTalk Server pour les Messages signés](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span><span class="sxs-lookup"><span data-stu-id="27d1b-135">[Certificates that BizTalk Server Uses for Signed Messages](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span></span>  
 [<span data-ttu-id="27d1b-136">Envoyer et recevoir des Messages signés</span><span class="sxs-lookup"><span data-stu-id="27d1b-136">Sending and Receiving Signed Messages</span></span>](../core/sending-and-receiving-signed-messages.md)