---
title: "Impossible d’accéder à l’accord à l’aide de destinataire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 470325f4-abc4-40bb-9109-9ffc73b496df
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f41b126ca0ebb96716f21381d2e1681ea59bd414
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-access-agreement-using-receiver-identity"></a><span data-ttu-id="c730f-102">Impossible d'accéder à l'accord avec l'id de destinataire</span><span class="sxs-lookup"><span data-stu-id="c730f-102">Unable to access agreement using receiver identity</span></span>
## <a name="details"></a><span data-ttu-id="c730f-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c730f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c730f-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c730f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c730f-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c730f-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c730f-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c730f-106">Event ID</span></span>|-|  
|<span data-ttu-id="c730f-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c730f-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c730f-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c730f-108"> EDI</span></span>|  
|<span data-ttu-id="c730f-109">Composant</span><span class="sxs-lookup"><span data-stu-id="c730f-109">Component</span></span>|<span data-ttu-id="c730f-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="c730f-110">AS2 Engine</span></span>|  
|<span data-ttu-id="c730f-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c730f-111">Symbolic Name</span></span>|<span data-ttu-id="c730f-112">UnableToLocateAS2PartyByPartyNameError</span><span class="sxs-lookup"><span data-stu-id="c730f-112">UnableToLocateAS2PartyByPartyNameError</span></span>|  
|<span data-ttu-id="c730f-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c730f-113">Message Text</span></span>|<span data-ttu-id="c730f-114">Impossible d’accéder à l’accord à l’aide de destinataire : {0}</span><span class="sxs-lookup"><span data-stu-id="c730f-114">Unable to access agreement using receiver identity: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c730f-115">Explication</span><span class="sxs-lookup"><span data-stu-id="c730f-115">Explanation</span></span>  
 <span data-ttu-id="c730f-116">Cette erreur indique que le pipeline d'envoi n'a pas pu déterminer le tiers pour un message AS2 sortant, car il n'est pas parvenu à mettre en correspondance la propriété de contexte AS2To du message sortant ou la propriété AS2To dans la propriété de contexte Http.UserHttpHeaders avec le nom du tiers dans la propriété AS2-To de la page Tiers considéré comme récepteur des messages AS2 dans la boîte de dialogue Propriétés AS2.</span><span class="sxs-lookup"><span data-stu-id="c730f-116">This error indicates that the send pipeline could not determine the party for an outgoing AS2 message because it could not match the AS2To context property of the outbound message or the AS2To property in the Http.UserHttpHeaders context property with the name of the party in the AS2-To property in the Party as AS2 Message Receiver page of the AS2 Properties dialog box.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c730f-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c730f-117">User Action</span></span>  
 <span data-ttu-id="c730f-118">Pour résoudre cette erreur, définissez la propriété AS2-To de la page Tiers considéré comme récepteur des messages AS2 dans la boîte de dialogue Propriétés AS2 sur le nom de tiers approprié associé au message AS2 en erreur.</span><span class="sxs-lookup"><span data-stu-id="c730f-118">To resolve this error, set the AS2-To property in the Party as AS2 Message Receiver page of the AS2 Properties dialog box to the appropriate party name associated with the AS2 message that is in error.</span></span>