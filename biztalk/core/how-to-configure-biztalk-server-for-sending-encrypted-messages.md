---
title: "Comment configurer BizTalk Server pour l’envoi des Messages chiffrés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb751d7c-49cd-46f0-9630-254cf06c497e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0b3ef721c263c892690b9ac5b7d2dd15155f0dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-for-sending-encrypted-messages"></a><span data-ttu-id="bc4e7-102">Configuration de BizTalk Server pour envoyer des messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="bc4e7-102">How to Configure BizTalk Server for Sending Encrypted Messages</span></span>
<span data-ttu-id="bc4e7-103">La procédure suivante présente les étapes à suivre pour configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l'envoi de messages chiffrés.</span><span class="sxs-lookup"><span data-stu-id="bc4e7-103">The following procedure lists the steps that you have to follow to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send encrypted messages.</span></span>  
  
-   <span data-ttu-id="bc4e7-104">Pour créer un pipeline afin d'envoyer des messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="bc4e7-104">To create a pipeline to send encrypted messages</span></span>  
  
-   <span data-ttu-id="bc4e7-105">Pour configurer le port d'envoi pour l'envoi de messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="bc4e7-105">To configure the send port for sending encrypted messages</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bc4e7-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="bc4e7-106">Prerequisites</span></span>  
 <span data-ttu-id="bc4e7-107">Avant de configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s pour l’envoi de messages chiffrés, vous devez effectuer les étapes de [comment installer les certificats pour les Messages chiffrés](../core/how-to-install-the-certificates-for-encrypted-messages.md).</span><span class="sxs-lookup"><span data-stu-id="bc4e7-107">Before configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s for sending encrypted messages, you must perform the steps in [How to Install the Certificates for Encrypted Messages](../core/how-to-install-the-certificates-for-encrypted-messages.md).</span></span>  
  
### <a name="to-create-a-pipeline-to-send-encrypted-messages"></a><span data-ttu-id="bc4e7-108">Pour créer un pipeline afin d'envoyer des messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="bc4e7-108">To create a pipeline to send encrypted messages</span></span>  
  
