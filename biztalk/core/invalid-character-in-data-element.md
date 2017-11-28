---
title: "Caractère non valide dans l’élément de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db7e2c72-f2cc-4157-aa26-062d2cc1210b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc805fbede667013b56088b3d2c29913157c2fe5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-character-in-data-element"></a><span data-ttu-id="53cc5-102">Caractère non valide dans l'élément de données</span><span class="sxs-lookup"><span data-stu-id="53cc5-102">Invalid character in data element</span></span>
## <a name="details"></a><span data-ttu-id="53cc5-103">Détails</span><span class="sxs-lookup"><span data-stu-id="53cc5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="53cc5-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="53cc5-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="53cc5-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="53cc5-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="53cc5-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="53cc5-106">Event ID</span></span>|-|  
|<span data-ttu-id="53cc5-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="53cc5-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="53cc5-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="53cc5-108"> EDI</span></span>|  
|<span data-ttu-id="53cc5-109">Composant</span><span class="sxs-lookup"><span data-stu-id="53cc5-109">Component</span></span>|<span data-ttu-id="53cc5-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="53cc5-110">EDI Engine</span></span>|  
|<span data-ttu-id="53cc5-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="53cc5-111">Symbolic Name</span></span>|<span data-ttu-id="53cc5-112">X12DeInvalidCharacterInDataElementDescription</span><span class="sxs-lookup"><span data-stu-id="53cc5-112">X12DeInvalidCharacterInDataElementDescription</span></span>|  
|<span data-ttu-id="53cc5-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="53cc5-113">Message Text</span></span>|<span data-ttu-id="53cc5-114">Caractère non valide dans l'élément de données</span><span class="sxs-lookup"><span data-stu-id="53cc5-114">Invalid character in data element</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="53cc5-115">Explication</span><span class="sxs-lookup"><span data-stu-id="53cc5-115">Explanation</span></span>  
 <span data-ttu-id="53cc5-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car la valeur d'un élément de données n'est pas conforme à celle spécifiée dans le schéma EDI.</span><span class="sxs-lookup"><span data-stu-id="53cc5-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of a data element did not conform to the value specified in the EDI schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="53cc5-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="53cc5-117">User Action</span></span>  
 <span data-ttu-id="53cc5-118">Pour résoudre cette erreur, assurez-vous que la valeur de l'élément de données est conforme à celle du schéma EDI, puis demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="53cc5-118">To resolve this error, make sure that the value in the data element conforms to the EDI schema, and then have the interchange resent.</span></span>