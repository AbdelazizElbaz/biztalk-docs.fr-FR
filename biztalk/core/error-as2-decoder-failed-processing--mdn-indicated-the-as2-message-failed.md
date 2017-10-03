---
title: "Le décodeur AS2 a échoué, car le MDN a indiqué que le traitement des messages a échoué AS2 de traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bce620a-f336-435e-b7c3-3db060f2819d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20454f1c551b6b4828c42e09f0442b83275256ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-as2-decoder-failed-processing-because-the-mdn-indicated-the-as2-message-failed-processing"></a><span data-ttu-id="178e3-102">Le traitement du décodeur AS2 a échoué car le MDN a indiqué que le traitement du message AS2 a échoué.</span><span class="sxs-lookup"><span data-stu-id="178e3-102">The AS2 Decoder failed processing because the MDN indicated the AS2 message failed processing</span></span>
## <a name="details"></a><span data-ttu-id="178e3-103">Détails</span><span class="sxs-lookup"><span data-stu-id="178e3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="178e3-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="178e3-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="178e3-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="178e3-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="178e3-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="178e3-106">Event ID</span></span>|-|  
|<span data-ttu-id="178e3-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="178e3-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="178e3-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="178e3-108"> EDI</span></span>|  
|<span data-ttu-id="178e3-109">Composant</span><span class="sxs-lookup"><span data-stu-id="178e3-109">Component</span></span>|<span data-ttu-id="178e3-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="178e3-110">AS2 Engine</span></span>|  
|<span data-ttu-id="178e3-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="178e3-111">Symbolic Name</span></span>|<span data-ttu-id="178e3-112">AS2DecoderMdnProcessingFailureReturned</span><span class="sxs-lookup"><span data-stu-id="178e3-112">AS2DecoderMdnProcessingFailureReturned</span></span>|  
|<span data-ttu-id="178e3-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="178e3-113">Message Text</span></span>|<span data-ttu-id="178e3-114">Le traitement du décodeur AS2, car le MDN a indiqué que le message AS2 le traitement a échoué.</span><span class="sxs-lookup"><span data-stu-id="178e3-114">The AS2 Decoder failure processing because the MDN indicated the AS2 message failed processing.</span></span>  <span data-ttu-id="178e3-115">Détails du message MDN sont les suivants : AS2-à partir de : « {0} » AS2-pour : « \ {1\\} » MessageID : « \ {2\} » OriginalMessageID : « \ {3\} »</span><span class="sxs-lookup"><span data-stu-id="178e3-115">Details of the MDN message are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" OriginalMessageID:"{3}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="178e3-116">Explication</span><span class="sxs-lookup"><span data-stu-id="178e3-116">Explanation</span></span>  
 <span data-ttu-id="178e3-117">Cet événement de type erreur/avertissement/information indique que la réponse MDN signale que le destinataire du message AS2 original n'a pas pu traiter le message AS2 original.</span><span class="sxs-lookup"><span data-stu-id="178e3-117">This Error/Warning/Information event indicates that the MDN response shows that the receiver of the original AS2 message could not process the original AS2 message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="178e3-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="178e3-118">User Action</span></span>  
 <span data-ttu-id="178e3-119">Pour résoudre cette erreur, contactez le destinataire du message AS2, déterminez la raison de l'échec du traitement à son niveau, réparez le message AS2 original, puis renvoyez-le.</span><span class="sxs-lookup"><span data-stu-id="178e3-119">To resolve this error, contact the receiver of the AS2 message, determine why processing failed at the receiver, fix the original AS2 message, and then resend.</span></span>