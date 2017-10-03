---
title: "Le décodeur AS2 a échoué lors de la validation de la valeur MIC retournée dans le MDN de traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fe2d76d-b0f1-4118-8483-547c2c9fffb7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90388f27c44314d1c5bc795744366cfc88ed6321
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-as2-decoder-failed-processing-when-validating-the-mic-value-returned-in-the-mdn"></a><span data-ttu-id="a13f6-102">Le traitement du décodeur AS2 a échoué lors de la validation de la valeur MIC retournée dans le MDN.</span><span class="sxs-lookup"><span data-stu-id="a13f6-102">The AS2 Decoder failed processing when validating the MIC value returned in the MDN</span></span>
## <a name="details"></a><span data-ttu-id="a13f6-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a13f6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a13f6-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a13f6-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a13f6-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a13f6-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a13f6-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a13f6-106">Event ID</span></span>|-|  
|<span data-ttu-id="a13f6-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a13f6-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a13f6-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a13f6-108"> EDI</span></span>|  
|<span data-ttu-id="a13f6-109">Composant</span><span class="sxs-lookup"><span data-stu-id="a13f6-109">Component</span></span>|<span data-ttu-id="a13f6-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="a13f6-110">AS2 Engine</span></span>|  
|<span data-ttu-id="a13f6-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a13f6-111">Symbolic Name</span></span>|<span data-ttu-id="a13f6-112">AS2DecoderMdnMicFailureDuringProcessing</span><span class="sxs-lookup"><span data-stu-id="a13f6-112">AS2DecoderMdnMicFailureDuringProcessing</span></span>|  
|<span data-ttu-id="a13f6-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a13f6-113">Message Text</span></span>|<span data-ttu-id="a13f6-114">Le décodeur AS2 a échoué lors de la validation de la valeur MIC retournée dans le MDN de traitement.</span><span class="sxs-lookup"><span data-stu-id="a13f6-114">The AS2 Decoder failed processing when validating the MIC value returned in the MDN.</span></span>  <span data-ttu-id="a13f6-115">Détails du message MDN sont les suivants : AS2-à partir de : « {0} » AS2-pour : « \ {1\\} » MessageID : « \ {2\} » OriginalMessageID : « \ {3\} »</span><span class="sxs-lookup"><span data-stu-id="a13f6-115">Details of the MDN message are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" OriginalMessageID:"{3}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a13f6-116">Explication</span><span class="sxs-lookup"><span data-stu-id="a13f6-116">Explanation</span></span>  
 <span data-ttu-id="a13f6-117">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter le MDN entrant, car la validation du MIC (Message Integrity Check) a échoué.</span><span class="sxs-lookup"><span data-stu-id="a13f6-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming MDN because the MIC (Message Integrity Check) failed validation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a13f6-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a13f6-118">User Action</span></span>  
 <span data-ttu-id="a13f6-119">Pour résoudre cette erreur, vérifiez que l'algorithme utilisé pour générer le MDN (dans l'en-tête Signed-Receipt-MICalg du message d'origine) est le même que celui spécifié dans la propriété Signed-Receipt-MICalg pour le récepteur des messages AS2.</span><span class="sxs-lookup"><span data-stu-id="a13f6-119">To resolve this error, verify that the algorithm used for generating the MDN (in the Signed-Receipt-MICalg header of the original message) is the same as the algorithm specified in the Signed-Receipt-MICalg property for the AS2 Message Receiver.</span></span> <span data-ttu-id="a13f6-120">Les deux doivent être soit SHA1, soit MD5.</span><span class="sxs-lookup"><span data-stu-id="a13f6-120">Both should be either SHA1 or MD5.</span></span> <span data-ttu-id="a13f6-121">Si l'algorithme spécifié est le même, vérifiez que le champ d'extension Received-Content-MIC de la seconde partie du message MDN signé à parties multiples inclut une synthèse MIC valide.</span><span class="sxs-lookup"><span data-stu-id="a13f6-121">If the algorithm specified is the same, verify that Received-Content-MIC extension field in the second part of the multipart signed MDN message includes a valid MIC digest.</span></span> <span data-ttu-id="a13f6-122">Si tel est le cas, déterminez la raison pour laquelle le MDN ne correspond pas à l'échange envoyé.</span><span class="sxs-lookup"><span data-stu-id="a13f6-122">If it does, determine why the MDN does not correspond to the interchange that was sent.</span></span>