---
title: "Élément de données trop court | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a22c0551-3262-476c-a6c6-2fd214331244
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 311c40d80f1299ce4abcf5f2e5aec5cac2681251
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-element-too-short"></a><span data-ttu-id="32115-102">Élément de données trop court</span><span class="sxs-lookup"><span data-stu-id="32115-102">Data element too short</span></span>
## <a name="details"></a><span data-ttu-id="32115-103">Détails</span><span class="sxs-lookup"><span data-stu-id="32115-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="32115-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="32115-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="32115-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="32115-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="32115-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="32115-106">Event ID</span></span>|-|  
|<span data-ttu-id="32115-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="32115-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="32115-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="32115-108"> EDI</span></span>|  
|<span data-ttu-id="32115-109">Composant</span><span class="sxs-lookup"><span data-stu-id="32115-109">Component</span></span>|<span data-ttu-id="32115-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="32115-110">EDI Engine</span></span>|  
|<span data-ttu-id="32115-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="32115-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="32115-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="32115-112">Message Text</span></span>|<span data-ttu-id="32115-113">Élément de données trop court</span><span class="sxs-lookup"><span data-stu-id="32115-113">Data element too short</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="32115-114">Explication</span><span class="sxs-lookup"><span data-stu-id="32115-114">Explanation</span></span>  
 <span data-ttu-id="32115-115">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI ou le pipeline d'envoi EDI n'a pas pu traiter l'échange entrant car la longueur de l'élément de données est inférieure à la longueur minimale spécifiée par le schéma.</span><span class="sxs-lookup"><span data-stu-id="32115-115">This Error/Warning/Information event indicates that the EDI receive pipeline or the EDI Send pipeline could not process the incoming interchange because a data element was shorter than the minimum length specified by the schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="32115-116">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="32115-116">User Action</span></span>  
 <span data-ttu-id="32115-117">Pour résoudre cette erreur, augmentez la longueur de l'élément de données de l'échange afin qu'elle soit supérieure à la longueur minimale.</span><span class="sxs-lookup"><span data-stu-id="32115-117">To resolve this error, lengthen the data element in the interchange that was too short so it is greater than the minimum length.</span></span> <span data-ttu-id="32115-118">Pour déterminer la longueur minimale, ouvrez le schéma dans le dossier \XSD_Schema, recherchez l'ID d'élément de données et identifiez la valeur minLength.</span><span class="sxs-lookup"><span data-stu-id="32115-118">To determine the minimum length, open the schema in the \XSD_Schema folder, search on the data element ID, and identify what the minLength value is.</span></span>