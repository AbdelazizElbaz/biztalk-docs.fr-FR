---
title: "Configuration des propriétés de l’enveloppe de secours (EDIFACT-informatisés paramètres) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b56a5a93-35ac-4293-b00e-28dcd89dfa2a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c93f9aae6d67e5dc56d383626e36d1db412be9d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-envelope-properties-edifact-transaction-set-settings"></a><span data-ttu-id="4833d-102">Configuration des propriétés d'enveloppe de secours (EDIFACT pour les paramètres des documents informatisés)</span><span class="sxs-lookup"><span data-stu-id="4833d-102">Configuring Fallback Envelope Properties (EDIFACT-Transaction Set Settings)</span></span>
<span data-ttu-id="4833d-103">Dans le **enveloppes** page de la **paramètres des documents informatisés** section, vous définissez la façon dont BizTalk Server génère les segments UNG pour un échange EDIFACT envoyé au tiers.</span><span class="sxs-lookup"><span data-stu-id="4833d-103">In the **Envelopes** page of the **Transaction Set Settings** section, you define how BizTalk Server generates the UNG segments for an EDIFACT-encoded interchange that it sends to the party.</span></span>  
  
 <span data-ttu-id="4833d-104">Le segment UNG est l'en-tête qui identifie et indique un groupe fonctionnel d'un échange EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="4833d-104">The UNG segment is the header that identifies and specifies a functional group of an EDIFACT-encoded interchange.</span></span> <span data-ttu-id="4833d-105">Il contient la date et l'heure de préparation du groupe fonctionnel, ainsi que le type et la version du document inclus dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="4833d-105">It contains information about the date and time that the functional group was prepared, together with the type and version of the document in the functional group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4833d-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4833d-106">Prerequisites</span></span>  
 <span data-ttu-id="4833d-107">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4833d-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-define-the-ung-segments"></a><span data-ttu-id="4833d-108">Pour définir les segments UNG</span><span class="sxs-lookup"><span data-stu-id="4833d-108">To define the UNG segments</span></span>  
  
1.  <span data-ttu-id="4833d-109">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **paramètres de secours EDIFACT**.</span><span class="sxs-lookup"><span data-stu-id="4833d-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="4833d-110">Dans le **paramètres de secours EDIFACT** boîte de dialogue le **accords EDIFACT** sous l’onglet sous la **paramètres des documents informatisés** , cliquez sur **enveloppes** .</span><span class="sxs-lookup"><span data-stu-id="4833d-110">In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Transaction Set Settings** section, click **Envelopes**.</span></span>  
  
3.  <span data-ttu-id="4833d-111">Pour **ID de groupe fonctionnel (UNG1)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de six caractères.</span><span class="sxs-lookup"><span data-stu-id="4833d-111">For **Functional group ID (UNG1)**, enter an alphanumeric value with a minimum of one character and a maximum of six characters.</span></span> <span data-ttu-id="4833d-112">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4833d-112">This is a required field.</span></span>  
  
4.  <span data-ttu-id="4833d-113">Entrez des valeurs pour identifier les **expéditeur de l’Application (UNG2)**.</span><span class="sxs-lookup"><span data-stu-id="4833d-113">Enter values to identify **Application sender (UNG2)**.</span></span>  
  
    -   <span data-ttu-id="4833d-114">Pour **d’Identification (UNG2.1)**, entrez une valeur alphanumérique comportant un caractère au minimum et 35 caractères au maximum.</span><span class="sxs-lookup"><span data-stu-id="4833d-114">For **Identification (UNG2.1)**, enter an alphanumeric value with a minimum of one character and a maximum of 35 characters.</span></span> <span data-ttu-id="4833d-115">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4833d-115">This is a required field.</span></span>  
  
    -   <span data-ttu-id="4833d-116">Pour **qualificateur de Code (UNG2.2)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de quatre caractères.</span><span class="sxs-lookup"><span data-stu-id="4833d-116">For **Code qualifier (UNG2.2)**, enter an alphanumeric value with a minimum of one character and a maximum of four characters.</span></span> <span data-ttu-id="4833d-117">Il s’agit d’un champ facultatif.</span><span class="sxs-lookup"><span data-stu-id="4833d-117">This is an optional field.</span></span>  
  
