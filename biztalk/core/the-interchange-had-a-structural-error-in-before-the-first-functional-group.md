---
title: "L’échange comportait une erreur structurelle-avant le premier groupe fonctionnel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12202148-0a32-464e-8dbd-d01b9ba530eb
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d5ab490de214f53e85ea32c1b243456f837c72e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-had-a-structural-error-in-before-the-first-functional-group"></a><span data-ttu-id="d880b-102">L’échange comportait une erreur structurelle-avant le premier groupe fonctionnel</span><span class="sxs-lookup"><span data-stu-id="d880b-102">The interchange had a structural error in-before the first functional group</span></span>
## <a name="details"></a><span data-ttu-id="d880b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="d880b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d880b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="d880b-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d880b-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="d880b-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d880b-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d880b-106">Event ID</span></span>|-|  
|<span data-ttu-id="d880b-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="d880b-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d880b-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="d880b-108"> EDI</span></span>|  
|<span data-ttu-id="d880b-109">Composant</span><span class="sxs-lookup"><span data-stu-id="d880b-109">Component</span></span>|<span data-ttu-id="d880b-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="d880b-110">EDI Engine</span></span>|  
|<span data-ttu-id="d880b-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="d880b-111">Symbolic Name</span></span>|<span data-ttu-id="d880b-112">X12InterchangeStructuralErrorBefore1stGroup</span><span class="sxs-lookup"><span data-stu-id="d880b-112">X12InterchangeStructuralErrorBefore1stGroup</span></span>|  
|<span data-ttu-id="d880b-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="d880b-113">Message Text</span></span>|<span data-ttu-id="d880b-114">L’échange avec l’id '{0}', id d’expéditeur « {{1} », id de récepteur « {{2} » comportait une erreur structurelle dans/avant le premier groupe fonctionnel</span><span class="sxs-lookup"><span data-stu-id="d880b-114">The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error in/before the first functional group</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d880b-115">Explication</span><span class="sxs-lookup"><span data-stu-id="d880b-115">Explanation</span></span>  
 <span data-ttu-id="d880b-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, pour l'une des raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="d880b-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, for one of the following reasons:</span></span>  
  
-   <span data-ttu-id="d880b-117">Une erreur structurelle s'est produite dans les segments ISA et IEA ou dans le premier groupe fonctionnel de l'échange, de sorte que ce dernier n'était plus conforme au schéma applicable.</span><span class="sxs-lookup"><span data-stu-id="d880b-117">A structural error occurred in either the ISA and IEA segments or the first functional group of the interchange, so the interchange did not conform to the applicable schema.</span></span>  
  
-   <span data-ttu-id="d880b-118">Le X12ServiceSchema (dans BaseArtifacts.dll) n'était pas déployé.</span><span class="sxs-lookup"><span data-stu-id="d880b-118">The X12ServiceSchema (in BaseArtifacts.dll) was not deployed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d880b-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="d880b-119">User Action</span></span>  
 <span data-ttu-id="d880b-120">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d880b-120">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="d880b-121">Demandez à l'expéditeur de l'échange de modifier les segments ISA et/ou IEA ou le premier groupe fonctionnel de sorte qu'il soit conforme au schéma applicable, puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="d880b-121">Have the sender of the interchange change the ISA and/or IEA segments or the first functional group so that it conforms to the applicable schema, and then resend the interchange.</span></span>  
  
-   <span data-ttu-id="d880b-122">Assurez-vous que le fichier BaseArtifacts.dll inclut le X12ServiceSchema et que ce dernier est déployé.</span><span class="sxs-lookup"><span data-stu-id="d880b-122">Ensure that BaseArtifacts.dll includes the X12ServiceSchema and is deployed.</span></span> <span data-ttu-id="d880b-123">Pour ce faire, ouvrez la console Administration de BizTalk Server, puis le nœud Application BizTalk EDI et le nœud Schémas, en vérifiant que X12ServiceSchema est répertorié.</span><span class="sxs-lookup"><span data-stu-id="d880b-123">You can do so by opening the BizTalk Server Administration Console, opening the BizTalk EDI Application node and the Schemas node, and verifying that X12ServiceSchema is listed.</span></span>