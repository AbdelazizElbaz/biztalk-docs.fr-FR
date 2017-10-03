---
title: "Impossible d’obtenir le schéma à partir de la liaison pour valider l’adresse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b002084a-63ae-4685-8ce3-88cc6489e19e
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c952e967a391011bbd887513d58e426d90d325a1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cannot-obtain-scheme-from-binding-to-validate-address"></a><span data-ttu-id="0d19c-102">Impossible d'obtenir le schéma à partir de la liaison pour valider l'adresse</span><span class="sxs-lookup"><span data-stu-id="0d19c-102">Cannot obtain scheme from binding to validate address</span></span>
## <a name="details"></a><span data-ttu-id="0d19c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="0d19c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d19c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="0d19c-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0d19c-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="0d19c-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="0d19c-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0d19c-106">Event ID</span></span>|<span data-ttu-id="0d19c-107">0</span><span class="sxs-lookup"><span data-stu-id="0d19c-107">0</span></span>|  
|<span data-ttu-id="0d19c-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="0d19c-108">Event Source</span></span>|<span data-ttu-id="0d19c-109">0</span><span class="sxs-lookup"><span data-stu-id="0d19c-109">0</span></span>|  
|<span data-ttu-id="0d19c-110">Composant</span><span class="sxs-lookup"><span data-stu-id="0d19c-110">Component</span></span>|<span data-ttu-id="0d19c-111">0</span><span class="sxs-lookup"><span data-stu-id="0d19c-111">0</span></span>|  
|<span data-ttu-id="0d19c-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="0d19c-112">Symbolic Name</span></span>|<span data-ttu-id="0d19c-113">0</span><span class="sxs-lookup"><span data-stu-id="0d19c-113">0</span></span>|  
|<span data-ttu-id="0d19c-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="0d19c-114">Message Text</span></span>|<span data-ttu-id="0d19c-115">Impossible d'obtenir le schéma à partir de la liaison pour valider l'adresse.</span><span class="sxs-lookup"><span data-stu-id="0d19c-115">Cannot obtain scheme from binding to validate address.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0d19c-116">Explication</span><span class="sxs-lookup"><span data-stu-id="0d19c-116">Explanation</span></span>  
 <span data-ttu-id="0d19c-117">L'élément de liaison de transport spécifié ne possède aucun schéma.</span><span class="sxs-lookup"><span data-stu-id="0d19c-117">The transport binding element that has been specified does not have a scheme.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0d19c-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="0d19c-118">User Action</span></span>  
 <span data-ttu-id="0d19c-119">Vérifiez que l'élément de liaison de transport est valide ou possède un schéma valide.</span><span class="sxs-lookup"><span data-stu-id="0d19c-119">Make sure that the transport binding element has a valid scheme, or that a valid transport binding element is selected.</span></span> <span data-ttu-id="0d19c-120">Si vous utilisez une liaison personnalisée, veillez à ce qu'un élément de liaison de transport valide soit spécifié.</span><span class="sxs-lookup"><span data-stu-id="0d19c-120">If using a custom binding, make sure a valid transport binding element is specified.</span></span>  
  
 <span data-ttu-id="0d19c-121">Pour plus d’informations, consultez les ressources suivantes dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide :</span><span class="sxs-lookup"><span data-stu-id="0d19c-121">For additional information, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="0d19c-122">Configuration de l’adaptateur WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="0d19c-122">Configuring the WCF-Custom Adapter</span></span>](../core/configuring-the-wcf-custom-adapter.md)