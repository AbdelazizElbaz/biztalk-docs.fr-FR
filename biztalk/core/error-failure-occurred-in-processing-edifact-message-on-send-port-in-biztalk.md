---
title: "Une erreur s’est produite lors du traitement du message Edifact sur le port d’envoi : aucun accord pour les paires qualificateur de l’identificateur expéditeur et destinataire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cffc4705-164f-4779-8f04-c6a2a7f1bbda
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4cb2b0637c54f6fdd13dc5f0d17d71817ce4453
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-failure-occurred-in-processing-edifact-message-on-send-port-no-agreement-for-receiver-and-sender-identifier-qualifier-pairs"></a><span data-ttu-id="6cbed-102">Une erreur s’est produite lors du traitement du message Edifact sur le port d’envoi : aucun accord pour les paires qualificateur de l’identificateur expéditeur et destinataire</span><span class="sxs-lookup"><span data-stu-id="6cbed-102">A failure occurred in processing Edifact message on send port: No agreement for receiver and sender identifier-qualifier pairs</span></span>
## <a name="details"></a><span data-ttu-id="6cbed-103">Détails</span><span class="sxs-lookup"><span data-stu-id="6cbed-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6cbed-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="6cbed-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6cbed-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="6cbed-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="6cbed-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6cbed-106">Event ID</span></span>|-|  
|<span data-ttu-id="6cbed-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="6cbed-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6cbed-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="6cbed-108"> EDI</span></span>|  
|<span data-ttu-id="6cbed-109">Composant</span><span class="sxs-lookup"><span data-stu-id="6cbed-109">Component</span></span>|<span data-ttu-id="6cbed-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="6cbed-110">EDI Engine</span></span>|  
|<span data-ttu-id="6cbed-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="6cbed-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="6cbed-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="6cbed-112">Message Text</span></span>|<span data-ttu-id="6cbed-113">Un échec s'est produit lors du traitement du message EDIFACT sur le port d'envoi {0}.</span><span class="sxs-lookup"><span data-stu-id="6cbed-113">A failure occurred in processing Edifact message on send port {0}.</span></span> <span data-ttu-id="6cbed-114">Il n’existe aucun accord pour les paires qualificateur/identificateur expéditeur et destinataire pour {{1}, {2}, {3}, {4}.</span><span class="sxs-lookup"><span data-stu-id="6cbed-114">No agreement exists for receiver and sender identifier/qualifier pairs for {1}, {2}, {3}, {4}.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6cbed-115">Explication</span><span class="sxs-lookup"><span data-stu-id="6cbed-115">Explanation</span></span>  
 <span data-ttu-id="6cbed-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas réussi à résoudre le tiers pour l'échange EDIFACT, car il n'a pas réussi à établir de correspondance entre les propriétés promues du qualificateur et de l'identificateur de l'expéditeur, ainsi qu'entre celles du qualificateur et de l'identificateur du récepteur, et les valeurs correspondantes d'un tiers.</span><span class="sxs-lookup"><span data-stu-id="6cbed-116">This Error/Warning/Information event indicates BizTalk Server was unable to resolve the party for the EDIFACT interchange because it was unable to match promoted sender qualifier and identifier properties, and promoted receiver qualifier and identifier properties, with the corresponding values for a party.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6cbed-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6cbed-117">User Action</span></span>  
 <span data-ttu-id="6cbed-118">Pour résoudre cette erreur, dans la boîte de dialogue Propriétés EDI, dans la page Définition des segments UNB associée au tiers, assurez-vous que le qualificateur et l'identificateur de l'expéditeur (UNB2.1 et UNB2.2) et que le qualificateur et l'identificateur du récepteur (UNB3.1 et UNB3.2) qui y sont définis correspondent aux propriétés promues dans le contexte de l'échange.</span><span class="sxs-lookup"><span data-stu-id="6cbed-118">To resolve this error, ensure that the sender qualifier and identifier (UNB2.1 and UNB2.2) and receiver qualifier and identifier (UNB3.1 and UNB3.2) defined in the party's UNB Segment Definition page of the EDI Properties dialog box match the corresponding promoted properties in the context of the interchange.</span></span>