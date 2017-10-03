---
title: "Adresse non valide (uri relatif a besoin d’une barre oblique (&quot;-&quot;)) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1376f924-f119-4ba8-9be1-eea7ba5f3eb6
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa1c43d4a86af788c67ea59c7bf0ca7dea43da39
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-address-relative-uri-needs-slash-quot-quot"></a><span data-ttu-id="5525d-102">Adresse non valide (uri relatif a besoin d’une barre oblique (&quot;-&quot;))</span><span class="sxs-lookup"><span data-stu-id="5525d-102">Invalid address (relative uri needs slash (&quot;-&quot;))</span></span>
## <a name="details"></a><span data-ttu-id="5525d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5525d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5525d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5525d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5525d-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5525d-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="5525d-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5525d-106">Event ID</span></span>|<span data-ttu-id="5525d-107">0</span><span class="sxs-lookup"><span data-stu-id="5525d-107">0</span></span>|  
|<span data-ttu-id="5525d-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5525d-108">Event Source</span></span>|<span data-ttu-id="5525d-109">0</span><span class="sxs-lookup"><span data-stu-id="5525d-109">0</span></span>|  
|<span data-ttu-id="5525d-110">Composant</span><span class="sxs-lookup"><span data-stu-id="5525d-110">Component</span></span>|<span data-ttu-id="5525d-111">0</span><span class="sxs-lookup"><span data-stu-id="5525d-111">0</span></span>|  
|<span data-ttu-id="5525d-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5525d-112">Symbolic Name</span></span>|<span data-ttu-id="5525d-113">0</span><span class="sxs-lookup"><span data-stu-id="5525d-113">0</span></span>|  
|<span data-ttu-id="5525d-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5525d-114">Message Text</span></span>|<span data-ttu-id="5525d-115">Adresse non valide ; URI relatif commençant par une barre oblique ("/") attendu</span><span class="sxs-lookup"><span data-stu-id="5525d-115">Invalid address; expecting relative uri starting with slash ("/")</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5525d-116">Explication</span><span class="sxs-lookup"><span data-stu-id="5525d-116">Explanation</span></span>  
 <span data-ttu-id="5525d-117">L'adresse relative fournie pour l'emplacement de réception WCF isolé n'est pas bien formée.</span><span class="sxs-lookup"><span data-stu-id="5525d-117">You did not provide an isolated WCF receive location with a well-formed relative address.</span></span> <span data-ttu-id="5525d-118">Par exemple, http://localhost/svc n'est pas une adresse relative correcte.</span><span class="sxs-lookup"><span data-stu-id="5525d-118">For example, http://localhost/svc will not work as a relative address.</span></span> <span data-ttu-id="5525d-119">Vous ne pouvez pas définir la propriété Adresse de l'emplacement de réception WCF isolé sur une adresse absolue.</span><span class="sxs-lookup"><span data-stu-id="5525d-119">You cannot set the Address property of the isolated WCF receive location to a absolute address.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5525d-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5525d-120">User Action</span></span>  
 <span data-ttu-id="5525d-121">La procédure suivante permet de configurer une adresse.</span><span class="sxs-lookup"><span data-stu-id="5525d-121">Use the following procedure to configure an address.</span></span>  
  
#### <a name="to-configure-an-address"></a><span data-ttu-id="5525d-122">Pour configurer une adresse</span><span class="sxs-lookup"><span data-stu-id="5525d-122">To configure an address</span></span>  
  
1.  <span data-ttu-id="5525d-123">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="5525d-123">Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="5525d-124">Dans la racine de la Console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="5525d-124">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="5525d-125">Recherchez votre application et votre transport.</span><span class="sxs-lookup"><span data-stu-id="5525d-125">Locate your application and locate your transport.</span></span>  
  
4.  <span data-ttu-id="5525d-126">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="5525d-126">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="5525d-127">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5525d-127">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="5525d-128">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="5525d-128">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="5525d-129">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="5525d-129">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="5525d-130">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="5525d-130">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="5525d-131">Dans le **adresse (URI)** texte, modifiez l’adresse.</span><span class="sxs-lookup"><span data-stu-id="5525d-131">In the **Address (URI)** text box, change the address.</span></span> <span data-ttu-id="5525d-132">/path/service.svc est un exemple d'adresse relative bien formée.</span><span class="sxs-lookup"><span data-stu-id="5525d-132">An example of a well-formed relative address is /path/service.svc.</span></span>  
  
 <span data-ttu-id="5525d-133">Pour plus d'informations sur les emplacements de réception, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5525d-133">For additional information on receive locations, see the following:</span></span>  
  
-   [<span data-ttu-id="5525d-134">Pour configurer les emplacement de réception WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="5525d-134">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="5525d-135">Pour configurer les emplacement de réception WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="5525d-135">How to Configure a WCF-WSHttp Receive Location</span></span>](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [<span data-ttu-id="5525d-136">Pour configurer les emplacement de réception WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="5525d-136">How to Configure a WCF-BasicHttp Receive Location</span></span>](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)