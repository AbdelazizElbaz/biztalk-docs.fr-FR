---
title: "Configuration des propriétés de l’enveloppe de secours (paramètres X12-Transaction) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a951f70-07d5-4a58-b1ea-e7117a45c545
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7aa7898d1e1a83da879400a89d5cd089ef2d4069
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-envelope-properties-x12-transaction-set-settings"></a><span data-ttu-id="97801-102">Configuration des propriétés d'enveloppe de secours (X12 pour les paramètres des documents informatisés)</span><span class="sxs-lookup"><span data-stu-id="97801-102">Configuring Fallback Envelope Properties (X12-Transaction Set Settings)</span></span>
<span data-ttu-id="97801-103">Dans le **enveloppes** page de la **paramètres des documents informatisés** section, vous définissez la façon dont BizTalk Server génère les segments GS pour un échange codé X12 qu’elle envoie au tiers.</span><span class="sxs-lookup"><span data-stu-id="97801-103">In the **Envelopes** page of the **Transaction Set Settings** section, you define how BizTalk Server generates the GS segments for an X12-encoded interchange that it sends to the party.</span></span> <span data-ttu-id="97801-104">Un segment GS identifie et spécifie un groupe fonctionnel pour un échange X12.</span><span class="sxs-lookup"><span data-stu-id="97801-104">A GS segment identifies and specifies a functional group for an X12-encoded interchange.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97801-105">Cette rubrique s'applique également aux paramètres liés à HIPAA.</span><span class="sxs-lookup"><span data-stu-id="97801-105">This topic applies also to HIPAA-related settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="97801-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="97801-106">Prerequisites</span></span>  
 <span data-ttu-id="97801-107">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97801-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-define-the-gs-segments"></a><span data-ttu-id="97801-108">Pour définir les segments GS</span><span class="sxs-lookup"><span data-stu-id="97801-108">To define the GS segments</span></span>  
  
1.  <span data-ttu-id="97801-109">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours**.</span><span class="sxs-lookup"><span data-stu-id="97801-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="97801-110">Dans le **X12 paramètres de secours** boîte de dialogue le **X12 page accords** sous l’onglet sous la **paramètres des documents informatisés** , cliquez sur **enveloppes**.</span><span class="sxs-lookup"><span data-stu-id="97801-110">In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Transaction Set Settings** section, click **Envelopes**.</span></span>  
  
3.  <span data-ttu-id="97801-111">Pour **code fonctionnel (GS01)**, sélectionnez une valeur dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="97801-111">For **Functional code (GS01)**, select a value from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="97801-112">Pour **Application émettrice (GS02)**, entrez une valeur alphanumérique contenant au minimum de 2 et un maximum de 15.</span><span class="sxs-lookup"><span data-stu-id="97801-112">For **Application sender (GS02)**, enter an alphanumeric value with a minimum of 2 and a maximum of 15.</span></span> <span data-ttu-id="97801-113">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="97801-113">This is a required field.</span></span>  
  
5.  <span data-ttu-id="97801-114">Pour **Application réceptrice (GS03)**, entrez une valeur alphanumérique contenant au minimum de 2 et un maximum de 15.</span><span class="sxs-lookup"><span data-stu-id="97801-114">For **Application receiver (GS03)**, enter an alphanumeric value with a minimum of 2 and a maximum of 15.</span></span> <span data-ttu-id="97801-115">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="97801-115">This is a required field.</span></span>  
  
6.  <span data-ttu-id="97801-116">Pour **format de Date (GS04)**, sélectionnez SSAAMMJJ ou aammjj dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="97801-116">For **Date format (GS04)**, select CCYYMMDD or YYMMDD from the drop-down list.</span></span> <span data-ttu-id="97801-117">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="97801-117">This is a required field.</span></span>  
  
7.  <span data-ttu-id="97801-118">Pour **format d’heure (GS05)**, sélectionnez HHMM, HHMMSS ou Hhmmssjj dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="97801-118">For **Time format (GS05)**, select HHMM, HHMMSS, or HHMMSSdd from the drop-down list.</span></span> <span data-ttu-id="97801-119">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="97801-119">This is a required field.</span></span>  
  
8.  <span data-ttu-id="97801-120">Pour **entité responsable (GS07)**, sélectionnez la valeur dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="97801-120">For **Responsible agency (GS07)**, select the value from the drop-down list.</span></span>  
  
9. <span data-ttu-id="97801-121">Pour **identificateur de Document (GS08)**, entrez une valeur alphanumérique comportant un minimum de 1 et un maximum de 12.</span><span class="sxs-lookup"><span data-stu-id="97801-121">For **Document identifier (GS08)**, enter an alphanumeric value with a minimum of 1 and a maximum of 12.</span></span> <span data-ttu-id="97801-122">Il s’agit d’un champ facultatif.</span><span class="sxs-lookup"><span data-stu-id="97801-122">This is an optional field.</span></span>  
  
10. <span data-ttu-id="97801-123">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="97801-123">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97801-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97801-124">See Also</span></span>  
 [<span data-ttu-id="97801-125">Configuration X12 définir les propriétés de l’accord de secours pour la Transaction paramètres</span><span class="sxs-lookup"><span data-stu-id="97801-125">Configuring X12 Fallback Agreement Properties for Transaction Set Settings</span></span>](../core/configuring-x12-fallback-agreement-properties-for-transaction-set-settings.md)