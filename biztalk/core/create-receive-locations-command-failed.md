---
title: "Créer échouée de la commande emplacements de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f73ff211-af7f-40be-ad7e-7bde7bf75a2d
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a6ad1c7992bb696eb05223e9830a7114d8a0fd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-receive-locations-command-failed"></a><span data-ttu-id="34de0-102">Échec de la commande de création d'emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="34de0-102">Create receive locations command failed</span></span>
## <a name="details"></a><span data-ttu-id="34de0-103">Détails</span><span class="sxs-lookup"><span data-stu-id="34de0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="34de0-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="34de0-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="34de0-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="34de0-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="34de0-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="34de0-106">Event ID</span></span>|<span data-ttu-id="34de0-107">0</span><span class="sxs-lookup"><span data-stu-id="34de0-107">0</span></span>|  
|<span data-ttu-id="34de0-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="34de0-108">Event Source</span></span>|<span data-ttu-id="34de0-109">0</span><span class="sxs-lookup"><span data-stu-id="34de0-109">0</span></span>|  
|<span data-ttu-id="34de0-110">Composant</span><span class="sxs-lookup"><span data-stu-id="34de0-110">Component</span></span>|<span data-ttu-id="34de0-111">0</span><span class="sxs-lookup"><span data-stu-id="34de0-111">0</span></span>|  
|<span data-ttu-id="34de0-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="34de0-112">Symbolic Name</span></span>|<span data-ttu-id="34de0-113">0</span><span class="sxs-lookup"><span data-stu-id="34de0-113">0</span></span>|  
|<span data-ttu-id="34de0-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="34de0-114">Message Text</span></span>|<span data-ttu-id="34de0-115">Créer échouée de la commande emplacements de réception : nom de fichier = {0} Arguments = \ {1\\} ExitCode = \ {2\}</span><span class="sxs-lookup"><span data-stu-id="34de0-115">Create receive locations command failed: FileName={0} Arguments={1} ExitCode={2}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="34de0-116">Explication</span><span class="sxs-lookup"><span data-stu-id="34de0-116">Explanation</span></span>  
 <span data-ttu-id="34de0-117">L'Assistant Publication n'a pas pu créer un emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="34de0-117">The publishing wizard failed to create a receive location.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="34de0-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="34de0-118">User Action</span></span>  
 <span data-ttu-id="34de0-119">Pour résoudre cette erreur, procédez comme suit : dans la console Administration de BizTalk, assurez-vous que l’emplacement de réception spécifié par l’attribut receiveLocationName dans le fichier Web.config que l’Assistant de publication WCF BizTalk a généré existe et qu’il est démarré.</span><span class="sxs-lookup"><span data-stu-id="34de0-119">To resolve this error, do the following: In the BizTalk Administration console, make sure that the receive location specified by the receiveLocationName attribute in the Web.config file that the BizTalk WCF Publishing Wizard generated exists and is started.</span></span>  
  
 <span data-ttu-id="34de0-120">Pour plus d'informations sur la création des emplacements de réception, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="34de0-120">For additional information on creating receive locations, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="34de0-121">Publication des Services WCF avec WCF isolé des adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="34de0-121">Publishing WCF Services with the Isolated WCF Receive Adapters</span></span>](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="34de0-122">Pour configurer les emplacement de réception WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="34de0-122">How to Configure a WCF-BasicHttp Receive Location</span></span>](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [<span data-ttu-id="34de0-123">Pour configurer les emplacement de réception WCF-WSHttp</span><span class="sxs-lookup"><span data-stu-id="34de0-123">How to Configure a WCF-WSHttp Receive Location</span></span>](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [<span data-ttu-id="34de0-124">Pour configurer les emplacement de réception WCF-CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="34de0-124">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="34de0-125">Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="34de0-125">Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter</span></span>](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)