---
title: "Le nom de propriété n’est pas une chaîne valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a0641e4-1267-44a0-8777-bd6e2baf1088
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 787d38dce9336eefa3715b5edd09db2cc426332b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-property-name-is-not-a-valid-string"></a><span data-ttu-id="f85c2-102">Le nom de propriété n'est pas une chaîne valide</span><span class="sxs-lookup"><span data-stu-id="f85c2-102">The property name is not a valid string</span></span>
## <a name="details"></a><span data-ttu-id="f85c2-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f85c2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f85c2-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f85c2-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f85c2-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f85c2-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f85c2-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f85c2-106">Event ID</span></span>|-|  
|<span data-ttu-id="f85c2-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f85c2-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f85c2-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f85c2-108"> EDI</span></span>|  
|<span data-ttu-id="f85c2-109">Composant</span><span class="sxs-lookup"><span data-stu-id="f85c2-109">Component</span></span>|<span data-ttu-id="f85c2-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="f85c2-110">Batching Engine</span></span>|  
|<span data-ttu-id="f85c2-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f85c2-111">Symbolic Name</span></span>|<span data-ttu-id="f85c2-112">InvalidPropertyName</span><span class="sxs-lookup"><span data-stu-id="f85c2-112">InvalidPropertyName</span></span>|  
|<span data-ttu-id="f85c2-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f85c2-113">Message Text</span></span>|<span data-ttu-id="f85c2-114">Le nom de propriété n'est pas une chaîne valide</span><span class="sxs-lookup"><span data-stu-id="f85c2-114">The property name is not a valid string</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f85c2-115">Explication</span><span class="sxs-lookup"><span data-stu-id="f85c2-115">Explanation</span></span>  
 <span data-ttu-id="f85c2-116">Cet événement d'erreur/d'avertissement/d'informations indique que le nom entré pour une propriété dans la boîte de dialogue Filtre par lot est non valide, car le nom de la propriété n'est pas du type chaîne requis.</span><span class="sxs-lookup"><span data-stu-id="f85c2-116">This Error/Warning/Information event indicates that the name entered for a property in the Batch Filter dialog box was invalid, because the property name was not a string, as required.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f85c2-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f85c2-117">User Action</span></span>  
 <span data-ttu-id="f85c2-118">Pour résoudre cette erreur, dans la boîte de dialogue Propriétés EDI, dans la page Paramètres de création de lots d'échange, ouvrez la boîte de dialogue Filtre par lot.</span><span class="sxs-lookup"><span data-stu-id="f85c2-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="f85c2-119">Vérifiez que tous les noms de propriété sont des chaînes.</span><span class="sxs-lookup"><span data-stu-id="f85c2-119">Make sure that all property names are strings.</span></span>