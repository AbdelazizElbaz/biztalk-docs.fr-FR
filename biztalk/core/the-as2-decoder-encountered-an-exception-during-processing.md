---
title: "Le décodeur AS2 a rencontré une exception lors du traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5f16d2e-e83c-4e2c-84be-41b5ed012dce
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2826a938a4f081b8c5895da809e9f16966e25834
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-as2-decoder-encountered-an-exception-during-processing"></a><span data-ttu-id="f2753-102">Le décodeur AS2 a rencontré une exception durant le traitement</span><span class="sxs-lookup"><span data-stu-id="f2753-102">The AS2 Decoder encountered an exception during processing</span></span>
## <a name="details"></a><span data-ttu-id="f2753-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f2753-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2753-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f2753-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f2753-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f2753-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f2753-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f2753-106">Event ID</span></span>|-|  
|<span data-ttu-id="f2753-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f2753-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f2753-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f2753-108"> EDI</span></span>|  
|<span data-ttu-id="f2753-109">Composant</span><span class="sxs-lookup"><span data-stu-id="f2753-109">Component</span></span>|<span data-ttu-id="f2753-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="f2753-110">AS2 Engine</span></span>|  
|<span data-ttu-id="f2753-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f2753-111">Symbolic Name</span></span>|<span data-ttu-id="f2753-112">AS2DecoderExceptionEncounteredDuringProcessing</span><span class="sxs-lookup"><span data-stu-id="f2753-112">AS2DecoderExceptionEncounteredDuringProcessing</span></span>|  
|<span data-ttu-id="f2753-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f2753-113">Message Text</span></span>|<span data-ttu-id="f2753-114">Le décodeur AS2 a rencontré une exception durant le traitement.</span><span class="sxs-lookup"><span data-stu-id="f2753-114">The AS2 Decoder encountered an exception during processing.</span></span>  <span data-ttu-id="f2753-115">Détails du message et de l’exception sont les suivants : AS2-à partir de : « {0} » AS2-pour : « \ {1\\} » MessageID : « \ {2\} » MessageType : « {3} » (Exception) : « \ {4\} »</span><span class="sxs-lookup"><span data-stu-id="f2753-115">Details of the message and exception are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" MessageType: "{3}" Exception:"{4}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f2753-116">Explication</span><span class="sxs-lookup"><span data-stu-id="f2753-116">Explanation</span></span>  
 <span data-ttu-id="f2753-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter le message AS2 entrant en raison d'un problème avec le décodeur AS2.</span><span class="sxs-lookup"><span data-stu-id="f2753-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming AS2 message because of an issue with the AS2 Decoder.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f2753-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f2753-118">User Action</span></span>  
 <span data-ttu-id="f2753-119">Pour résoudre cette erreur, déterminez la nature de la condition d'erreur en vérifiant le code d'erreur AS2.</span><span class="sxs-lookup"><span data-stu-id="f2753-119">To resolve this error, determine the nature of the error condition by checking the AS2 error code.</span></span> <span data-ttu-id="f2753-120">Pour plus d'informations sur les codes d'erreur AS2, consultez la rubrique « Codes d'erreur AS2 » du fichier d'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2753-120">For more information on AS2 error codes, see the "AS2 Error Codes" topic in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] help file.</span></span>