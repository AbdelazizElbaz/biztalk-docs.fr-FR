---
title: Configuration des identificateurs de secours (EDIFACT) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2ce56c1-44f1-42dc-94e8-36e5ba664f53
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81ddf25726d7413727fef1f4f41d99916c18c21d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-identifiers-edifact"></a><span data-ttu-id="502b9-102">Configuration des identificateurs de secours (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="502b9-102">Configuring Fallback Identifiers (EDIFACT)</span></span>
<span data-ttu-id="502b9-103">Dans l'accord de secours, vous devez définir le mot de passe du destinataire pour vérifier que l'échange n'est pas reçu par des destinataires non autorisés.</span><span class="sxs-lookup"><span data-stu-id="502b9-103">In the fallback agreement, you must set the recipient reference password, in order to verify that the interchange is not being received by unauthorized recipients.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="502b9-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="502b9-104">Prerequisites</span></span>  
 <span data-ttu-id="502b9-105">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="502b9-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-set-the-sender-recipient-recipient-password"></a><span data-ttu-id="502b9-106">Pour définir l’expéditeur, le destinataire, le mot de passe destinataire</span><span class="sxs-lookup"><span data-stu-id="502b9-106">To set the sender, recipient, recipient password</span></span>  
  
1.  <span data-ttu-id="502b9-107">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **paramètres de secours EDIFACT**.</span><span class="sxs-lookup"><span data-stu-id="502b9-107">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="502b9-108">Dans le **paramètres de secours EDIFACT** boîte de dialogue le **accords EDIFACT** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **identificateurs** .</span><span class="sxs-lookup"><span data-stu-id="502b9-108">In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Interchange Settings** section, click **Identifiers**.</span></span>  
  
3.  <span data-ttu-id="502b9-109">Dans le **expéditeur (UNB2)** section, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="502b9-109">In the **Sender (UNB2)** section, do the following:</span></span>  
  
    1.  <span data-ttu-id="502b9-110">Pour **d’Identification (UNB2.1)**, entrez une valeur alphanumérique contenant au minimum 1 et 35 caractères au maximum.</span><span class="sxs-lookup"><span data-stu-id="502b9-110">For **Identification (UNB2.1)**, enter an alphanumeric value with a minimum of one and a maximum of 35.</span></span> <span data-ttu-id="502b9-111">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="502b9-111">This is a required field.</span></span>  
  
    2.  <span data-ttu-id="502b9-112">Pour **qualificateur de Code (UNB2.2)**, sélectionnez une valeur dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="502b9-112">For **Code qualifier (UNB2.2)**, select a value from the drop-down list.</span></span> <span data-ttu-id="502b9-113">Il s’agit d’un champ facultatif.</span><span class="sxs-lookup"><span data-stu-id="502b9-113">This is an optional field.</span></span>  
  
    3.  <span data-ttu-id="502b9-114">Pour **(UNB2.3) adresse de routage inverse**, entrez une valeur alphanumérique comportant un caractère au minimum et maximum 14 caractères.</span><span class="sxs-lookup"><span data-stu-id="502b9-114">For **Reverse routing address (UNB2.3)**, enter an alphanumeric value with a minimum of one character and a maximum of 14 characters.</span></span> <span data-ttu-id="502b9-115">Il s’agit d’un champ facultatif.</span><span class="sxs-lookup"><span data-stu-id="502b9-115">This is an optional field.</span></span>  
  
    4.  <span data-ttu-id="502b9-116">Pour **identifiant de l’Application (UNB7)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de six caractères.</span><span class="sxs-lookup"><span data-stu-id="502b9-116">For **Application reference ID (UNB7)**, enter an alphanumeric value with a minimum of one character and a maximum of six characters.</span></span> <span data-ttu-id="502b9-117">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="502b9-117">This is a required field.</span></span>  
  
