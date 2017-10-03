---
title: "Numéro de contrôle dupliqué | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 331ad173-29b3-427c-8104-60d80c580a5a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e83f685242f4c69e6a142f3abb027017657611f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="duplicate-control-number"></a><span data-ttu-id="e0394-102">Numéro de contrôle dupliqué</span><span class="sxs-lookup"><span data-stu-id="e0394-102">Duplicate Control Number</span></span>
## <a name="details"></a><span data-ttu-id="e0394-103">Détails</span><span class="sxs-lookup"><span data-stu-id="e0394-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e0394-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e0394-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e0394-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e0394-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="e0394-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e0394-106">Event ID</span></span>|-|  
|<span data-ttu-id="e0394-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e0394-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e0394-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="e0394-108"> EDI</span></span>|  
|<span data-ttu-id="e0394-109">Composant</span><span class="sxs-lookup"><span data-stu-id="e0394-109">Component</span></span>|<span data-ttu-id="e0394-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="e0394-110">EDI Engine</span></span>|  
|<span data-ttu-id="e0394-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e0394-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="e0394-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e0394-112">Message Text</span></span>|<span data-ttu-id="e0394-113">Numéro de contrôle dupliqué</span><span class="sxs-lookup"><span data-stu-id="e0394-113">Duplicate Control Number</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e0394-114">Explication</span><span class="sxs-lookup"><span data-stu-id="e0394-114">Explanation</span></span>  
 <span data-ttu-id="e0394-115">Cet événement de type erreur/avertissement/information indique que le pipeline de réception EDI n'a pas pu traiter un échange entrant, car il présentait le même numéro de contrôle d'échange, de groupe ou de document informatisé qu'un échange reçu précédemment.</span><span class="sxs-lookup"><span data-stu-id="e0394-115">This Error/Warning/Information event indicates that the EDI receive pipeline could not process an incoming interchange because it had the same interchange, group, or transaction set control number as a previously received interchange.</span></span> <span data-ttu-id="e0394-116">Cette situation aboutit à un échec tant que les vérifications de numéro de contrôle dupliqué appropriées sont activées.</span><span class="sxs-lookup"><span data-stu-id="e0394-116">This will result in a failure as long as the appropriate duplicate control number checks are enabled.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e0394-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e0394-117">User Action</span></span>  
 <span data-ttu-id="e0394-118">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0394-118">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="e0394-119">Assurez-vous que l'échange envoyé à BizTalk Server ne présente pas le même numéro de contrôle d'échange, de groupe ou de document informatisé qu'un échange précédent, si la vérification de numéro de contrôle dupliqué correspondante est activée.</span><span class="sxs-lookup"><span data-stu-id="e0394-119">Ensure that the interchange sent to BizTalk Server does not have the same interchange, group, or transaction set control number as a previous interchange, if the corresponding duplicate control number check is enabled.</span></span>  
  
-   <span data-ttu-id="e0394-120">Désactivez la vérification du numéro de contrôle dupliqué.</span><span class="sxs-lookup"><span data-stu-id="e0394-120">Disable the duplicate control number check.</span></span> <span data-ttu-id="e0394-121">Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], cliquez avec le bouton droit de la souris sur le tiers approprié, puis ouvrez la boîte de dialogue Propriétés du traitement de l'échange EDIFACT ou Propriétés du processus d'échange X12 correspondant au tiers jouant le rôle d'expéditeur de l'échange.</span><span class="sxs-lookup"><span data-stu-id="e0394-121">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the appropriate party, and open either the EDIFACT Interchange Processing Properties or the X12 Interchange Processing Properties dialog box for the party as an interchange sender.</span></span> <span data-ttu-id="e0394-122">Pour désactiver la vérification d'un échange EDIFACT, désélectionnez la propriété Vérifier qu'aucun doublon n'existe pour UNB5 (Numéro de contrôle de l'échange), Vérifier qu'aucun doublon n'existe pour UNG5 (Numéro de contrôle de l'échange) dans l'échange ou Vérifier qu'aucun doublon n'existe pour UNH1 (Numéro de référence du document informatisé) dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="e0394-122">To disable a check for an EDIFACT interchange, clear the Check for duplicate UNB5 (Interchange control number), Check for duplicate UNG5 (Group control number) in interchange, or Check for duplicate UNH1 (Transaction set reference number) in group property.</span></span> <span data-ttu-id="e0394-123">Pour désactiver la vérification d'un échange X12, désélectionnez la propriété Vérifier qu'aucun doublon n'existe pour ISA13 (Numéro de contrôle de l'échange), Vérifier qu'aucun doublon n'existe pour GS6 (Numéro de contrôle de l'échange) dans l'échange ou Vérifier qu'aucun doublon n'existe pour ST2 (Numéro de contrôle du document informatisé) dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="e0394-123">To disable a check for an X12 interchange, clear the Check for duplicate ISA13 (Interchange control number), Check for duplicate GS6 (Group control number) in interchange, or Check for duplicate ST2 (Transaction set control number) in group property.</span></span>