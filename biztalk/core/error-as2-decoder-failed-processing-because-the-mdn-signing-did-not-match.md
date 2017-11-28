---
title: "Le décodeur AS2 a échoué car la signature du MDN ne correspondait à notre demande de traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a42d344-fc28-4bc4-9328-46158f15a008
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc0660a64ff0aeb35976ad1aa45a602d8db0913a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-as2-decoder-failed-processing-because-the-mdn-signing-did-not-match-our-request"></a><span data-ttu-id="57cf9-102">Le traitement du décodeur AS2 a échoué car la signature du MDN ne correspondait pas à notre demande</span><span class="sxs-lookup"><span data-stu-id="57cf9-102">The AS2 Decoder failed processing because the MDN signing did not match our request</span></span>
## <a name="details"></a><span data-ttu-id="57cf9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="57cf9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57cf9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="57cf9-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="57cf9-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="57cf9-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="57cf9-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="57cf9-106">Event ID</span></span>|-|  
|<span data-ttu-id="57cf9-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="57cf9-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="57cf9-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="57cf9-108"> EDI</span></span>|  
|<span data-ttu-id="57cf9-109">Composant</span><span class="sxs-lookup"><span data-stu-id="57cf9-109">Component</span></span>|<span data-ttu-id="57cf9-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="57cf9-110">AS2 Engine</span></span>|  
|<span data-ttu-id="57cf9-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="57cf9-111">Symbolic Name</span></span>|<span data-ttu-id="57cf9-112">AS2DecoderMdnSigningMismatchFailureDuringProcessing</span><span class="sxs-lookup"><span data-stu-id="57cf9-112">AS2DecoderMdnSigningMismatchFailureDuringProcessing</span></span>|  
|<span data-ttu-id="57cf9-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="57cf9-113">Message Text</span></span>|<span data-ttu-id="57cf9-114">Le traitement du décodeur AS2 a échoué car la signature du MDN ne correspondait pas à notre demande.</span><span class="sxs-lookup"><span data-stu-id="57cf9-114">The AS2 Decoder failure processing because the MDN signing did not match our request.</span></span>  <span data-ttu-id="57cf9-115">Détails du message MDN sont les suivants : AS2-à partir de : « {0} » AS2-pour : « \ {1\\} » MessageID : « \ {2\} » OriginalMessageID : « \ {3\} »</span><span class="sxs-lookup"><span data-stu-id="57cf9-115">Details of the MDN message are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" OriginalMessageID:"{3}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="57cf9-116">Explication</span><span class="sxs-lookup"><span data-stu-id="57cf9-116">Explanation</span></span>  
 <span data-ttu-id="57cf9-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter le MDN entrant, soit parce que ce dernier était signé par erreur, soit parce qu'il n'était pas signé alors qu'il aurait dû l'être.</span><span class="sxs-lookup"><span data-stu-id="57cf9-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming MDN either because the MDN was signed, but signing wasn't requested for the MDN, or the MDN was unsigned, but signing was requested for the MDN.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="57cf9-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="57cf9-118">User Action</span></span>  
 <span data-ttu-id="57cf9-119">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="57cf9-119">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="57cf9-120">Modifiez la demande de signature pour que le MDN corresponde à la demande.</span><span class="sxs-lookup"><span data-stu-id="57cf9-120">Change the signature request for the MDN to match the request.</span></span> <span data-ttu-id="57cf9-121">Pour ce faire, ouvrez la page Tiers considéré comme récepteur des messages AS2 de la boîte de dialogue Propriétés AS2, activez la propriété « Exiger le MDN » et activez ou désactivez la propriété « Exiger le MDN signé ».</span><span class="sxs-lookup"><span data-stu-id="57cf9-121">To do so, open the Party as AS2 Message Receiver page of the AS2 Properties dialog box, and with the "Request MDN" property selected, either select or clear the "Request signed MDN" property.</span></span>  
  
2.  <span data-ttu-id="57cf9-122">Contactez le destinataire du message AS2 d'origine pour déterminer si les MDN doivent être signés ou non.</span><span class="sxs-lookup"><span data-stu-id="57cf9-122">Contact the receiver of the original AS2 message to resolve whether MDNs should be signed or not.</span></span>