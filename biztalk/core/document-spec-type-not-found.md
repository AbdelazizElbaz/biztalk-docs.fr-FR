---
title: "Ne pas trouvé de type de spécification de document | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cb2a458-d0f4-420d-8d35-0e739167464f
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 886f4ac81ab7fb2c4a844f50348d84bead65a892
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="document-spec-type-not-found"></a><span data-ttu-id="54b85-102">Type de spécification de document non trouvé</span><span class="sxs-lookup"><span data-stu-id="54b85-102">Document spec type not found</span></span>
## <a name="details"></a><span data-ttu-id="54b85-103">Détails</span><span class="sxs-lookup"><span data-stu-id="54b85-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="54b85-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="54b85-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="54b85-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="54b85-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="54b85-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="54b85-106">Event ID</span></span>|-|  
|<span data-ttu-id="54b85-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="54b85-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="54b85-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="54b85-108"> EDI</span></span>|  
|<span data-ttu-id="54b85-109">Composant</span><span class="sxs-lookup"><span data-stu-id="54b85-109">Component</span></span>|<span data-ttu-id="54b85-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="54b85-110">EDI Engine</span></span>|  
|<span data-ttu-id="54b85-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="54b85-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="54b85-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="54b85-112">Message Text</span></span>|<span data-ttu-id="54b85-113">Type de spécification de document {0} non trouvé</span><span class="sxs-lookup"><span data-stu-id="54b85-113">Document spec type {0} not found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="54b85-114">Explication</span><span class="sxs-lookup"><span data-stu-id="54b85-114">Explanation</span></span>  
 <span data-ttu-id="54b85-115">Cette erreur indique que le schéma est introuvable.</span><span class="sxs-lookup"><span data-stu-id="54b85-115">This error indicates the schema is not found.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="54b85-116">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="54b85-116">User Action</span></span>  
 <span data-ttu-id="54b85-117">Pour résoudre cette erreur, déployez le schéma de document :</span><span class="sxs-lookup"><span data-stu-id="54b85-117">To resolve this error, deploy the document schema:</span></span>  
  
1.  <span data-ttu-id="54b85-118">Démarrer **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="54b85-118">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="54b85-119">Créez un projet ou ouvrez-en un qui existe déjà.</span><span class="sxs-lookup"><span data-stu-id="54b85-119">Create or open an existing project</span></span>  
  
3.  <span data-ttu-id="54b85-120">Ajoutez le schéma au projet.</span><span class="sxs-lookup"><span data-stu-id="54b85-120">Add the schema to the project.</span></span>  
  
4.  <span data-ttu-id="54b85-121">Déployez le projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="54b85-121">Deploy the project in Visual Studio.</span></span>