---
title: "Activation de la réception de plusieurs échanges dans un seul Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c98bcd2e-495a-49d8-a471-6e23b1e161f9
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec1b282908424100ddfd0363fd6bede9011d53a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-the-receiving-of-multiple-interchanges-in-a-single-message"></a><span data-ttu-id="29111-102">Activation de la réception de plusieurs échanges dans un seul message</span><span class="sxs-lookup"><span data-stu-id="29111-102">Enabling the Receiving of Multiple Interchanges in a Single Message</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="29111-103"> peut traiter un message contenant plusieurs échanges.</span><span class="sxs-lookup"><span data-stu-id="29111-103"> can process a message that contains multiple interchanges.</span></span> <span data-ttu-id="29111-104">Un tel message X12 inclurait plusieurs en-têtes ISA et codes de fin IEA.</span><span class="sxs-lookup"><span data-stu-id="29111-104">For an X12 message, such a message would include multiple ISA headers and IEA trailers.</span></span> <span data-ttu-id="29111-105">Un tel message EDIFACT inclurait quant à lui plusieurs en-têtes UNA/UNB et codes de fin UNZ.</span><span class="sxs-lookup"><span data-stu-id="29111-105">For an EDIFACT message, such a message would include multiple UNA/UNB headers and UNZ trailers.</span></span>  
  
 <span data-ttu-id="29111-106">Pour activer le désassembleur EDI dans le pipeline EdiReceive ou AS2EdiReceive d’analyser plusieurs échanges dans un seul message, vous devez définir le **DetectMID** propriété de pipeline **True**.</span><span class="sxs-lookup"><span data-stu-id="29111-106">To enable the EDI Disassembler in the EdiReceive or AS2EdiReceive pipeline to parse multiple interchanges in a single message, you must set the **DetectMID** pipeline property to **True**.</span></span> <span data-ttu-id="29111-107">(MID signifie Multiple Interchange Disassembling [Désassemblage de plusieurs échanges]). Par défaut, cette propriété est définie sur True.</span><span class="sxs-lookup"><span data-stu-id="29111-107">(MID stands for multiple interchange disassembling.) This property is set to True by default.</span></span>  
  
 <span data-ttu-id="29111-108">Lorsque le pipeline de réception qui inclut le Désassembleur EDI reçoit un message contenant plusieurs échanges, le Désassembleur analyse chaque échange depuis son en-tête jusqu'à son code de fin.</span><span class="sxs-lookup"><span data-stu-id="29111-108">When the receive pipeline that includes the EDI Disassembler receives a message with multiple interchange, the Disassembler will parse each interchange from the interchange header to the interchange trailer.</span></span> <span data-ttu-id="29111-109">Ce traitement est effectué selon les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="29111-109">This processing is done according to the following rules:</span></span>  
  
-   <span data-ttu-id="29111-110">Tous les échanges d'un même message doivent posséder le même type de codage, à savoir soit X12 soit EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="29111-110">All interchanges in the same message must be of the same encoding type, either X12 or EDIFACT.</span></span> <span data-ttu-id="29111-111">Si ce n'est pas le cas, le Désassembleur EDI traite tous les échanges disposant du même type de codage que celui du premier échange du message.</span><span class="sxs-lookup"><span data-stu-id="29111-111">If the message contains interchanges of more than one encoding type, the EDI Disassembler will process all interchanges that have the same encoding type as the first interchange in the message.</span></span> <span data-ttu-id="29111-112">Il ignore les échanges possédant un type de codage différent de celui du premier échange.</span><span class="sxs-lookup"><span data-stu-id="29111-112">The Disassembler will ignore all interchanges that are of a different encoding type from the first interchange.</span></span>  
  
-   <span data-ttu-id="29111-113">Le Désassembleur EDI ignore tout caractère situé entre le code de fin d'un échange et l'en-tête de l'échange suivant.</span><span class="sxs-lookup"><span data-stu-id="29111-113">The EDI Disassembler will ignore any character between the interchange trailer of one interchange and the interchange heading of the next interchange.</span></span>  
  
-   <span data-ttu-id="29111-114">Si vous activez l’authentification en sélectionnant le **supprimer les messages si l’authentification échoue** ou **conserver les messages si l’authentification échoue** propriété du port de réception, puis [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sera suspendre le message entier si l’un des échanges dans le message échoue.</span><span class="sxs-lookup"><span data-stu-id="29111-114">If you enable authentication by selecting either the **Drop messages if authentication fails** or the **Keep messages if authentication fails** property for the receive port, then [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the entire message if any one of the multiple interchanges in the message fails.</span></span>  
  
-   <span data-ttu-id="29111-115">Si vous activez l'authentification et si l'un des échanges du même message ne correspond à aucun accord, tous les échanges du message sont interrompus et aucun accusé de réception n'est renvoyé, même pour les échanges correspondant à un accord.</span><span class="sxs-lookup"><span data-stu-id="29111-115">If you enable authentication, and if any one interchange in the same message does not resolve to an agreement, then all interchanges in the message will be suspended, and no acknowledgments will be returned, even for those interchanges that did resolve to an agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="29111-116">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="29111-116">Prerequisites</span></span>  
 <span data-ttu-id="29111-117">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="29111-117">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-enable-the-receiving-of-multiple-interchanges-in-a-message"></a><span data-ttu-id="29111-118">Pour activer la réception de plusieurs échanges dans un message</span><span class="sxs-lookup"><span data-stu-id="29111-118">To enable the receiving of multiple interchanges in a message</span></span>  
  
1.  <span data-ttu-id="29111-119">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le **emplacements de réception** nœud, avec le bouton de l’emplacement de réception que vous souhaitez activer la réception de plusieurs échanges au sein d’un seul message, puis cliquez sur  **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="29111-119">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **Receive Locations** node, right-click the receive location that you want to enable to receive multiple interchange in a single message, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="29111-120">Cliquez sur les points de suspension en regard du pipeline de réception (à savoir soit EdiReceive soit AS2EdiReceive).</span><span class="sxs-lookup"><span data-stu-id="29111-120">Click the ellipses next to the receive pipeline (which must be either EdiReceive or AS2EdiReceive).</span></span>  
  
3.  <span data-ttu-id="29111-121">Dans le **configurer le Pipeline** boîte de dialogue, définissez la **DetectMID** propriété de pipeline **True**.</span><span class="sxs-lookup"><span data-stu-id="29111-121">In the **Configure Pipeline** dialog box, set the **DetectMID** pipeline property to **True**.</span></span>  
  
4.  <span data-ttu-id="29111-122">Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="29111-122">Click **OK**, then click **OK** again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29111-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29111-123">See Also</span></span>  
 [<span data-ttu-id="29111-124">Configuration des Ports pour une Solution EDI</span><span class="sxs-lookup"><span data-stu-id="29111-124">Configuring Ports for an EDI Solution</span></span>](../core/configuring-ports-for-an-edi-solution.md)