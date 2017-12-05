---
title: Configuration des identificateurs (AS2) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29f12696-8257-4664-8e61-292678e98b6b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1f4c8ddde24c32f93d003f778b9359d70e87170
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-identifiers-as2"></a><span data-ttu-id="07b87-102">Configuration des identificateurs (AS2)</span><span class="sxs-lookup"><span data-stu-id="07b87-102">Configuring Identifiers (AS2)</span></span>
<span data-ttu-id="07b87-103">Dans l'accord partenaire, vous devez spécifier les tiers expéditeur et récepteur.</span><span class="sxs-lookup"><span data-stu-id="07b87-103">In the partner agreement, you must specify the sender and receiver parties.</span></span> <span data-ttu-id="07b87-104">Ces valeurs sont également utilisées pour la résolution d'accord pour les messages entrants et sortants.</span><span class="sxs-lookup"><span data-stu-id="07b87-104">These values are also used for agreement resolution for the inbound or outbound messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="07b87-105">Les propriétés suivantes sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.</span><span class="sxs-lookup"><span data-stu-id="07b87-105">The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  -   <span data-ttu-id="07b87-106">**AS2To** sous **supplémentaires de résolution d’accord** section.</span><span class="sxs-lookup"><span data-stu-id="07b87-106">**AS2To** under **Additional Agreement Resolvers** section.</span></span>  
>   
>  <span data-ttu-id="07b87-107">Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers.</span><span class="sxs-lookup"><span data-stu-id="07b87-107">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="07b87-108">Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="07b87-108">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="07b87-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="07b87-109">Prerequisites</span></span>  
 <span data-ttu-id="07b87-110">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07b87-110">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-the-identifier-properties"></a><span data-ttu-id="07b87-111">Pour configurer les propriétés d'identificateur</span><span class="sxs-lookup"><span data-stu-id="07b87-111">To configure the identifier properties</span></span>  
  
1.  <span data-ttu-id="07b87-112">Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md).</span><span class="sxs-lookup"><span data-stu-id="07b87-112">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="07b87-113">Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="07b87-113">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="07b87-114">Sous l’onglet accord unidirectionnel, cliquez sur **identificateurs**.</span><span class="sxs-lookup"><span data-stu-id="07b87-114">On a one-way agreement tab, click **Identifiers**.</span></span>  
  
3.  <span data-ttu-id="07b87-115">Dans le **AS2-de** page, spécifiez le nom du partenaire commercial qui envoie le message AS2.</span><span class="sxs-lookup"><span data-stu-id="07b87-115">In the **AS2-From** page, specify the name of the trading partner sending the AS2 message.</span></span>  
  
4.  <span data-ttu-id="07b87-116">Dans le **AS2-pour** page, spécifiez le nom du partenaire commercial qui reçoit le message AS2.</span><span class="sxs-lookup"><span data-stu-id="07b87-116">In the **AS2-To** page, specify the name of the trading partner receiving the AS2 message.</span></span>  
  
5.  <span data-ttu-id="07b87-117">Sous le **supplémentaires de résolution d’accord** section, pour le **AS2To** propriété, entrez un alias supplémentaire pour le partenaire qui reçoit le message.</span><span class="sxs-lookup"><span data-stu-id="07b87-117">Under the **Additional Agreement Resolvers** section, for the **AS2To** property, enter an additional alias for the partner that receives the message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="07b87-118">Cette propriété est facultative.</span><span class="sxs-lookup"><span data-stu-id="07b87-118">This property is optional.</span></span> <span data-ttu-id="07b87-119">Elle est disponible à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="07b87-119">This property is available for backward compatibility.</span></span> <span data-ttu-id="07b87-120">Lorsqu’une définition de tiers est migrée à partir de BizTalk Server 2006 R2 ou BizTalk Server 2009 à BizTalk Server, le nom du tiers dans les versions précédentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est inclus en tant que valeur de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="07b87-120">When a party definition is migrated from BizTalk Server 2006 R2 or BizTalk Server 2009 to BizTalk Server, the name of the party in the previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is included as a value for this property.</span></span> <span data-ttu-id="07b87-121">Cela garantit que la résolution de l’accord se produit et les applications existantes et les définitions de partenaire peuvent être utilisées avec BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="07b87-121">This ensures that the agreement resolution happens and the existing applications and partner definitions can be used with BizTalk Server.</span></span>  
  
6.  <span data-ttu-id="07b87-122">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="07b87-122">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07b87-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07b87-123">See Also</span></span>  
 [<span data-ttu-id="07b87-124">Configuration des propriétés de l’accord AS2</span><span class="sxs-lookup"><span data-stu-id="07b87-124">Configuring AS2 Agreement Properties</span></span>](../core/configuring-as2-agreement-properties.md)