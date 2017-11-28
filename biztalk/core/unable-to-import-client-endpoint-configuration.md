---
title: "Impossible d’importer la configuration du point de terminaison client | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8375e153-ed1c-4bf4-b461-ac026a4b3478
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30be7958ca07dde47d147711da06a276e86ff714
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-import-client-endpoint-configuration"></a><span data-ttu-id="49608-102">Impossible d'importer la configuration du point de terminaison client</span><span class="sxs-lookup"><span data-stu-id="49608-102">Unable to import client endpoint configuration</span></span>
## <a name="details"></a><span data-ttu-id="49608-103">Détails</span><span class="sxs-lookup"><span data-stu-id="49608-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49608-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="49608-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="49608-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="49608-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="49608-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="49608-106">Event ID</span></span>|<span data-ttu-id="49608-107">0</span><span class="sxs-lookup"><span data-stu-id="49608-107">0</span></span>|  
|<span data-ttu-id="49608-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="49608-108">Event Source</span></span>|<span data-ttu-id="49608-109">0</span><span class="sxs-lookup"><span data-stu-id="49608-109">0</span></span>|  
|<span data-ttu-id="49608-110">Composant</span><span class="sxs-lookup"><span data-stu-id="49608-110">Component</span></span>|<span data-ttu-id="49608-111">0</span><span class="sxs-lookup"><span data-stu-id="49608-111">0</span></span>|  
|<span data-ttu-id="49608-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="49608-112">Symbolic Name</span></span>|<span data-ttu-id="49608-113">0</span><span class="sxs-lookup"><span data-stu-id="49608-113">0</span></span>|  
|<span data-ttu-id="49608-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="49608-114">Message Text</span></span>|<span data-ttu-id="49608-115">Impossible d'importer la configuration du point de terminaison client</span><span class="sxs-lookup"><span data-stu-id="49608-115">Unable to import client endpoint configuration</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="49608-116">Explication</span><span class="sxs-lookup"><span data-stu-id="49608-116">Explanation</span></span>  
 <span data-ttu-id="49608-117">Plusieurs explications sont possibles.</span><span class="sxs-lookup"><span data-stu-id="49608-117">There could be more than one explanation for this error.</span></span> <span data-ttu-id="49608-118">Le fichier de configuration peut contenir des caractères non valides.</span><span class="sxs-lookup"><span data-stu-id="49608-118">The configuration file may contain invalid characters.</span></span> <span data-ttu-id="49608-119">L'élément racine est peut-être manquant.</span><span class="sxs-lookup"><span data-stu-id="49608-119">The root element may be missing.</span></span> <span data-ttu-id="49608-120">Les données au niveau racine sont peut-être non valides.</span><span class="sxs-lookup"><span data-stu-id="49608-120">The data at the root level may be invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="49608-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="49608-121">User Action</span></span>  
 <span data-ttu-id="49608-122">Vérifier la validité du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="49608-122">Verify the validity of the configuration file.</span></span> <span data-ttu-id="49608-123">Essayez d’ouvrir le fichier de configuration avec l’éditeur de Configuration de Service (**svcConfigEditor.exe**) et vérifiez chaque propriété.</span><span class="sxs-lookup"><span data-stu-id="49608-123">Try to open the configuration file with the Service Configuration Editor (**svcConfigEditor.exe**) and verify each property.</span></span>