5.  <span data-ttu-id="4833d-118">Entrez des valeurs pour identifier les **destinataire de l’Application (UNG3)**.</span><span class="sxs-lookup"><span data-stu-id="4833d-118">Enter values to identify **Application recipient (UNG3)**.</span></span>  
  
    -   <span data-ttu-id="4833d-119">Pour **d’Identification (UNG3.1)**, entrez une valeur alphanumérique comportant un caractère au minimum et 35 caractères au maximum.</span><span class="sxs-lookup"><span data-stu-id="4833d-119">For **Identification (UNG3.1)**, enter an alphanumeric value with a minimum of one character and a maximum of 35 characters.</span></span> <span data-ttu-id="4833d-120">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4833d-120">This is a required field.</span></span>  
  
    -   <span data-ttu-id="4833d-121">Pour **qualificateur de Code (UNG3.2)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de quatre caractères.</span><span class="sxs-lookup"><span data-stu-id="4833d-121">For **Code qualifier (UNG3.2)**, enter an alphanumeric value with a minimum of one character and a maximum of four characters.</span></span> <span data-ttu-id="4833d-122">Il s’agit d’un champ facultatif.</span><span class="sxs-lookup"><span data-stu-id="4833d-122">This is an optional field.</span></span>  
  
6.  <span data-ttu-id="4833d-123">Pour **agence de contrôle (UNG6)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de deux caractères.</span><span class="sxs-lookup"><span data-stu-id="4833d-123">For **Controlling agency (UNG6)**, enter an alphanumeric value with a minimum of one character and a maximum of two characters.</span></span> <span data-ttu-id="4833d-124">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4833d-124">This is a required field.</span></span>  
  
7.  <span data-ttu-id="4833d-125">Entrez des valeurs pour identifier les **version du Message (UNG7)**.</span><span class="sxs-lookup"><span data-stu-id="4833d-125">Enter values to identify **Message version (UNG7)**.</span></span>  
  
    -   <span data-ttu-id="4833d-126">Pour **Version (UNG7.1)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de trois caractères.</span><span class="sxs-lookup"><span data-stu-id="4833d-126">For **Version (UNG7.1)**, enter an alphanumeric value with a minimum of one character and a maximum of three characters.</span></span> <span data-ttu-id="4833d-127">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4833d-127">This is a required field.</span></span>  
  
    -   <span data-ttu-id="4833d-128">Pour **version finale (UNG7.2)**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de trois caractères.</span><span class="sxs-lookup"><span data-stu-id="4833d-128">For **Release (UNG7.2)**, enter an alphanumeric value with a minimum of one character and a maximum of three characters.</span></span> <span data-ttu-id="4833d-129">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4833d-129">This is a required field.</span></span>  
  
    -   <span data-ttu-id="4833d-130">Pour **d’Association assigné (UNG7.3) de code**, entrez une valeur alphanumérique contenant au minimum 1 caractère et un maximum de 6 caractères.</span><span class="sxs-lookup"><span data-stu-id="4833d-130">For **Association assigned code (UNG7.3)**, enter an alphanumeric value with a minimum of 1 character and a maximum of 6 characters.</span></span> <span data-ttu-id="4833d-131">Il s’agit d’un champ facultatif.</span><span class="sxs-lookup"><span data-stu-id="4833d-131">This is an optional field.</span></span>  
  
8.  <span data-ttu-id="4833d-132">Pour **passe d’Application (UNG8)**, entrez une valeur alphanumérique comportant un caractère au minimum et maximum 14 caractères.</span><span class="sxs-lookup"><span data-stu-id="4833d-132">For **Application password (UNG8)**, enter an alphanumeric value with a minimum of one character and a maximum of 14 characters.</span></span> <span data-ttu-id="4833d-133">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4833d-133">This is a required field.</span></span>  
  
9. <span data-ttu-id="4833d-134">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4833d-134">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4833d-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4833d-135">See Also</span></span>  
 [<span data-ttu-id="4833d-136">Configuration des propriétés d’accord de secours EDIFACT Transaction définie les paramètres</span><span class="sxs-lookup"><span data-stu-id="4833d-136">Configuring EDIFACT Fallback Agreement Properties for Transaction Set Settings</span></span>](../core/configuring-edifact-fallback-agreement-properties-for-transaction-set-settings.md)