1.  <span data-ttu-id="bc4e7-109">Dans l'Explorateur de solutions de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], sélectionnez le projet dans lequel créer le pipeline.</span><span class="sxs-lookup"><span data-stu-id="bc4e7-109">In Solution Explorer in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], select the project in which you want to create the pipeline.</span></span>  
  
    1.  <span data-ttu-id="bc4e7-110">Sur le **fichier** menu, cliquez sur **ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="bc4e7-110">On the **File** menu, click **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="bc4e7-111">Dans le **ajouter un nouvel élément** boîte de dialogue, développez les éléments de projet BizTalk, cliquez sur **fichiers de Pipeline**, puis cliquez sur le **Pipeline d’envoi** modèle.</span><span class="sxs-lookup"><span data-stu-id="bc4e7-111">In the **Add New Item** dialog box, expand BizTalk Project Items, click **Pipeline Files**, and then click the **Send Pipeline** template.</span></span>  
  
    3.  <span data-ttu-id="bc4e7-112">Dans le **nom** , tapez un nom pour le pipeline.</span><span class="sxs-lookup"><span data-stu-id="bc4e7-112">In the **Name** field, type a name for the pipeline.</span></span>  
  
    4.  <span data-ttu-id="bc4e7-113">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="bc4e7-113">Click **Add**.</span></span>  
  
         <span data-ttu-id="bc4e7-114">Le nouveau pipeline apparaît dans l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="bc4e7-114">The new pipeline appears in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="bc4e7-115">Faites glisser le composant de pipeline Encodeur MIME/SMIME dans l'étape Encoder d'un pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="bc4e7-115">Drag the MIME/SMIME Encoder pipeline component into the Encode stage of a receive pipeline.</span></span>  
  
     <span data-ttu-id="bc4e7-116">![MIME &#47; Composant de pipeline encodeur SMIME](../core/media/bts-dev-mimesmimeencoder.gif "BTS_DEV_MIMESMIMEEncoder")</span><span class="sxs-lookup"><span data-stu-id="bc4e7-116">![MIME&#47;SMIME Encoder pipeline component](../core/media/bts-dev-mimesmimeencoder.gif "BTS_DEV_MIMESMIMEEncoder")</span></span>  
  
    -   <span data-ttu-id="bc4e7-117">Dans la fenêtre Propriétés, configurez le composant de pipeline Encodeur MIME/SMIME **activer le chiffrement** propriété `True`.</span><span class="sxs-lookup"><span data-stu-id="bc4e7-117">In the Properties window, configure the MIME/SMIME Encoder pipeline component **Enable encryption** property to `True`.</span></span> <span data-ttu-id="bc4e7-118">Pour plus d’informations sur la **activer le chiffrement** propriété, consultez [comment configurer le composant de Pipeline encodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="bc4e7-118">For more information about the **Enable encryption** property, see [How to Configure the MIME-SMIME Encoder Pipeline Component](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bc4e7-119">Vous pouvez configurer les propriétés du composant du pipeline d'envoi à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] après le déploiement du pipeline dans un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="bc4e7-119">You can configure the send pipeline component properties using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console after the pipeline has been deployed into a BizTalk group.</span></span> <span data-ttu-id="bc4e7-120">Pour plus d’informations, consultez [comment configurer des propriétés de Pipeline par Instance pour un Port d’envoi](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="bc4e7-120">For more information, see [How to Configure Per-Instance Pipeline Properties for a Send Port](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bc4e7-121">Le composant de pipeline Encodeur MIME/SMIME effectue à la fois le chiffrement et les opérations de signature numérique (lorsqu'il est configuré pour exécuter ces deux fonctions).</span><span class="sxs-lookup"><span data-stu-id="bc4e7-121">The MIME/SMIME Encoder pipeline component performs both encryption and digital signing (when configured to perform both functions).</span></span> <span data-ttu-id="bc4e7-122">Par conséquent, si vous configurez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour envoyer des messages chiffrés et signés, vous pouvez utiliser le même pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="bc4e7-122">Therefore, if you are configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send encrypted and signed messages, you can use the same send pipeline.</span></span> <span data-ttu-id="bc4e7-123">En d'autres termes, il est inutile que vous créiez des pipelines distincts pour les opérations de chiffrement et de signature numérique.</span><span class="sxs-lookup"><span data-stu-id="bc4e7-123">In other words, you do not have to create separate pipelines for encryption and digital signing.</span></span>  
  
3.  <span data-ttu-id="bc4e7-124">Construisez et déployez le pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="bc4e7-124">Build and deploy the send pipeline.</span></span>  
  
### <a name="to-configure-the-send-port-for-sending-encrypted-messages"></a><span data-ttu-id="bc4e7-125">Pour configurer le port d'envoi pour l'envoi de messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="bc4e7-125">To configure the send port for sending encrypted messages</span></span>  
  
1.  <span data-ttu-id="bc4e7-126">Ajoutez l'assembly BizTalk créé dans la procédure précédente à l'application BizTalk en incluant les ports d’envoi pour envoyer des messages chiffrés.</span><span class="sxs-lookup"><span data-stu-id="bc4e7-126">Add the BizTalk assembly that you created in previous procedure to the BizTalk Application including the send ports to send encrypted messages.</span></span> <span data-ttu-id="bc4e7-127">Pour plus d’informations sur l’ajout d’assemblys BizTalk, consultez [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="bc4e7-127">For more information about how to add BizTalk assemblies, see [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
2.  <span data-ttu-id="bc4e7-128">Configurez le port d’envoi dans l’Application BizTalk avec le pipeline d’envoi que vous avez créé dans la procédure précédente, puis attribuez le certificat de chiffrement que vous avez installé dans [comment installer les certificats pour les Messages chiffrés](../core/how-to-install-the-certificates-for-encrypted-messages.md).</span><span class="sxs-lookup"><span data-stu-id="bc4e7-128">Configure the send port in the BizTalk Application with the send pipeline that you created in previous procedure, and then assign the encryption certificate that you installed in [How to Install the Certificates for Encrypted Messages](../core/how-to-install-the-certificates-for-encrypted-messages.md).</span></span> <span data-ttu-id="bc4e7-129">Pour plus d’informations sur la configuration des ports d’envoi, consultez [comment attribuer un certificat à un Port d’envoi](../core/how-to-assign-a-certificate-to-a-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="bc4e7-129">For more information about how to configure send ports, see [How to Assign a Certificate to a Send Port](../core/how-to-assign-a-certificate-to-a-send-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc4e7-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc4e7-130">See Also</span></span>  
 <span data-ttu-id="bc4e7-131">[Comment configurer BizTalk Server pour recevoir des Messages chiffrés](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md) </span><span class="sxs-lookup"><span data-stu-id="bc4e7-131">[How to Configure BizTalk Server for Receiving Encrypted Messages](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md) </span></span>  
 <span data-ttu-id="bc4e7-132">[Certificats utilisés par BizTalk Server pour les Messages chiffrés](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span><span class="sxs-lookup"><span data-stu-id="bc4e7-132">[Certificates that BizTalk Server Uses for Encrypted Messages](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span></span>  
 [<span data-ttu-id="bc4e7-133">Envoyer et recevoir des Messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="bc4e7-133">Sending and Receiving Encrypted Messages</span></span>](../core/sending-and-receiving-encrypted-messages.md)