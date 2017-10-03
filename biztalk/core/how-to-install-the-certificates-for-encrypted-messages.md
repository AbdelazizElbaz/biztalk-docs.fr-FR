---
title: "Comment installer les certificats pour les Messages chiffrés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e11fdb81-041c-4ba6-849d-d511ead0e8be
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b1df2e9e5bf42a215420dac155fafac8e92ae21
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-certificates-for-encrypted-messages"></a><span data-ttu-id="7ad94-102">Installation des certificats pour les messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="7ad94-102">How to Install the Certificates for Encrypted Messages</span></span>
<span data-ttu-id="7ad94-103">La procédure suivante présente les étapes à suivre pour installer les certificats permettant de recevoir et d'envoyer des messages chiffrés.</span><span class="sxs-lookup"><span data-stu-id="7ad94-103">The following procedure lists the high-level steps that you have to follow to install the certificates for receiving and sending encrypted messages.</span></span>  
  
-   <span data-ttu-id="7ad94-104">Pour installer les certificats dans le magasin dans un objectif de déchiffrement</span><span class="sxs-lookup"><span data-stu-id="7ad94-104">To install certificates in the certificates store for decryption</span></span>  
  
-   <span data-ttu-id="7ad94-105">Pour installer les certificats dans le magasin dans un objectif de chiffrement</span><span class="sxs-lookup"><span data-stu-id="7ad94-105">To install certificates in the certificates store for encryption</span></span>  
  
-   <span data-ttu-id="7ad94-106">Pour configurer les hôtes BizTalk pour la réception de messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="7ad94-106">To configure BizTalk hosts for receiving encrypted messages</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ad94-107">Vous pouvez utiliser un seul certificat pour les opérations de signature et de déchiffrement, ou en utiliser un pour chaque fonction.</span><span class="sxs-lookup"><span data-stu-id="7ad94-107">You can use one certificate for both signing and decryption operations, or you can use one certificate for each function.</span></span>  
  
### <a name="to-install-the-decryption-certificates-in-the-certificates-store"></a><span data-ttu-id="7ad94-108">Pour installer les certificats de déchiffrement dans le magasin</span><span class="sxs-lookup"><span data-stu-id="7ad94-108">To install the decryption certificates in the certificates store</span></span>  
  
1.  <span data-ttu-id="7ad94-109">L'un des administrateurs de votre entreprise demande auprès de l'autorité de certification une paire de clés publique/privée pour le chiffrement qui sera utilisée par le serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ad94-109">An administrator in your organization requests a private-public key pair for encryption from the certification authority (CA) for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use.</span></span>  
  
2.  <span data-ttu-id="7ad94-110">Il envoie au Partenaire A la clé publique de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="7ad94-110">The administrator sends the public key for encryption to Partner A.</span></span>  
  
3.  <span data-ttu-id="7ad94-111">Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ouvrez une session en tant que compte de service pour l'instance d'hôte exécutant le gestionnaire qui recevra les messages du Partenaire A. Installez le certificat de clé privée du serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour le déchiffrement des messages dans le magasin personnel du compte de service.</span><span class="sxs-lookup"><span data-stu-id="7ad94-111">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], log on as the service account for the host instance running the handler that will receive messages from Partner A. Install the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] private key certificate for decrypting messages in the personal store for the service account.</span></span> <span data-ttu-id="7ad94-112">La figure suivante présente le magasin dans lequel vous installez le certificat.</span><span class="sxs-lookup"><span data-stu-id="7ad94-112">The following figure shows the certificate store where you install the certificate.</span></span>  
  
     <span data-ttu-id="7ad94-113">![Certificats requis pour recevoir des messages sécurisés](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")</span><span class="sxs-lookup"><span data-stu-id="7ad94-113">![Certificates required to receive secure messages](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")</span></span>  
  
4.  <span data-ttu-id="7ad94-114">Dans Partenaire A, installez le certificat de clé publique du serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour le chiffrement des messages envoyés au Partenaire A dans le magasin approprié.</span><span class="sxs-lookup"><span data-stu-id="7ad94-114">In Partner A, install the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] public key certificate for encrypting messages sent to Partner A in the appropriate store.</span></span> <span data-ttu-id="7ad94-115">(Si le partenaire a utilise [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)], [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], installez la clé publique dans le magasin autres personnes.)</span><span class="sxs-lookup"><span data-stu-id="7ad94-115">(If Partner A is using [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)], [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], install the public key in the Other People store.)</span></span>  
  
### <a name="to-install-the-encryption-certificates-in-the-certificates-store"></a><span data-ttu-id="7ad94-116">Pour installer les certificats de chiffrement dans le magasin</span><span class="sxs-lookup"><span data-stu-id="7ad94-116">To install the encryption certificates in the certificates store</span></span>  
  
1.  <span data-ttu-id="7ad94-117">Le Partenaire A demande une paire de clés publique/privée pour le chiffrement auprès de l'autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="7ad94-117">Partner A requests a private-public key pair for encryption from the CA.</span></span>  
  
