---
title: "Élément de données trop long | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf608cc1-d482-4e19-8f56-10d9e03feb79
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbfe63fccc442c35411bfae04c7f27629ce066ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-element-too-long"></a><span data-ttu-id="7828a-102">Élément de données trop long</span><span class="sxs-lookup"><span data-stu-id="7828a-102">Data element too long</span></span>
## <a name="details"></a><span data-ttu-id="7828a-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7828a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7828a-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7828a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7828a-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7828a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="7828a-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7828a-106">Event ID</span></span>|-|  
|<span data-ttu-id="7828a-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7828a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7828a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="7828a-108"> EDI</span></span>|  
|<span data-ttu-id="7828a-109">Composant</span><span class="sxs-lookup"><span data-stu-id="7828a-109">Component</span></span>|<span data-ttu-id="7828a-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="7828a-110">EDI Engine</span></span>|  
|<span data-ttu-id="7828a-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7828a-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="7828a-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7828a-112">Message Text</span></span>|<span data-ttu-id="7828a-113">Élément de données trop long</span><span class="sxs-lookup"><span data-stu-id="7828a-113">Data element too long</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7828a-114">Explication</span><span class="sxs-lookup"><span data-stu-id="7828a-114">Explanation</span></span>  
 <span data-ttu-id="7828a-115">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI ou le pipeline d'envoi EDI n'a pas pu traiter l'échange entrant car la longueur de l'élément de données est supérieure à la longueur maximale spécifiée par le schéma.</span><span class="sxs-lookup"><span data-stu-id="7828a-115">This Error/Warning/Information event indicates that the EDI receive pipeline or the EDI Send pipeline could not process the incoming interchange because a data element was longer than the maximum length specified by the schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7828a-116">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7828a-116">User Action</span></span>  
 <span data-ttu-id="7828a-117">Pour résoudre cette erreur, réduisez la longueur de l'élément de données de l'échange afin qu'elle soit inférieure à la longueur maximale.</span><span class="sxs-lookup"><span data-stu-id="7828a-117">To resolve this error, shorten the data element in the interchange that was too long so it is below the maximum limit.</span></span> <span data-ttu-id="7828a-118">Pour déterminer la longueur maximale, ouvrez le schéma dans le dossier \XSD_Schema, recherchez l'ID d'élément de données et identifiez la valeur maxLength.</span><span class="sxs-lookup"><span data-stu-id="7828a-118">To determine the maximum length, open the schema in the \XSD_Schema folder, search on the data element ID, and identify what the maxLength value is.</span></span>