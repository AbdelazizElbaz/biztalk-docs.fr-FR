---
title: "Comment configurer BizTalk Server pour recevoir des Messages chiffrés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd1e7e4c-f80c-468e-aa86-7c18406feead
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33a4a3ed307f86ec1edba6ef59eee5b806caf75e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-for-receiving-encrypted-messages"></a><span data-ttu-id="b484c-102">Configuration de BizTalk Server pour la réception des messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="b484c-102">How to Configure BizTalk Server for Receiving Encrypted Messages</span></span>
<span data-ttu-id="b484c-103">La procédure suivante présente les étapes à suivre pour configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour la réception de messages chiffrés.</span><span class="sxs-lookup"><span data-stu-id="b484c-103">The following procedure lists the steps that you have to follow to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive encrypted messages.</span></span>  
  
-   <span data-ttu-id="b484c-104">Pour créer un pipeline qui reçoit des messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="b484c-104">To create a pipeline to receive encrypted messages</span></span>  
  
-   <span data-ttu-id="b484c-105">Pour configurer l'emplacement de réception des messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="b484c-105">To configure the receive location for receiving encrypted messages</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b484c-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b484c-106">Prerequisites</span></span>  
 <span data-ttu-id="b484c-107">Avant de configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s pour la réception des messages chiffrés, vous devez effectuer les étapes de [comment installer les certificats pour les Messages chiffrés](../core/how-to-install-the-certificates-for-encrypted-messages.md).</span><span class="sxs-lookup"><span data-stu-id="b484c-107">Before configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s for receiving encrypted messages, you must perform the steps in [How to Install the Certificates for Encrypted Messages](../core/how-to-install-the-certificates-for-encrypted-messages.md).</span></span>  
  
### <a name="to-create-a-pipeline-to-receive-encrypted-messages"></a><span data-ttu-id="b484c-108">Pour créer un pipeline qui reçoit des messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="b484c-108">To create a pipeline to receive encrypted messages</span></span>  
  
