---
title: "Configuration de l’Association de Port d’envoi (EDIFACT) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7faabc7-072c-408c-bbd5-f0a039be81f8
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 629bde13f8edc9074b3e6bcb4741746e3de8e1a6
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-send-port-association-edifact"></a><span data-ttu-id="ab33b-102">Configuration de l'association de port d'envoi (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="ab33b-102">Configuring Send Port Association (EDIFACT)</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ab33b-103"> utilise l'association de ports d'envoi pour résoudre un accord pour un échange EDI sortant.</span><span class="sxs-lookup"><span data-stu-id="ab33b-103"> uses send port association to resolve an agreement for an outgoing EDI interchange.</span></span> <span data-ttu-id="ab33b-104">Pour ce faire, le port d'envoi abonné au message est mappé au port d'envoi associé à un accord.</span><span class="sxs-lookup"><span data-stu-id="ab33b-104">An EDI interchange is resolved to an agreement by matching the send port that subscribed to the message with the send port associated with an agreement.</span></span> <span data-ttu-id="ab33b-105">Cette rubrique fournit des instructions sur l'association de ports d'envoi à un accord.</span><span class="sxs-lookup"><span data-stu-id="ab33b-105">This topic provides instructions on how to associate send ports to an agreement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab33b-106">Si le même port d'envoi est associé à plusieurs accords, BizTalk Server génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="ab33b-106">If the same send port is associated with multiple agreements, BizTalk Server will generate an error.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ab33b-107">Dans BizTalk Server, l’association de ports d’envoi est effectuée uniquement au niveau de l’accord.</span><span class="sxs-lookup"><span data-stu-id="ab33b-107">In BizTalk Server, the send port association is done only at the agreement level.</span></span> <span data-ttu-id="ab33b-108">Dans BizTalk Server 2009, les ports d'envoi étaient associés au niveau du tiers.</span><span class="sxs-lookup"><span data-stu-id="ab33b-108">However, in BizTalk Server 2009, the send ports were associated at the party level.</span></span> <span data-ttu-id="ab33b-109">Pour la compatibilité descendante, un **Ports d’envoi** page est également disponible dans le cadre des propriétés du tiers (consultez [configuration des propriétés de tiers générales](../core/configuring-general-party-properties.md)).</span><span class="sxs-lookup"><span data-stu-id="ab33b-109">For backward compatibility, a **Send Ports** page is also available as part of the party properties (see [Configuring General Party Properties](../core/configuring-general-party-properties.md)).</span></span> <span data-ttu-id="ab33b-110">Chaque fois que vous associez un port d'envoi à un accord, le paramètre de port d'envoi est propagé au paramètre du tiers et l'association de ports d'envoi est visible dans cette page.</span><span class="sxs-lookup"><span data-stu-id="ab33b-110">Whenever you associate a send port with an agreement, the send port setting is also propagated to the party setting and you can see the send port association in this page as well.</span></span> <span data-ttu-id="ab33b-111">L'inverse n'est toutefois pas vrai.</span><span class="sxs-lookup"><span data-stu-id="ab33b-111">However, the reverse is not true.</span></span> <span data-ttu-id="ab33b-112">Vous ne pouvez pas associer un port d'envoi à un tiers, puis rendre ce port d'envoi automatiquement disponible dans le cadre des paramètres de l'accord.</span><span class="sxs-lookup"><span data-stu-id="ab33b-112">You cannot associate a send port with a party and then have that send port be automatically available as part of the agreement settings.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ab33b-113">La grille d’association de port envoi est désactivée sur cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez l’accord.</span><span class="sxs-lookup"><span data-stu-id="ab33b-113">The send port association grid is disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  <span data-ttu-id="ab33b-114">La grille est désactivée uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers.</span><span class="sxs-lookup"><span data-stu-id="ab33b-114">The grid is disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="ab33b-115">Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la grille est désactivée sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="ab33b-115">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the grid is disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ab33b-116">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ab33b-116">Prerequisites</span></span>  
 <span data-ttu-id="ab33b-117">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab33b-117">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-associate-send-ports-with-an-agreement"></a><span data-ttu-id="ab33b-118">Pour associer des ports d'envoi à un accord</span><span class="sxs-lookup"><span data-stu-id="ab33b-118">To associate send ports with an agreement</span></span>  
  
1.  <span data-ttu-id="ab33b-119">Créer un accord le codage comme décrit dans EDIFACT, [paramètres généraux configuration (EDIFACT)](../core/configuring-general-settings-edifact.md).</span><span class="sxs-lookup"><span data-stu-id="ab33b-119">Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md).</span></span> <span data-ttu-id="ab33b-120">Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ab33b-120">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="ab33b-121">Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="ab33b-121">On a one-way agreement tab, under **Interchange Settings** section, click **Send Ports**.</span></span>  
  
3.  <span data-ttu-id="ab33b-122">Cliquez sur la cellule vide sous la **nom** colonne et dans la liste déroulante, sélectionnez le port d’envoi à associer à l’accord.</span><span class="sxs-lookup"><span data-stu-id="ab33b-122">Click the empty cell under the **Name** column, and from the drop-down list, select the send port to associate with the agreement.</span></span> <span data-ttu-id="ab33b-123">Le **URI** colonne affiche l’adresse de port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="ab33b-123">The **URI** column displays the send port address.</span></span>  
  
4.  <span data-ttu-id="ab33b-124">Pour supprimer une association de port d’envoi, sélectionnez la ligne pour un port d’envoi, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="ab33b-124">To remove a send port association, select the row for a send port and click **Remove**.</span></span>  
  
5.  <span data-ttu-id="ab33b-125">Pour afficher les propriétés d’un port d’envoi, sélectionnez la ligne pour un port d’envoi, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ab33b-125">To see the properties for a send port, select the row for a send port and click **Properties**.</span></span>  
  
6.  <span data-ttu-id="ab33b-126">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ab33b-126">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab33b-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab33b-127">See Also</span></span>  
 [<span data-ttu-id="ab33b-128">Configuration des paramètres des échanges (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="ab33b-128">Configuring Interchange Settings (EDIFACT)</span></span>](../core/configuring-interchange-settings-edifact.md)