---
title: "Échec de l’enregistrement du récepteur isolé pour l’adresse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 313b436a-d7c5-4b46-bfe3-bbad0d8efe42
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: edd55360a1638128ed687cf83f2e05bf52ad9dfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="failed-to-register-isolated-receiver-for-address"></a><span data-ttu-id="02561-102">Échec de l'enregistrement du récepteur isolé pour l'adresse</span><span class="sxs-lookup"><span data-stu-id="02561-102">Failed to register isolated receiver for address</span></span>
## <a name="details"></a><span data-ttu-id="02561-103">Détails</span><span class="sxs-lookup"><span data-stu-id="02561-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02561-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="02561-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="02561-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="02561-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="02561-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="02561-106">Event ID</span></span>|<span data-ttu-id="02561-107">0</span><span class="sxs-lookup"><span data-stu-id="02561-107">0</span></span>|  
|<span data-ttu-id="02561-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="02561-108">Event Source</span></span>|<span data-ttu-id="02561-109">0</span><span class="sxs-lookup"><span data-stu-id="02561-109">0</span></span>|  
|<span data-ttu-id="02561-110">Composant</span><span class="sxs-lookup"><span data-stu-id="02561-110">Component</span></span>|<span data-ttu-id="02561-111">0</span><span class="sxs-lookup"><span data-stu-id="02561-111">0</span></span>|  
|<span data-ttu-id="02561-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="02561-112">Symbolic Name</span></span>|<span data-ttu-id="02561-113">0</span><span class="sxs-lookup"><span data-stu-id="02561-113">0</span></span>|  
|<span data-ttu-id="02561-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="02561-114">Message Text</span></span>|<span data-ttu-id="02561-115">Échec de l'enregistrement du récepteur isolé pour l'adresse « {0} » ; l'emplacement de réception n'existe pas ou est désactivé.</span><span class="sxs-lookup"><span data-stu-id="02561-115">Failed to register isolated receiver for address "{0}"; receive location does not exist or is disabled.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="02561-116">Explication</span><span class="sxs-lookup"><span data-stu-id="02561-116">Explanation</span></span>  
 <span data-ttu-id="02561-117">Cette erreur indique qu'un emplacement de réception WCF isolé et publié n'a pas pu trouver l'emplacement de réception correspondant.</span><span class="sxs-lookup"><span data-stu-id="02561-117">This error indicates that a published isolated WCF receive location could not find the corresponding receive location.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="02561-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="02561-118">User Action</span></span>  
 <span data-ttu-id="02561-119">Pour résoudre cette erreur, procédez comme suit : dans la console Administration de BizTalk, assurez-vous que l’emplacement de réception spécifié par l’attribut receiveLocationName dans le fichier Web.config que l’Assistant Publication Services WCF BizTalk a généré existe et qu’il est a démarré.</span><span class="sxs-lookup"><span data-stu-id="02561-119">To resolve this error, do the following: In the BizTalk Administration console, make sure that the receive location specified by the receiveLocationName attribute in the Web.config file that the BizTalk WCF Services Publishing Wizard generated exists and is started.</span></span>  
  
 <span data-ttu-id="02561-120">Pour plus d'informations sur la création des emplacements de réception, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="02561-120">For additional information on creating receive locations, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="02561-121">Publication des Services WCF avec WCF isolé des adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="02561-121">Publishing WCF Services with the Isolated WCF Receive Adapters</span></span>](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="02561-122">Pour configurer les emplacement de réception WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="02561-122">How to Configure a WCF-BasicHttp Receive Location</span></span>](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [<span data-ttu-id="02561-123">Pour configurer les emplacement de réception WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="02561-123">How to Configure a WCF-WSHttp Receive Location</span></span>](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [<span data-ttu-id="02561-124">Pour configurer les emplacement de réception WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="02561-124">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="02561-125">Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="02561-125">Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter</span></span>](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)