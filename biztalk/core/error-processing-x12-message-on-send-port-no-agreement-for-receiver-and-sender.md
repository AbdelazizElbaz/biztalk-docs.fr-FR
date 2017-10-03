---
title: "Une erreur s’est produite lors du traitement de X12 message sur le port d’envoi : aucun accord pour les paires qualificateur de l’identificateur expéditeur et destinataire et aucun tiers ayant le nom | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fdf445e8-51a3-44fb-aa71-e0b0ab9c428f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acb05b7795c48c161ab50ab5e79d18a225306fd2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-failure-occurred-in-processing-x12-message-on-send-port-no-agreement-for-receiver-and-sender-identifier-qualifier-pairs-and-no-party-with-name"></a><span data-ttu-id="82a3f-102">Une erreur s’est produite lors du traitement de X12 message sur le port d’envoi : aucun accord pour les paires qualificateur de l’identificateur expéditeur et destinataire et aucun tiers ayant le nom</span><span class="sxs-lookup"><span data-stu-id="82a3f-102">A failure occurred in processing X12 message on send port: No agreement for receiver and sender identifier-qualifier pairs and no party with name</span></span>
## <a name="details"></a><span data-ttu-id="82a3f-103">Détails</span><span class="sxs-lookup"><span data-stu-id="82a3f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82a3f-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="82a3f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="82a3f-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="82a3f-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="82a3f-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="82a3f-106">Event ID</span></span>|-|  
|<span data-ttu-id="82a3f-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="82a3f-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="82a3f-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="82a3f-108"> EDI</span></span>|  
|<span data-ttu-id="82a3f-109">Composant</span><span class="sxs-lookup"><span data-stu-id="82a3f-109">Component</span></span>|<span data-ttu-id="82a3f-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="82a3f-110">EDI Engine</span></span>|  
|<span data-ttu-id="82a3f-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="82a3f-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="82a3f-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="82a3f-112">Message Text</span></span>|<span data-ttu-id="82a3f-113">Un échec s'est produit lors du traitement du message X12 sur le port d'envoi {0}.</span><span class="sxs-lookup"><span data-stu-id="82a3f-113">A failure occurred in processing X12 message on send port {0}.</span></span> <span data-ttu-id="82a3f-114">Il n’existe aucun accord pour les paires qualificateur/identificateur expéditeur et destinataire pour {{1}, {2}, {3}, {4}.</span><span class="sxs-lookup"><span data-stu-id="82a3f-114">No agreement exists for receiver and sender identifier/qualifier pairs for {1}, {2}, {3}, {4}.</span></span> <span data-ttu-id="82a3f-115">Il n’existe aucun tiers avec {5} de nom.</span><span class="sxs-lookup"><span data-stu-id="82a3f-115">No Party exists with name {5}.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="82a3f-116">Explication</span><span class="sxs-lookup"><span data-stu-id="82a3f-116">Explanation</span></span>  
 <span data-ttu-id="82a3f-117">Cet événement d’erreur/avertissement/Information indique BizTalk Server n’a pas pu résoudre le tiers pour l’échange EDIFACT, car BizTalk Server n’a pas pu correspondent promu propriétés qualificateur et identificateur de l’expéditeur et promues du qualificateur du récepteur et propriétés de l’identificateur, avec les valeurs correspondantes pour un tiers.</span><span class="sxs-lookup"><span data-stu-id="82a3f-117">This Error/Warning/Information event indicates BizTalk Server was unable to resolve the party for the EDIFACT interchange because BizTalk Server was unable to match promoted sender qualifier and identifier properties, and promoted receiver qualifier and identifier properties, with the corresponding values for a party.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="82a3f-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="82a3f-118">User Action</span></span>  
 <span data-ttu-id="82a3f-119">Pour résoudre cette erreur, dans la boîte de dialogue Propriétés EDI, dans la page Définition des segments ISA associée au tiers, assurez-vous que le qualificateur et l'identificateur de l'expéditeur (ISA5 et ISA6) et que le qualificateur et l'identificateur du récepteur (ISA7 et ISA8) qui y sont définis correspondent aux propriétés promues dans le contexte de l'échange.</span><span class="sxs-lookup"><span data-stu-id="82a3f-119">To resolve this error, ensure that the sender qualifier and identifier (ISA5 and ISA6) and receiver qualifier and identifier (ISA7 and ISA8) defined in the party's ISA Segment Definition page of the EDI Properties dialog box match the corresponding promoted properties in the context of the interchange.</span></span>