---
title: "Comment configurer BizTalk Server pour recevoir signés MIME ou Messages SMIME | Documents Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50570257-7bb6-4ede-9026-873eefd06483
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88487fb96c89b8a611ab591223fa1820f70de1cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-to-receive-signed-mime-or-smime-messages"></a><span data-ttu-id="4013b-102">Comment configurer BizTalk Server pour recevoir signés MIME ou Messages SMIME</span><span class="sxs-lookup"><span data-stu-id="4013b-102">How to Configure BizTalk Server to Receive Signed MIME or SMIME Messages</span></span>
<span data-ttu-id="4013b-103">Cette rubrique explique comment configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser des certificats pour recevoir les messages MIME/SMIME signés.</span><span class="sxs-lookup"><span data-stu-id="4013b-103">This topic describes how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use certificates to receive signed MIME/SMIME messages.</span></span> <span data-ttu-id="4013b-104">La procédure ci-dessous s’applique également à la configuration de la réception de messages signés via le transport AS2.</span><span class="sxs-lookup"><span data-stu-id="4013b-104">The procedure below also applies to configuring the receiving of signed messages over AS2 transport.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4013b-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4013b-105">Prerequisites</span></span>  
 <span data-ttu-id="4013b-106">Pour exécuter la procédure dans cette rubrique, vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="4013b-106">To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-biztalk-server-to-receive-signed-messages"></a><span data-ttu-id="4013b-107">Pour configurer BizTalk Server pour recevoir des messages signés</span><span class="sxs-lookup"><span data-stu-id="4013b-107">To configure BizTalk Server to receive signed messages</span></span>  
  
1.  <span data-ttu-id="4013b-108">Créer un pipeline afin de recevoir des messages signés, comme suit :</span><span class="sxs-lookup"><span data-stu-id="4013b-108">Create a pipeline to receive signed messages, as follows:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4013b-109">Cette étape n’est pas nécessaire lors de la configuration de transport AS2 pour la réception des messages signés, car le AS2Receive et AS2EdiReceive de pipelines qui sont inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cette fonction.</span><span class="sxs-lookup"><span data-stu-id="4013b-109">This step is not necessary when configuring AS2 transport for receiving signed messages because the AS2Receive and AS2EdiReceive pipelines that are included in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serve this function.</span></span>  
  
    1.  <span data-ttu-id="4013b-110">Créer un pipeline de réception et puis faites glisser le composant de pipeline Décodeur MIME/SMIME dans l’étape décoder du pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="4013b-110">Create a receive pipeline and then drag the MIME/SMIME Decoder pipeline component into the Decode stage of the receive pipeline.</span></span>  
  
    2.  <span data-ttu-id="4013b-111">Dans le **propriétés** fenêtre, configurer les propriétés de composant de pipeline Décodeur MIME/SMIME.</span><span class="sxs-lookup"><span data-stu-id="4013b-111">In the **Properties** window, configure the MIME/SMIME Decoder pipeline component properties.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4013b-112">Vous pouvez configurer les propriétés de pipeline d'un emplacement de réception à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] après le déploiement du pipeline dans un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4013b-112">You can configure pipeline properties for a receive location after the pipeline has been deployed into a BizTalk group using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="4013b-113">Vous pouvez configurer des propriétés de pipeline différentes pour chaque emplacement de réception du groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4013b-113">You can configure different pipeline properties for each receive location in the BizTalk group.</span></span>  
  
    3.  <span data-ttu-id="4013b-114">Construisez et déployez le pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="4013b-114">Build and deploy the receive pipeline.</span></span>  
  
2.  <span data-ttu-id="4013b-115">Configurer un emplacement de réception pour la réception des messages signés, comme suit :</span><span class="sxs-lookup"><span data-stu-id="4013b-115">Configure a receive location for receiving signed messages, as follows:</span></span>  
  
    1.  <span data-ttu-id="4013b-116">Ajoutez l’assembly BizTalk que vous avez créé contenant le pipeline de réception à l’application BizTalk en incluant les emplacements de réception pour recevoir des messages signés.</span><span class="sxs-lookup"><span data-stu-id="4013b-116">Add the BizTalk assembly that you created containing the receive pipeline to the BizTalk application including the receive locations to receive signed messages.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4013b-117">Cette étape n’est pas nécessaire lors de la configuration de transport AS2 pour la réception des messages signés, car les pipelines AS2Receive et AS2EdiReceive sont inclus dans l’Application EDI BizTalk [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4013b-117">This step is not necessary when configuring AS2 transport for receiving signed messages because the AS2Receive and AS2EdiReceive pipelines are included in the BizTalk EDI Application in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    2.  <span data-ttu-id="4013b-118">Configurer les emplacements de réception dans l’application BizTalk avec le pipeline de réception que vous avez créé dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="4013b-118">Configure the receive locations in the BizTalk application with the receive pipeline that you created in previous procedure.</span></span>  
  
3.  <span data-ttu-id="4013b-119">Configurer le tiers avec un certificat pour la réception des messages signés, comme suit :</span><span class="sxs-lookup"><span data-stu-id="4013b-119">Configure the party with a certificate for receiving signed messages, as follows:</span></span>  
  
    -   <span data-ttu-id="4013b-120">Ouvrez le **propriétés de tiers** boîte de dialogue dans la Console Administration de BizTalk Server, cliquez sur le **certificat** , cliquez sur **Parcourir**, sélectionnez le certificat approprié, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4013b-120">Open the **Party Properties** dialog box in the BizTalk Server Administration Console, click the **Certificate** tab, click **Browse**, select the appropriate certificate, and then click **OK**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4013b-121">Le certificat utilisé pour vérifier une signature pour un tiers doit se différencier des certificats utilisés pour vérifier les signatures pour d'autres tiers.</span><span class="sxs-lookup"><span data-stu-id="4013b-121">The certificate used to verify a signature for a party must be unique from the certificates used to verify signatures for other parties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4013b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4013b-122">See Also</span></span>  
 [<span data-ttu-id="4013b-123">Configuration des certificats pour MIME ou Messages SMIME</span><span class="sxs-lookup"><span data-stu-id="4013b-123">Configuring Certificates for MIME or SMIME Messages</span></span>](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)