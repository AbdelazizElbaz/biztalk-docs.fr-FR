---
title: "Requis empreinte de certificat client non spécifié | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19307bdb-29d7-4a79-9472-dda24dd8b263
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17eb34655ab0acd379e493540f8cd0922e5d8be9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="required-client-certificate-thumbprint-not-specified"></a><span data-ttu-id="ce2ea-102">L'empreinte de certificat client obligatoire n'a pas été indiquée</span><span class="sxs-lookup"><span data-stu-id="ce2ea-102">Required client certificate thumbprint not specified</span></span>
## <a name="details"></a><span data-ttu-id="ce2ea-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ce2ea-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce2ea-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ce2ea-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ce2ea-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ce2ea-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="ce2ea-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ce2ea-106">Event ID</span></span>|<span data-ttu-id="ce2ea-107">0</span><span class="sxs-lookup"><span data-stu-id="ce2ea-107">0</span></span>|  
|<span data-ttu-id="ce2ea-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ce2ea-108">Event Source</span></span>|<span data-ttu-id="ce2ea-109">0</span><span class="sxs-lookup"><span data-stu-id="ce2ea-109">0</span></span>|  
|<span data-ttu-id="ce2ea-110">Composant</span><span class="sxs-lookup"><span data-stu-id="ce2ea-110">Component</span></span>|<span data-ttu-id="ce2ea-111">0</span><span class="sxs-lookup"><span data-stu-id="ce2ea-111">0</span></span>|  
|<span data-ttu-id="ce2ea-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ce2ea-112">Symbolic Name</span></span>|<span data-ttu-id="ce2ea-113">0</span><span class="sxs-lookup"><span data-stu-id="ce2ea-113">0</span></span>|  
|<span data-ttu-id="ce2ea-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ce2ea-114">Message Text</span></span>|<span data-ttu-id="ce2ea-115">L'empreinte de certificat client obligatoire n'a pas été indiquée.</span><span class="sxs-lookup"><span data-stu-id="ce2ea-115">Required client certificate thumbprint not specified.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ce2ea-116">Explication</span><span class="sxs-lookup"><span data-stu-id="ce2ea-116">Explanation</span></span>  
 <span data-ttu-id="ce2ea-117">Vous n'avez pas défini la propriété Certificat client requise pour les paramètres de sécurité d'un port d'envoi WCF.</span><span class="sxs-lookup"><span data-stu-id="ce2ea-117">You did not set the Client certificate property required for the security settings of a WCF send port.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ce2ea-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ce2ea-118">User Action</span></span>  
 <span data-ttu-id="ce2ea-119">La procédure suivante permet de configurer les paramètres de sécurité d'un port d'envoi WCF.</span><span class="sxs-lookup"><span data-stu-id="ce2ea-119">Use the following procedure to configure security settings of a WCF send port.</span></span>  
  
#### <a name="to-configure-security-settings"></a><span data-ttu-id="ce2ea-120">Pour configurer les paramètres de sécurité</span><span class="sxs-lookup"><span data-stu-id="ce2ea-120">To configure security settings</span></span>  
  
1.  <span data-ttu-id="ce2ea-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="ce2ea-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ce2ea-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="ce2ea-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="ce2ea-123">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="ce2ea-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="ce2ea-124">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="ce2ea-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="ce2ea-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ce2ea-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="ce2ea-126">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="ce2ea-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="ce2ea-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="ce2ea-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="ce2ea-128">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **sécurité** onglet.</span><span class="sxs-lookup"><span data-stu-id="ce2ea-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Security** tab.</span></span>  
  
9. <span data-ttu-id="ce2ea-129">Vérifiez que le **certificat Client** propriété est configurée.</span><span class="sxs-lookup"><span data-stu-id="ce2ea-129">Ensure that the **Client certificate** property is configured.</span></span>  
  
 <span data-ttu-id="ce2ea-130">Pour plus d'informations sur les certificats, consultez la ressource suivante :</span><span class="sxs-lookup"><span data-stu-id="ce2ea-130">For additional information on certificates, see the following resource:</span></span>  
  
-   [<span data-ttu-id="ce2ea-131">Installation des certificats pour les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="ce2ea-131">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)