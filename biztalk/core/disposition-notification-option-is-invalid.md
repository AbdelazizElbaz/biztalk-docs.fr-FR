---
title: "Disposition-Notification-Option n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1b807a8-eec9-45a5-83cc-075c91b4bc9e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72221c98dfcac42f735f63a1ce01a7c26bc45387
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="disposition-notification-option-is-invalid"></a><span data-ttu-id="dc9c5-102">Disposition-Notification-Option non valide</span><span class="sxs-lookup"><span data-stu-id="dc9c5-102">Disposition-Notification-Option is invalid</span></span>
## <a name="details"></a><span data-ttu-id="dc9c5-103">Détails</span><span class="sxs-lookup"><span data-stu-id="dc9c5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dc9c5-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="dc9c5-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="dc9c5-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="dc9c5-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="dc9c5-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="dc9c5-106">Event ID</span></span>|-|  
|<span data-ttu-id="dc9c5-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="dc9c5-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="dc9c5-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="dc9c5-108"> EDI</span></span>|  
|<span data-ttu-id="dc9c5-109">Composant</span><span class="sxs-lookup"><span data-stu-id="dc9c5-109">Component</span></span>|<span data-ttu-id="dc9c5-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="dc9c5-110">AS2 Engine</span></span>|  
|<span data-ttu-id="dc9c5-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="dc9c5-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="dc9c5-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="dc9c5-112">Message Text</span></span>|<span data-ttu-id="dc9c5-113">Valeur de disposition-Notification-Option : « {0} » n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="dc9c5-113">Disposition-Notification-Option value: "{0}" is invalid.</span></span> <span data-ttu-id="dc9c5-114">{1}</span><span class="sxs-lookup"><span data-stu-id="dc9c5-114">{1}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dc9c5-115">Explication</span><span class="sxs-lookup"><span data-stu-id="dc9c5-115">Explanation</span></span>  
 <span data-ttu-id="dc9c5-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception AS2 n'a pas pu générer le MDN car l'en-tête Disposition-Notification-Option est non valide.</span><span class="sxs-lookup"><span data-stu-id="dc9c5-116">This Error/Warning/Information event indicates that the AS2 receive pipeline could not generate the MDN because the Disposition-Notification-Option header was invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dc9c5-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="dc9c5-117">User Action</span></span>  
 <span data-ttu-id="dc9c5-118">Pour résoudre cette erreur, assurez-vous que l'en-tête Disposition-Notification-Option du message AS2 est conforme à la syntaxe décrite dans la norme RFC 4130, « Échange de données d'entreprise MIME pair à pair sécurisé via HTTP, AS2 (Applicability Statement 2) ».</span><span class="sxs-lookup"><span data-stu-id="dc9c5-118">To resolve this error, make sure that the Disposition-Notification-Option header in the AS2 message conforms to the syntax described in RFC 4130, "MIME-Based Secure Peer-to-Peer Business Data Interchange Using HTTP, Applicability Statement 2 (AS2").</span></span> <span data-ttu-id="dc9c5-119">Vérifiez que l'en-tête Signed-Receipt-Protocol est défini sur « facultatif » ou « pcks7-signature », et que l'en-tête Signed-Receipt-MICAlg est défini sur « facultatif »,  « MD5 » ou « SHA1 ».</span><span class="sxs-lookup"><span data-stu-id="dc9c5-119">Ensure that the Signed-Receipt-Protocol header is set to "optional" or "pcks7-signature", and that the Signed-Receipt-MICAlg header is set to "optional", "MD5", or "SHA1".</span></span> <span data-ttu-id="dc9c5-120">(Ces deux en-têtes sont inclus dans l'en-tête Disposition-Notification-Option.)</span><span class="sxs-lookup"><span data-stu-id="dc9c5-120">(Both of these headers are included in the Disposition-Notification-Option header.)</span></span>