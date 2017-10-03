---
title: "Sécurisation de la Page ASPX expéditeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ASPX pages, protocol rules
- security, ASPX pages
- RNIFSend.aspx
- ASPX pages, security
- protocol rules [ASPX pages]
ms.assetid: 8214e3f5-a8e9-4d71-957d-ed0852035030
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0c5d5ec97d4d4aed862ffc1dbc0d75d0c0430d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="securing-the-sender-aspx-page"></a><span data-ttu-id="4840d-102">Sécurisation de la Page ASPX expéditeur</span><span class="sxs-lookup"><span data-stu-id="4840d-102">Securing the Sender ASPX Page</span></span>
<span data-ttu-id="4840d-103">Cette rubrique décrit comment protéger la page du fichier RNIFSend.aspx à partir de toute utilisation non autorisée.</span><span class="sxs-lookup"><span data-stu-id="4840d-103">This topic describes how to protect the RNIFSend.aspx page from unauthorized use.</span></span> <span data-ttu-id="4840d-104">Il existe deux procédures que vous pouvez utiliser :</span><span class="sxs-lookup"><span data-stu-id="4840d-104">There are two procedures that you can use:</span></span>  
  
-   <span data-ttu-id="4840d-105">Dans Gestionnaire des Services Internet (IIS), sécurisez le fichier RNIFSend.aspx pour vous assurer qu’aucun serveur non autorisé n’utilise la page de fichier RNIFSend.aspx pour transmettre des messages non autorisés de votre réseau.</span><span class="sxs-lookup"><span data-stu-id="4840d-105">In Internet Information Services (IIS) Manager, secure RNIFSend.aspx to make sure that no unauthorized server will use the RNIFSend.aspx page to transmit unauthorized messages from your network.</span></span>  
  
-   <span data-ttu-id="4840d-106">Utilisez Microsoft Internet Security and Acceleration (ISA) Server pour créer une règle de protocole de demandes HTTP sortantes.</span><span class="sxs-lookup"><span data-stu-id="4840d-106">Use Microsoft Internet Security and Acceleration (ISA) Server to create a protocol rule of outgoing HTTP requests.</span></span>  
  
### <a name="to-secure-rnifsendaspx"></a><span data-ttu-id="4840d-107">Pour sécuriser le fichier RNIFSend.aspx</span><span class="sxs-lookup"><span data-stu-id="4840d-107">To secure RNIFSend.aspx</span></span>  
  
1.  <span data-ttu-id="4840d-108">Sur le serveur Web que vous utilisez pour la transmission de message RNIF, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur  **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="4840d-108">On the Web server you use for RNIF message transmission, click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="4840d-109">Dans le Gestionnaire IIS, développez le nœud ordinateur local, **Sites Web**, puis développez **Site Web par défaut**.</span><span class="sxs-lookup"><span data-stu-id="4840d-109">In IIS Manager, expand the local computer node, expand **Web Sites**, and then expand **Default Web Site**.</span></span>  
  
3.  <span data-ttu-id="4840d-110">Cliquez sur **btarnapp fait**et, dans le volet droit, cliquez sur **fichier RNIFSend.aspx**.</span><span class="sxs-lookup"><span data-stu-id="4840d-110">Click **BTARNApp**, and then in the right pane, right-click **RNIFSend.aspx**.</span></span>  
  
4.  <span data-ttu-id="4840d-111">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="4840d-111">Click **Properties**.</span></span> <span data-ttu-id="4840d-112">Sur le **sécurité du fichier** sous l’onglet du **restrictions de nom de domaine et les adresses IP** , cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="4840d-112">On the **File Security** tab, in the **IP address and domain name restrictions** section, click **Edit**.</span></span>  
  