1.  <span data-ttu-id="b484c-109">Dans l'Explorateur de solutions de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], sélectionnez le projet dans lequel créer le pipeline.</span><span class="sxs-lookup"><span data-stu-id="b484c-109">In Solution Explorer in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], select the project in which you want to create the pipeline.</span></span>  
  
    1.  <span data-ttu-id="b484c-110">Sur le **fichier** menu, cliquez sur **ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="b484c-110">On the **File** menu, click **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="b484c-111">Dans le **ajouter un nouvel élément** boîte de dialogue, développez les éléments de projet BizTalk, cliquez sur **fichiers de Pipeline**, puis cliquez sur le **Pipeline de réception** modèle.</span><span class="sxs-lookup"><span data-stu-id="b484c-111">In the **Add New Item** dialog box, expand BizTalk Project Items, click **Pipeline Files**, and then click the **Receive Pipeline** template.</span></span>  
  
    3.  <span data-ttu-id="b484c-112">Dans le **nom** , tapez un nom pour le pipeline.</span><span class="sxs-lookup"><span data-stu-id="b484c-112">In the **Name** field, type a name for the pipeline.</span></span>  
  
    4.  <span data-ttu-id="b484c-113">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="b484c-113">Click **Add**.</span></span>  
  
         <span data-ttu-id="b484c-114">Le nouveau pipeline apparaît dans l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="b484c-114">The new pipeline appears in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="b484c-115">Faites glisser le composant de pipeline Décodeur MIME/SMIME dans l'étape Décoder d'un pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="b484c-115">Drag the MIME/SMIME Decoder pipeline component into the Decode stage of a receive pipeline.</span></span>  
  
     <span data-ttu-id="b484c-116">![MIME &#47; Composant de pipeline décodeur SMIME](../core/media/bts-dev-mimesmimedecoder.gif "BTS_DEV_MIMESMIMEDecoder")</span><span class="sxs-lookup"><span data-stu-id="b484c-116">![MIME&#47;SMIME Decoder pipeline component](../core/media/bts-dev-mimesmimedecoder.gif "BTS_DEV_MIMESMIMEDecoder")</span></span>  
  
    -   <span data-ttu-id="b484c-117">Configurer les propriétés du composant de pipeline Décodeur MIME/SMIME dans le **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="b484c-117">Configure the MIME/SMIME Decoder pipeline component properties in the **Properties** window.</span></span> <span data-ttu-id="b484c-118">Pour plus d’informations sur le décodeur MIME/SMIME, consultez [comment configurer le composant de Pipeline décodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="b484c-118">For more information about the MIME/SMIME decoder, see [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b484c-119">Vous pouvez configurer les propriétés de pipeline d'un emplacement de réception à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] après le déploiement du pipeline dans un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b484c-119">You can configure pipeline properties for a receive location after the pipeline has been deployed into a BizTalk group using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="b484c-120">Vous pouvez configurer des propriétés de pipeline différentes pour chaque emplacement de réception du groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b484c-120">You can configure different pipeline properties for each receive location in the BizTalk group.</span></span> <span data-ttu-id="b484c-121">Pour plus d’informations, consultez [comment configurer les propriétés de Pipeline par instance pour un emplacement de réception](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md).</span><span class="sxs-lookup"><span data-stu-id="b484c-121">For more information, see [How to Configure Per-instance Pipeline Properties for a Receive Location](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b484c-122">Le composant de pipeline Décodeur MIME/SMIME effectue à la fois le déchiffrement et la validation des signatures numériques (lorsqu'il est configuré pour exécuter ces deux fonctions).</span><span class="sxs-lookup"><span data-stu-id="b484c-122">The MIME/SMIME Decoder pipeline component performs both decryption and digital signature validation (when configured to perform both functions).</span></span> <span data-ttu-id="b484c-123">Par conséquent, si vous configurez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour recevoir des messages chiffrés et signés, vous pouvez utiliser le même pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="b484c-123">Therefore, if you are configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive encrypted and signed messages, you can use the same receive pipeline.</span></span> <span data-ttu-id="b484c-124">En d'autres termes, il est inutile de créer des pipelines distincts pour le chiffrement et la validation des signatures numériques.</span><span class="sxs-lookup"><span data-stu-id="b484c-124">In other words, you do not have to create separate pipelines for decryption and digital signature validation.</span></span>  
  
3.  <span data-ttu-id="b484c-125">Construisez et déployez le pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="b484c-125">Build and deploy the receive pipeline.</span></span>  
  
### <a name="to-configure-the-receive-location-for-receiving-encrypted-messages"></a><span data-ttu-id="b484c-126">Pour configurer l'emplacement de réception des messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="b484c-126">To configure the receive location for receiving encrypted messages</span></span>  
  
1.  <span data-ttu-id="b484c-127">Ajoutez l'assembly BizTalk créé dans la procédure précédente à l'application BizTalk en incluant les emplacements de réception afin de recevoir des messages chiffrés.</span><span class="sxs-lookup"><span data-stu-id="b484c-127">Add the BizTalk assembly that you created in previous procedure to the BizTalk Application including the receive locations to receive encrypted messages.</span></span> <span data-ttu-id="b484c-128">Pour plus d’informations sur l’ajout d’assemblys BizTalk, consultez [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="b484c-128">For more information about how to add BizTalk assemblies, see [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
2.  <span data-ttu-id="b484c-129">Configurez les emplacements de réception de l'application BizTalk avec le pipeline de réception créé dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="b484c-129">Configure the receive locations in the BizTalk Application with the receive pipeline that you created in previous procedure.</span></span> <span data-ttu-id="b484c-130">Pour plus d’informations sur la façon de configurer les emplacements de réception, consultez [comment modifier les propriétés d’un emplacement de réception](../core/how-to-edit-the-properties-of-a-receive-location.md).</span><span class="sxs-lookup"><span data-stu-id="b484c-130">For more information about how to configure receive locations, see [How to Edit the Properties of a Receive Location](../core/how-to-edit-the-properties-of-a-receive-location.md).</span></span>  
  
3.  <span data-ttu-id="b484c-131">Configurer l’hôte utilisé comme gestionnaire de réception pour l’emplacement de réception avec le certificat de déchiffrement que vous avez installé la procédure » pour configurer les hôtes BizTalk pour la réception des messages chiffrés » dans [comment installer les certificats de chiffrement intégral Messages](../core/how-to-install-the-certificates-for-encrypted-messages.md).</span><span class="sxs-lookup"><span data-stu-id="b484c-131">Configure the host used as receive handler for the receive location with the decryption certificate that you installed in the procedure," To configure BizTalk hosts for receiving encrypted messages" in [How to Install the Certificates for Encrypted Messages](../core/how-to-install-the-certificates-for-encrypted-messages.md).</span></span> <span data-ttu-id="b484c-132">Pour savoir comment configurer les propriétés de l’hôte, consultez [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md).</span><span class="sxs-lookup"><span data-stu-id="b484c-132">For more information how to configure host properties, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b484c-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b484c-133">See Also</span></span>  
 <span data-ttu-id="b484c-134">[Certificats utilisés par BizTalk Server pour les Messages chiffrés](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span><span class="sxs-lookup"><span data-stu-id="b484c-134">[Certificates that BizTalk Server Uses for Encrypted Messages](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span></span>  
 <span data-ttu-id="b484c-135">[Comment configurer BizTalk Server pour envoyer des Messages chiffrés](../core/how-to-configure-biztalk-server-for-sending-encrypted-messages.md) </span><span class="sxs-lookup"><span data-stu-id="b484c-135">[How to Configure BizTalk Server for Sending Encrypted Messages](../core/how-to-configure-biztalk-server-for-sending-encrypted-messages.md) </span></span>  
 [<span data-ttu-id="b484c-136">Envoyer et recevoir des Messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="b484c-136">Sending and Receiving Encrypted Messages</span></span>](../core/sending-and-receiving-encrypted-messages.md)