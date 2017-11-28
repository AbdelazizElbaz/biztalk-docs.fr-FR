---
title: ID de destinataire non valide | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: feabf940-c49b-4f4a-8906-230dc8fb1b30
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d397c75efe1172f87def3dee92e20f4d0d7ef4d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-receiverid"></a><span data-ttu-id="38048-102">Id de destinataire non valide</span><span class="sxs-lookup"><span data-stu-id="38048-102">Invalid ReceiverId</span></span>
## <a name="details"></a><span data-ttu-id="38048-103">Détails</span><span class="sxs-lookup"><span data-stu-id="38048-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="38048-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="38048-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="38048-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="38048-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="38048-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="38048-106">Event ID</span></span>|-|  
|<span data-ttu-id="38048-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="38048-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="38048-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="38048-108"> EDI</span></span>|  
|<span data-ttu-id="38048-109">Composant</span><span class="sxs-lookup"><span data-stu-id="38048-109">Component</span></span>|<span data-ttu-id="38048-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="38048-110">EDI Engine</span></span>|  
|<span data-ttu-id="38048-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="38048-111">Symbolic Name</span></span>|<span data-ttu-id="38048-112">X12Ta1InvalidReceiverIdDescription</span><span class="sxs-lookup"><span data-stu-id="38048-112">X12Ta1InvalidReceiverIdDescription</span></span>|  
|<span data-ttu-id="38048-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="38048-113">Message Text</span></span>|<span data-ttu-id="38048-114">Id de destinataire non valide</span><span class="sxs-lookup"><span data-stu-id="38048-114">Invalid ReceiverId</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="38048-115">Explication</span><span class="sxs-lookup"><span data-stu-id="38048-115">Explanation</span></span>  
 <span data-ttu-id="38048-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas réussi à traiter l'échange entrant, car l'ID de destinataire dans le champ ISA08 ou l'identification du destinataire dans le champ UNB3.1 n'est pas conforme au type de données et au nombre de chiffres qui ont été définis par le schéma de service (X12ServiceSchema ou EdifactServiceSchema dans le fichier BaseArtifacts.dll).</span><span class="sxs-lookup"><span data-stu-id="38048-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Receiver ID in the ISA08 field or the Recipient Identification in the UNB3.1 field did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="38048-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="38048-117">User Action</span></span>  
 <span data-ttu-id="38048-118">Pour résoudre cette erreur, veillez à ce que le champ ISA08 soit défini sur le type de données X12_AN et comporte 15 caractères (avec ou sans espace de fin) ou que le champ UNB3.1 soit défini sur le type de données EDIFACT_AN et comporte entre 1 et 35 caractères.</span><span class="sxs-lookup"><span data-stu-id="38048-118">To resolve this error, make sure that the ISA08 field is of the X12_AN data type and is 15 characters long (with or without trailing spaces) or that the UNB3.1 field is of the EDIFACT_AN data type and is between 1 and 35 characters.</span></span> <span data-ttu-id="38048-119">Demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="38048-119">Have the interchange resent.</span></span>