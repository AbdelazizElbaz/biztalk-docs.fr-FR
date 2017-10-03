---
title: "Configuration d’enveloppes (paramètres d’échange EDIFACT) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 501ccc5f-e21c-4c36-9509-217d5b3ba21f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 531b559e690fae5369298a90cd372edcae79db57
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-envelopes-edifact-interchange-settings"></a><span data-ttu-id="8a1b9-102">Configuration d'enveloppes (paramètres d'échange EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="8a1b9-102">Configuring Envelopes (EDIFACT-Interchange Settings)</span></span>
<span data-ttu-id="8a1b9-103">Cette section fournit des instructions sur la manière de configurer l'enveloppe des messages EDIFACT sortants.</span><span class="sxs-lookup"><span data-stu-id="8a1b9-103">This section provides instructions on how to configure the envelope for outgoing EDIFACT messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8a1b9-104">Toutes les propriétés sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.</span><span class="sxs-lookup"><span data-stu-id="8a1b9-104">All the properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  <span data-ttu-id="8a1b9-105">Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers.</span><span class="sxs-lookup"><span data-stu-id="8a1b9-105">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="8a1b9-106">Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="8a1b9-106">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8a1b9-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8a1b9-107">Prerequisites</span></span>  
 <span data-ttu-id="8a1b9-108">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a1b9-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-the-interchange-envelope"></a><span data-ttu-id="8a1b9-109">Pour configurer l'enveloppe d'échange</span><span class="sxs-lookup"><span data-stu-id="8a1b9-109">To configure the interchange envelope</span></span>  
  
1.  <span data-ttu-id="8a1b9-110">Créer un accord le codage comme décrit dans EDIFACT, [paramètres généraux configuration (EDIFACT)](../core/configuring-general-settings-edifact.md).</span><span class="sxs-lookup"><span data-stu-id="8a1b9-110">Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md).</span></span> <span data-ttu-id="8a1b9-111">Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8a1b9-111">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="8a1b9-112">Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **enveloppes**.</span><span class="sxs-lookup"><span data-stu-id="8a1b9-112">On a one-way agreement tab, under **Interchange Settings** section, click **Envelopes**.</span></span>  
  
3.  <span data-ttu-id="8a1b9-113">Pour **code (UNB8) de la priorité de traitement**, entrez une valeur alphabétique comportant un caractère au minimum et maximum d’un seul caractère.</span><span class="sxs-lookup"><span data-stu-id="8a1b9-113">For **Processing priority code (UNB8)**, enter an alphabetical value with a minimum of one character and a maximum of one character.</span></span> <span data-ttu-id="8a1b9-114">Il s’agit d’un champ facultatif.</span><span class="sxs-lookup"><span data-stu-id="8a1b9-114">This is an optional field.</span></span>  
  
4.  <span data-ttu-id="8a1b9-115">Pour **accord de Communication (UNB10)**, entrez une valeur alphanumérique comportant un caractère au minimum et 35 caractères au maximum.</span><span class="sxs-lookup"><span data-stu-id="8a1b9-115">For **Communication agreement (UNB10)**, enter an alphanumeric value with a minimum of one character and a maximum of 35 characters.</span></span> <span data-ttu-id="8a1b9-116">Il s’agit d’un champ facultatif</span><span class="sxs-lookup"><span data-stu-id="8a1b9-116">This is an optional field</span></span>  
  
5.  <span data-ttu-id="8a1b9-117">Sélectionnez **indicateur de Test (UNB11)** pour indiquer que l’échange généré par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les données de test.</span><span class="sxs-lookup"><span data-stu-id="8a1b9-117">Select **Test indicator (UNB11)** to indicate that the interchange generated by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is test data.</span></span>  
  
6.  <span data-ttu-id="8a1b9-118">Sélectionnez **appliquer le segment UNA (options de l’échange)** pour générer un segment UNA pour l’échange à envoyer.</span><span class="sxs-lookup"><span data-stu-id="8a1b9-118">Select **Apply UNA segment (String service advice)** to generate a UNA segment for the interchange to be sent.</span></span> <span data-ttu-id="8a1b9-119">Si cette option est activée, puis **UNA6** ne peut pas être vide et **suffixe una6** ne peut pas être **aucun**.</span><span class="sxs-lookup"><span data-stu-id="8a1b9-119">If this option is checked, then **UNA6** cannot be empty and **UNA 6 Suffix** cannot be **None**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8a1b9-120">Vous spécifiez **UNA6** et **suffixe UNA6** dans les **jeu de caractères et séparateurs** comme décrit dans la page [configuration d’un jeu de caractères et séparateurs (EDIFACT)](../core/configuring-charset-and-separators-edifact.md).</span><span class="sxs-lookup"><span data-stu-id="8a1b9-120">You specify **UNA6** and **UNA6 Suffix** in the **Charset and Separators** page as described in [Configuring Charset and Separators (EDIFACT)](../core/configuring-charset-and-separators-edifact.md).</span></span>  
  
7.  <span data-ttu-id="8a1b9-121">Sélectionnez **appliquer les segments UNG (en-tête de groupe fonctionnel)** pour créer des groupes de segments dans l’en-tête de groupe fonctionnel dans les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="8a1b9-121">Select **Apply UNG segments (Functional group header)** to create grouping segments in the functional group header in outgoing messages.</span></span>  
  
8.  <span data-ttu-id="8a1b9-122">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8a1b9-122">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a1b9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a1b9-123">See Also</span></span>  
 [<span data-ttu-id="8a1b9-124">Configuration des paramètres d’échange (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="8a1b9-124">Configuring Interchange Settings (EDIFACT)</span></span>](../core/configuring-interchange-settings-edifact.md)