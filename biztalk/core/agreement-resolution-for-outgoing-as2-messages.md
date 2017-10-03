---
title: "Résolution de l’accord pour les Messages AS2 sortants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 578d7565-534c-4c13-b473-975f347f3a9b
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5cf35a15ca7d0e27ba0c2bf1a05781d6512e0bef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="agreement-resolution-for-outgoing-as2-messages"></a><span data-ttu-id="bec8f-102">Résolution de l'accord pour les messages AS2 sortants</span><span class="sxs-lookup"><span data-stu-id="bec8f-102">Agreement Resolution for Outgoing AS2 Messages</span></span>
<span data-ttu-id="bec8f-103">Lorsqu'un pipeline d'envoi AS2 traite un message sortant encodé en EDIINT/AS2 via le transport HTTP/HTTPS, il détermine l'accord correspondant au message.</span><span class="sxs-lookup"><span data-stu-id="bec8f-103">When an AS2 send pipeline processes an outgoing EDIINT/AS2-encoded message over HTTP/HTTPS transport, it determines the agreement that the message will resolve to.</span></span> <span data-ttu-id="bec8f-104">Il utilise ensuite ces propriétés d'accord pour traiter le message sortant.</span><span class="sxs-lookup"><span data-stu-id="bec8f-104">It will then use those agreement properties to process the outgoing message.</span></span> <span data-ttu-id="bec8f-105">Le pipeline d'envoi utilise les critères suivants pour déterminer l'accord (dans l'ordre de priorité) :</span><span class="sxs-lookup"><span data-stu-id="bec8f-105">The send pipeline will use the following criteria to determine the agreement (in order of priority):</span></span>  
  
1.  <span data-ttu-id="bec8f-106">Le pipeline d'envoi tente d'établir une correspondance entre les propriétés de contexte AS2From et AS2To et les valeurs AS2From et AS2To spécifiées dans les propriétés de l'accord.</span><span class="sxs-lookup"><span data-stu-id="bec8f-106">The send pipeline attempts to match the AS2From and AS2To context properties with the values of AS2From and AS2To specified as part of the agreement properties.</span></span>  
  
2.  <span data-ttu-id="bec8f-107">Si l’étape précédente échoue, le pipeline d’envoi tente de correspondre à la propriété de contexte AS2To du message sortant avec la valeur de la propriété AS2To, qui est définie en tant que programme de résolution d’accord supplémentaire dans le **identificateurs** onglet d’accord Propriétés.</span><span class="sxs-lookup"><span data-stu-id="bec8f-107">If the previous step fails, the send pipeline will attempt to match the AS2To context property of the outbound message with the value of AS2To property, which is set as additional agreement resolver in the **Identifiers** tab of agreement properties.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bec8f-108"> n'écrit pas la propriété AS2To dans le contexte.</span><span class="sxs-lookup"><span data-stu-id="bec8f-108"> does not write the AS2To property to the context.</span></span> <span data-ttu-id="bec8f-109">Si vous souhaitez que la résolution de l'accord se déroule sur la propriété de contexte AS2To, vous devez intégrer une orchestration personnalisée ou un composant de pipeline personnalisé chargé d'exécuter cette opération.</span><span class="sxs-lookup"><span data-stu-id="bec8f-109">If you want to perform agreement resolution on the AS2To context property, you will have to incorporate a custom orchestration or a custom pipeline component to do so.</span></span> <span data-ttu-id="bec8f-110">Pour plus d’informations, consultez [l’écriture des propriétés de contexte AS2 pour la résolution du tiers sortant](../core/writing-as2-context-properties-for-outbound-party-resolution.md).</span><span class="sxs-lookup"><span data-stu-id="bec8f-110">For more information, see [Writing AS2 Context Properties for Outbound Party Resolution](../core/writing-as2-context-properties-for-outbound-party-resolution.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bec8f-111">Lorsque vous utilisez un port d'envoi dynamique, la propriété AS2To doit être écrite dans le contexte pour permettre la résolution de l'accord.</span><span class="sxs-lookup"><span data-stu-id="bec8f-111">When you are using a dynamic send port, the AS2To property must be written to the context for agreement resolution.</span></span>  
  
3.  <span data-ttu-id="bec8f-112">En cas d'échec de l'étape précédente, le port d'envoi tente d'établir une correspondance entre le port d'envoi associé à un accord et le port d'envoi abonné au message.</span><span class="sxs-lookup"><span data-stu-id="bec8f-112">If the previous step fails, the send pipeline will attempt to match the send port that is associated with an agreement with the send port that subscribed to the message.</span></span> <span data-ttu-id="bec8f-113">Le port d’envoi est associé à l’accord dans le **Ports d’envoi** page de l’accord AS2 unidirectionnel de la **propriétés de l’accord** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bec8f-113">The send port is associated with the agreement in the **Send Ports** page of the one-way AS2 agreement of the **Agreement Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bec8f-114">Contrairement au traitement EDI, il n'existe pas de propriétés AS2 de secours que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut utiliser s'il ne peut pas déterminer l'accord.</span><span class="sxs-lookup"><span data-stu-id="bec8f-114">Unlike in EDI processing, there are no fallback AS2 properties that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can use if it cannot determine the agreement.</span></span> <span data-ttu-id="bec8f-115">En revanche, il existe un accord par défaut utilisé pour envoyer un MDN.</span><span class="sxs-lookup"><span data-stu-id="bec8f-115">There is, however, a default agreement used to send an MDN.</span></span> <span data-ttu-id="bec8f-116">En outre, ni le port d'envoi ni la propriété de contexte Http.UserHttpHeaders ne sont utilisés pour résoudre l'accord pour un MDN.</span><span class="sxs-lookup"><span data-stu-id="bec8f-116">In addition, neither the send port nor the Http.UserHttpHeaders context property is used to resolve the agreement for an MDN.</span></span> <span data-ttu-id="bec8f-117">Pour plus d’informations, consultez la section « Résolution de contrat pour un MDN » de [envoyer un MDN sortant](../core/sending-an-outgoing-mdn.md).</span><span class="sxs-lookup"><span data-stu-id="bec8f-117">For more information, see the "Agreement Resolution for an MDN" section of [Sending an Outgoing MDN](../core/sending-an-outgoing-mdn.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bec8f-118">Si AS2-pour la propriété d’accord dans le **identificateurs** page de l’accord AS2 unidirectionnel de la **propriétés de l’accord** boîte de dialogue a la valeur par défaut pour un nom de tiers anglais et la valeur AS2-à l’en-tête de AS2 message doit avoir un nom non anglais, puis la correspondance ne sera pas trouvée.</span><span class="sxs-lookup"><span data-stu-id="bec8f-118">If the AS2-To agreement property in the **Identifiers** page of the one-way AS2 agreement of the **Agreement Properties** dialog box is set by default to an English party name, and the value in the AS2-To header of the AS2 message is set to a non-English name, then the match will not be found.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bec8f-119">Lorsque vous envoyez EDI via AS2, vous devez utiliser des accords distincts pour EDI et AS2.</span><span class="sxs-lookup"><span data-stu-id="bec8f-119">When sending EDI over AS2, you are required to use separate agreements for both EDI and AS2.</span></span>  
  
 <span data-ttu-id="bec8f-120">Pour plus d’informations sur le processus d’envoi, consultez [génération d’un Message AS2 sortant](../core/generating-an-outgoing-as2-message.md).</span><span class="sxs-lookup"><span data-stu-id="bec8f-120">For more details on the send process, see [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec8f-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bec8f-121">See Also</span></span>  
 [<span data-ttu-id="bec8f-122">Envoi des Messages AS2 par BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="bec8f-122">How BizTalk Server Sends AS2 Messages</span></span>](../core/how-biztalk-server-sends-as2-messages.md)