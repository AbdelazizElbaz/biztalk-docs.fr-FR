---
title: TIBCO Enterprise Message Service et les Limitations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption
- messages, compression
- EMS limitations
- message compression
- API, adding to GAC
- global assembly cache, adding API
- GAC, adding TIBCO EMS API
- system requirements
- TIBCO.EMS.dll
- EMS requirements
- messages, encryption
ms.assetid: 6e4c022c-e6a8-4ac5-b998-b0465002a31e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81e49f4a74cce4414fd9d0b069a382d9facb03d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-enterprise-message-service-requirements-and-limitations"></a><span data-ttu-id="b2233-102">Impératifs et restrictions de TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="b2233-102">TIBCO Enterprise Message Service Requirements and Limitations</span></span>
## <a name="system-requirements"></a><span data-ttu-id="b2233-103">Configuration système requise</span><span class="sxs-lookup"><span data-stu-id="b2233-103">System Requirements</span></span>  
 <span data-ttu-id="b2233-104">L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service prend en charge TIBCO Enterprise Message Service (EMS) version 4.2.</span><span class="sxs-lookup"><span data-stu-id="b2233-104">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service supports TIBCO Enterprise Message Service (EMS) version 4.2.</span></span> <span data-ttu-id="b2233-105">Un client SDK est inclus avec TIBCO EMS version 4.2 (via l'API TIBCO EMS C# ).</span><span class="sxs-lookup"><span data-stu-id="b2233-105">Included with TIBCO EMS version 4.2 is a client SDK (using the TIBCO EMS C# API).</span></span> <span data-ttu-id="b2233-106">L'adaptateur BizTalk pour TIBCO EMS utilise cette API pour communiquer avec TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="b2233-106">BizTalk Adapter for TIBCO EMS uses this API to communicate with TIBCO EMS.</span></span>  
  
## <a name="adding-the-api-to-the-gac"></a><span data-ttu-id="b2233-107">Ajout de l'API au GAC</span><span class="sxs-lookup"><span data-stu-id="b2233-107">Adding the API to the GAC</span></span>  
 <span data-ttu-id="b2233-108">L'adaptateur BizTalk pour TIBCO EMS requiert l'ajout de l'API TIBCO EMS C#, TIBCO.EMS.dll, au GAC (Global Assembly Cache).</span><span class="sxs-lookup"><span data-stu-id="b2233-108">BizTalk Adapter for TIBCO EMS requires the TIBCO EMS C# API, TIBCO.EMS.dll, to be added to the global assembly cache (GAC).</span></span> <span data-ttu-id="b2233-109">Si cet assembly n'est pas installé, l'adaptateur déclenche une exception et consigne un message approprié.</span><span class="sxs-lookup"><span data-stu-id="b2233-109">The adapter triggers an exception and logs an appropriate message if this assembly is not installed.</span></span>  
  
#### <a name="to-add-the-tibco-ems-c-api-to-the-gac"></a><span data-ttu-id="b2233-110">Pour ajouter l'API TIBCO EMS C# au GAC</span><span class="sxs-lookup"><span data-stu-id="b2233-110">To add the TIBCO EMS C# API to the GAC</span></span>  
  
1.  <span data-ttu-id="b2233-111">Copiez l'API TIBCO EMS C# sur votre ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b2233-111">Copy the TIBCO EMS C#API to your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer.</span></span>  
  
2.  <span data-ttu-id="b2233-112">Accédez au répertoire contenant le fichier de l'API C#, TIBCO.EMS.DLL.</span><span class="sxs-lookup"><span data-stu-id="b2233-112">Change directories to the location of the C# API file, TIBCO.EMS.DLL.</span></span>  
  
     <span data-ttu-id="b2233-113">Dans le cas d'une installation par défaut, le chemin d'accès à cette DLL est c:\tibco\ems\clients\cs\TIBCO.EMS.DLL.</span><span class="sxs-lookup"><span data-stu-id="b2233-113">In the default installation, the path to this DLL is c:\tibco\ems\clients\cs\TIBCO.EMS.DLL.</span></span>  
  
3.  <span data-ttu-id="b2233-114">Ouvrez une invite de commandes, puis tapez :</span><span class="sxs-lookup"><span data-stu-id="b2233-114">In a command prompt, type:</span></span>  
  
     `C:\bin> gacutil /i TIBCO.EMS.dll`  
  
     <span data-ttu-id="b2233-115">Le fichier TIBCO.EMS.dll affiche maintenant le GAC.</span><span class="sxs-lookup"><span data-stu-id="b2233-115">The TIBCO.EMS.dll now shows the GAC.</span></span>  
  
     <span data-ttu-id="b2233-116">Pour afficher la liste du GAC, dans le panneau de configuration, ouvrez **outils d’administration**, ouvrez **Microsoft .NET Framework x.x configuration**, puis cliquez sur **Assembly Cache**.</span><span class="sxs-lookup"><span data-stu-id="b2233-116">To view the GAC list, in Control Panel, open **Administrative Tools**, open **Microsoft .NET Framework X.XConfiguration**, and then click **Assembly Cache**.</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="b2233-117">Limitations</span><span class="sxs-lookup"><span data-stu-id="b2233-117">Limitations</span></span>  
 <span data-ttu-id="b2233-118">L'adaptateur BizTalk pour TIBCO Enterprise Message Service utilise le fichier TIBCO.EMS.dll pour communiquer avec TIBCO Enterprise Message Service.</span><span class="sxs-lookup"><span data-stu-id="b2233-118">BizTalk Adapter for TIBCO Enterprise Message Service uses TIBCO.EMS.dll to communicate with TIBCO Enterprise Message Service.</span></span> <span data-ttu-id="b2233-119">Lorsque vous utilisez l'API TIBCO EMS C#, vous devez prendre en compte les limitations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b2233-119">You should consider the following limitations when you use the TIBCO EMS C# API:</span></span>  
  
-   <span data-ttu-id="b2233-120">La compression des messages, qui permet au client TIBCO EMS d'envoyer des messages à EMS sous une forme compressée, n'est pas disponible avec l'API C#.</span><span class="sxs-lookup"><span data-stu-id="b2233-120">Message compression, which enables the TIBCO EMS client to send messages in a compressed form to EMS, is not available with the C# API.</span></span>  
  
-   <span data-ttu-id="b2233-121">Le chiffrement des messages entre l'adaptateur et le serveur n'est pas disponible avec l'API C#.</span><span class="sxs-lookup"><span data-stu-id="b2233-121">Encryption of messages between the adapter and the server is not available with the C# API.</span></span> <span data-ttu-id="b2233-122">Cette API n'autorise pas le chiffrement SSL à l'aide des bibliothèques OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="b2233-122">The C# API does not allow for SSL encryption using the OpenSSL libraries.</span></span>  
  
-   <span data-ttu-id="b2233-123">L'API C# ne prend pas en charge l'API d'administration pour EMS.</span><span class="sxs-lookup"><span data-stu-id="b2233-123">The C# API does not support the Administration API for EMS.</span></span>  
  
-   <span data-ttu-id="b2233-124">L'adaptateur BizTalk pour TIBCO EMS ne peut ni envoyer ni recevoir les messages dont la taille dépasse 50 Mo.</span><span class="sxs-lookup"><span data-stu-id="b2233-124">Messages greater than 50MB in size cannot be sent or received using the BizTalk TIBCO EMS adapter.</span></span> <span data-ttu-id="b2233-125">Au-delà de cette taille, l'environnement rencontre des exceptions System.OutOfMemoryException.</span><span class="sxs-lookup"><span data-stu-id="b2233-125">Beyond this size, the environment experiences System.OutOfMemoryException exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2233-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2233-126">See Also</span></span>  
 [<span data-ttu-id="b2233-127">Planification et Architecture</span><span class="sxs-lookup"><span data-stu-id="b2233-127">Planning and Architecture</span></span>](../core/planning-and-architecture16.md)