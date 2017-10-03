---
title: Empreinte de certificat client non valide | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f18fa0a2-b0d9-4190-aa96-12ab7007edd1
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84401d28261b13c6f49a063f34e29054a4aba108
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-client-certificate-thumbprint"></a><span data-ttu-id="6e788-102">Empreinte de certificat client non valide</span><span class="sxs-lookup"><span data-stu-id="6e788-102">Invalid client certificate thumbprint</span></span>
## <a name="details"></a><span data-ttu-id="6e788-103">Détails</span><span class="sxs-lookup"><span data-stu-id="6e788-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e788-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="6e788-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6e788-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="6e788-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="6e788-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6e788-106">Event ID</span></span>|<span data-ttu-id="6e788-107">0</span><span class="sxs-lookup"><span data-stu-id="6e788-107">0</span></span>|  
|<span data-ttu-id="6e788-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="6e788-108">Event Source</span></span>|<span data-ttu-id="6e788-109">0</span><span class="sxs-lookup"><span data-stu-id="6e788-109">0</span></span>|  
|<span data-ttu-id="6e788-110">Composant</span><span class="sxs-lookup"><span data-stu-id="6e788-110">Component</span></span>|<span data-ttu-id="6e788-111">0</span><span class="sxs-lookup"><span data-stu-id="6e788-111">0</span></span>|  
|<span data-ttu-id="6e788-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="6e788-112">Symbolic Name</span></span>|<span data-ttu-id="6e788-113">0</span><span class="sxs-lookup"><span data-stu-id="6e788-113">0</span></span>|  
|<span data-ttu-id="6e788-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="6e788-114">Message Text</span></span>|<span data-ttu-id="6e788-115">Empreinte de certificat client non valide ; elle doit comporter 40 chiffres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="6e788-115">Invalid client certificate thumbprint; expected 40 hexadecimal digits.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6e788-116">Explication</span><span class="sxs-lookup"><span data-stu-id="6e788-116">Explanation</span></span>  
 <span data-ttu-id="6e788-117">Une empreinte de certificat client non valide a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6e788-117">An invalid client certificate thumbprint was specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6e788-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6e788-118">User Action</span></span>  
 <span data-ttu-id="6e788-119">Dans le code de configuration du port d'envoi WCF, la propriété Certificat client de l'interface utilisateur attend 40 chiffres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="6e788-119">In the code configuring the WCF send port, the client certificate property of the user interface expects a hexadecimal 40-digit value.</span></span> <span data-ttu-id="6e788-120">Exemple : 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39</span><span class="sxs-lookup"><span data-stu-id="6e788-120">Example: 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39</span></span>  
  
 <span data-ttu-id="6e788-121">Pour plus d’informations sur les certificats, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="6e788-121">For additional information on certificates, see the following:</span></span>  
  
-   [<span data-ttu-id="6e788-122">Installation des certificats pour les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="6e788-122">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)