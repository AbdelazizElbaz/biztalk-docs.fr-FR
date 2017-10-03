---
title: Le segment ISA doit avoir une longueur minimale de 108 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57641445-cebb-4219-998d-54038d7ddf19
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ecd5c6761c6dbcc59ad6353efa2772b9eecf387
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="isa-segment-needs-to-have-a-minimum-length-of-108"></a><span data-ttu-id="5bab5-102">Le segment ISA doit avoir une longueur minimale de 108.</span><span class="sxs-lookup"><span data-stu-id="5bab5-102">ISA segment needs to have a minimum length of 108</span></span>
## <a name="details"></a><span data-ttu-id="5bab5-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5bab5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5bab5-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5bab5-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5bab5-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5bab5-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5bab5-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5bab5-106">Event ID</span></span>|-|  
|<span data-ttu-id="5bab5-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5bab5-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5bab5-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="5bab5-108"> EDI</span></span>|  
|<span data-ttu-id="5bab5-109">Composant</span><span class="sxs-lookup"><span data-stu-id="5bab5-109">Component</span></span>|<span data-ttu-id="5bab5-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="5bab5-110">EDI Engine</span></span>|  
|<span data-ttu-id="5bab5-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5bab5-111">Symbolic Name</span></span>|<span data-ttu-id="5bab5-112">NseIsaSuffix1LFDescription</span><span class="sxs-lookup"><span data-stu-id="5bab5-112">NseIsaSuffix1LFDescription</span></span>|  
|<span data-ttu-id="5bab5-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5bab5-113">Message Text</span></span>|<span data-ttu-id="5bab5-114">Le segment ISA doit avoir une longueur minimale de 108, l'instance a {0}</span><span class="sxs-lookup"><span data-stu-id="5bab5-114">ISA segment needs to have a minimum length of 108, instance has {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5bab5-115">Explication</span><span class="sxs-lookup"><span data-stu-id="5bab5-115">Explanation</span></span>  
 <span data-ttu-id="5bab5-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car le segment ISA de celui-ci n'était pas conforme au nombre de chiffres établi par le schéma de service (X12ServiceSchema ou EdifactServiceSchema dans BaseArtifacts.dll).</span><span class="sxs-lookup"><span data-stu-id="5bab5-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the ISA segment in the interchange did not conform to the number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5bab5-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5bab5-117">User Action</span></span>  
 <span data-ttu-id="5bab5-118">Pour résoudre cette erreur, vérifiez que chacun des champs du segment ISA (de ISA01 à ISA16) comporte le nombre de chiffres minimum requis.</span><span class="sxs-lookup"><span data-stu-id="5bab5-118">To resolve this error, make sure that each of the fields in the ISA segment (from ISA01 to ISA16) has the required minimum number of digits.</span></span> <span data-ttu-id="5bab5-119">Pour savoir quel est le nombre de chiffres minimum, ouvrez la console Administration de BizTalk Server, le nœud Groupe BizTalk, le nœud Applications, le nœud Application BizTalk EDI, puis le nœud de schéma. Ouvrez ensuite Microsoft.BizTalk.Edi.BaseArtifacts.X12ServiceSchema avec le nœud racine d'ISA, puis cliquez sur Affichage de schéma.</span><span class="sxs-lookup"><span data-stu-id="5bab5-119">You can see the minimum number of digits by opening the BizTalk Server Administration Console; opening the BizTalk Group node, the Applications node, the BizTalk EDI Application node, and then the schema node; opening the Microsoft.BizTalk.Edi.BaseArtifacts.X12ServiceSchema with the root node of ISA; and then clicking the Schema View.</span></span>