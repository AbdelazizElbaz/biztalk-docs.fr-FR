---
title: "Empreinte numérique du certificat de service non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22e7d74e-40ec-4187-9246-bc8da2a9ce86
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a465d631e72bc27c6b24274deb31e396037aa182
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-service-certificate-thumbprint"></a><span data-ttu-id="756d0-102">Empreinte de certificat de service non valide</span><span class="sxs-lookup"><span data-stu-id="756d0-102">Invalid service certificate thumbprint</span></span>
## <a name="details"></a><span data-ttu-id="756d0-103">Détails</span><span class="sxs-lookup"><span data-stu-id="756d0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="756d0-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="756d0-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="756d0-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="756d0-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="756d0-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="756d0-106">Event ID</span></span>|<span data-ttu-id="756d0-107">0</span><span class="sxs-lookup"><span data-stu-id="756d0-107">0</span></span>|  
|<span data-ttu-id="756d0-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="756d0-108">Event Source</span></span>|<span data-ttu-id="756d0-109">0</span><span class="sxs-lookup"><span data-stu-id="756d0-109">0</span></span>|  
|<span data-ttu-id="756d0-110">Composant</span><span class="sxs-lookup"><span data-stu-id="756d0-110">Component</span></span>|<span data-ttu-id="756d0-111">0</span><span class="sxs-lookup"><span data-stu-id="756d0-111">0</span></span>|  
|<span data-ttu-id="756d0-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="756d0-112">Symbolic Name</span></span>|<span data-ttu-id="756d0-113">0</span><span class="sxs-lookup"><span data-stu-id="756d0-113">0</span></span>|  
|<span data-ttu-id="756d0-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="756d0-114">Message Text</span></span>|<span data-ttu-id="756d0-115">Empreinte de certificat de service non valide ; elle doit comporter 40 chiffres hexadécimaux</span><span class="sxs-lookup"><span data-stu-id="756d0-115">Invalid service certificate thumbprint; expected 40 hexadecimal digits</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="756d0-116">Explication</span><span class="sxs-lookup"><span data-stu-id="756d0-116">Explanation</span></span>  
 <span data-ttu-id="756d0-117">Une empreinte de certificat de service non valide a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="756d0-117">An invalid service certificate thumbprint was specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="756d0-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="756d0-118">User Action</span></span>  
 <span data-ttu-id="756d0-119">Dans le code de configuration du port WCF, la propriété Certificat de service de l'interface utilisateur attend 40 chiffres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="756d0-119">In the code configuring the WCF port, the service certificate property of the user interface expects a hexadecimal 40-digit value.</span></span> <span data-ttu-id="756d0-120">Exemple : 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39</span><span class="sxs-lookup"><span data-stu-id="756d0-120">Example: 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39</span></span>  
  
 <span data-ttu-id="756d0-121">Pour plus d'informations sur les certificats, consultez la ressource suivante :</span><span class="sxs-lookup"><span data-stu-id="756d0-121">For additional information on certificates, see the following resource:</span></span>  
  
-   [<span data-ttu-id="756d0-122">Installation des certificats pour les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="756d0-122">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)