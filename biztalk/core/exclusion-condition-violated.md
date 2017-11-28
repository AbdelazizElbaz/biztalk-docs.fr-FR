---
title: "Condition d’exclusion violée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e508da6-7edc-45c0-a7ab-f23337dc1b54
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5a508c113daf628491837adee119649ac17b478
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exclusion-condition-violated"></a><span data-ttu-id="3dbb8-102">Condition d'exclusion non respectée</span><span class="sxs-lookup"><span data-stu-id="3dbb8-102">Exclusion Condition Violated</span></span>
## <a name="details"></a><span data-ttu-id="3dbb8-103">Détails</span><span class="sxs-lookup"><span data-stu-id="3dbb8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3dbb8-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="3dbb8-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3dbb8-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="3dbb8-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="3dbb8-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="3dbb8-106">Event ID</span></span>|-|  
|<span data-ttu-id="3dbb8-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="3dbb8-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3dbb8-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="3dbb8-108"> EDI</span></span>|  
|<span data-ttu-id="3dbb8-109">Composant</span><span class="sxs-lookup"><span data-stu-id="3dbb8-109">Component</span></span>|<span data-ttu-id="3dbb8-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="3dbb8-110">EDI Engine</span></span>|  
|<span data-ttu-id="3dbb8-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="3dbb8-111">Symbolic Name</span></span>|<span data-ttu-id="3dbb8-112">X12DeExclusionConditionViolatedDescription</span><span class="sxs-lookup"><span data-stu-id="3dbb8-112">X12DeExclusionConditionViolatedDescription</span></span>|  
|<span data-ttu-id="3dbb8-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="3dbb8-113">Message Text</span></span>|<span data-ttu-id="3dbb8-114">Condition d'exclusion non respectée, pour plus de détails, consultez la valeur du champ dans l'instance</span><span class="sxs-lookup"><span data-stu-id="3dbb8-114">Exclusion Condition Violated, refer to field value in instance for details</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3dbb8-115">Explication</span><span class="sxs-lookup"><span data-stu-id="3dbb8-115">Explanation</span></span>  
 <span data-ttu-id="3dbb8-116">Cet événement de type erreur/avertissement/information indique que la validation d'un échange X12 a échoué, soit lors de la phase de conception (à l'aide de l'outil de validation XML) ou lors de l'exécution, côté réception ou envoi, car un segment dans l'instance n'a pas respecté une règle d'exclusion de validation de champ croisée.</span><span class="sxs-lookup"><span data-stu-id="3dbb8-116">This Error/Warning/Information event indicates that validation of an X12 interchange failed either at design time (using the XML validation tool) or at run time, on either the receive side or the send side, because a segment in the instance failed a cross-field validation exclusion rule.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3dbb8-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="3dbb8-117">User Action</span></span>  
 <span data-ttu-id="3dbb8-118">Pour résoudre cette erreur, vérifiez que le segment qui n'a pas respecté la règle d'exclusion est modifié de sorte qu'il subisse avec succès la validation de champ croisée, puis réexécutez le processus de validation.</span><span class="sxs-lookup"><span data-stu-id="3dbb8-118">To resolve this error, ensure that the segment that failed the exclusion rule is changed so that it passes cross-field validation, and then run the validation process again.</span></span>