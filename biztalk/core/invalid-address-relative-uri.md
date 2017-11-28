---
title: Adresse non valide (uri relatif) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a953f3e-3768-4e61-8f25-ea958a5a701a
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 101a4544a83eb02438478d6d526dba422c44ae7b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-address-relative-uri"></a><span data-ttu-id="bd3e5-102">Adresse non valide (Uri relatif)</span><span class="sxs-lookup"><span data-stu-id="bd3e5-102">Invalid address (relative uri)</span></span>
## <a name="details"></a><span data-ttu-id="bd3e5-103">Détails</span><span class="sxs-lookup"><span data-stu-id="bd3e5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bd3e5-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="bd3e5-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="bd3e5-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="bd3e5-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="bd3e5-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="bd3e5-106">Event ID</span></span>|<span data-ttu-id="bd3e5-107">000</span><span class="sxs-lookup"><span data-stu-id="bd3e5-107">000</span></span>|  
|<span data-ttu-id="bd3e5-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="bd3e5-108">Event Source</span></span>|<span data-ttu-id="bd3e5-109">0</span><span class="sxs-lookup"><span data-stu-id="bd3e5-109">0</span></span>|  
|<span data-ttu-id="bd3e5-110">Composant</span><span class="sxs-lookup"><span data-stu-id="bd3e5-110">Component</span></span>|<span data-ttu-id="bd3e5-111">0</span><span class="sxs-lookup"><span data-stu-id="bd3e5-111">0</span></span>|  
|<span data-ttu-id="bd3e5-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="bd3e5-112">Symbolic Name</span></span>|<span data-ttu-id="bd3e5-113">0</span><span class="sxs-lookup"><span data-stu-id="bd3e5-113">0</span></span>|  
|<span data-ttu-id="bd3e5-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="bd3e5-114">Message Text</span></span>|<span data-ttu-id="bd3e5-115">Schéma d'adresse non valide ; schéma « {0} » attendu.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-115">Invalid address scheme; expecting "{0}" scheme.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bd3e5-116">Explication</span><span class="sxs-lookup"><span data-stu-id="bd3e5-116">Explanation</span></span>  
 <span data-ttu-id="bd3e5-117">L'adresse relative fournie pour l'emplacement de réception WCF isolé n'est pas bien formée.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-117">You did not provide an isolated WCF receive location with a well-formed relative address.</span></span> <span data-ttu-id="bd3e5-118">Par exemple, http://localhost/svc n'est pas une adresse relative correcte.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-118">For example, http://localhost/svc will not work as a relative address.</span></span> <span data-ttu-id="bd3e5-119">Vous ne pouvez pas définir la propriété Adresse de l'emplacement de réception WCF isolé sur une adresse absolue.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-119">You cannot set the Address property of the isolated WCF receive location to a absolute address.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bd3e5-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="bd3e5-120">User Action</span></span>  
 <span data-ttu-id="bd3e5-121">La procédure suivante permet de configurer l'adresse de l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-121">Use the following procedure to configure the receive location address.</span></span>  
  
#### <a name="to-configure-the-receive-location-address"></a><span data-ttu-id="bd3e5-122">Pour configurer l'adresse de l'emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="bd3e5-122">To configure the receive location address</span></span>  
  
1.  <span data-ttu-id="bd3e5-123">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-123">Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="bd3e5-124">Dans la racine de la Console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-124">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="bd3e5-125">Localisez votre application et du localiser votre transport.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-125">Locate your application and the locate your transport.</span></span>  
  
4.  <span data-ttu-id="bd3e5-126">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-126">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="bd3e5-127">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-127">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="bd3e5-128">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-128">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="bd3e5-129">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-129">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="bd3e5-130">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-130">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="bd3e5-131">Dans le **adresse (URI)** texte, changez l’adresse afin qu’elle commence par une barre oblique (« / »).</span><span class="sxs-lookup"><span data-stu-id="bd3e5-131">In the **Address (URI)** text box, change the address so that it starts with a forward slash ("/").</span></span>  
  
 <span data-ttu-id="bd3e5-132">Pour plus d'informations sur les emplacements de réception, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="bd3e5-132">For additional information on receive locations, see the following resources:</span></span>  
  
-   [<span data-ttu-id="bd3e5-133">Pour configurer les emplacement de réception WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="bd3e5-133">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="bd3e5-134">Pour configurer les emplacement de réception WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="bd3e5-134">How to Configure a WCF-WSHttp Receive Location</span></span>](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [<span data-ttu-id="bd3e5-135">Pour configurer les emplacement de réception WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="bd3e5-135">How to Configure a WCF-BasicHttp Receive Location</span></span>](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)