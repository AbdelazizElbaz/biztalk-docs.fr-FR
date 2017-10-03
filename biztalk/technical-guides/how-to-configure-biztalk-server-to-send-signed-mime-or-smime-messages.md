---
title: "Comment configurer BizTalk Server pour l’envoi signés MIME ou Messages SMIME | Documents Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba42463b-2c12-4329-919e-aca427d14eee
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 623e8e6349494ce1d15089093b1620b4da76adbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-to-send-signed-mime-or-smime-messages"></a><span data-ttu-id="3d3c1-102">Comment configurer BizTalk Server pour envoyer signés MIME ou Messages SMIME</span><span class="sxs-lookup"><span data-stu-id="3d3c1-102">How to Configure BizTalk Server to Send Signed MIME or SMIME Messages</span></span>
<span data-ttu-id="3d3c1-103">Cette rubrique explique comment configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser des certificats pour envoyer des messages MIME/SMIME signés.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-103">This topic describes how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use certificates to send signed MIME/SMIME messages.</span></span> <span data-ttu-id="3d3c1-104">La procédure ci-dessous s’applique également à la configuration de l’envoi de messages signés via le transport AS2.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-104">The procedure below also applies to configuring the sending of signed messages over AS2 transport.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3d3c1-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="3d3c1-105">Prerequisites</span></span>  
 <span data-ttu-id="3d3c1-106">Pour exécuter la procédure dans cette rubrique, vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-106">To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-biztalk-server-to-send-signed-messages"></a><span data-ttu-id="3d3c1-107">Pour configurer BizTalk Server pour envoyer des messages signés</span><span class="sxs-lookup"><span data-stu-id="3d3c1-107">To configure BizTalk Server to send signed messages</span></span>  
  
1.  <span data-ttu-id="3d3c1-108">Créer un pipeline pour envoyer des messages signés, comme suit :</span><span class="sxs-lookup"><span data-stu-id="3d3c1-108">Create a pipeline to send signed messages, as follows:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3d3c1-109">Cette étape n’est pas nécessaire lors de la configuration de transport AS2 pour envoyer des messages signés, car le AS2Send et AS2EdiSend de pipelines qui sont inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cette fonction.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-109">This step is not necessary when configuring AS2 transport for sending signed messages because the AS2Send and AS2EdiSend pipelines that are included in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serve this function.</span></span>  
  
    1.  <span data-ttu-id="3d3c1-110">Créer un pipeline d’envoi et puis faites glisser le composant de pipeline Encodeur MIME/SMIME dans la phase de codage du pipeline.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-110">Create a send pipeline and then drag the MIME/SMIME Encoder pipeline component into the Encode stage of the pipeline.</span></span>  
  
    2.  <span data-ttu-id="3d3c1-111">Dans le **propriétés** fenêtre, configurer la propriété type Signature de composant de pipeline Encodeur MIME/SMIME ClearSign ou BlobSign.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-111">In the **Properties** window, configure the MIME/SMIME Encoder pipeline component Signature type property to ClearSign or BlobSign.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="3d3c1-112">Si vous utilisez également le chiffrement, vous pouvez uniquement sélectionner BlobSign.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-112">If you are also using encryption, you can only select BlobSign.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="3d3c1-113">Vous pouvez configurer les propriétés du composant du pipeline d'envoi à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] après le déploiement du pipeline dans un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-113">You can configure the send pipeline component properties using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console after the pipeline has been deployed into a BizTalk group.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="3d3c1-114">Le composant de pipeline Encodeur MIME/SMIME effectue à la fois le chiffrement et les opérations de signature numérique (lorsqu'il est configuré pour exécuter ces deux fonctions).</span><span class="sxs-lookup"><span data-stu-id="3d3c1-114">The MIME/SMIME Encoder pipeline component performs both encryption and digital signing (when configured to perform both functions).</span></span> <span data-ttu-id="3d3c1-115">Par conséquent, si vous configurez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour envoyer des messages chiffrés et signés, vous pouvez utiliser le même pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-115">Therefore, if you are configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send encrypted and signed messages, you can use the same send pipeline.</span></span> <span data-ttu-id="3d3c1-116">En d'autres termes, il est inutile que vous créiez des pipelines distincts pour les opérations de chiffrement et de signature numérique.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-116">In other words, you do not have to create separate pipelines for encryption and digital signing.</span></span>  
  
    3.  <span data-ttu-id="3d3c1-117">Construisez et déployez le pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-117">Build and deploy the send pipeline.</span></span>  
  
2.  <span data-ttu-id="3d3c1-118">Configurer le port d’envoi pour envoyer des messages signés, comme suit :</span><span class="sxs-lookup"><span data-stu-id="3d3c1-118">Configure the send port for sending signed messages, as follows:</span></span>  
  
    1.  <span data-ttu-id="3d3c1-119">Ajoutez l’assembly BizTalk que vous avez créé contenant le pipeline d’envoi à l’application BizTalk qui comprend les ports d’envoi pour envoyer des messages signés.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-119">Add the BizTalk assembly that you created containing the send pipeline to the BizTalk application that includes the send ports to send signed messages.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="3d3c1-120">Cette étape n’est pas nécessaire lors de la configuration de transport AS2 pour envoyer des messages signés, car les pipelines AS2Send et AS2EdiSend sont inclus dans l’Application EDI BizTalk [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3d3c1-120">This step is not necessary when configuring AS2 transport for sending signed messages because the AS2Send and AS2EdiSend pipelines are included in the BizTalk EDI Application in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    2.  <span data-ttu-id="3d3c1-121">Configurer le port d’envoi dans l’application BizTalk avec le pipeline d’envoi que vous avez créé dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-121">Configure the send port in the BizTalk application with the send pipeline that you created in the previous procedure.</span></span>  
  
3.  <span data-ttu-id="3d3c1-122">Configurez le groupe avec un certificat pour l’envoi de messages signés, comme suit :</span><span class="sxs-lookup"><span data-stu-id="3d3c1-122">Configure the group with a certificate for sending signed messages, as follows:</span></span>  
  
    1.  <span data-ttu-id="3d3c1-123">Configurer le groupe BizTalk avec le certificat de signature que vous avez installé en développant le groupe BizTalk dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit **groupe BizTalk**, puis en cliquant sur  **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-123">Configure the BizTalk group with the signing certificate that you installed by expanding the BizTalk group in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-clicking **BizTalk Group**, and then clicking **Properties**.</span></span>  
  
    2.  <span data-ttu-id="3d3c1-124">Cliquez sur l’onglet certificat, cliquez sur **Parcourir**, sélectionnez le certificat approprié, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3d3c1-124">Click the Certificate tab, click **Browse**, select the appropriate certificate, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d3c1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d3c1-125">See Also</span></span>  
 [<span data-ttu-id="3d3c1-126">Configuration des certificats pour MIME ou Messages SMIME</span><span class="sxs-lookup"><span data-stu-id="3d3c1-126">Configuring Certificates for MIME or SMIME Messages</span></span>](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)