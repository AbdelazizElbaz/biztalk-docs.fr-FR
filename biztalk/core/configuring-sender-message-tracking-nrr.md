---
title: "Configuration des messages de l’expéditeur (NRR) de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6ca2709-ac4b-48c0-82f8-8a43971a86cb
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1785a5502bc1adb9cc8b9aa7f85b6a4473d21c5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-sender-message-tracking-nrr"></a><span data-ttu-id="293b6-102">Configuration du Suivi des messages de l'expéditeur (NRR)</span><span class="sxs-lookup"><span data-stu-id="293b6-102">Configuring Sender Message Tracking (NRR)</span></span>
<span data-ttu-id="293b6-103">Dans le cadre des paramètres de cette page, vous pouvez spécifier si les messages sortants et leurs accusés de réception (MDN) sont stockés dans la base de données de non-répudiation.</span><span class="sxs-lookup"><span data-stu-id="293b6-103">As part of the settings on this page, you can specify whether the outbound messages and their acknowledgements (MDNs) are stored in the non-repudiation database.</span></span> <span data-ttu-id="293b6-104">Pour plus d’informations, consultez [traitement AS2 dans BizTalk Server](../core/as2-processing-in-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="293b6-104">For more information, see [AS2 Processing in BizTalk Server](../core/as2-processing-in-biztalk-server.md).</span></span>  
  
 <span data-ttu-id="293b6-105">Pour stocker les messages dans la base de données de non-répudiation, les tiers doivent activer NRR (non-répudiation de réception) dans le cadre des propriétés de l'accord AS2.</span><span class="sxs-lookup"><span data-stu-id="293b6-105">To store messages in the non-repudiation database, the parties must enable NRR (Non-repudiation of receipt) as part of the AS2 agreement properties.</span></span> <span data-ttu-id="293b6-106">NRR garantit que le tiers expéditeur a vérifié l'accusé de réception signé du destinataire du message.</span><span class="sxs-lookup"><span data-stu-id="293b6-106">NRR ensures that the sender party has verified the signed receipt from the message recipient.</span></span> <span data-ttu-id="293b6-107">De manière conceptuelle, un NRR est une preuve indéniable pour l'expéditeur du message que le message a atteint sa destination sans altération.</span><span class="sxs-lookup"><span data-stu-id="293b6-107">Conceptually, an NRR is an undeniable proof for the message sender that the message reached the destination unaltered.</span></span> <span data-ttu-id="293b6-108">Le NRR peut être uniquement établit lorsque le message original et l'accusé de réception sont signés de manière digitale.</span><span class="sxs-lookup"><span data-stu-id="293b6-108">NRR can be established only when the original message and the receipt are digitally signed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="293b6-109">Toutes les propriétés sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.</span><span class="sxs-lookup"><span data-stu-id="293b6-109">All the properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  <span data-ttu-id="293b6-110">Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers.</span><span class="sxs-lookup"><span data-stu-id="293b6-110">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="293b6-111">Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="293b6-111">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="293b6-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="293b6-112">Prerequisites</span></span>  
 <span data-ttu-id="293b6-113">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="293b6-113">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-message-tracking-for-outbound-as2-messages-and-inbound-mdn"></a><span data-ttu-id="293b6-114">Configuration des options de suivi des messages pour les messages AS2 sortants et les MDN entrants.</span><span class="sxs-lookup"><span data-stu-id="293b6-114">To configure message tracking for outbound AS2 messages and inbound MDN</span></span>  
  
1.  <span data-ttu-id="293b6-115">Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md).</span><span class="sxs-lookup"><span data-stu-id="293b6-115">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="293b6-116">Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="293b6-116">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="293b6-117">Sous l’onglet accord unidirectionnel, sous **paramètres d’hôte Local** , cliquez sur **de suivi des messages de l’expéditeur (NRR)**.</span><span class="sxs-lookup"><span data-stu-id="293b6-117">On a one-way agreement tab, under **Local Host Settings** section, click **Sender Message Tracking (NRR)**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="293b6-118">Pour garantir la non-répudiation de la réception, vous devez établir l'authentification et l'intégrité du message.</span><span class="sxs-lookup"><span data-stu-id="293b6-118">To guarantee non-repudiation of receipt, you must establish the authentication and integrity of the message.</span></span> <span data-ttu-id="293b6-119">La méthode recommandée pour cela consiste à utiliser une signature numérique sur le message.</span><span class="sxs-lookup"><span data-stu-id="293b6-119">The recommended way of doing so is by using a digital signature on the message.</span></span> <span data-ttu-id="293b6-120">Par conséquent, si vous sélectionnez une des propriétés pour stocker des messages dans la base de données de non-répudiation, vous devez signer le message en sélectionnant le **Message doit être signé** propriété sur le **Validation** page.</span><span class="sxs-lookup"><span data-stu-id="293b6-120">As a result, if you select any of the properties to store messages in the non-repudiation database, you should sign the message by selecting the **Message should be signed** property on the **Validation** page.</span></span>  
  
3.  <span data-ttu-id="293b6-121">Sélectionnez **NRR activé pour les messages AS2 encodés sortants** pour stocker les messages AS2 encodés sortants dans la base de données de non-répudiation.</span><span class="sxs-lookup"><span data-stu-id="293b6-121">Select **NRR enabled for outbound encoded AS2 messages** to store outbound encoded AS2 messages in the non-repudiation database.</span></span>  
  
4.  <span data-ttu-id="293b6-122">Sélectionnez **NRR activé pour les messages AS2 décodés sortants** pour stocker les messages AS2 décodés sortants dans la base de données de non-répudiation.</span><span class="sxs-lookup"><span data-stu-id="293b6-122">Select **NRR enabled for outbound decoded AS2 messages** to store outbound decoded AS2 messages in the non-repudiation database.</span></span>  
  
5.  <span data-ttu-id="293b6-123">Sélectionnez **NRR activé pour les MDN entrants** pour stocker les MDN entrants dans la base de données de non-répudiation.</span><span class="sxs-lookup"><span data-stu-id="293b6-123">Select **NRR enabled for inbound MDN** to store inbound MDN in the non-repudiation database.</span></span>  
  
6.  <span data-ttu-id="293b6-124">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="293b6-124">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="293b6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="293b6-125">See Also</span></span>  
 [<span data-ttu-id="293b6-126">Configuration des paramètres de l’hôte Local (AS2)</span><span class="sxs-lookup"><span data-stu-id="293b6-126">Configuring Local Host Settings (AS2)</span></span>](../core/configuring-local-host-settings-as2.md)