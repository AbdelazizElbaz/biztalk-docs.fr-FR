---
title: "L’opérateur de comparaison n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8383230d-9bf6-4bc5-9300-4cfd0ad38f28
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12652fbd59fde08d8321c6fdd85bb0998ce8ccc6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-comparison-operator-is-not-valid"></a><span data-ttu-id="4215b-102">Opérateur de comparaison non valide</span><span class="sxs-lookup"><span data-stu-id="4215b-102">The comparison operator is not valid</span></span>
## <a name="details"></a><span data-ttu-id="4215b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="4215b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4215b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="4215b-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="4215b-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="4215b-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="4215b-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="4215b-106">Event ID</span></span>|-|  
|<span data-ttu-id="4215b-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="4215b-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4215b-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="4215b-108"> EDI</span></span>|  
|<span data-ttu-id="4215b-109">Composant</span><span class="sxs-lookup"><span data-stu-id="4215b-109">Component</span></span>|<span data-ttu-id="4215b-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="4215b-110">Batching Engine</span></span>|  
|<span data-ttu-id="4215b-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="4215b-111">Symbolic Name</span></span>|<span data-ttu-id="4215b-112">InvalidComparisonOperator</span><span class="sxs-lookup"><span data-stu-id="4215b-112">InvalidComparisonOperator</span></span>|  
|<span data-ttu-id="4215b-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="4215b-113">Message Text</span></span>|<span data-ttu-id="4215b-114">Opérateur de comparaison non valide.</span><span class="sxs-lookup"><span data-stu-id="4215b-114">The comparison operator is not valid.</span></span> <span data-ttu-id="4215b-115">Message d'exception = {0}</span><span class="sxs-lookup"><span data-stu-id="4215b-115">Exception message = {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4215b-116">Explication</span><span class="sxs-lookup"><span data-stu-id="4215b-116">Explanation</span></span>  
 <span data-ttu-id="4215b-117">Cet événement d'erreur/d'avertissement/d'informations indique que l'opérateur de comparaison entré pour une ligne de la boîte de dialogue Filtre par lot n'était pas valide pour la propriété et la valeur.</span><span class="sxs-lookup"><span data-stu-id="4215b-117">This Error/Warning/Information event indicates that the comparison operator entered for a row of the Batch Filter dialog box was not valid for the property and the value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4215b-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4215b-118">User Action</span></span>  
 <span data-ttu-id="4215b-119">Pour résoudre cette erreur, dans la boîte de dialogue Propriétés EDI, dans la page Paramètres de création de lots d'échange, ouvrez la boîte de dialogue Filtre par lot.</span><span class="sxs-lookup"><span data-stu-id="4215b-119">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="4215b-120">Assurez-vous que les opérateurs de comparaison entrés pour les lignes dans la grille Filtre par lot sont valides pour la propriété et la valeur.</span><span class="sxs-lookup"><span data-stu-id="4215b-120">Make sure that the comparison operators entered for rows in the Batch Filter grid are valid for the property and the value.</span></span>