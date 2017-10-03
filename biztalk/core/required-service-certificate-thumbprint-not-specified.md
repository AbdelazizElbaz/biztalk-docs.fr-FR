---
title: "Requis d’empreinte numérique du certificat de service non spécifié | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca853667-83b5-41f2-9b54-8117b87e27d3
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6dc43d9ed50aaacd108b275063cf00d18aea743
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="required-service-certificate-thumbprint-not-specified"></a><span data-ttu-id="1c9cd-102">L'empreinte de certificat de service obligatoire n'a pas été indiquée</span><span class="sxs-lookup"><span data-stu-id="1c9cd-102">Required service certificate thumbprint not specified</span></span>
## <a name="details"></a><span data-ttu-id="1c9cd-103">Détails</span><span class="sxs-lookup"><span data-stu-id="1c9cd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c9cd-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="1c9cd-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="1c9cd-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="1c9cd-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="1c9cd-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="1c9cd-106">Event ID</span></span>|<span data-ttu-id="1c9cd-107">0</span><span class="sxs-lookup"><span data-stu-id="1c9cd-107">0</span></span>|  
|<span data-ttu-id="1c9cd-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="1c9cd-108">Event Source</span></span>|<span data-ttu-id="1c9cd-109">0</span><span class="sxs-lookup"><span data-stu-id="1c9cd-109">0</span></span>|  
|<span data-ttu-id="1c9cd-110">Composant</span><span class="sxs-lookup"><span data-stu-id="1c9cd-110">Component</span></span>|<span data-ttu-id="1c9cd-111">0</span><span class="sxs-lookup"><span data-stu-id="1c9cd-111">0</span></span>|  
|<span data-ttu-id="1c9cd-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="1c9cd-112">Symbolic Name</span></span>|<span data-ttu-id="1c9cd-113">0</span><span class="sxs-lookup"><span data-stu-id="1c9cd-113">0</span></span>|  
|<span data-ttu-id="1c9cd-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="1c9cd-114">Message Text</span></span>|<span data-ttu-id="1c9cd-115">L'empreinte de certificat de service obligatoire n'a pas été indiquée</span><span class="sxs-lookup"><span data-stu-id="1c9cd-115">Required service certificate thumbprint not specified</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1c9cd-116">Explication</span><span class="sxs-lookup"><span data-stu-id="1c9cd-116">Explanation</span></span>  
 <span data-ttu-id="1c9cd-117">Vous n'avez pas défini la propriété Certificat de service requise pour les paramètres de sécurité d'un port d'envoi WCF.</span><span class="sxs-lookup"><span data-stu-id="1c9cd-117">You did not set the Service certificate property required for the security settings of a WCF send port.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1c9cd-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="1c9cd-118">User Action</span></span>  
 <span data-ttu-id="1c9cd-119">La procédure suivante permet de configurer la propriété Certificat de service.</span><span class="sxs-lookup"><span data-stu-id="1c9cd-119">Use the following procedure to configure the Service certificate property.</span></span>  
  
#### <a name="to-configure-the-service-certificate-property"></a><span data-ttu-id="1c9cd-120">Pour configurer la propriété Certificat de service</span><span class="sxs-lookup"><span data-stu-id="1c9cd-120">To configure the Service certificate property</span></span>  
  
1.  <span data-ttu-id="1c9cd-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="1c9cd-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="1c9cd-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="1c9cd-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="1c9cd-123">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="1c9cd-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="1c9cd-124">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="1c9cd-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="1c9cd-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1c9cd-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="1c9cd-126">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="1c9cd-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="1c9cd-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="1c9cd-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="1c9cd-128">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **sécurité** onglet.</span><span class="sxs-lookup"><span data-stu-id="1c9cd-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Security** tab.</span></span>  
  
9. <span data-ttu-id="1c9cd-129">Vérifiez que le **certificat de Service** propriété est configurée.</span><span class="sxs-lookup"><span data-stu-id="1c9cd-129">Ensure that the **Service certificate** property is configured.</span></span>  
  
 <span data-ttu-id="1c9cd-130">Pour plus d'informations sur les certificats, consultez la ressource suivante :</span><span class="sxs-lookup"><span data-stu-id="1c9cd-130">For additional information on certificates, see the following resource:</span></span>  
  
-   [<span data-ttu-id="1c9cd-131">Installation des certificats pour les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="1c9cd-131">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)