---
title: "Emplacement de réception pour les métadonnées non trouvé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c397fb5-f400-4cff-85b9-5bf0d2069557
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3eb45272f7d3ef4491b59d5b019eb4499bcf5dff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-location-for-metadata-not-found"></a><span data-ttu-id="0f936-102">Emplacement de réception pour les métadonnées non trouvé</span><span class="sxs-lookup"><span data-stu-id="0f936-102">Receive location for metadata not found</span></span>
## <a name="details"></a><span data-ttu-id="0f936-103">Détails</span><span class="sxs-lookup"><span data-stu-id="0f936-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0f936-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="0f936-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0f936-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="0f936-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="0f936-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0f936-106">Event ID</span></span>|<span data-ttu-id="0f936-107">0</span><span class="sxs-lookup"><span data-stu-id="0f936-107">0</span></span>|  
|<span data-ttu-id="0f936-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="0f936-108">Event Source</span></span>|<span data-ttu-id="0f936-109">0</span><span class="sxs-lookup"><span data-stu-id="0f936-109">0</span></span>|  
|<span data-ttu-id="0f936-110">Composant</span><span class="sxs-lookup"><span data-stu-id="0f936-110">Component</span></span>|<span data-ttu-id="0f936-111">0</span><span class="sxs-lookup"><span data-stu-id="0f936-111">0</span></span>|  
|<span data-ttu-id="0f936-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="0f936-112">Symbolic Name</span></span>|<span data-ttu-id="0f936-113">0</span><span class="sxs-lookup"><span data-stu-id="0f936-113">0</span></span>|  
|<span data-ttu-id="0f936-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="0f936-114">Message Text</span></span>|<span data-ttu-id="0f936-115">Emplacement de réception « {0} » pour les métadonnées non trouvé.</span><span class="sxs-lookup"><span data-stu-id="0f936-115">Receive location "{0}" for metadata not found.</span></span> <span data-ttu-id="0f936-116">(Vérifiez le mappage de l'emplacement de réception dans Web.config et l'existence de l'emplacement de réception.)</span><span class="sxs-lookup"><span data-stu-id="0f936-116">(Check receive location mapping in Web.config and verify the receive location exists.)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0f936-117">Explication</span><span class="sxs-lookup"><span data-stu-id="0f936-117">Explanation</span></span>  
 <span data-ttu-id="0f936-118">Cette erreur indique qu'un emplacement de réception WCF isolé et publié n'a pas pu trouver l'emplacement de réception correspondant pour les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="0f936-118">This error indicates that a published isolated WCF receive location could not find the corresponding receive location for metadata.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0f936-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="0f936-119">User Action</span></span>  
 <span data-ttu-id="0f936-120">Pour résoudre cette erreur, procédez comme suit : dans la console Administration de BizTalk, assurez-vous que l’emplacement de réception spécifié par l’attribut receiveLocationName dans le fichier Web.config que l’Assistant de publication WCF BizTalk a généré existe et qu’il est démarré.</span><span class="sxs-lookup"><span data-stu-id="0f936-120">To resolve this error, do the following: In the BizTalk Administration console, make sure that the receive location specified by the receiveLocationName attribute in the Web.config file that the BizTalk WCF Publishing Wizard generated exists and is started.</span></span>  
  
 <span data-ttu-id="0f936-121">Pour plus d'informations sur les emplacements de réception, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="0f936-121">For additional information on receive locations, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="0f936-122">Publication des Services WCF</span><span class="sxs-lookup"><span data-stu-id="0f936-122">Publishing WCF Services</span></span>](../core/publishing-wcf-services.md)  
  
-   [<span data-ttu-id="0f936-123">Pour configurer les emplacement de réception WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="0f936-123">How to Configure a WCF-BasicHttp Receive Location</span></span>](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [<span data-ttu-id="0f936-124">Pour configurer les emplacement de réception WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="0f936-124">How to Configure a WCF-WSHttp Receive Location</span></span>](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [<span data-ttu-id="0f936-125">Pour configurer les emplacement de réception WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="0f936-125">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="0f936-126">Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="0f936-126">Walkthrough: Publishing WCF Services with the WCF-NetMsmq Adapter</span></span>](../core/walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter.md)