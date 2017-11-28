---
title: "Un message AS2 vide a été reçu et interrompu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 349f7134-d039-44ab-b2b3-d378d38dfd38
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90c8221c7e0bd5b297b33118b8672fbe55612244
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-empty-as2-message-was-received-and-suspended"></a><span data-ttu-id="77824-102">Un message AS2 vide a été reçu et interrompu.</span><span class="sxs-lookup"><span data-stu-id="77824-102">An empty AS2 message was received and suspended</span></span>
## <a name="details"></a><span data-ttu-id="77824-103">Détails</span><span class="sxs-lookup"><span data-stu-id="77824-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77824-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="77824-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="77824-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="77824-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="77824-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="77824-106">Event ID</span></span>|-|  
|<span data-ttu-id="77824-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="77824-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="77824-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="77824-108"> EDI</span></span>|  
|<span data-ttu-id="77824-109">Composant</span><span class="sxs-lookup"><span data-stu-id="77824-109">Component</span></span>|<span data-ttu-id="77824-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="77824-110">AS2 Engine</span></span>|  
|<span data-ttu-id="77824-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="77824-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="77824-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="77824-112">Message Text</span></span>|<span data-ttu-id="77824-113">Un message AS2 vide a été reçu.</span><span class="sxs-lookup"><span data-stu-id="77824-113">An empty AS2 message was received.</span></span>  <span data-ttu-id="77824-114">Le message sera interrompu.</span><span class="sxs-lookup"><span data-stu-id="77824-114">The message will be suspended.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="77824-115">Explication</span><span class="sxs-lookup"><span data-stu-id="77824-115">Explanation</span></span>  
 <span data-ttu-id="77824-116">Cet événement de type erreur/avertissement/information indique que BizTalk Server n'a pas pu traiter le message AS2 entrant, car celui-ci était dépourvu de corps.</span><span class="sxs-lookup"><span data-stu-id="77824-116">This Error/Warning/Information event indicates BizTalk Server could not process the incoming AS2 message because the message does not contain a body.</span></span> <span data-ttu-id="77824-117">Le corps du message doit être séparé des en-têtes par deux retours chariot ou deux sauts de ligne.</span><span class="sxs-lookup"><span data-stu-id="77824-117">The body must be separated from the headers by two carriage return/line feeds.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="77824-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="77824-118">User Action</span></span>  
 <span data-ttu-id="77824-119">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="77824-119">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="77824-120">Assurez-vous que le tiers expéditeur ajoute un corps (séparé des en-têtes par deux retours chariot ou deux sauts de ligne) au message AS2 avant de l'envoyer.</span><span class="sxs-lookup"><span data-stu-id="77824-120">Ensure the sending party adds a body (separated from the headers by two carriage return/line feeds) to the AS2 message before sending it.</span></span>