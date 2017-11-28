---
title: "Numéro de contrôle de groupe ne respecte pas la syntaxe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e173c914-cb5c-4369-ac2f-8f9abee420cb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c9364260d9c90b9935f894eb3a0ada882057ea5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="group-control-number-violates-syntax"></a><span data-ttu-id="05ed0-102">Ce numéro de contrôle de groupe ne respecte pas la syntaxe</span><span class="sxs-lookup"><span data-stu-id="05ed0-102">Group control number violates syntax</span></span>
## <a name="details"></a><span data-ttu-id="05ed0-103">Détails</span><span class="sxs-lookup"><span data-stu-id="05ed0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="05ed0-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="05ed0-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="05ed0-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="05ed0-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="05ed0-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="05ed0-106">Event ID</span></span>|-|  
|<span data-ttu-id="05ed0-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="05ed0-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="05ed0-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="05ed0-108"> EDI</span></span>|  
|<span data-ttu-id="05ed0-109">Composant</span><span class="sxs-lookup"><span data-stu-id="05ed0-109">Component</span></span>|<span data-ttu-id="05ed0-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="05ed0-110">EDI Engine</span></span>|  
|<span data-ttu-id="05ed0-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="05ed0-111">Symbolic Name</span></span>|<span data-ttu-id="05ed0-112">X12FaInvalidControlNumberDescription</span><span class="sxs-lookup"><span data-stu-id="05ed0-112">X12FaInvalidControlNumberDescription</span></span>|  
|<span data-ttu-id="05ed0-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="05ed0-113">Message Text</span></span>|<span data-ttu-id="05ed0-114">Ce numéro de contrôle de groupe ne respecte pas la syntaxe</span><span class="sxs-lookup"><span data-stu-id="05ed0-114">Group control number violates syntax</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="05ed0-115">Explication</span><span class="sxs-lookup"><span data-stu-id="05ed0-115">Explanation</span></span>  
 <span data-ttu-id="05ed0-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange X12 entrant car le numéro de contrôle du groupe des champs GS06 et GE02 de l'échange n'est pas conforme au type de données et à la longueur spécifiés dans le schéma de service.</span><span class="sxs-lookup"><span data-stu-id="05ed0-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because the group control number in the GS06 and GE02 fields of the interchange did not conform to the data type or length specified in the service schema.</span></span> <span data-ttu-id="05ed0-117">Le schéma du service est X12ServiceSchema dans BaseArtifacts.dll.</span><span class="sxs-lookup"><span data-stu-id="05ed0-117">The service schema is the X12ServiceSchema in BaseArtifacts.dll.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="05ed0-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="05ed0-118">User Action</span></span>  
 <span data-ttu-id="05ed0-119">Pour résoudre cette erreur, assurez-vous que les numéros de contrôle du groupe contenus dans les champs GS06 et GE02 de l'échange sont conformes au type de données (X12_N0) et à la longueur (entre un et neuf chiffres) spécifiés dans le schéma de service, puis demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="05ed0-119">To resolve this error, make sure that the group control numbers contained in the GS06 and GE02 fields of the interchange conform to the data type (X12_N0) and length (between one and nine digits) specified in the service schema, and then have the interchange resent.</span></span>