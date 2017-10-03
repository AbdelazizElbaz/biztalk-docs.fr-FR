---
title: "Adresse de proxy non valide (pour le port d’envoi et de gestionnaire d’envoi) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccedd23e-7d44-4419-b519-e04511e1f176
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d33af2f4fa068294c38ecb4146cd1f8d05d68aea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-proxy-address-for-send-handler-and-send-port"></a><span data-ttu-id="062c6-102">Adresse de proxy non valide (pour le port et le gestionnaire d'envoi)</span><span class="sxs-lookup"><span data-stu-id="062c6-102">Invalid proxy address (for send handler and send port)</span></span>
## <a name="details"></a><span data-ttu-id="062c6-103">Détails</span><span class="sxs-lookup"><span data-stu-id="062c6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="062c6-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="062c6-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="062c6-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="062c6-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="062c6-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="062c6-106">Event ID</span></span>|<span data-ttu-id="062c6-107">0</span><span class="sxs-lookup"><span data-stu-id="062c6-107">0</span></span>|  
|<span data-ttu-id="062c6-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="062c6-108">Event Source</span></span>|<span data-ttu-id="062c6-109">0</span><span class="sxs-lookup"><span data-stu-id="062c6-109">0</span></span>|  
|<span data-ttu-id="062c6-110">Composant</span><span class="sxs-lookup"><span data-stu-id="062c6-110">Component</span></span>|<span data-ttu-id="062c6-111">0</span><span class="sxs-lookup"><span data-stu-id="062c6-111">0</span></span>|  
|<span data-ttu-id="062c6-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="062c6-112">Symbolic Name</span></span>|<span data-ttu-id="062c6-113">0</span><span class="sxs-lookup"><span data-stu-id="062c6-113">0</span></span>|  
|<span data-ttu-id="062c6-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="062c6-114">Message Text</span></span>|<span data-ttu-id="062c6-115">Adresse de proxy non valide : {0}</span><span class="sxs-lookup"><span data-stu-id="062c6-115">Invalid proxy address: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="062c6-116">Explication</span><span class="sxs-lookup"><span data-stu-id="062c6-116">Explanation</span></span>  
 <span data-ttu-id="062c6-117">Le gestionnaire d'envoi WCF ou le port d'envoi WCF fourni ne possède pas d'adresse de proxy valide.</span><span class="sxs-lookup"><span data-stu-id="062c6-117">You did not provide a WCF send handler or a WCF send port with a valid proxy address.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="062c6-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="062c6-118">User Action</span></span>  
 <span data-ttu-id="062c6-119">La procédure suivante permet de configurer une adresse de proxy.</span><span class="sxs-lookup"><span data-stu-id="062c6-119">Use the following procedure to configure a proxy address.</span></span>  
  
#### <a name="to-configure-a-proxy-address"></a><span data-ttu-id="062c6-120">Pour configurer une adresse de proxy</span><span class="sxs-lookup"><span data-stu-id="062c6-120">To configure a proxy address</span></span>  
  
1.  <span data-ttu-id="062c6-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="062c6-121">Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="062c6-122">Dans la racine de la Console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="062c6-122">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="062c6-123">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="062c6-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="062c6-124">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="062c6-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="062c6-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="062c6-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="062c6-126">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="062c6-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="062c6-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="062c6-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="062c6-128">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **Proxy** onglet.</span><span class="sxs-lookup"><span data-stu-id="062c6-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Proxy** tab.</span></span>  
  
9. <span data-ttu-id="062c6-129">Vérifiez que l’adresse proxy dans le **paramètres Proxy** section est correctement configurée.</span><span class="sxs-lookup"><span data-stu-id="062c6-129">Verify that the proxy address in the **Proxy settings** section is configured properly.</span></span>  
  
 <span data-ttu-id="062c6-130">Pour plus d'informations sur les ports et gestionnaires d'envoi, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="062c6-130">For additional information on send ports and send handlers, see the following resources:</span></span>  
  
-   [<span data-ttu-id="062c6-131">Comment configurer un Port d’envoi WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="062c6-131">How to Configure a WCF-WSHttp Send Port</span></span>](../core/how-to-configure-a-wcf-wshttp-send-port.md)  
  
-   [<span data-ttu-id="062c6-132">Comment configurer un Port d’envoi WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="062c6-132">How to Configure a WCF-BasicHttp Send Port</span></span>](http://msdn.microsoft.com/library/acdb50fa-57fe-4657-9561-b6b2f4919c7f)  
  
-   [<span data-ttu-id="062c6-133">Comment configurer un gestionnaire d’envoi WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="062c6-133">How to Configure a WCF-BasicHttp Send Handler</span></span>](http://msdn.microsoft.com/library/18dcc616-4732-42f8-bd64-e55a5ebbaa49)  
  
-   [<span data-ttu-id="062c6-134">Comment configurer un gestionnaire d’envoi WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="062c6-134">How to Configure a WCF-WSHttp Send Handler</span></span>](../core/how-to-configure-a-wcf-wshttp-send-handler.md)  
  
-   [<span data-ttu-id="062c6-135">Comment configurer un Port d’envoi WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="062c6-135">How to Configure a WCF-Custom Send Port</span></span>](../core/how-to-configure-a-wcf-custom-send-port.md)