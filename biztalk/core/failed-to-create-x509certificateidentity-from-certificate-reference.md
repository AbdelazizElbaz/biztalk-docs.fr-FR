---
title: "Échec de création de X509CertificateIdentity à partir de la référence de certificat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3acee8e-c035-4e58-8bfc-397885b4d185
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c6bb03698010d667b27334f17fa7270de845c68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="failed-to-create-x509certificateidentity-from-certificate-reference"></a><span data-ttu-id="9ce2a-102">Échec de création de X509CertificateIdentity à partir de la référence du certificat</span><span class="sxs-lookup"><span data-stu-id="9ce2a-102">Failed to create X509CertificateIdentity from certificate reference</span></span>
## <a name="details"></a><span data-ttu-id="9ce2a-103">Détails</span><span class="sxs-lookup"><span data-stu-id="9ce2a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ce2a-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="9ce2a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="9ce2a-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="9ce2a-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="9ce2a-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="9ce2a-106">Event ID</span></span>|<span data-ttu-id="9ce2a-107">0</span><span class="sxs-lookup"><span data-stu-id="9ce2a-107">0</span></span>|  
|<span data-ttu-id="9ce2a-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="9ce2a-108">Event Source</span></span>|<span data-ttu-id="9ce2a-109">0</span><span class="sxs-lookup"><span data-stu-id="9ce2a-109">0</span></span>|  
|<span data-ttu-id="9ce2a-110">Composant</span><span class="sxs-lookup"><span data-stu-id="9ce2a-110">Component</span></span>|<span data-ttu-id="9ce2a-111">0</span><span class="sxs-lookup"><span data-stu-id="9ce2a-111">0</span></span>|  
|<span data-ttu-id="9ce2a-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="9ce2a-112">Symbolic Name</span></span>|<span data-ttu-id="9ce2a-113">0</span><span class="sxs-lookup"><span data-stu-id="9ce2a-113">0</span></span>|  
|<span data-ttu-id="9ce2a-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="9ce2a-114">Message Text</span></span>|<span data-ttu-id="9ce2a-115">Échec de création de X509CertificateIdentity à partir de la référence du certificat.</span><span class="sxs-lookup"><span data-stu-id="9ce2a-115">Failed to create X509CertificateIdentity from certificate reference.</span></span> <span data-ttu-id="9ce2a-116">(StoreName = {0}, StoreLocation = \ {1\\}, X509FindType = \ {2\}, FindValue = "\ {3\} »)</span><span class="sxs-lookup"><span data-stu-id="9ce2a-116">(StoreName={0}, StoreLocation={1}, X509FindType={2}, FindValue="{3}")</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9ce2a-117">Explication</span><span class="sxs-lookup"><span data-stu-id="9ce2a-117">Explanation</span></span>  
 <span data-ttu-id="9ce2a-118">Cette erreur indique que l'adaptateur n'a pas pu créer le X509Certificate spécifié pour la configuration de l'identité du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="9ce2a-118">This error indicates the adapter failed to create the X509Certificate specified in the endpoint identity configuration.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9ce2a-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="9ce2a-119">User Action</span></span>  
 <span data-ttu-id="9ce2a-120">La procédure suivante permet de vérifier les paramètres de la référence de certificat.</span><span class="sxs-lookup"><span data-stu-id="9ce2a-120">Use the following procedure to verify the certificate reference settings.</span></span>  
  
#### <a name="to-configure-the-certificate-reference-settings"></a><span data-ttu-id="9ce2a-121">Pour configurer les paramètres de la référence de certificat</span><span class="sxs-lookup"><span data-stu-id="9ce2a-121">To configure the certificate reference settings</span></span>  
  
1.  <span data-ttu-id="9ce2a-122">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="9ce2a-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="9ce2a-123">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="9ce2a-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="9ce2a-124">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="9ce2a-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="9ce2a-125">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="9ce2a-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="9ce2a-126">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="9ce2a-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="9ce2a-127">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="9ce2a-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="9ce2a-128">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="9ce2a-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="9ce2a-129">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="9ce2a-129">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="9ce2a-130">Dans le **identité du point de terminaison** , cliquez sur **modifier.**</span><span class="sxs-lookup"><span data-stu-id="9ce2a-130">In the **Endpoint Identity** section, click **Edit.**</span></span>  
  
10. <span data-ttu-id="9ce2a-131">Dans le **Éditeur d’identités** boîte de dialogue zone, vérifiez que le **référence du certificat** les paramètres sont valides.</span><span class="sxs-lookup"><span data-stu-id="9ce2a-131">In the **Identity Editor** dialog box, ensure that the **Certificate Reference** settings are valid.</span></span>