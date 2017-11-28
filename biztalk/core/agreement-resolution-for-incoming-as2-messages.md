---
title: "Résolution de l’accord pour les Messages AS2 entrants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 746d01af-de6a-4d5d-9433-b0e1a2b41861
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24e5e9795979ddf0a8b8f13fe7ab53bd4e783bd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="agreement-resolution-for-incoming-as2-messages"></a><span data-ttu-id="ff587-102">Résolution de l'accord pour les messages AS2 entrants</span><span class="sxs-lookup"><span data-stu-id="ff587-102">Agreement Resolution for Incoming AS2 Messages</span></span>
<span data-ttu-id="ff587-103">Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message EDIINT/AS2 via le transport HTTP/HTTPS, il tente de déterminer le profil d'entreprise du partenaire commercial qui a envoyé le message.</span><span class="sxs-lookup"><span data-stu-id="ff587-103">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an EDIINT/AS2-encoded message over HTTP/HTTPS transport, it attempts to determine the trading partner’s business profile that sent the message.</span></span> <span data-ttu-id="ff587-104">Pour cela, il tente de réaliser les actions suivantes (dans l'ordre indiqué) :</span><span class="sxs-lookup"><span data-stu-id="ff587-104">It does so by attempting to do the following (in the order shown):</span></span>  
  
1.  <span data-ttu-id="ff587-105">Établir une correspondance entre AS2-à partir de l’en-tête du message entrant avec la valeur de **AS2-de** dans les **identificateurs** page de l’accord AS2 unidirectionnel dans le **Propriétésdel’accord** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ff587-105">Make a match between the AS2-From header in the incoming message with the value for **AS2-From** in the **Identifiers** page of the one-way AS2 agreement in the **Agreement Properties** dialog box.</span></span>  
  
2.  <span data-ttu-id="ff587-106">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peut pas déterminer l'accord, il tente de faire correspondre la propriété de contexte AS2-From définie pour le message entrant avec le nom d'un partenaire commercial.</span><span class="sxs-lookup"><span data-stu-id="ff587-106">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot determine the agreement, it will attempt to match the AS2-From context property that is set for the incoming message with the name of a trading partner.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff587-107">Dans la mesure où l'en-tête AS2-From peut contenir uniquement des caractères ASCII, vous devez vous assurer que le nom de votre partenaire commercial et l'alias AS2-From contiennent eux aussi uniquement des caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="ff587-107">Since the AS2-From header can only contain ASCII characters, you must ensure that your trading partner name and the AS2-From alias also contain only ASCII characters.</span></span> <span data-ttu-id="ff587-108">Si aucune correspondance exacte n'est trouvée, BizTalk ne pourra pas déterminer l'accord par rapport aux en-têtes du message entrant.</span><span class="sxs-lookup"><span data-stu-id="ff587-108">If an exact match does not occur, BizTalk will be unable to determine the agreement based on the incoming message headers.</span></span>  
  
 <span data-ttu-id="ff587-109">Le pipeline de réception AS2 ne traitera le message que si un accord est déterminé.</span><span class="sxs-lookup"><span data-stu-id="ff587-109">The AS2 receive pipeline will process the message only if an agreement is determined.</span></span> <span data-ttu-id="ff587-110">Contrairement au traitement EDI, il n'existe pas de propriétés AS2 de secours que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut utiliser s'il ne peut pas déterminer l'accord.</span><span class="sxs-lookup"><span data-stu-id="ff587-110">Unlike in EDI processing, there are no fallback AS2 properties that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can use if it cannot determine the agreement.</span></span>  
  
 <span data-ttu-id="ff587-111">Une fois que le pipeline a déterminé l’accord, il vérifie le paramètre de la **utilise accord de paramètres pour la validation et MDN au lieu de cela l’en-tête du message** propriété dans le **Validation** page d’AS2 unidirectionnel accord dans le **paramètres de l’accord** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ff587-111">Once the pipeline has determined the agreement, it will check the setting of the **Use agreement settings for validation and MDN instead message header** property in the **Validation** page of the one-way AS2 agreement in the **Agreement Settings** dialog box.</span></span> <span data-ttu-id="ff587-112">Si cette propriété est sélectionnée, le pipeline de réception utilise les propriétés de l'accord pour traiter le message.</span><span class="sxs-lookup"><span data-stu-id="ff587-112">If that property is checked, the receive pipeline will use the agreement properties to process the message.</span></span> <span data-ttu-id="ff587-113">Si la propriété n'est pas sélectionnée, le pipeline de réception utilise les valeurs de l'en-tête AS2 du message pour le traiter.</span><span class="sxs-lookup"><span data-stu-id="ff587-113">If the property is cleared, the receive pipeline will use the values in the AS2 header of the message to process it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff587-114">L'accord AS2 déterminé lors de la résolution de l'accord peut être différent de la charge EDI.</span><span class="sxs-lookup"><span data-stu-id="ff587-114">The AS2 agreement that is determined during agreement resolution may not be the same agreement as the EDI payload.</span></span> <span data-ttu-id="ff587-115">Il n'est pas obligatoire qu'un même accord soit partagé par AS2 et EDI, dans la mesure où l'accord AS2 peut représenter un centre d'échanges qui achemine les documents EDI à partir de plusieurs tiers.</span><span class="sxs-lookup"><span data-stu-id="ff587-115">There is no requirement that AS2 and EDI must share the same agreement, as the AS2 agreement may represent a clearinghouse that routes EDI documents from multiple parties.</span></span>  
  
 <span data-ttu-id="ff587-116">Pour plus d’informations sur le processus de réception, consultez [du traitement d’un Message AS2 entrant](../core/processing-an-incoming-as2-message.md).</span><span class="sxs-lookup"><span data-stu-id="ff587-116">For more details on the receive process, see [Processing an Incoming AS2 Message](../core/processing-an-incoming-as2-message.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff587-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff587-117">See Also</span></span>  
 [<span data-ttu-id="ff587-118">Réception des Messages AS2 par BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="ff587-118">How BizTalk Server Receives AS2 Messages</span></span>](../core/how-biztalk-server-receives-as2-messages.md)