---
title: "Référence de certificat ambiguë | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7a6a60d-97e6-4c60-86be-83efb4a50f99
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 304ded9572ba6598f7f2132a678a14b2b3301c10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ambiguous-certificate-reference"></a><span data-ttu-id="382f0-102">Référence de certificat ambiguë</span><span class="sxs-lookup"><span data-stu-id="382f0-102">Ambiguous certificate reference</span></span>
## <a name="details"></a><span data-ttu-id="382f0-103">Détails</span><span class="sxs-lookup"><span data-stu-id="382f0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="382f0-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="382f0-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="382f0-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="382f0-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="382f0-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="382f0-106">Event ID</span></span>|<span data-ttu-id="382f0-107">0</span><span class="sxs-lookup"><span data-stu-id="382f0-107">0</span></span>|  
|<span data-ttu-id="382f0-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="382f0-108">Event Source</span></span>|<span data-ttu-id="382f0-109">0</span><span class="sxs-lookup"><span data-stu-id="382f0-109">0</span></span>|  
|<span data-ttu-id="382f0-110">Composant</span><span class="sxs-lookup"><span data-stu-id="382f0-110">Component</span></span>|<span data-ttu-id="382f0-111">0</span><span class="sxs-lookup"><span data-stu-id="382f0-111">0</span></span>|  
|<span data-ttu-id="382f0-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="382f0-112">Symbolic Name</span></span>|<span data-ttu-id="382f0-113">0</span><span class="sxs-lookup"><span data-stu-id="382f0-113">0</span></span>|  
|<span data-ttu-id="382f0-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="382f0-114">Message Text</span></span>|<span data-ttu-id="382f0-115">Référence de certificat ambiguë ; plusieurs certificats valides trouvés</span><span class="sxs-lookup"><span data-stu-id="382f0-115">Ambiguous certificate reference; more than one valid certificate found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="382f0-116">Explication</span><span class="sxs-lookup"><span data-stu-id="382f0-116">Explanation</span></span>  
 <span data-ttu-id="382f0-117">Plusieurs certificats valides ont été trouvés.</span><span class="sxs-lookup"><span data-stu-id="382f0-117">More than one valid certificate was found.</span></span>  
  
#### <a name="user-action"></a><span data-ttu-id="382f0-118">Action de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="382f0-118">User action</span></span>  
 <span data-ttu-id="382f0-119">Vérifiez qu’un seul certificat valide est configuré.</span><span class="sxs-lookup"><span data-stu-id="382f0-119">Verify only one valid certificate is configured.</span></span>  
  
## <a name="verify-certificate"></a><span data-ttu-id="382f0-120">Vérifier le certificat</span><span class="sxs-lookup"><span data-stu-id="382f0-120">Verify certificate</span></span> 
  
1.  <span data-ttu-id="382f0-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="382f0-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="382f0-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="382f0-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="382f0-123">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="382f0-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="382f0-124">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="382f0-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="382f0-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="382f0-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="382f0-126">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="382f0-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="382f0-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="382f0-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="382f0-128">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="382f0-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="382f0-129">Cliquez sur **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="382f0-129">Click **Edit**.</span></span>  
  
10. <span data-ttu-id="382f0-130">Dans le **Éditeur d’identités** boîte de dialogue zone, assurez-vous que les critères de recherche dans les **référence du certificat** section est correctement configurée pour n'indiquer qu’un seul certificat dans le certificat **magasin nom**.</span><span class="sxs-lookup"><span data-stu-id="382f0-130">In the **Identity Editor** dialog box, make sure the search criteria in the **Certificate Reference** section is configured properly to indicate only one certificate in the certificate **Store name**.</span></span>  
  
## <a name="verify-a-certificate-for-the-wcf-custom-and-the-wcf-customisolated-adapters"></a><span data-ttu-id="382f0-131">Vérifier un certificat de WCF-Custom et les adaptateurs WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="382f0-131">Verify a certificate for the WCF-Custom and the WCF-CustomIsolated adapters</span></span>  
  
1.  <span data-ttu-id="382f0-132">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="382f0-132">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2.  <span data-ttu-id="382f0-133">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="382f0-133">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="382f0-134">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="382f0-134">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="382f0-135">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="382f0-135">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="382f0-136">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="382f0-136">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="382f0-137">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="382f0-137">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="382f0-138">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="382f0-138">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="382f0-139">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **comportement** onglet.</span><span class="sxs-lookup"><span data-stu-id="382f0-139">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Behavior** tab.</span></span>  
  
9. <span data-ttu-id="382f0-140">Vérifiez les critères de recherche dans les **référence du certificat** section est correctement configurée pour n'indiquer qu’un seul certificat dans le certificat **nom de magasin**.</span><span class="sxs-lookup"><span data-stu-id="382f0-140">Ensure the search criteria in the **Certificate Reference** section is configured properly to indicate only one certificate in the certificate **Store name**.</span></span>  
  
10. <span data-ttu-id="382f0-141">Dans le composant logiciel enfichable Certificat, vérifiez que seul un certificat valide est installé pour les critères de recherche configurés dans le transport WCF.</span><span class="sxs-lookup"><span data-stu-id="382f0-141">In the Certificate snap-in, make sure only one certificate is installed for the search criteria you configured to the WCF transport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="382f0-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="382f0-142">See also</span></span>
[<span data-ttu-id="382f0-143">Installation des certificats pour les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="382f0-143">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)  
 