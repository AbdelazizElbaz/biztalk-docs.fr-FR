---
title: "Comment installer les certificats pour les Signatures numériques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 910ccd84-c022-46a5-a9de-b99046a480b8
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a755e59c7c916f3abe037513ddbc9e2a89892fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-certificates-for-digital-signatures"></a><span data-ttu-id="1887d-102">Installation des certificats pour les signatures numériques</span><span class="sxs-lookup"><span data-stu-id="1887d-102">How to install the Certificates for Digital Signatures</span></span>
<span data-ttu-id="1887d-103">La procédure suivante présente les étapes à suivre pour installer les certificats permettant de recevoir et d'envoyer des messages signés.</span><span class="sxs-lookup"><span data-stu-id="1887d-103">The following procedure lists the high-level steps that you have to follow to install the certificates for receiving and sending signed messages.</span></span>  
  
-   <span data-ttu-id="1887d-104">Pour installer les certificats dans le magasin de certificats afin de recevoir des messages signés</span><span class="sxs-lookup"><span data-stu-id="1887d-104">To install the certificates in the certificates store to receive signed messages</span></span>  
  
-   <span data-ttu-id="1887d-105">Pour installer les certificats de signature afin d'envoyer des messages signés dans le magasin de certificats</span><span class="sxs-lookup"><span data-stu-id="1887d-105">To install the signing certificates for sending signed messages in the certificates store</span></span>  
  
-   <span data-ttu-id="1887d-106">Pour configurer le groupe BizTalk afin d'envoyer des messages signés</span><span class="sxs-lookup"><span data-stu-id="1887d-106">To configure the BizTalk Group for sending signed messages</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1887d-107">Vous pouvez utiliser un seul certificat pour les opérations de signature et de déchiffrement, ou en utiliser un pour chaque fonction.</span><span class="sxs-lookup"><span data-stu-id="1887d-107">You can use one certificate for both signing and decryption operations, or you can use one certificate for each function.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1887d-108">Le serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'utilise qu'un seul certificat pour la signature de tous les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="1887d-108">You can only specify one signing certificate with which [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] signs all outbound messages.</span></span> <span data-ttu-id="1887d-109">En d'autres termes, vous ne pouvez pas utiliser de certificats de signature différents selon la personne à qui vous envoyez le message.</span><span class="sxs-lookup"><span data-stu-id="1887d-109">In other words, you cannot use different signing certificates depending on who you are sending the message to.</span></span>  
  
### <a name="to-install-the-certificates-in-the-certificates-store-to-receive-signed-messages"></a><span data-ttu-id="1887d-110">Pour installer les certificats dans le magasin de certificats afin de recevoir des messages signés</span><span class="sxs-lookup"><span data-stu-id="1887d-110">To install the certificates in the certificates store to receive signed messages</span></span>  
  
1.  <span data-ttu-id="1887d-111">Le Partenaire A demande une paire de clés publique/privée pour les signatures numériques auprès de l'autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="1887d-111">Partner A requests a private-public key pair for digital signatures from the certification authority (CA).</span></span>  
  
2.  <span data-ttu-id="1887d-112">Le Partenaire A vous envoie sa clé publique pour les signatures numériques.</span><span class="sxs-lookup"><span data-stu-id="1887d-112">Partner A sends you its public key for digital signatures.</span></span>  
  
3.  <span data-ttu-id="1887d-113">Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], connectez-vous au serveur ayant une instance d'hôte qui exécute un gestionnaire qui reçoit les messages du Partenaire A. Installez le certificat de clé publique de ce partenaire afin de vérifier sa signature dans le magasin Autres personnes.</span><span class="sxs-lookup"><span data-stu-id="1887d-113">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], log on to the server that has a host instance running a handler that will receive messages from Partner A. Install the Partner A public key certificate to verify their signature in the Other People store.</span></span> <span data-ttu-id="1887d-114">La figure suivante présente le magasin dans lequel vous installez le certificat.</span><span class="sxs-lookup"><span data-stu-id="1887d-114">The following figure shows the certificate store where you install the certificate.</span></span>  
  
     <span data-ttu-id="1887d-115">![Certificats requis pour recevoir des messages sécurisés](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")</span><span class="sxs-lookup"><span data-stu-id="1887d-115">![Certificates required to receive secure messages](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")</span></span>  
  
4.  <span data-ttu-id="1887d-116">Dans Partenaire A, installez le certificat de clé privée du Partenaire A pour signer les messages dans le magasin approprié.</span><span class="sxs-lookup"><span data-stu-id="1887d-116">In Partner A, install the Partner A private key certificate for signing messages in the appropriate store.</span></span> <span data-ttu-id="1887d-117">(Si le Partenaire A exécute [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], installez la clé privée dans le magasin personnel du compte qui signera les messages envoyés à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].)</span><span class="sxs-lookup"><span data-stu-id="1887d-117">(If Partner A is using [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)], or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], install the private key in the personal store for the account that will sign messages sent to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].)</span></span>  
  
