---
title: Certificat introuvable | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 629b199f-1884-4e88-beaa-a2e5c5e792e9
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1c18f112edc14375e6edc2aaa52c9e468d1bd39
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="certificate-not-found"></a><span data-ttu-id="e7281-102">Certificat introuvable</span><span class="sxs-lookup"><span data-stu-id="e7281-102">Certificate not found</span></span>
## <a name="details"></a><span data-ttu-id="e7281-103">Détails</span><span class="sxs-lookup"><span data-stu-id="e7281-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e7281-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e7281-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e7281-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e7281-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="e7281-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e7281-106">Event ID</span></span>|<span data-ttu-id="e7281-107">0</span><span class="sxs-lookup"><span data-stu-id="e7281-107">0</span></span>|  
|<span data-ttu-id="e7281-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e7281-108">Event Source</span></span>|<span data-ttu-id="e7281-109">0</span><span class="sxs-lookup"><span data-stu-id="e7281-109">0</span></span>|  
|<span data-ttu-id="e7281-110">Composant</span><span class="sxs-lookup"><span data-stu-id="e7281-110">Component</span></span>|<span data-ttu-id="e7281-111">0</span><span class="sxs-lookup"><span data-stu-id="e7281-111">0</span></span>|  
|<span data-ttu-id="e7281-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e7281-112">Symbolic Name</span></span>|<span data-ttu-id="e7281-113">0</span><span class="sxs-lookup"><span data-stu-id="e7281-113">0</span></span>|  
|<span data-ttu-id="e7281-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e7281-114">Message Text</span></span>|<span data-ttu-id="e7281-115">Certificat introuvable.</span><span class="sxs-lookup"><span data-stu-id="e7281-115">Certificate not found.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e7281-116">Explication</span><span class="sxs-lookup"><span data-stu-id="e7281-116">Explanation</span></span>  
 <span data-ttu-id="e7281-117">Aucun certificat correspondant aux critères de recherche n'a été trouvé.</span><span class="sxs-lookup"><span data-stu-id="e7281-117">A certificate could not be found for the given search criteria.</span></span>  

#### <a name="user-action"></a><span data-ttu-id="e7281-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e7281-118">User Action</span></span>
<span data-ttu-id="e7281-119">Vérifiez les critères de recherche de certificats.</span><span class="sxs-lookup"><span data-stu-id="e7281-119">Verify search criteria for certificates.</span></span> 
  
## <a name="verify-search-criteria"></a><span data-ttu-id="e7281-120">Vérifier les critères de recherche</span><span class="sxs-lookup"><span data-stu-id="e7281-120">Verify search criteria</span></span>  
  
1.  <span data-ttu-id="e7281-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="e7281-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e7281-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="e7281-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="e7281-123">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="e7281-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="e7281-124">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="e7281-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="e7281-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e7281-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="e7281-126">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="e7281-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="e7281-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="e7281-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="e7281-128">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="e7281-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="e7281-129">Cliquez sur **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="e7281-129">Click **Edit**.</span></span>  
  
10. <span data-ttu-id="e7281-130">Dans le **Éditeur d’identités** boîte de dialogue zone, assurez-vous que les critères de recherche dans les **référence du certificat** section est correctement configurée pour indiquer des certificats valides.</span><span class="sxs-lookup"><span data-stu-id="e7281-130">In the **Identity Editor** dialog box, make sure that the search criteria in the **Certificate Reference** section is configured properly to indicate valid certificates.</span></span>  
  
 <span data-ttu-id="e7281-131">Pour WCF-Custom et les adaptateurs WCF-CustomIsolated, vérifiez que les critères de recherche dans les **référence du certificat** section est correctement configurée pour indiquer un certificat valide dans le certificat **nom de magasin** .</span><span class="sxs-lookup"><span data-stu-id="e7281-131">For the WCF-Custom and the WCF-CustomIsolated adapters, ensure that the search criteria in the **Certificate Reference** section is configured properly to indicate a valid certificate in the certificate **Store name**.</span></span>  
  
## <a name="verify-search-criteria-for-standard-wcf-adapters"></a><span data-ttu-id="e7281-132">Vérifier les critères de recherche pour les adaptateurs WCF standards</span><span class="sxs-lookup"><span data-stu-id="e7281-132">Verify search criteria for standard WCF adapters</span></span>  
  
1.  <span data-ttu-id="e7281-133">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="e7281-133">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e7281-134">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="e7281-134">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="e7281-135">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="e7281-135">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="e7281-136">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="e7281-136">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="e7281-137">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e7281-137">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="e7281-138">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="e7281-138">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="e7281-139">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="e7281-139">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="e7281-140">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **sécurité** onglet.</span><span class="sxs-lookup"><span data-stu-id="e7281-140">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Security** tab.</span></span>  
  
9. <span data-ttu-id="e7281-141">Vérifiez que le **l’empreinte numérique** propriétés pour les certificats de client et service indiquent des certificats valides dans les magasins de certificats.</span><span class="sxs-lookup"><span data-stu-id="e7281-141">Ensure that the **Thumbprint** properties for the service and client certificates indicate valid certificates in certificate stores.</span></span>  
  
10. <span data-ttu-id="e7281-142">Dans le composant logiciel enfichable Certificat, vérifiez que des certificats valides sont installés pour le transport WCF.</span><span class="sxs-lookup"><span data-stu-id="e7281-142">In the Certificate snap-in, make sure that valid certificates are installed for the WCF transport.</span></span>  

## <a name="see-also"></a><span data-ttu-id="e7281-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7281-143">See also</span></span> 
  
-   [<span data-ttu-id="e7281-144">Installation des certificats pour les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="e7281-144">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)  
  
