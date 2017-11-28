---
title: "Certificat non valide trouvé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b3a9ae8-a9d7-4025-bacd-443e136ff980
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fdf1d80818dd8e7dba349ea1dec9b69fa66a2fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-certificate-found"></a><span data-ttu-id="e59e9-102">Certificat non valide trouvé</span><span class="sxs-lookup"><span data-stu-id="e59e9-102">Invalid certificate found</span></span>
## <a name="details"></a><span data-ttu-id="e59e9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="e59e9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e59e9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e59e9-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e59e9-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e59e9-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="e59e9-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e59e9-106">Event ID</span></span>|<span data-ttu-id="e59e9-107">0</span><span class="sxs-lookup"><span data-stu-id="e59e9-107">0</span></span>|  
|<span data-ttu-id="e59e9-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e59e9-108">Event Source</span></span>|<span data-ttu-id="e59e9-109">0</span><span class="sxs-lookup"><span data-stu-id="e59e9-109">0</span></span>|  
|<span data-ttu-id="e59e9-110">Composant</span><span class="sxs-lookup"><span data-stu-id="e59e9-110">Component</span></span>|<span data-ttu-id="e59e9-111">0</span><span class="sxs-lookup"><span data-stu-id="e59e9-111">0</span></span>|  
|<span data-ttu-id="e59e9-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e59e9-112">Symbolic Name</span></span>|<span data-ttu-id="e59e9-113">0</span><span class="sxs-lookup"><span data-stu-id="e59e9-113">0</span></span>|  
|<span data-ttu-id="e59e9-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e59e9-114">Message Text</span></span>|<span data-ttu-id="e59e9-115">Certificat non valide trouvé</span><span class="sxs-lookup"><span data-stu-id="e59e9-115">Invalid certificate found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e59e9-116">Explication</span><span class="sxs-lookup"><span data-stu-id="e59e9-116">Explanation</span></span>  
 <span data-ttu-id="e59e9-117">Le certificat fourni pour le transport WCF est non valide.</span><span class="sxs-lookup"><span data-stu-id="e59e9-117">You did not provide a valid certificate for a WCF transport.</span></span>  

#### <a name="user-action"></a><span data-ttu-id="e59e9-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e59e9-118">User Action</span></span>
<span data-ttu-id="e59e9-119">Ajouter un certificat.</span><span class="sxs-lookup"><span data-stu-id="e59e9-119">Add a certificate.</span></span> 
  
## <a name="add-a-certificate"></a><span data-ttu-id="e59e9-120">Ajouter un certificat</span><span class="sxs-lookup"><span data-stu-id="e59e9-120">Add a certificate</span></span>  
  
1.  <span data-ttu-id="e59e9-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="e59e9-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e59e9-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="e59e9-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="e59e9-123">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="e59e9-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="e59e9-124">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="e59e9-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="e59e9-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e59e9-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="e59e9-126">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="e59e9-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="e59e9-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="e59e9-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="e59e9-128">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="e59e9-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="e59e9-129">Cliquez sur **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="e59e9-129">Click **Edit**.</span></span>  
  
10. <span data-ttu-id="e59e9-130">Dans le **Éditeur d’identités** boîte de dialogue zone, assurez-vous que les critères de recherche dans les **référence du certificat** section est correctement configurée pour indiquer des certificats valides.</span><span class="sxs-lookup"><span data-stu-id="e59e9-130">In the **Identity Editor** dialog box, make sure the search criteria in the **Certificate Reference** section is configured properly to indicate valid certificates.</span></span>  
  
 <span data-ttu-id="e59e9-131">Pour WCF-Custom et les adaptateurs WCF-CustomIsolated, vérifiez que les critères de recherche dans les **référence du certificat** section est correctement configurée pour indiquer un certificat valide dans le certificat **nom de magasin** .</span><span class="sxs-lookup"><span data-stu-id="e59e9-131">For the WCF-Custom and the WCF-CustomIsolated adapters, ensure that the search criteria in the **Certificate Reference** section is configured properly to indicate a valid certificate in the certificate **Store name**.</span></span>  
  
## <a name="add-a-certificate-for-standard-wcf-adapters"></a><span data-ttu-id="e59e9-132">Ajouter un certificat pour les adaptateurs WCF standard</span><span class="sxs-lookup"><span data-stu-id="e59e9-132">Add a certificate for standard WCF adapters</span></span>  
  
1.  <span data-ttu-id="e59e9-133">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="e59e9-133">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e59e9-134">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="e59e9-134">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="e59e9-135">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="e59e9-135">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="e59e9-136">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="e59e9-136">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="e59e9-137">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e59e9-137">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="e59e9-138">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="e59e9-138">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="e59e9-139">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="e59e9-139">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="e59e9-140">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **sécurité** onglet.</span><span class="sxs-lookup"><span data-stu-id="e59e9-140">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Security** tab.</span></span>  
  
9. <span data-ttu-id="e59e9-141">Vérifiez que le **l’empreinte numérique** propriétés pour les certificats de client et service indiquent des certificats valides dans le certificat **nom de magasin**.</span><span class="sxs-lookup"><span data-stu-id="e59e9-141">Ensure that the **Thumbprint** properties for the service and client certificates indicate valid certificates in the certificate **Store name**.</span></span>  
  
 <span data-ttu-id="e59e9-142">Dans le composant logiciel enfichable Certificat, vérifiez que des certificats valides sont installés pour le transport WCF.</span><span class="sxs-lookup"><span data-stu-id="e59e9-142">In the Certificate snap-in, make sure that valid certificates are installed for the WCF transport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e59e9-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e59e9-143">See also</span></span> 
  
[<span data-ttu-id="e59e9-144">Installation des certificats pour les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="e59e9-144">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)  