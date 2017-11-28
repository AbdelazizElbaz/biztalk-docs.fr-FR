---
title: "Comment configurer BizTalk Server pour l’envoi chiffré des Messages MIME/SMIME | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14f67152-5f80-4040-a9d6-0819fab7fcb5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c83b5f28ac3716376aa93cff22f933363825615e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-to-send-encrypted-mimesmime-messages"></a><span data-ttu-id="87b51-102">Comment configurer BizTalk Server pour envoyer des Messages MIME/SMIME chiffrée</span><span class="sxs-lookup"><span data-stu-id="87b51-102">How to Configure BizTalk Server to Send Encrypted MIME/SMIME Messages</span></span>
<span data-ttu-id="87b51-103">Cette rubrique décrit comment configurer BizTalk Server pour utiliser des certificats pour envoyer des messages MIME/SMIME chiffrés.</span><span class="sxs-lookup"><span data-stu-id="87b51-103">This topic describes how to configure BizTalk Server to use certificates to send encrypted MIME/SMIME messages.</span></span> <span data-ttu-id="87b51-104">La procédure ci-dessous s’applique également à la configuration de l’envoi de messages chiffrés via le transport AS2.</span><span class="sxs-lookup"><span data-stu-id="87b51-104">The procedure below also applies to configuring the sending of encrypted messages over AS2 transport.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="87b51-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="87b51-105">Prerequisites</span></span>  
 <span data-ttu-id="87b51-106">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="87b51-106">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-configure-biztalk-server-to-send-encrypted-messages"></a><span data-ttu-id="87b51-107">Pour configurer BizTalk Server pour envoyer des messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="87b51-107">To configure BizTalk Server to send encrypted messages</span></span>  
  
1.  <span data-ttu-id="87b51-108">Créer un pipeline pour envoyer des messages chiffrés, comme suit :</span><span class="sxs-lookup"><span data-stu-id="87b51-108">Create a pipeline to send encrypted messages, as follows:</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="87b51-109">Cette étape n’est pas nécessaire lors de la configuration de transport AS2 pour envoyer des messages chiffrés, car le AS2Send et AS2EdiSend de pipelines qui sont inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cette fonction.</span><span class="sxs-lookup"><span data-stu-id="87b51-109">This step is not necessary when configuring AS2 transport for sending encrypted messages because the AS2Send and AS2EdiSend pipelines that are included in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serve this function.</span></span>  
  
    1.  <span data-ttu-id="87b51-110">Créer un pipeline d’envoi et puis faites glisser le composant de pipeline Encodeur MIME/SMIME dans la phase de codage du pipeline.</span><span class="sxs-lookup"><span data-stu-id="87b51-110">Create a send pipeline and then drag the MIME/SMIME Encoder pipeline component into the Encode stage of the pipeline.</span></span>  
  
    2.  <span data-ttu-id="87b51-111">Dans le **propriétés** fenêtre, configurez la propriété chiffrement activer de composant de pipeline Encodeur MIME/SMIME pour **True**.</span><span class="sxs-lookup"><span data-stu-id="87b51-111">In the **Properties** window, configure the MIME/SMIME Encoder pipeline component Enable encryption property to **True**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="87b51-112">Vous pouvez configurer les propriétés du composant du pipeline d'envoi à l'aide de la console Administration de BizTalk Server après le déploiement du pipeline dans un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="87b51-112">You can configure the send pipeline component properties using the BizTalk Server Administration console after the pipeline has been deployed into a BizTalk group.</span></span>  
  
    3.  <span data-ttu-id="87b51-113">Construisez et déployez le pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="87b51-113">Build and deploy the send pipeline.</span></span>  
  
2.  <span data-ttu-id="87b51-114">Configurer le port d’envoi pour envoyer des messages chiffrés, comme suit :</span><span class="sxs-lookup"><span data-stu-id="87b51-114">Configure the send port for sending encrypted messages, as follows:</span></span>  
  
    1.  <span data-ttu-id="87b51-115">Ajoutez l’assembly BizTalk que vous avez créé contenant le pipeline d’envoi à l’application BizTalk en incluant les emplacements de réception pour recevoir des messages chiffrés.</span><span class="sxs-lookup"><span data-stu-id="87b51-115">Add the BizTalk assembly that you created containing the send pipeline to the BizTalk application including the receive locations to receive encrypted messages.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="87b51-116">Cette étape n’est pas nécessaire lors de la configuration de transport AS2 pour envoyer des messages chiffrés, car les pipelines AS2Send et AS2EdiSend sont inclus dans l’Application EDI BizTalk.</span><span class="sxs-lookup"><span data-stu-id="87b51-116">This step is not necessary when configuring AS2 transport for sending encrypted messages because the AS2Send and AS2EdiSend pipelines are included in the BizTalk EDI Application.</span></span>  
  
    2.  <span data-ttu-id="87b51-117">Configurer le port d’envoi dans l’Application BizTalk avec le pipeline d’envoi que vous avez créé dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="87b51-117">Configure the send port in the BizTalk Application with the send pipeline that you created in the previous procedure.</span></span>  
  
    3.  <span data-ttu-id="87b51-118">Affectez le certificat de chiffrement que vous avez installé en double-cliquant sur le port d’envoi, en cliquant sur **propriétés**, puis en cliquant sur **certificat**.</span><span class="sxs-lookup"><span data-stu-id="87b51-118">Assign the encryption certificate that you installed by right-clicking the send port, clicking **Properties**, and then clicking **Certificate**.</span></span> <span data-ttu-id="87b51-119">Cliquez sur **Parcourir**, accédez au certificat que vous souhaitez attribuer à ce port d’envoi, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="87b51-119">Click **Browse**, browse to the certificate that you want to assign to this send port, and then click **OK**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="87b51-120">Si le certificat n’existe pas sur l’ordinateur local, dans le **l’empreinte numérique** zone, tapez ou collez l’empreinte numérique du certificat, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="87b51-120">If the certificate does not exist on the local computer, in the **Thumbprint** box, type or paste the certificate thumbprint, and then click **OK**.</span></span> <span data-ttu-id="87b51-121">Le format de l'empreinte du certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est un nombre hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="87b51-121">The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit.</span></span>