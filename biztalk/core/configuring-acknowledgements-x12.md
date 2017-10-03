---
title: "Configuration des accusés de réception (X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eec2dbff-5d04-4a38-bad0-33d040b6dd12
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: edec872f4055bb2c06772d361f18345d4a4be2d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-acknowledgements-x12"></a><span data-ttu-id="326a2-102">Configuration des accusés de réception (X12)</span><span class="sxs-lookup"><span data-stu-id="326a2-102">Configuring Acknowledgements (X12)</span></span>
<span data-ttu-id="326a2-103">Dans l'accord de partenariat, vous pouvez spécifier comment [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère des accusés de réception en réponse aux échanges X12 reçus du tiers, ainsi que le type d'accusé de réception à renvoyer à un tiers.</span><span class="sxs-lookup"><span data-stu-id="326a2-103">In the partner agreement, you can specify how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates acknowledgments in response to X12-encoded interchanges received from the party and what type of acknowledgment to return to a party.</span></span> <span data-ttu-id="326a2-104">Vous pouvez également spécifier si l'accusé de réception doit être traité par lot et si des boucles AK2 sont générées pour les documents informatisés acceptés.</span><span class="sxs-lookup"><span data-stu-id="326a2-104">You can also specify whether to batch an acknowledgement and whether AK2 loops are generated for accepted transaction sets.</span></span> <span data-ttu-id="326a2-105">Cette section fournit des instructions sur ces opérations.</span><span class="sxs-lookup"><span data-stu-id="326a2-105">This section provides instructions on how to do so.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="326a2-106">Les propriétés de l'accusé de réception décrites dans cette rubrique s'appliquent également aux accusés de réception HIPAA.</span><span class="sxs-lookup"><span data-stu-id="326a2-106">The acknowledgement properties described here apply also for HIPAA acknowledgements.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="326a2-107">Les propriétés suivantes sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.</span><span class="sxs-lookup"><span data-stu-id="326a2-107">The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  -   <span data-ttu-id="326a2-108">**Boucle AK2 pour les documents informatisés acceptés (si elle est désactivée, boucle sera générée que si AK501 n’est pas égal à A)**.</span><span class="sxs-lookup"><span data-stu-id="326a2-108">**Include AK2 loop for accepted transaction sets (if unchecked, loop will be generated only if AK501 is not equal to A)**.</span></span>  
>   
>  <span data-ttu-id="326a2-109">Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers.</span><span class="sxs-lookup"><span data-stu-id="326a2-109">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="326a2-110">Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="326a2-110">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="326a2-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="326a2-111">Prerequisites</span></span>  
 <span data-ttu-id="326a2-112">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="326a2-112">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-x12-ack-properties"></a><span data-ttu-id="326a2-113">Pour configurer les propriétés de l'accusé de réception X12</span><span class="sxs-lookup"><span data-stu-id="326a2-113">To configure X12 ACK properties</span></span>  
  
1.  <span data-ttu-id="326a2-114">Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md).</span><span class="sxs-lookup"><span data-stu-id="326a2-114">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="326a2-115">Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="326a2-115">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="326a2-116">Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange**, cliquez sur **accusés de réception**.</span><span class="sxs-lookup"><span data-stu-id="326a2-116">On a one-way agreement tab, under **Interchange Settings**, click **Acknowledgements**.</span></span>  
  
3.  <span data-ttu-id="326a2-117">Sélectionnez **TA1 attendu** pour renvoyer un accusé de réception technique (TA1) à l’expéditeur des échanges.</span><span class="sxs-lookup"><span data-stu-id="326a2-117">Select **TA1 Expected** to return a technical (TA1) acknowledgment to the interchange sender.</span></span> <span data-ttu-id="326a2-118">Si sélectionné, sélectionnez **ne pas traiter par lot TA1** pour envoyer chaque accusé de réception technique séparément ou laissez la case à cocher désactivée pour traiter par lot des accusés de réception techniques.</span><span class="sxs-lookup"><span data-stu-id="326a2-118">If selected, select **Do not batch TA1** to send each technical acknowledgment separately, or leave the check box cleared to batch the technical acknowledgments.</span></span>  
  
4.  <span data-ttu-id="326a2-119">Sélectionnez **997 attendu** pour renvoyer un accusé de réception fonctionnel (997) à l’expéditeur des échanges.</span><span class="sxs-lookup"><span data-stu-id="326a2-119">Select **997 Expected** to return a functional (997) acknowledgment to the interchange sender.</span></span> <span data-ttu-id="326a2-120">Si sélectionné, sélectionnez **ne pas traiter par lot 997** pour envoyer chaque accusé de réception fonctionnel séparément ou laissez la case à cocher désactivée pour traiter par lot des accusés de réception fonctionnels.</span><span class="sxs-lookup"><span data-stu-id="326a2-120">If selected, select **Do not batch 997** to send each functional acknowledgment separately, or leave the check box cleared to batch the functional acknowledgments.</span></span>  
  
5.  <span data-ttu-id="326a2-121">Pour activer la création de boucles AK2 dans les accusés de 997 réception pour les documents informatisés acceptés, sélectionnez **boucle AK2 pour les documents informatisés acceptés (si elle est désactivée, boucle sera générée que si AK501 n’est pas égal à A)**.</span><span class="sxs-lookup"><span data-stu-id="326a2-121">To enable generation of AK2 loops in 997 acknowledgments for accepted transaction sets, select **Include AK2 loop for accepted transaction sets (if unchecked, loop will be generated only if AK501 is not equal to A)**.</span></span> <span data-ttu-id="326a2-122">Pour plus d’informations sur les boucles AK2, consultez [X12 accusé de réception 997](../core/x12-997-acknowledgment.md).</span><span class="sxs-lookup"><span data-stu-id="326a2-122">For more information about AK2 loops, see [X12 997 Acknowledgment](../core/x12-997-acknowledgment.md).</span></span>  
  
6.  <span data-ttu-id="326a2-123">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="326a2-123">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="326a2-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="326a2-124">See Also</span></span>  
 [<span data-ttu-id="326a2-125">Configuration des paramètres d’échange (X12)</span><span class="sxs-lookup"><span data-stu-id="326a2-125">Configuring Interchange Settings (X12)</span></span>](../core/configuring-interchange-settings-x12.md)