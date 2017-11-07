---
title: TIBCO Enterprise Message Service et les Limitations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e4c022c-e6a8-4ac5-b998-b0465002a31e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcd386245ba06c2e3b5a5b92df7b7a7f01a1a749
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="tibco-enterprise-message-service-requirements-and-limitations"></a><span data-ttu-id="bdd0e-102">Impératifs et restrictions de TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="bdd0e-102">TIBCO Enterprise Message Service Requirements and Limitations</span></span>

## <a name="system-requirements"></a><span data-ttu-id="bdd0e-103">Configuration système requise</span><span class="sxs-lookup"><span data-stu-id="bdd0e-103">System Requirements</span></span>  
<span data-ttu-id="bdd0e-104">Inclus avec TIBCO Enterprise Message Service inclut un client SDK (à l’aide de l’API TIBCO EMS c#).</span><span class="sxs-lookup"><span data-stu-id="bdd0e-104">Included with TIBCO Enterprise Message Service includes a client SDK (using the TIBCO EMS C# API).</span></span> <span data-ttu-id="bdd0e-105">L'adaptateur BizTalk pour TIBCO EMS utilise cette API pour communiquer avec TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="bdd0e-105">BizTalk Adapter for TIBCO EMS uses this API to communicate with TIBCO EMS.</span></span>  
  
## <a name="add-the-api-to-the-gac"></a><span data-ttu-id="bdd0e-106">Ajout de l’API dans le GAC</span><span class="sxs-lookup"><span data-stu-id="bdd0e-106">Add the API to the GAC</span></span>  
 <span data-ttu-id="bdd0e-107">L'adaptateur BizTalk pour TIBCO EMS requiert l'ajout de l'API TIBCO EMS C#, TIBCO.EMS.dll, au GAC (Global Assembly Cache).</span><span class="sxs-lookup"><span data-stu-id="bdd0e-107">BizTalk Adapter for TIBCO EMS requires the TIBCO EMS C# API, TIBCO.EMS.dll, to be added to the global assembly cache (GAC).</span></span> <span data-ttu-id="bdd0e-108">Si cet assembly n'est pas installé, l'adaptateur déclenche une exception et consigne un message approprié.</span><span class="sxs-lookup"><span data-stu-id="bdd0e-108">The adapter triggers an exception and logs an appropriate message if this assembly is not installed.</span></span>  
  
1.  <span data-ttu-id="bdd0e-109">Copiez l'API TIBCO EMS C# sur votre ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bdd0e-109">Copy the TIBCO EMS C#API to your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer.</span></span>  
  
2.  <span data-ttu-id="bdd0e-110">Accédez au répertoire contenant le fichier de l'API C#, TIBCO.EMS.DLL.</span><span class="sxs-lookup"><span data-stu-id="bdd0e-110">Change directories to the location of the C# API file, TIBCO.EMS.DLL.</span></span>  
  
     <span data-ttu-id="bdd0e-111">Dans le cas d'une installation par défaut, le chemin d'accès à cette DLL est c:\tibco\ems\clients\cs\TIBCO.EMS.DLL.</span><span class="sxs-lookup"><span data-stu-id="bdd0e-111">In the default installation, the path to this DLL is c:\tibco\ems\clients\cs\TIBCO.EMS.DLL.</span></span>  
  
3.  <span data-ttu-id="bdd0e-112">Ouvrez une invite de commandes, puis tapez :</span><span class="sxs-lookup"><span data-stu-id="bdd0e-112">In a command prompt, type:</span></span>  
  
     `C:\bin> gacutil /i TIBCO.EMS.dll`  
  
     <span data-ttu-id="bdd0e-113">Le fichier TIBCO.EMS.dll affiche maintenant le GAC.</span><span class="sxs-lookup"><span data-stu-id="bdd0e-113">The TIBCO.EMS.dll now shows the GAC.</span></span>  
  
     <span data-ttu-id="bdd0e-114">Pour afficher la liste du GAC, dans le panneau de configuration, ouvrez **outils d’administration**, ouvrez **Microsoft .NET Framework x.x configuration**, puis cliquez sur **Assembly Cache**.</span><span class="sxs-lookup"><span data-stu-id="bdd0e-114">To view the GAC list, in Control Panel, open **Administrative Tools**, open **Microsoft .NET Framework X.XConfiguration**, and then click **Assembly Cache**.</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="bdd0e-115">Limitations</span><span class="sxs-lookup"><span data-stu-id="bdd0e-115">Limitations</span></span>  
 <span data-ttu-id="bdd0e-116">L'adaptateur BizTalk pour TIBCO Enterprise Message Service utilise le fichier TIBCO.EMS.dll pour communiquer avec TIBCO Enterprise Message Service.</span><span class="sxs-lookup"><span data-stu-id="bdd0e-116">BizTalk Adapter for TIBCO Enterprise Message Service uses TIBCO.EMS.dll to communicate with TIBCO Enterprise Message Service.</span></span> <span data-ttu-id="bdd0e-117">Lorsque vous utilisez l'API TIBCO EMS C#, vous devez prendre en compte les limitations suivantes :</span><span class="sxs-lookup"><span data-stu-id="bdd0e-117">You should consider the following limitations when you use the TIBCO EMS C# API:</span></span>  
  
-   <span data-ttu-id="bdd0e-118">La compression des messages, qui permet au client TIBCO EMS d'envoyer des messages à EMS sous une forme compressée, n'est pas disponible avec l'API C#.</span><span class="sxs-lookup"><span data-stu-id="bdd0e-118">Message compression, which enables the TIBCO EMS client to send messages in a compressed form to EMS, is not available with the C# API.</span></span>  
  
-   <span data-ttu-id="bdd0e-119">Le chiffrement des messages entre l'adaptateur et le serveur n'est pas disponible avec l'API C#.</span><span class="sxs-lookup"><span data-stu-id="bdd0e-119">Encryption of messages between the adapter and the server is not available with the C# API.</span></span> <span data-ttu-id="bdd0e-120">Cette API n'autorise pas le chiffrement SSL à l'aide des bibliothèques OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="bdd0e-120">The C# API does not allow for SSL encryption using the OpenSSL libraries.</span></span>  
  
-   <span data-ttu-id="bdd0e-121">L'API C# ne prend pas en charge l'API d'administration pour EMS.</span><span class="sxs-lookup"><span data-stu-id="bdd0e-121">The C# API does not support the Administration API for EMS.</span></span>  
  
-   <span data-ttu-id="bdd0e-122">L'adaptateur BizTalk pour TIBCO EMS ne peut ni envoyer ni recevoir les messages dont la taille dépasse 50 Mo.</span><span class="sxs-lookup"><span data-stu-id="bdd0e-122">Messages greater than 50MB in size cannot be sent or received using the BizTalk TIBCO EMS adapter.</span></span> <span data-ttu-id="bdd0e-123">Au-delà de cette taille, l'environnement rencontre des exceptions System.OutOfMemoryException.</span><span class="sxs-lookup"><span data-stu-id="bdd0e-123">Beyond this size, the environment experiences System.OutOfMemoryException exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd0e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdd0e-124">See Also</span></span>  
 [<span data-ttu-id="bdd0e-125">Planification et architecture</span><span class="sxs-lookup"><span data-stu-id="bdd0e-125">Planning and Architecture</span></span>](../core/planning-and-architecture16.md)