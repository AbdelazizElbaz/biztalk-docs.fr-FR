---
title: "Étape 4 : Configurer un tiers et un profil d’entreprise pour votre commercial Partner1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db50d0f6-e838-4e92-8548-a63a2c445d55
caps.latest.revision: "40"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7b8be8215b790e74a3c1a8ecd8324d62454c2ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-configure-a-party-and-business-profile-for-your-trading-partner"></a><span data-ttu-id="e4ef9-102">Étape 4 : Configurer un tiers et un profil d’entreprise pour votre partenaire commercial</span><span class="sxs-lookup"><span data-stu-id="e4ef9-102">Step 4: Configure a Party and Business Profile for Your Trading Partner</span></span>
<span data-ttu-id="e4ef9-103">![L’étape 4 de 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-4of9.gif "Step_4of9")</span><span class="sxs-lookup"><span data-stu-id="e4ef9-103">![Step 4 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-4of9.gif "Step_4of9")</span></span>  
  
 <span data-ttu-id="e4ef9-104">Au cours de cette étape, vous allez configurer un tiers et un profil d'entreprise de manière à ce que votre partenaire commercial Fabrikam envoie un message 850 à votre organisation et reçoive un accusé de réception 997 en retour.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-104">In this step, you configure a party and business profile for your trading partner Fabrikam to send an 850 message to your organization and receive a 997 acknowledgment message in return.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e4ef9-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e4ef9-105">Prerequisites</span></span>  
 <span data-ttu-id="e4ef9-106">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e4ef9-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-a-party-and-business-profile-for-your-trading-partner"></a><span data-ttu-id="e4ef9-107">Pour configurer un tiers et un profil d'entreprise pour votre partenaire commercial</span><span class="sxs-lookup"><span data-stu-id="e4ef9-107">To configure a party and business profile for your trading partner</span></span>  
  
1.  <span data-ttu-id="e4ef9-108">Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration en cliquant sur **Démarrer**, en pointant sur **tous les programmes**, en pointant sur **Microsoft BizTalk Server**, puis en cliquant sur  **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-108">Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console by clicking **Start**, pointing to **All Programs**, pointing to **Microsoft BizTalk Server**, and then clicking **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e4ef9-109">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis développez **groupe BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then expand **BizTalk Group**.</span></span> <span data-ttu-id="e4ef9-110">Avec le bouton droit **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-110">Right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
3.  <span data-ttu-id="e4ef9-111">Dans le **propriétés de tiers** boîte de dialogue, entrez **Fabrikam** dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-111">In the **Party Properties** dialog box, enter **Fabrikam** in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="e4ef9-112">Désactivez le **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-112">Clear the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box.</span></span> <span data-ttu-id="e4ef9-113">En désactivant la case à cocher, vous spécifiez que le tiers (dans ce cas, **Fabrikam**) n’héberge pas BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-113">By clearing the check box you specify that the party (in this case, **Fabrikam**) does not host BizTalk Server.</span></span>  
  
5.  <span data-ttu-id="e4ef9-114">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-114">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="e4ef9-115">Cliquez sur le nom du tiers, pointez sur **nouveau**, puis cliquez sur **profil d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-115">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  
  
7.  <span data-ttu-id="e4ef9-116">Dans le **propriétés de profil** boîte de dialogue le **général** , entrez `Fabrikam_Profile` dans les **nom** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-116">In the **Profile Properties** dialog box, on the **General** page, enter `Fabrikam_Profile` in the **Name** text box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e4ef9-117">Lorsque vous créez un tiers, un profil nommé *Nom_tiers*_Profile est automatiquement créé.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-117">When you create a party, a profile named *PartyName*_Profile is automatically created.</span></span> <span data-ttu-id="e4ef9-118">Vous pouvez utiliser ce profil plutôt que d'en créer un.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-118">You can use this profile instead of creating a new one.</span></span> <span data-ttu-id="e4ef9-119">Pour renommer un profil, cliquez sur le profil et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-119">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="e4ef9-120">Dans le **général** , spécifiez un nom pour le profil.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-120">In the **General** page, specify a name for the profile.</span></span>  
  
8.  <span data-ttu-id="e4ef9-121">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e4ef9-121">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e4ef9-122">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e4ef9-122">Next Steps</span></span>  
 <span data-ttu-id="e4ef9-123">Vous configurez l’emplacement de réception (**fromTHEM_4010_850**) pour recevoir le message 850 de Fabrikam, comme décrit dans [étape 5 : configurer un Port de réception et l’emplacement de réception](../core/step-5-configure-a-receive-port-and-receive-location.md).</span><span class="sxs-lookup"><span data-stu-id="e4ef9-123">You configure the receive location (**fromTHEM_4010_850**) to receive the 850 message from Fabrikam, as described in [Step 5: Configure a Receive Port and Receive Location](../core/step-5-configure-a-receive-port-and-receive-location.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ef9-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4ef9-124">See Also</span></span>  
 [<span data-ttu-id="e4ef9-125">Configuration des propriétés EDI</span><span class="sxs-lookup"><span data-stu-id="e4ef9-125">Configuring EDI Properties</span></span>](../core/configuring-edi-properties.md)