2.  <span data-ttu-id="7ad94-118">Le Partenaire A installe le certificat de clé privée pour déchiffrer les messages dans le magasin approprié.</span><span class="sxs-lookup"><span data-stu-id="7ad94-118">Partner A installs the private key certificate for decrypting the messages in the appropriate store.</span></span> <span data-ttu-id="7ad94-119">(Si le Partenaire A exécute [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], installez la clé privée dans le magasin de certificats personnel.)</span><span class="sxs-lookup"><span data-stu-id="7ad94-119">(If Partner A is using [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)], [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], install the private key in the personal certificate store.)</span></span>  
  
3.  <span data-ttu-id="7ad94-120">Le Partenaire A vous envoie sa clé publique pour le chiffrement des messages vers le Partenaire A.</span><span class="sxs-lookup"><span data-stu-id="7ad94-120">Partner A sends you its public key for encrypting messages sent to Partner A.</span></span>  
  
4.  <span data-ttu-id="7ad94-121">Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], connectez-vous au serveur ayant une instance d'hôte qui exécute un gestionnaire qui enverra les messages au Partenaire A. Installez le certificat de clé publique de ce partenaire afin de chiffrer les messages envoyés au Partenaire A dans le magasin Autres personnes.</span><span class="sxs-lookup"><span data-stu-id="7ad94-121">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], log on to the server that has a host instance running a handler that will send messages to Partner A. Install the Partner A public key certificate for encrypting messages sent to Partner A in the Other People store.</span></span> <span data-ttu-id="7ad94-122">La figure suivante présente le magasin dans lequel vous installez le certificat.</span><span class="sxs-lookup"><span data-stu-id="7ad94-122">The following figure shows the certificate store where you install the certificate.</span></span>  
  
     <span data-ttu-id="7ad94-123">![Certificats requis pour envoyer des messages sécurisés](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")</span><span class="sxs-lookup"><span data-stu-id="7ad94-123">![Certificates required to send secure messages](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")</span></span>  
  
### <a name="to-configure-biztalk-hosts-for-receiving-encrypted-messages"></a><span data-ttu-id="7ad94-124">Pour configurer les hôtes BizTalk pour la réception de messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="7ad94-124">To configure BizTalk hosts for receiving encrypted messages</span></span>  
  
1.  <span data-ttu-id="7ad94-125">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="7ad94-125">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="7ad94-126">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **paramètres de plateforme**, développez **hôtes**.</span><span class="sxs-lookup"><span data-stu-id="7ad94-126">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **Platform Settings**, expand **Hosts**.</span></span>  
  
    1.  <span data-ttu-id="7ad94-127">Dans le volet droit, cliquez sur un hôte BizTalk qui est le Gestionnaire de réception des messages chiffrés, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7ad94-127">On the right pane, right-click a BizTalk host that is the handler for receiving the encrypted messages, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="7ad94-128">Sur le **propriétés de l’hôte** boîte de dialogue, cliquez sur **certificat**, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="7ad94-128">On the **Host Properties** dialog box, click **Certificate**, click **Browse**.</span></span>  
  
    3.  <span data-ttu-id="7ad94-129">Sur le **sélectionner un certificat** boîte de dialogue, sélectionnez le certificat de déchiffrement que vous avez installé, puis fermez toutes les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="7ad94-129">On the **Select Certificate** dialog box, select the decryption certificate that you installed, and then close all of the dialog boxes.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="7ad94-130">Pour plus d’informations, consultez [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md).</span><span class="sxs-lookup"><span data-stu-id="7ad94-130">For more information, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7ad94-131">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7ad94-131">Next Steps</span></span>  
 <span data-ttu-id="7ad94-132">Vous créez un pipeline afin de recevoir des messages chiffrés dans [comment configurer BizTalk Server pour recevoir des Messages chiffrés](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md)</span><span class="sxs-lookup"><span data-stu-id="7ad94-132">You create a pipeline to receive encrypted messages in [How to Configure BizTalk Server for Receiving Encrypted Messages](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md)</span></span>  
  
 <span data-ttu-id="7ad94-133">Pour créer un pipeline pour envoyer des messages chiffrés [comment configurer BizTalk Server pour envoyer des Messages chiffrés](../core/how-to-configure-biztalk-server-for-sending-encrypted-messages.md)</span><span class="sxs-lookup"><span data-stu-id="7ad94-133">You create a pipeline to send encrypted messages in [How to Configure BizTalk Server for Sending Encrypted Messages](../core/how-to-configure-biztalk-server-for-sending-encrypted-messages.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ad94-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ad94-134">See Also</span></span>  
 <span data-ttu-id="7ad94-135">[Certificats utilisés par BizTalk Server pour les Messages chiffrés](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span><span class="sxs-lookup"><span data-stu-id="7ad94-135">[Certificates that BizTalk Server Uses for Encrypted Messages](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span></span>  
 [<span data-ttu-id="7ad94-136">Envoyer et recevoir des Messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="7ad94-136">Sending and Receiving Encrypted Messages</span></span>](../core/sending-and-receiving-encrypted-messages.md)