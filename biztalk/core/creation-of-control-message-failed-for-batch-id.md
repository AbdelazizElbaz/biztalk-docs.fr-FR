---
title: "Échec de la création du Message de contrôle pour l’id de lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f03078e7-46b0-4082-9d66-6b892152a12d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a5650ab649e9b0957e64f3cdecc13c725d64536
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creation-of-control-message-failed-for-batch-id"></a><span data-ttu-id="6ae02-102">Échec de la création du message de contrôle pour l'ID de lot</span><span class="sxs-lookup"><span data-stu-id="6ae02-102">Creation of Control Message failed for Batch id</span></span>
## <a name="details"></a><span data-ttu-id="6ae02-103">Détails</span><span class="sxs-lookup"><span data-stu-id="6ae02-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6ae02-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="6ae02-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6ae02-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="6ae02-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="6ae02-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6ae02-106">Event ID</span></span>|-|  
|<span data-ttu-id="6ae02-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="6ae02-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6ae02-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="6ae02-108"> EDI</span></span>|  
|<span data-ttu-id="6ae02-109">Composant</span><span class="sxs-lookup"><span data-stu-id="6ae02-109">Component</span></span>|<span data-ttu-id="6ae02-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="6ae02-110">EDI Engine</span></span>|  
|<span data-ttu-id="6ae02-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="6ae02-111">Symbolic Name</span></span>|<span data-ttu-id="6ae02-112">CreateControlMessageFailed</span><span class="sxs-lookup"><span data-stu-id="6ae02-112">CreateControlMessageFailed</span></span>|  
|<span data-ttu-id="6ae02-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="6ae02-113">Message Text</span></span>|<span data-ttu-id="6ae02-114">Échec de la création du message de contrôle pour l'ID de lot {0}.</span><span class="sxs-lookup"><span data-stu-id="6ae02-114">Creation of Control Message failed for Batch id {0}.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6ae02-115">Explication</span><span class="sxs-lookup"><span data-stu-id="6ae02-115">Explanation</span></span>  
 <span data-ttu-id="6ae02-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server a arrêté ou démarré un lot.</span><span class="sxs-lookup"><span data-stu-id="6ae02-116">This Error/Warning/Information event indicates BizTalk Server was start/stop a batch.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6ae02-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6ae02-117">User Action</span></span>  
 <span data-ttu-id="6ae02-118">Pour résoudre cette erreur, assurez-vous qu'un lot doté d'un ID donné est présent dans les propriétés de l'accord dans lequel il est contenu et que la base de données est active.</span><span class="sxs-lookup"><span data-stu-id="6ae02-118">To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement and the database is up.</span></span>