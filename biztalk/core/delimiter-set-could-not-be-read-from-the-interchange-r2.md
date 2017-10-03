---
title: "L’ensemble de délimiteurs n’a pas pu être lue dans l’échange (R2) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17bdd32e-d43f-4f59-af27-5d3054fd5432
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3836b218ac3596bef25edb29eaf72c38f65b6e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delimiter-set-could-not-be-read-from-the-interchange-r2"></a><span data-ttu-id="ca697-102">Un ensemble de délimiteurs n'a pu être lu à partir de l'échange (R2).</span><span class="sxs-lookup"><span data-stu-id="ca697-102">Delimiter set could not be read from the interchange (R2)</span></span>
## <a name="details"></a><span data-ttu-id="ca697-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ca697-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ca697-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ca697-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ca697-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ca697-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ca697-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ca697-106">Event ID</span></span>|-|  
|<span data-ttu-id="ca697-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ca697-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ca697-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="ca697-108"> EDI</span></span>|  
|<span data-ttu-id="ca697-109">Composant</span><span class="sxs-lookup"><span data-stu-id="ca697-109">Component</span></span>|<span data-ttu-id="ca697-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="ca697-110">EDI Engine</span></span>|  
|<span data-ttu-id="ca697-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ca697-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="ca697-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ca697-112">Message Text</span></span>|<span data-ttu-id="ca697-113">L’ensemble de délimiteurs n’a pas pu être lus à partir de l’échange.</span><span class="sxs-lookup"><span data-stu-id="ca697-113">Delimiter set could not be read from the interchange.</span></span> <span data-ttu-id="ca697-114">L'attribut DelimiterSetSerializedData est manquant dans le noeud racine.</span><span class="sxs-lookup"><span data-stu-id="ca697-114">The attribute DelimiterSetSerializedData is missing from root node.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ca697-115">Explication</span><span class="sxs-lookup"><span data-stu-id="ca697-115">Explanation</span></span>  
 <span data-ttu-id="ca697-116">Cette erreur indique que l'échange ne contient pas les valeurs de l'ensemble de délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="ca697-116">This error indicates the interchange does not contain the delimiter set values.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ca697-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ca697-117">User Action</span></span>  
 <span data-ttu-id="ca697-118">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ca697-118">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="ca697-119">Ajoutez les valeurs de l'ensemble de délimiteurs à l'échange, de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ca697-119">Add delimiter set values to the interchange, as follows:</span></span>  
  
    1.  <span data-ttu-id="ca697-120">Ouvrez le message.</span><span class="sxs-lookup"><span data-stu-id="ca697-120">Open up the message.</span></span>  
  
    2.  <span data-ttu-id="ca697-121">Déterminez s'il existe un segment UNA dans l'échange.</span><span class="sxs-lookup"><span data-stu-id="ca697-121">Determine whether there is a UNA segment in the interchange.</span></span> <span data-ttu-id="ca697-122">S'il n'existe pas de segment UNA, demandez au partenaire de l'ajouter à l'échange.</span><span class="sxs-lookup"><span data-stu-id="ca697-122">If there is not a UNA segment, ask the partner to add the UNA segment to the interchange.</span></span>  
  
-   <span data-ttu-id="ca697-123">Entrez les valeurs du délimiteur à la propriété de pipeline EfactDelimiters, de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ca697-123">Enter the delimiter values to the EfactDelimiters pipeline property, as follows:</span></span>  
  
    1.  <span data-ttu-id="ca697-124">Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], cliquez avec le bouton droit sur l'emplacement de réception ou sur le port d'envoi qui utilise le pipeline pour lequel définir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="ca697-124">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the receive location or send port using the pipeline that you want to set properties for.</span></span> <span data-ttu-id="ca697-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ca697-125">Click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="ca697-126">Cliquez sur le bouton représentant des points de suspension (…) en regard du pipeline pour lequel définir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="ca697-126">Click the ellipsis button (…) next to the pipeline that you want to set properties for.</span></span>  
  
    3.  <span data-ttu-id="ca697-127">Entrez les valeurs des délimiteurs UNA sous la forme d'une liste délimitée par des virgules (pour UNA1, UNA2, UNA3, UNA4, UNA5 et UNA6), en modifiant les paramètres par défaut si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="ca697-127">Enter values for the UNA delimiters as a comma-delimited list (for UNA1, UNA2, UNA3, UNA4, UNA5, and UNA6), changing the defaults as required.</span></span> <span data-ttu-id="ca697-128">Les valeurs par défaut sont les suivantes : 0x3A, 0x2B, 0x2C, 0x3F, 0 x 20, 0 x 27.</span><span class="sxs-lookup"><span data-stu-id="ca697-128">The defaults are as follows: 0x3A, 0x2B, 0x2C, 0x3F, 0x20, 0x27.</span></span>  
  
    4.  <span data-ttu-id="ca697-129">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ca697-129">Click **OK**.</span></span>