5.  <span data-ttu-id="4840d-113">Dans la boîte de dialogue adresse IP et les Restrictions de nom de domaine, cliquez sur **accès refusé**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="4840d-113">In the IP Address and Domain Name Restrictions dialog box, click **Denied Access**, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="4840d-114">Dans le **accorder l’accès** boîte de dialogue Ajouter des serveurs BizTalk toutes les opérations d’envoi.</span><span class="sxs-lookup"><span data-stu-id="4840d-114">In the **Grant Access** dialog box, add all BizTalk Servers performing send operations.</span></span> <span data-ttu-id="4840d-115">Si vous ajoutez un serveur unique, cliquez sur **seul ordinateur**.</span><span class="sxs-lookup"><span data-stu-id="4840d-115">If adding a single server, click **Single computer**.</span></span> <span data-ttu-id="4840d-116">Dans le **adresse IP** zone, tapez l’adresse IP de l’ordinateur, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4840d-116">In the **IP Address** box, type the IP address for the computer, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="4840d-117">Si vous ajoutez un groupe de serveurs, cliquez sur **groupe d’ordinateurs**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4840d-117">If adding a group of servers, click **Group of Computers**, and then do the following:</span></span>  
  
    |<span data-ttu-id="4840d-118">Utiliser</span><span class="sxs-lookup"><span data-stu-id="4840d-118">Use this</span></span>|<span data-ttu-id="4840d-119">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="4840d-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4840d-120">**ID de réseau**</span><span class="sxs-lookup"><span data-stu-id="4840d-120">**Network ID**</span></span>|<span data-ttu-id="4840d-121">Tapez le réseau que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="4840d-121">Type the network you want to use.</span></span>|  
    |<span data-ttu-id="4840d-122">**Masque de sous-réseau**</span><span class="sxs-lookup"><span data-stu-id="4840d-122">**Subnet mask**</span></span>|<span data-ttu-id="4840d-123">Tapez le masque de sous-réseau que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="4840d-123">Type the subnet mask you want to use.</span></span>|  
  
8.  <span data-ttu-id="4840d-124">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4840d-124">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4840d-125">Si vous avez réparti vos opérations d’envoi à un hôte distinct en cours d’exécution sur une instance distincte, vous devez uniquement ajouter cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4840d-125">If you have separated all your send operations to a separate host running on a separate instance, then you only have to add this computer.</span></span> <span data-ttu-id="4840d-126">Vous pouvez refuser tous les autres accès.</span><span class="sxs-lookup"><span data-stu-id="4840d-126">You can deny all others access.</span></span>  
  
9. <span data-ttu-id="4840d-127">Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="4840d-127">Click **OK**, and then click **OK** again.</span></span>  
  
### <a name="to-create-a-protocol-rule-of-outgoing-http-requests"></a><span data-ttu-id="4840d-128">Pour créer une règle de protocole de demandes HTTP sortantes</span><span class="sxs-lookup"><span data-stu-id="4840d-128">To create a protocol rule of outgoing HTTP requests</span></span>  
  
1.  <span data-ttu-id="4840d-129">Dans Gestion ISA, cliquez sur **la stratégie d’accès**, puis cliquez sur **les règles de protocole**.</span><span class="sxs-lookup"><span data-stu-id="4840d-129">In ISA Management, click **Access Policy**, and then click **Protocol Rules**.</span></span>  
  
2.  <span data-ttu-id="4840d-130">Créer une nouvelle règle de protocole nommée **HTTP** qui utilise le protocole TCP.</span><span class="sxs-lookup"><span data-stu-id="4840d-130">Create a new protocol rule named **HTTP** that uses TCP protocol.</span></span>  
  
3.  <span data-ttu-id="4840d-131">Dans la page de propriétés de votre HTTP nouvelle règle, de protocole dans la **s’applique à** onglet, sélectionnez **s’applique à des ensembles d’adresses Client spécifiés ci-dessous**.</span><span class="sxs-lookup"><span data-stu-id="4840d-131">In the property page of your new HTTP protocol rule, in the **Applies To** tab, select **Applies to Client address sets specified below**.</span></span> <span data-ttu-id="4840d-132">Entrez uniquement les adresses IP que vous souhaitez accéder à la page client.</span><span class="sxs-lookup"><span data-stu-id="4840d-132">Enter only those client IPs that you want to access the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4840d-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4840d-133">See Also</span></span>  
 [<span data-ttu-id="4840d-134">Gérer la configuration, les certificats, les bases de données et la sécurité</span><span class="sxs-lookup"><span data-stu-id="4840d-134">Manage configuration, certificates, databases, and security</span></span>](manage-configuration-certificates-databases-security.md)