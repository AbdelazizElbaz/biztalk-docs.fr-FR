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
ms.openlocfilehash: 79b649f69b7503f345f212aa5f014ce7b256148d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="unable-to-get-binding-type-for-binding-extension"></a><span data-ttu-id="b75ca-102">Impossible d'obtenir le type de liaison pour l'extension de liaison</span><span class="sxs-lookup"><span data-stu-id="b75ca-102">Unable to get binding type for binding extension</span></span>
## <a name="details"></a><span data-ttu-id="b75ca-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b75ca-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b75ca-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b75ca-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b75ca-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b75ca-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="b75ca-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b75ca-106">Event ID</span></span>|<span data-ttu-id="b75ca-107">0</span><span class="sxs-lookup"><span data-stu-id="b75ca-107">0</span></span>|  
|<span data-ttu-id="b75ca-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b75ca-108">Event Source</span></span>|<span data-ttu-id="b75ca-109">0</span><span class="sxs-lookup"><span data-stu-id="b75ca-109">0</span></span>|  
|<span data-ttu-id="b75ca-110">Composant</span><span class="sxs-lookup"><span data-stu-id="b75ca-110">Component</span></span>|<span data-ttu-id="b75ca-111">0</span><span class="sxs-lookup"><span data-stu-id="b75ca-111">0</span></span>|  
|<span data-ttu-id="b75ca-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b75ca-112">Symbolic Name</span></span>|<span data-ttu-id="b75ca-113">0</span><span class="sxs-lookup"><span data-stu-id="b75ca-113">0</span></span>|  
|<span data-ttu-id="b75ca-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b75ca-114">Message Text</span></span>|<span data-ttu-id="b75ca-115">Impossible d'obtenir le type de liaison pour l'extension de liaison « {0} ».</span><span class="sxs-lookup"><span data-stu-id="b75ca-115">Unable to get binding type for binding extension "{0}".</span></span> <span data-ttu-id="b75ca-116">Si machine.config a été mis à jour alors que votre application était ouverte, redémarrez votre application pour prendre les modifications en compte.</span><span class="sxs-lookup"><span data-stu-id="b75ca-116">If machine.config was updated while your application was open, restart your application to pick up changes.</span></span> <span data-ttu-id="b75ca-117">Vérifiez que l'extension de liaison est enregistrée dans machine.config</span><span class="sxs-lookup"><span data-stu-id="b75ca-117">Verify the binding extension is registered in machine.config</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b75ca-118">Explication</span><span class="sxs-lookup"><span data-stu-id="b75ca-118">Explanation</span></span>  
 <span data-ttu-id="b75ca-119">Une extension de liaison personnalisée pour un transport WCF-Custom ou WCF-CustomIsolated n'a pas été correctement configurée.</span><span class="sxs-lookup"><span data-stu-id="b75ca-119">A custom binding extension for a WCF-Custom or a WCF-CustomIsolated transport was not configured properly.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b75ca-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b75ca-120">User Action</span></span>  
 <span data-ttu-id="b75ca-121">Pour résoudre cette erreur, effectuez l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b75ca-121">To resolve this error do one or more of the following:</span></span>  
  
-   <span data-ttu-id="b75ca-122">Vérifiez le **fichier machine.config** dans **%WinDir%\Microsoft.NET\Framework\v4.0.30319\Config** a le \< **bindingExtensions** \> élément configuré correctement.</span><span class="sxs-lookup"><span data-stu-id="b75ca-122">Ensure the **machine.config file** in **%WinDir%\Microsoft.NET\Framework\v4.0.30319\Config** has the \<**bindingExtensions**\> element configured properly.</span></span>  
  
-   <span data-ttu-id="b75ca-123">Dans l’Explorateur Windows, accédez à **%WinDir%\Assembly**et assurez-vous que l’implémentation de l’extension de liaison personnalisée sont correctement installés.</span><span class="sxs-lookup"><span data-stu-id="b75ca-123">In Windows Explorer, go to **%WinDir%\Assembly**, and make sure the assemblies implementing the custom binding extension are installed properly.</span></span>  
  
-   <span data-ttu-id="b75ca-124">Pour l'adaptateur WCF-Custom, dans la console Administration de BizTalk, redémarrez l'instance d'hôte exécutant le transport WCF.</span><span class="sxs-lookup"><span data-stu-id="b75ca-124">For the WCF-Custom adapter, in the BizTalk Administration console, restart the host instance running the WCF transport.</span></span>  
  
-   <span data-ttu-id="b75ca-125">Pour l'adaptateur WCF-CustomIsolated, dans la console de gestion IIS, redémarrez le pool d'applications hébergeant le transport WCF.</span><span class="sxs-lookup"><span data-stu-id="b75ca-125">For the WCF-CustomIsolated adapter, in the IIS Management console, restart the application pool hosting the WCF transport.</span></span>  
  
-   <span data-ttu-id="b75ca-126">Ouvrez puis fermez la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b75ca-126">Open and close the BizTalk Administration console if it was opened</span></span>  
  
 <span data-ttu-id="b75ca-127">Pour plus d'informations, consultez la ressource suivante :</span><span class="sxs-lookup"><span data-stu-id="b75ca-127">For further information, see the following resource:</span></span>  
  
-   [<span data-ttu-id="b75ca-128">Comment activer les Points d’extensibilité WCF avec les adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="b75ca-128">How to Enable the WCF Extensibility Points with the WCF Adapters</span></span>](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)