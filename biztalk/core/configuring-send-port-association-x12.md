---
title: "Configuration de l’Association de Port d’envoi (X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 496beb0a-fabf-416e-bc3c-d8537097b50e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d81eee157c84677470e542c5d4ee5f9bf2cb5df5
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-send-port-association-x12"></a><span data-ttu-id="5fcb8-102">Configuration de l'association de port d'envoi (X12)</span><span class="sxs-lookup"><span data-stu-id="5fcb8-102">Configuring Send Port Association (X12)</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5fcb8-103"> utilise l'association de ports d'envoi pour résoudre un accord pour un échange EDI sortant.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-103"> uses send port association to resolve an agreement for an outgoing EDI interchange.</span></span> <span data-ttu-id="5fcb8-104">Pour ce faire, le port d'envoi abonné au message est mappé au port d'envoi associé à un accord.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-104">An EDI interchange is resolved to an agreement by matching the send port that subscribed to the message with the send port associated with an agreement.</span></span> <span data-ttu-id="5fcb8-105">Cette rubrique fournit des instructions sur l'association de ports d'envoi à un accord.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-105">This topic provides instructions on how to associate send ports to an agreement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fcb8-106">Si le même port d'envoi est associé à plusieurs accords, BizTalk Server génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-106">If the same send port is associated with multiple agreements, BizTalk Server will generate an error.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5fcb8-107">Dans BizTalk Server, l’association de ports d’envoi est effectuée uniquement au niveau de l’accord.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-107">In BizTalk Server, the send port association is done only at the agreement level.</span></span> <span data-ttu-id="5fcb8-108">Dans BizTalk Server 2009, les ports d'envoi étaient associés au niveau du tiers.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-108">However, in BizTalk Server 2009, the send ports were associated at the party level.</span></span> <span data-ttu-id="5fcb8-109">Pour la compatibilité descendante, un **Ports d’envoi** page est également disponible dans le cadre des propriétés du tiers (consultez [configuration des propriétés de tiers générales](../core/configuring-general-party-properties.md)).</span><span class="sxs-lookup"><span data-stu-id="5fcb8-109">For backward compatibility, a **Send Ports** page is also available as part of the party properties (see [Configuring General Party Properties](../core/configuring-general-party-properties.md)).</span></span> <span data-ttu-id="5fcb8-110">Chaque fois que vous associez un port d'envoi à un accord, le paramètre de port d'envoi est propagé au paramètre du tiers et l'association de ports d'envoi est visible dans cette page.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-110">Whenever you associate a send port with an agreement, the send port setting is also propagated to the party setting and you can see the send port association in this page as well.</span></span> <span data-ttu-id="5fcb8-111">L'inverse n'est toutefois pas vrai.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-111">However, the reverse is not true.</span></span> <span data-ttu-id="5fcb8-112">Vous ne pouvez pas associer un port d'envoi à un tiers, puis rendre ce port d'envoi automatiquement disponible dans le cadre des paramètres de l'accord.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-112">You cannot associate a send port with a party and then have that send port be automatically available as part of the agreement settings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fcb8-113">Les paramètres décrits dans cette rubrique s'appliquent également aux échanges HIPAA.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-113">The settings described here also apply to HIPAA interchanges.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5fcb8-114">La grille d’association de port envoi est désactivée sur cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez l’accord.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-114">The send port association grid is disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  <span data-ttu-id="5fcb8-115">La grille est désactivée uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-115">The grid is disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="5fcb8-116">Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la grille est désactivée sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-116">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the grid is disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5fcb8-117">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="5fcb8-117">Prerequisites</span></span>  
 <span data-ttu-id="5fcb8-118">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5fcb8-118">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-associate-send-ports-with-an-agreement"></a><span data-ttu-id="5fcb8-119">Pour associer des ports d'envoi à un accord</span><span class="sxs-lookup"><span data-stu-id="5fcb8-119">To associate send ports with an agreement</span></span>  
  
1.  <span data-ttu-id="5fcb8-120">Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md).</span><span class="sxs-lookup"><span data-stu-id="5fcb8-120">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="5fcb8-121">Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-121">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="5fcb8-122">Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-122">On a one-way agreement tab, under **Interchange Settings** section, click **Send Ports**.</span></span>  
  
3.  <span data-ttu-id="5fcb8-123">Cliquez sur la cellule vide sous la **nom** colonne et dans la liste déroulante, sélectionnez le port d’envoi à associer à l’accord.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-123">Click the empty cell under the **Name** column, and from the drop-down list, select the send port to associate with the agreement.</span></span> <span data-ttu-id="5fcb8-124">Le **URI** colonne affiche l’adresse de port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-124">The **URI** column displays the send port address.</span></span>  
  
4.  <span data-ttu-id="5fcb8-125">Pour supprimer une association de port d’envoi, sélectionnez la ligne pour un port d’envoi, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-125">To remove a send port association, select the row for a send port and click **Remove**.</span></span>  
  
5.  <span data-ttu-id="5fcb8-126">Pour afficher les propriétés d’un port d’envoi, sélectionnez la ligne pour un port d’envoi, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-126">To see the properties for a send port, select the row for a send port and click **Properties**.</span></span>  
  
6.  <span data-ttu-id="5fcb8-127">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="5fcb8-127">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fcb8-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fcb8-128">See Also</span></span>  
 [<span data-ttu-id="5fcb8-129">Configuration des paramètres des échanges (X12)</span><span class="sxs-lookup"><span data-stu-id="5fcb8-129">Configuring Interchange Settings (X12)</span></span>](../core/configuring-interchange-settings-x12.md)