4.  <span data-ttu-id="502b9-118">Dans le **destinataire (UNB3)** section, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="502b9-118">In the **Recipient (UNB3)** section, do the following:</span></span>  
  
    1.  <span data-ttu-id="502b9-119">Pour **d’Identification (UNB3.1)**, entrez une valeur alphanumérique contenant au minimum 1 et 35 caractères au maximum.</span><span class="sxs-lookup"><span data-stu-id="502b9-119">For **Identification (UNB3.1)**, enter an alphanumeric value with a minimum of one and a maximum of 35.</span></span> <span data-ttu-id="502b9-120">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="502b9-120">This is a required field.</span></span>  
  
    2.  <span data-ttu-id="502b9-121">Pour **qualificateur de Code (UNB3.2)**, sélectionnez une valeur dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="502b9-121">For **Code qualifier (UNB3.2)**, select a value from the drop-down list.</span></span> <span data-ttu-id="502b9-122">Il s’agit d’un champ facultatif.</span><span class="sxs-lookup"><span data-stu-id="502b9-122">This is an optional field.</span></span>  
  
    3.  <span data-ttu-id="502b9-123">Pour **(UNB3.3) adresse de routage inverse**, entrez une valeur alphanumérique comportant un caractère au minimum et maximum 14 caractères.</span><span class="sxs-lookup"><span data-stu-id="502b9-123">For **Reverse routing address (UNB3.3)**, enter an alphanumeric value with a minimum of one character and a maximum of 14 characters.</span></span> <span data-ttu-id="502b9-124">Il s’agit d’un champ facultatif.</span><span class="sxs-lookup"><span data-stu-id="502b9-124">This is an optional field.</span></span>  
  
    4.  <span data-ttu-id="502b9-125">Si nécessaire, dans le **mot de passe du destinataire (UNB6)** section, entrez des valeurs pour le mot de passe du destinataire.</span><span class="sxs-lookup"><span data-stu-id="502b9-125">If required, in the **Recipient reference password (UNB6)** section, enter values for the recipient reference password.</span></span> <span data-ttu-id="502b9-126">Pour **valeur (UNB6.1)**, entrez une valeur alphanumérique contenant au moins un et un maximum de 14.</span><span class="sxs-lookup"><span data-stu-id="502b9-126">For **Value (UNB6.1)**, enter an alphanumeric value with a minimum of one and a maximum of 14.</span></span> <span data-ttu-id="502b9-127">Pour **qualificateur (UNB6.2)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de deux caractères.</span><span class="sxs-lookup"><span data-stu-id="502b9-127">For **Qualifier (UNB6.2)**, enter an alphanumeric value with a minimum of one character and a maximum of two characters.</span></span> <span data-ttu-id="502b9-128">Ces champs sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="502b9-128">These are optional fields.</span></span> <span data-ttu-id="502b9-129">Si ces valeurs ne correspondent pas aux champs UNB6.1 et UNB6.2 dans un échange reçu, BizTalk Server interrompt l'échange.</span><span class="sxs-lookup"><span data-stu-id="502b9-129">If these values do not match the UNB6.1 and UNB6.2 fields in a received interchange, BizTalk Server will suspend the interchange.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="502b9-130">La combinaison de **UNB6.1** et **UNB6.2** doit être unique.</span><span class="sxs-lookup"><span data-stu-id="502b9-130">The combination of **UNB6.1** and **UNB6.2** must be unique.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="502b9-131">Si vous entrez des valeurs pour les champs UNB6.1 et UNB6.2, que vous appliquez les modifications et que vous videz à nouveau le champ UNB6.1, la valeur du champ UNB6.2 sera également supprimée et le champ désactivé.</span><span class="sxs-lookup"><span data-stu-id="502b9-131">If you enter values for both UNB6.1 and UNB6.2, apply the changes and then blank out UNB6.1, the value in UNB6.2 will also be deleted and the field will be disabled.</span></span>  
  
5.  <span data-ttu-id="502b9-132">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="502b9-132">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="502b9-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="502b9-133">See Also</span></span>  
 [<span data-ttu-id="502b9-134">Configuration des propriétés de l’accord de secours EDIFACT pour le traitement des échanges</span><span class="sxs-lookup"><span data-stu-id="502b9-134">Configuring EDIFACT Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)