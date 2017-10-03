---
title: "Configuration des messages du récepteur (NRR) de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce30737a-341b-45be-81a0-a7336219185e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 942a9c62e69f9f39bf445f0b3028a4e6707f48d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-receiver-message-tracking-nrr"></a><span data-ttu-id="df684-102">Configuration du Suivi des messages du récepteur (NRR)</span><span class="sxs-lookup"><span data-stu-id="df684-102">Configuring Receiver Message Tracking (NRR)</span></span>
<span data-ttu-id="df684-103">Dans le cadre des paramètres de cette page, vous pouvez spécifier si les messages entrants et leurs accusés de réception (MDN) sont stockés dans la base de données de non-répudiation.</span><span class="sxs-lookup"><span data-stu-id="df684-103">As part of the settings on this page, you can specify whether the inbound messages and their acknowledgements (MDNs) are stored in the non-repudiation database.</span></span> <span data-ttu-id="df684-104">Pour plus d’informations, consultez [traitement AS2 dans BizTalk Server](../core/as2-processing-in-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="df684-104">For more information, see [AS2 Processing in BizTalk Server](../core/as2-processing-in-biztalk-server.md).</span></span>  
  
 <span data-ttu-id="df684-105">Pour stocker les messages dans la base de données de non-répudiation, les tiers doivent activer NRR (non-répudiation de réception) dans le cadre des propriétés de l'accord AS2.</span><span class="sxs-lookup"><span data-stu-id="df684-105">To store messages in the non-repudiation database, the parties must enable NRR (Non-repudiation of receipt) as part of the AS2 agreement properties.</span></span> <span data-ttu-id="df684-106">NRR garantit que le tiers expéditeur a vérifié l'accusé de réception signé du destinataire du message.</span><span class="sxs-lookup"><span data-stu-id="df684-106">NRR ensures that the sender party has verified the signed receipt from the message recipient.</span></span> <span data-ttu-id="df684-107">De manière conceptuelle, un NRR est une preuve indéniable pour l'expéditeur du message que le message a atteint sa destination sans altération.</span><span class="sxs-lookup"><span data-stu-id="df684-107">Conceptually, an NRR is an undeniable proof for the message sender that the message reached the destination unaltered.</span></span> <span data-ttu-id="df684-108">Le NRR peut être uniquement établit lorsque le message original et l'accusé de réception sont signés de manière digitale.</span><span class="sxs-lookup"><span data-stu-id="df684-108">NRR can be established only when the original message and the receipt are digitally signed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="df684-109">Aucuns propriétés ne sont désactivées sur **tiers A -> tiers B** onglet d’accord unidirectionnel si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher pour le tiers A. Toutefois, toutes les propriétés sont désactivées sur la même page dans le **tiers B -> tiers A** onglet si vous avez sélectionné la case à cocher lors de la création du tiers A.</span><span class="sxs-lookup"><span data-stu-id="df684-109">No properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="df684-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="df684-110">Prerequisites</span></span>  
 <span data-ttu-id="df684-111">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="df684-111">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-message-tracking-for-inbound-as2-messages-and-outbound-mdn"></a><span data-ttu-id="df684-112">Configuration des options de suivi des messages pour les messages AS2 entrants et MDN sortants.</span><span class="sxs-lookup"><span data-stu-id="df684-112">To configure message tracking for inbound AS2 messages and outbound MDN</span></span>  
  
1.  <span data-ttu-id="df684-113">Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md).</span><span class="sxs-lookup"><span data-stu-id="df684-113">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="df684-114">Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="df684-114">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="df684-115">Sous l’onglet accord unidirectionnel, sous **paramètres d’hôte Local** , cliquez sur **le suivi des messages du récepteur (NRR)**.</span><span class="sxs-lookup"><span data-stu-id="df684-115">On a one-way agreement tab, under **Local Host Settings** section, click **Receiver Message Tracking (NRR)**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df684-116">Pour garantir la non-répudiation de la réception, vous devez établir l'authentification et l'intégrité du message.</span><span class="sxs-lookup"><span data-stu-id="df684-116">To guarantee non-repudiation of receipt, you must establish the authentication and integrity of the message.</span></span> <span data-ttu-id="df684-117">La méthode recommandée pour cela consiste à utiliser une signature numérique sur le message.</span><span class="sxs-lookup"><span data-stu-id="df684-117">The recommended way of doing so is by using a digital signature on the message.</span></span> <span data-ttu-id="df684-118">Par conséquent, si vous sélectionnez une des propriétés pour stocker des messages dans la base de données de non-répudiation, vous devez signer le message en sélectionnant le **Message doit être signé** propriété sur le **Validation** page.</span><span class="sxs-lookup"><span data-stu-id="df684-118">As a result, if you select any of the properties to store messages in the non-repudiation database, you should sign the message by selecting the **Message should be signed** property on the **Validation** page.</span></span>  
  
3.  <span data-ttu-id="df684-119">Sélectionnez **NRR activé pour les messages AS2 encodés entrants** pour stocker les messages AS2 encodés sortants dans la base de données de non-répudiation.</span><span class="sxs-lookup"><span data-stu-id="df684-119">Select **NRR enabled for inbound encoded AS2 messages** to store outbound encoded AS2 messages in the non-repudiation database.</span></span>  
  
4.  <span data-ttu-id="df684-120">Sélectionnez **NRR activé pour les messages AS2 décodés entrants** pour stocker les messages AS2 décodés sortants dans la base de données de non-répudiation.</span><span class="sxs-lookup"><span data-stu-id="df684-120">Select **NRR enabled for inbound decoded AS2 messages** to store outbound decoded AS2 messages in the non-repudiation database.</span></span>  
  
5.  <span data-ttu-id="df684-121">Sélectionnez **NRR activé pour les MDN sortants** pour stocker les MDN entrants dans la base de données de non-répudiation.</span><span class="sxs-lookup"><span data-stu-id="df684-121">Select **NRR enabled for outbound MDN** to store inbound MDN in the non-repudiation database.</span></span>  
  
6.  <span data-ttu-id="df684-122">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="df684-122">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df684-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df684-123">See Also</span></span>  
 [<span data-ttu-id="df684-124">Configuration des paramètres de l’hôte Local (AS2)</span><span class="sxs-lookup"><span data-stu-id="df684-124">Configuring Local Host Settings (AS2)</span></span>](../core/configuring-local-host-settings-as2.md)