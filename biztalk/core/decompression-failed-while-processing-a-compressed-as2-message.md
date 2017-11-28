---
title: "Échec de la décompression lors du traitement d'un message AS2 compressé. | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5246ee97-cc60-4878-9447-de870c0f4c34
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4121fc3598913f4c3edab52655866c02b5a4fe86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="decompression-failed-while-processing-a-compressed-as2-message"></a><span data-ttu-id="96f64-103">Échec de la décompression lors du traitement d'un message AS2 compressé.</span><span class="sxs-lookup"><span data-stu-id="96f64-103">Decompression failed while processing a compressed AS2 message.</span></span>
## <a name="details"></a><span data-ttu-id="96f64-104">Détails</span><span class="sxs-lookup"><span data-stu-id="96f64-104">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="96f64-105">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="96f64-105">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="96f64-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="96f64-106">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="96f64-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="96f64-107">Event ID</span></span>|-|  
|<span data-ttu-id="96f64-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="96f64-108">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="96f64-109"> EDI</span><span class="sxs-lookup"><span data-stu-id="96f64-109"> EDI</span></span>|  
|<span data-ttu-id="96f64-110">Composant</span><span class="sxs-lookup"><span data-stu-id="96f64-110">Component</span></span>|<span data-ttu-id="96f64-111">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="96f64-111">AS2 Engine</span></span>|  
|<span data-ttu-id="96f64-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="96f64-112">Symbolic Name</span></span>|-|  
|<span data-ttu-id="96f64-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="96f64-113">Message Text</span></span>|<span data-ttu-id="96f64-114">Échec de la décompression lors du traitement d'un message AS2 compressé.</span><span class="sxs-lookup"><span data-stu-id="96f64-114">Decompression failed while processing a compressed AS2 message.</span></span> <span data-ttu-id="96f64-115">Erreur : {0}</span><span class="sxs-lookup"><span data-stu-id="96f64-115">Error: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="96f64-116">Explication</span><span class="sxs-lookup"><span data-stu-id="96f64-116">Explanation</span></span>  
 <span data-ttu-id="96f64-117">Cet événement de type erreur/avertissement/information indique que le composant Décodeur AS2 du pipeline de réception n'a pas pu décompresser le message AS2.</span><span class="sxs-lookup"><span data-stu-id="96f64-117">This Error/Warning/Information event indicates that the AS2 Decoder component of the receive pipeline could not decompress the AS2 message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="96f64-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="96f64-118">User Action</span></span>  
 <span data-ttu-id="96f64-119">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="96f64-119">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="96f64-120">Vérifier que le wrapper de compression dans le message AS2 est valide.</span><span class="sxs-lookup"><span data-stu-id="96f64-120">Verify that the compression wrapper in the AS2 message is valid.</span></span>  
  
-   <span data-ttu-id="96f64-121">Vérifier que la décompression est activée pour BizTalk Server en vérifiant que la propriété « Le message doit être compressé » est activée dans la page Tiers considéré comme expéditeur des messages AS2 de la boîte de dialogue Propriétés AS2 (si la propriété Remplacer les propriétés du message entrant est activée).</span><span class="sxs-lookup"><span data-stu-id="96f64-121">Verify that decompression is enabled for BizTalk Server by verifying that the "Message should be compressed" property is checked on the Party as AS2 Message Sender page of the AS2 Properties dialog box (if the Override inbound message properties property is checked).</span></span>  
  
-   <span data-ttu-id="96f64-122">Consultez la description de l'erreur fournie dans le texte du message d'erreur pour identifier le problème.</span><span class="sxs-lookup"><span data-stu-id="96f64-122">Use the error description provided in the error message text to identify the specific issue.</span></span>