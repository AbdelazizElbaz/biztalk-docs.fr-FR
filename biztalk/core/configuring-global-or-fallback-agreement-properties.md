---
title: "Configuration des propriétés de l’accord Global ou de secours | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c375d03-6f22-4a67-9eac-d8896de2f7ee
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0eb693a17cad17eadaf0d005d12075dde30daa33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-global-or-fallback-agreement-properties"></a><span data-ttu-id="298a6-102">Configuration des propriétés d'un accord global ou de secours</span><span class="sxs-lookup"><span data-stu-id="298a6-102">Configuring Global or Fallback Agreement Properties</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="298a6-103"> exploite les propriétés d'accord de secours pour traiter un message lorsqu'il ne détecte aucun accord correspondant à un échange.</span><span class="sxs-lookup"><span data-stu-id="298a6-103"> uses fallback agreement properties to process a message when it does not discover an agreement to resolve to for an interchange.</span></span> <span data-ttu-id="298a6-104">Ces propriétés restent inexploitées lorsque l'accord est connu et ne s'appliquent à aucun accord.</span><span class="sxs-lookup"><span data-stu-id="298a6-104">Fallback agreement properties are not used when the agreement is known, and do not apply to any or all agreements.</span></span>  
  
 <span data-ttu-id="298a6-105">Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message, il tente de trouver une correspondance entre les informations d'accord de l'expéditeur et les informations de l'expéditeur se trouvant dans le message.</span><span class="sxs-lookup"><span data-stu-id="298a6-105">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives a message, it attempts to match the sender information for an agreement with the sender information in the message.</span></span> <span data-ttu-id="298a6-106">Les informations de l'expéditeur se trouvent dans les éléments de données ISA5 et ISA6 d'un message X12 et dans les éléments de données UNB2.1 et UNB2.2 d'un message EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="298a6-106">The sender information is in the ISA5 and ISA6 data elements for X12 message, and the UNB2.1 and UNB 2.2 data elements for EDIFACT.</span></span> <span data-ttu-id="298a6-107">Les informations de contrat sont dans les onglets identificateur dans l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="298a6-107">The agreement information is in the Identifier tabs in the one-way agreement tab of the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="298a6-108">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne détecte pas l’accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les propriétés de l’accord de secours pour déterminer l’espace de noms, de traiter le message et d’envoyer les accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="298a6-108">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not discover the agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the fallback agreement properties to determine the namespace, process the message, and send any acknowledgments.</span></span>  
  
 <span data-ttu-id="298a6-109">Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie un message, le pipeline de réception EDI détermine l'accord correspondant à celui-ci en recherchant une correspondance entre le port d'envoi s'abonnant au message XML dans MessageBox et le port d'envoi associé à l'accord.</span><span class="sxs-lookup"><span data-stu-id="298a6-109">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends a message, the EDI send pipeline determines the agreement that the message resolves to by matching the send port that subscribes to the XML message in the MessageBox, with the send port associated with the agreement.</span></span> <span data-ttu-id="298a6-110">Si le port d'envoi n'est associé à aucun accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fait appel aux propriétés d'accord de secours pour traiter l'envoi du message.</span><span class="sxs-lookup"><span data-stu-id="298a6-110">If the send port is not associated with an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the fallback agreement properties to process the message for sending.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="298a6-111">L'association des ports d'envoi ne représente qu'une méthode de résolution d'accord parmi d'autres.</span><span class="sxs-lookup"><span data-stu-id="298a6-111">Send port association is only one way of doing agreement resolution.</span></span> <span data-ttu-id="298a6-112">Pour plus d’informations sur la résolution de l’accord pour les messages sortants, consultez [résolution de l’accord et détermination du schéma pour les Messages EDI sortants](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).</span><span class="sxs-lookup"><span data-stu-id="298a6-112">For more information about agreement resolution for outgoing messages, see [Agreement Resolution and Schema Determination for Outgoing EDI Messages](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="298a6-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="298a6-113">In This Section</span></span>  
  
-   [<span data-ttu-id="298a6-114">Configuration X12 propriétés de l’accord de secours</span><span class="sxs-lookup"><span data-stu-id="298a6-114">Configuring X12 Fallback Agreement Properties</span></span>](../core/configuring-x12-fallback-agreement-properties.md)  
  
-   [<span data-ttu-id="298a6-115">Configuration des propriétés d’accord de secours EDIFACT</span><span class="sxs-lookup"><span data-stu-id="298a6-115">Configuring EDIFACT Fallback Agreement Properties</span></span>](../core/configuring-edifact-fallback-agreement-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="298a6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="298a6-116">See Also</span></span>  
 [<span data-ttu-id="298a6-117">Le rôle des accords dans le traitement EDI</span><span class="sxs-lookup"><span data-stu-id="298a6-117">The Role of Agreements in EDI Processing</span></span>](../core/the-role-of-agreements-in-edi-processing.md)