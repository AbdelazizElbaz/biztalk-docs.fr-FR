---
title: "Une exception de sécurité s’est produite durant la réflexion d’un assembly BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 301b85c7-8e67-482e-8666-67a91ca5c73d
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cca28c534b910479be3ae6ad26bd1e0a27a1637d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-security-exception-occurred-while-reflecting-a-biztalk-assembly"></a><span data-ttu-id="b4442-102">Exception de sécurité lors de la mise en correspondance de l'assembly BizTalk</span><span class="sxs-lookup"><span data-stu-id="b4442-102">A security exception occurred while reflecting a BizTalk assembly</span></span>
## <a name="details"></a><span data-ttu-id="b4442-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b4442-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b4442-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b4442-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b4442-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b4442-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="b4442-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b4442-106">Event ID</span></span>|<span data-ttu-id="b4442-107">0</span><span class="sxs-lookup"><span data-stu-id="b4442-107">0</span></span>|  
|<span data-ttu-id="b4442-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b4442-108">Event Source</span></span>|<span data-ttu-id="b4442-109">0</span><span class="sxs-lookup"><span data-stu-id="b4442-109">0</span></span>|  
|<span data-ttu-id="b4442-110">Composant</span><span class="sxs-lookup"><span data-stu-id="b4442-110">Component</span></span>|<span data-ttu-id="b4442-111">0</span><span class="sxs-lookup"><span data-stu-id="b4442-111">0</span></span>|  
|<span data-ttu-id="b4442-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b4442-112">Symbolic Name</span></span>|<span data-ttu-id="b4442-113">0</span><span class="sxs-lookup"><span data-stu-id="b4442-113">0</span></span>|  
|<span data-ttu-id="b4442-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b4442-114">Message Text</span></span>|<span data-ttu-id="b4442-115">Exception de sécurité lors de la mise en correspondance de l'assembly BizTalk « {0} ».</span><span class="sxs-lookup"><span data-stu-id="b4442-115">A security exception occurred while reflecting BizTalk assembly "{0}".</span></span> <span data-ttu-id="b4442-116">Ce problème peut survenir lorsque l'assembly est situé dans un dossier réseau partagé.</span><span class="sxs-lookup"><span data-stu-id="b4442-116">This problem may occur if the assembly is located in a shared network folder.</span></span> <span data-ttu-id="b4442-117">Pour corriger ce problème, essayez l’une des opérations suivantes : 1.</span><span class="sxs-lookup"><span data-stu-id="b4442-117">To correct this problem, try one of the following: 1.</span></span> <span data-ttu-id="b4442-118">Copiez l'assembly et ses dépendances sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b4442-118">Copy the assembly and its dependencies to the local machine.</span></span> <span data-ttu-id="b4442-119">2.</span><span class="sxs-lookup"><span data-stu-id="b4442-119">2.</span></span> <span data-ttu-id="b4442-120">Ajustez la stratégie de sécurité de l'exécution de la configuration .NET afin d'autoriser l'accès.</span><span class="sxs-lookup"><span data-stu-id="b4442-120">Adjust the .NET Configuration Runtime Security policy to permit access.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b4442-121">Explication</span><span class="sxs-lookup"><span data-stu-id="b4442-121">Explanation</span></span>  
 <span data-ttu-id="b4442-122">Cette erreur se produit lorsque vous tentez de publier un assembly BizTalk situé sur un partage réseau sans la stratégie .NET appropriée.</span><span class="sxs-lookup"><span data-stu-id="b4442-122">This error will occur when trying to publish a BizTalk assembly that is on a network share without the right .NET policy.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b4442-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b4442-123">User Action</span></span>  
 <span data-ttu-id="b4442-124">Outre la procédure décrite dans le message d'erreur, copiez l'assembly localement.</span><span class="sxs-lookup"><span data-stu-id="b4442-124">In addition to taking the specific steps outlined in the error message, copy the assembly locally.</span></span> <span data-ttu-id="b4442-125">Vous pouvez également modifier la stratégie pour accorder une confiance totale à l'intranet local.</span><span class="sxs-lookup"><span data-stu-id="b4442-125">Or edit the policy to grant full trust to the local intranet.</span></span>  
  
 <span data-ttu-id="b4442-126">**À l’aide de l’outil Code Access Security Policy (Caspol.exe)**</span><span class="sxs-lookup"><span data-stu-id="b4442-126">**Using the Code Access Security Policy Tool (Caspol.exe)**</span></span>  
  
 <span data-ttu-id="b4442-127">Vous pouvez approuver un dossier de votre ordinateur local au niveau Utilisateur avec des autorisations d'utilisateur normales.</span><span class="sxs-lookup"><span data-stu-id="b4442-127">You can grant trust to a folder on your local computer at the User level with normal user permissions.</span></span> <span data-ttu-id="b4442-128">Pour approuver un emplacement réseau, vous devez disposer de privilèges d'administrateur et modifier la stratégie de sécurité au niveau Ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b4442-128">To grant trust to a network location, you must have administrator privileges and change the security policy at the Machine level.</span></span> <span data-ttu-id="b4442-129">Ce niveau est indépendant du niveau de stratégie Utilisateur. Il n'accorde pas de confiance totale à la zone Intranet, contrairement à la stratégie Utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b4442-129">The Machine policy level acts independently of the User policy level, and the machine policy level does not grant full trust to the Intranet zone even if the User policy does.</span></span> <span data-ttu-id="b4442-130">Les niveaux de stratégie doivent être cohérents.</span><span class="sxs-lookup"><span data-stu-id="b4442-130">The policy levels must agree.</span></span>  
  
 <span data-ttu-id="b4442-131">**Pour accorder une confiance totale à un dossier local**</span><span class="sxs-lookup"><span data-stu-id="b4442-131">**To grant full trust to a local folder**</span></span>  
  
-   <span data-ttu-id="b4442-132">Tapez la commande suivante dans l'invite de commandes Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="b4442-132">Type the following command in the Visual Studio Command Prompt:</span></span>  
  
```  
caspol -u -ag All_Code -url   
C:\<FolderName>\<FolderName>\* FullTrust -n "<Name>" -d  
"<Description>"  
```  
  
 <span data-ttu-id="b4442-133">**Pour accorder une confiance totale à un dossier réseau**</span><span class="sxs-lookup"><span data-stu-id="b4442-133">**To grant full trust to a network folder**</span></span>  
  
-   <span data-ttu-id="b4442-134">Tapez la commande suivante dans l'invite de commandes Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="b4442-134">Type the following command in the Visual Studio Command Prompt:</span></span>  
  
```  
caspol -m -ag LocalIntranet_Zone -url   
\\<ServerName>\<FolderName>\* FullTrust -n "<Name>" -d   
"<Description>"  
```