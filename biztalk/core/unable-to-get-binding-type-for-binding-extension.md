---
title: "Impossible d’obtenir le type de liaison pour l’extension de liaison | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a7cfc81-7439-48f9-8cac-42b2419ecd9d
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 453a579daae80a202df1ed4d3c72ae9c13f47d9b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-get-binding-type-for-binding-extension"></a><span data-ttu-id="4ba08-102">Impossible d'obtenir le type de liaison pour l'extension de liaison</span><span class="sxs-lookup"><span data-stu-id="4ba08-102">Unable to get binding type for binding extension</span></span>
## <a name="details"></a><span data-ttu-id="4ba08-103">Détails</span><span class="sxs-lookup"><span data-stu-id="4ba08-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4ba08-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="4ba08-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="4ba08-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="4ba08-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="4ba08-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="4ba08-106">Event ID</span></span>|<span data-ttu-id="4ba08-107">0</span><span class="sxs-lookup"><span data-stu-id="4ba08-107">0</span></span>|  
|<span data-ttu-id="4ba08-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="4ba08-108">Event Source</span></span>|<span data-ttu-id="4ba08-109">0</span><span class="sxs-lookup"><span data-stu-id="4ba08-109">0</span></span>|  
|<span data-ttu-id="4ba08-110">Composant</span><span class="sxs-lookup"><span data-stu-id="4ba08-110">Component</span></span>|<span data-ttu-id="4ba08-111">0</span><span class="sxs-lookup"><span data-stu-id="4ba08-111">0</span></span>|  
|<span data-ttu-id="4ba08-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="4ba08-112">Symbolic Name</span></span>|<span data-ttu-id="4ba08-113">0</span><span class="sxs-lookup"><span data-stu-id="4ba08-113">0</span></span>|  
|<span data-ttu-id="4ba08-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="4ba08-114">Message Text</span></span>|<span data-ttu-id="4ba08-115">Impossible d'obtenir le type de liaison pour l'extension de liaison « {0} ».</span><span class="sxs-lookup"><span data-stu-id="4ba08-115">Unable to get binding type for binding extension "{0}".</span></span> <span data-ttu-id="4ba08-116">Si machine.config a été mis à jour alors que votre application était ouverte, redémarrez votre application pour prendre les modifications en compte.</span><span class="sxs-lookup"><span data-stu-id="4ba08-116">If machine.config was updated while your application was open, restart your application to pick up changes.</span></span> <span data-ttu-id="4ba08-117">Vérifiez que l'extension de liaison est enregistrée dans machine.config</span><span class="sxs-lookup"><span data-stu-id="4ba08-117">Verify the binding extension is registered in machine.config</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4ba08-118">Explication</span><span class="sxs-lookup"><span data-stu-id="4ba08-118">Explanation</span></span>  
 <span data-ttu-id="4ba08-119">Une extension de liaison personnalisée pour un transport WCF-Custom ou WCF-CustomIsolated n'a pas été correctement configurée.</span><span class="sxs-lookup"><span data-stu-id="4ba08-119">A custom binding extension for a WCF-Custom or a WCF-CustomIsolated transport was not configured properly.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4ba08-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4ba08-120">User Action</span></span>  
 <span data-ttu-id="4ba08-121">Pour résoudre cette erreur, effectuez l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4ba08-121">To resolve this error do one or more of the following:</span></span>  
  
-   <span data-ttu-id="4ba08-122">Vérifiez le **fichier machine.config** dans **%WinDir%\Microsoft.NET\Framework\v4.0.30319\Config** a le \< **bindingExtensions**> élément configuré correctement.</span><span class="sxs-lookup"><span data-stu-id="4ba08-122">Ensure the **machine.config file** in **%WinDir%\Microsoft.NET\Framework\v4.0.30319\Config** has the \<**bindingExtensions**> element configured properly.</span></span>  
  
-   <span data-ttu-id="4ba08-123">Dans l’Explorateur Windows, accédez à **%WinDir%\Assembly**et assurez-vous que l’implémentation de l’extension de liaison personnalisée sont correctement installés.</span><span class="sxs-lookup"><span data-stu-id="4ba08-123">In Windows Explorer, go to **%WinDir%\Assembly**, and make sure the assemblies implementing the custom binding extension are installed properly.</span></span>  
  
-   <span data-ttu-id="4ba08-124">Pour l'adaptateur WCF-Custom, dans la console Administration de BizTalk, redémarrez l'instance d'hôte exécutant le transport WCF.</span><span class="sxs-lookup"><span data-stu-id="4ba08-124">For the WCF-Custom adapter, in the BizTalk Administration console, restart the host instance running the WCF transport.</span></span>  
  
-   <span data-ttu-id="4ba08-125">Pour l'adaptateur WCF-CustomIsolated, dans la console de gestion IIS, redémarrez le pool d'applications hébergeant le transport WCF.</span><span class="sxs-lookup"><span data-stu-id="4ba08-125">For the WCF-CustomIsolated adapter, in the IIS Management console, restart the application pool hosting the WCF transport.</span></span>  
  
-   <span data-ttu-id="4ba08-126">Ouvrez puis fermez la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4ba08-126">Open and close the BizTalk Administration console if it was opened</span></span>  
  
 <span data-ttu-id="4ba08-127">Pour plus d'informations, consultez la ressource suivante :</span><span class="sxs-lookup"><span data-stu-id="4ba08-127">For further information, see the following resource:</span></span>  
  
-   [<span data-ttu-id="4ba08-128">Comment activer les Points d’extensibilité WCF avec les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="4ba08-128">How to Enable the WCF Extensibility Points with the WCF Adapters</span></span>](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)