### <a name="to-install-the-signing-certificates-for-sending-signed-messages-in-the-certificates-store"></a><span data-ttu-id="1887d-118">Pour installer les certificats de signature afin d'envoyer des messages signés dans le magasin de certificats</span><span class="sxs-lookup"><span data-stu-id="1887d-118">To install the signing certificates for sending signed messages in the certificates store</span></span>  
  
1.  <span data-ttu-id="1887d-119">L'un des administrateurs de votre entreprise demande auprès de l'autorité de certification une paire de clés publique/privée pour les signatures numériques qui sera utilisée par le serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1887d-119">An administrator in your organization requests a private-public key pair for digital signatures from the CA for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use.</span></span>  
  
2.  <span data-ttu-id="1887d-120">Il envoie au Partenaire A (ainsi qu'à tous les autres partenaires) la clé publique pour les signatures numériques.</span><span class="sxs-lookup"><span data-stu-id="1887d-120">The administrator sends Partner A (and all other partners) the public key for digital signatures.</span></span>  
  
3.  <span data-ttu-id="1887d-121">Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ouvrez une session en tant que compte de service pour l'instance d'hôte exécutant le gestionnaire qui enverra les messages au Partenaire A. Installez le certificat de clé privée du serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour la signature des messages dans le magasin personnel du compte de service.</span><span class="sxs-lookup"><span data-stu-id="1887d-121">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], log on as service account for the host instance running the handler that will send messages to Partner A. Install the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] private key certificate for signing messages in the personal store for the service account.</span></span> <span data-ttu-id="1887d-122">La figure suivante présente le magasin dans lequel vous installez le certificat.</span><span class="sxs-lookup"><span data-stu-id="1887d-122">The following figure shows the certificate store where you install the certificate.</span></span>  
  
     <span data-ttu-id="1887d-123">![Certificats requis pour envoyer des messages sécurisés](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")</span><span class="sxs-lookup"><span data-stu-id="1887d-123">![Certificates required to send secure messages](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")</span></span>  
  
4.  <span data-ttu-id="1887d-124">Dans Partenaire A, installez le certificat de clé publique du serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour la vérification de sa signature numérique dans le magasin approprié.</span><span class="sxs-lookup"><span data-stu-id="1887d-124">In Partner A, install the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] public key certificate for verifying its digital signature in the appropriate store.</span></span> <span data-ttu-id="1887d-125">(Si le Partenaire A exécute [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], installez la clé publique dans le magasin Autres personnes.)</span><span class="sxs-lookup"><span data-stu-id="1887d-125">(If Partner A is using [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)], or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], install the public key in the Other people store.)</span></span>  
  
### <a name="to-configure-the-biztalk-group-for-sending-signed-messages"></a><span data-ttu-id="1887d-126">Pour configurer le groupe BizTalk afin d'envoyer des messages signés</span><span class="sxs-lookup"><span data-stu-id="1887d-126">To configure the BizTalk Group for sending signed messages</span></span>  
  
1.  <span data-ttu-id="1887d-127">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="1887d-127">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="1887d-128">Avec le bouton droit **groupe BizTalk**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1887d-128">Right-click **BizTalk Group**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="1887d-129">Sur le **propriétés d’un groupe** boîte de dialogue, cliquez sur **certificat**, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="1887d-129">On the **Group Properties** dialog box, click **Certificate**, click **Browse**.</span></span>  
  
4.  <span data-ttu-id="1887d-130">Sur le **sélectionner un certificat** boîte de dialogue, sélectionnez le certificat de signature que vous avez installé, puis fermez toutes les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="1887d-130">On the **Select Certificate** dialog box, select the signing certificate that you installed, and then close all of the dialog boxes.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1887d-131">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1887d-131">Next Steps</span></span>  
 <span data-ttu-id="1887d-132">Vous créez un pipeline afin de recevoir des messages signés dans [comment configurer BizTalk Server pour la réception de Messages signés](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md).</span><span class="sxs-lookup"><span data-stu-id="1887d-132">You create a pipeline to receive signed messages in [How to Configure BizTalk Server for Receiving Signed Messages](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md).</span></span>  
  
 <span data-ttu-id="1887d-133">Pour créer un pipeline pour envoyer des messages signés [comment configurer BizTalk Server pour l’envoi de Messages signés](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md).</span><span class="sxs-lookup"><span data-stu-id="1887d-133">You create a pipeline to send signed messages in [How to Configure BizTalk Server for Sending Signed Messages](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1887d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1887d-134">See Also</span></span>  
 <span data-ttu-id="1887d-135">[Certificats utilisés par BizTalk Server pour les Messages signés](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span><span class="sxs-lookup"><span data-stu-id="1887d-135">[Certificates that BizTalk Server Uses for Signed Messages](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span></span>  
 [<span data-ttu-id="1887d-136">Envoyer et recevoir des Messages signés</span><span class="sxs-lookup"><span data-stu-id="1887d-136">Sending and Receiving Signed Messages</span></span>](../core/sending-and-receiving-signed-messages.md)