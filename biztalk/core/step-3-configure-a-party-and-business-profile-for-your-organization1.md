---
title: "Étape 3 : Configurer un tiers et un profil d’entreprise pour votre Organisation1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 849e5146-a82a-41f2-bb96-089841b2444d
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1eff579959840f760449422ebbe7af35792e7cc8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-configure-a-party-and-business-profile-for-your-organization"></a><span data-ttu-id="f3b2c-102">Étape 3 : Configurer un tiers et un profil d’entreprise pour votre organisation</span><span class="sxs-lookup"><span data-stu-id="f3b2c-102">Step 3: Configure a Party and Business Profile for Your Organization</span></span>
<span data-ttu-id="f3b2c-103">![Étape 3 de 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-3of9.gif "Step_3of9")</span><span class="sxs-lookup"><span data-stu-id="f3b2c-103">![Step 3 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-3of9.gif "Step_3of9")</span></span>  
  
 <span data-ttu-id="f3b2c-104">Au cours de cette étape, vous allez configurer un tiers et un profil d'entreprise de manière à ce que votre organisation reçoive un message 850 de votre partenaire commercial et renvoie un accusé de réception 997.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-104">In this step, you configure a party and a business profile for your organization to receive an 850 message from your trading partner and return a 997 acknowledgment message.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f3b2c-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f3b2c-105">Prerequisites</span></span>  
 <span data-ttu-id="f3b2c-106">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f3b2c-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-a-party-and-business-profile-for-your-organization"></a><span data-ttu-id="f3b2c-107">Pour configurer un tiers et un profil d'entreprise pour votre organisation</span><span class="sxs-lookup"><span data-stu-id="f3b2c-107">To configure a party and business profile for your organization</span></span>  
  
1.  <span data-ttu-id="f3b2c-108">Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration en cliquant sur **Démarrer**, en pointant sur **tous les programmes**, en pointant sur **Microsoft BizTalk Server**, puis en cliquant sur  **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-108">Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console by clicking **Start**, pointing to **All Programs**, pointing to **Microsoft BizTalk Server**, and then clicking **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="f3b2c-109">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis développez **groupe BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then expand **BizTalk Group**.</span></span> <span data-ttu-id="f3b2c-110">Avec le bouton droit **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-110">Right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
3.  <span data-ttu-id="f3b2c-111">Dans le **propriétés de tiers** boîte de dialogue, entrez **OrderSystem** dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-111">In the **Party Properties** dialog box, enter **OrderSystem** in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="f3b2c-112">Sélectionnez le **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-112">Select the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box.</span></span> <span data-ttu-id="f3b2c-113">En activant la case à cocher, vous spécifiez que le tiers (dans ce cas, **OrderSystem**) héberge également BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-113">By selecting the check box you specify that the party (in this case, **OrderSystem**) also hosts BizTalk Server.</span></span>  
  
5.  <span data-ttu-id="f3b2c-114">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-114">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="f3b2c-115">Cliquez sur le nom du tiers, pointez sur **nouveau**, puis cliquez sur **profil d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-115">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  
  
7.  <span data-ttu-id="f3b2c-116">Dans le **propriétés de profil** boîte de dialogue le **général** , entrez `OrderSystem_Profile` dans les **nom** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-116">In the **Profile Properties** dialog box, on the **General** page, enter `OrderSystem_Profile` in the **Name** text box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f3b2c-117">Lorsque vous créez un tiers, un profil nommé *Nom_tiers*_Profile est automatiquement créé.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-117">When you create a party, a profile named *PartyName*_Profile is automatically created.</span></span> <span data-ttu-id="f3b2c-118">Vous pouvez utiliser ce profil plutôt que d'en créer un.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-118">You can use this profile instead of creating a new one.</span></span> <span data-ttu-id="f3b2c-119">Pour renommer un profil, cliquez sur le profil et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-119">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="f3b2c-120">Dans le **général** , spécifiez un nom pour le profil.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-120">In the **General** page, specify a name for the profile.</span></span>  
  
8.  <span data-ttu-id="f3b2c-121">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f3b2c-121">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f3b2c-122">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f3b2c-122">Next Steps</span></span>  
 <span data-ttu-id="f3b2c-123">Vous configurez un profil de tiers et d’entreprise de votre organisation partenaire (**Fabrikam**), comme décrit dans [étape 4 : configurer un tiers et un profil d’entreprise pour votre partenaire commercial](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner1.md).</span><span class="sxs-lookup"><span data-stu-id="f3b2c-123">You configure a party and business profile for your partner organization (**Fabrikam**), as described in [Step 4: Configure a Party and Business Profile for Your Trading Partner](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner1.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b2c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3b2c-124">See Also</span></span>  
 [<span data-ttu-id="f3b2c-125">Configuration des propriétés EDI</span><span class="sxs-lookup"><span data-stu-id="f3b2c-125">Configuring EDI Properties</span></span>](../core/configuring-edi-properties.md)