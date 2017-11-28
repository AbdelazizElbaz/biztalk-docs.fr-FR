---
title: "Paramètre des CIDX chem échange de messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CIDX, configuring message exchange
ms.assetid: 90468459-cef7-436b-8c0b-3a7455a091c3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c4606dfc4b912d884a997bb65acb26cb4352448
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-up-cidx-estandards-message-exchange"></a><span data-ttu-id="5d555-102">Paramètre des CIDX chem échange de messages</span><span class="sxs-lookup"><span data-stu-id="5d555-102">Setting Up CIDX eStandards Message Exchange</span></span>
<span data-ttu-id="5d555-103">Cette rubrique décrit comment configurer l’échange de messages chem chimiques données Exchange (CHEMICAL).</span><span class="sxs-lookup"><span data-stu-id="5d555-103">This topic describes how to set up Chemical Data Exchange (CIDX) eStandards message exchange.</span></span> <span data-ttu-id="5d555-104">CIDX nécessite que vous définissez les trois propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="5d555-104">CIDX requires that you set the following three properties:</span></span>  
  
-   <span data-ttu-id="5d555-105">`Standard`propriété dans les paramètres de configuration de processus **CIDX**</span><span class="sxs-lookup"><span data-stu-id="5d555-105">`Standard` property in the process configuration settings to **CIDX**</span></span>  
  
-   <span data-ttu-id="5d555-106">`Is Single Action`propriété dans les paramètres de configuration de processus`True`</span><span class="sxs-lookup"><span data-stu-id="5d555-106">`Is Single Action` property in the process configuration settings to `True`</span></span>  
  
-   <span data-ttu-id="5d555-107">`0A1 agreement`propriété dans l’accord de partenariat commercial à **aucune 0 a 1**</span><span class="sxs-lookup"><span data-stu-id="5d555-107">`0A1 agreement` property in the trading partner agreement to **No 0A1**</span></span>  
  
 <span data-ttu-id="5d555-108">Pour plus d’informations sur les différences entre CIDX et RosettaNet, consultez [prise en charge CIDX](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md).</span><span class="sxs-lookup"><span data-stu-id="5d555-108">For information about the differences between CIDX and RosettaNet, see [CIDX Support](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md).</span></span>  
  
### <a name="to-set-up-cidx-message-exchange"></a><span data-ttu-id="5d555-109">Pour configurer l’échange de messages CIDX</span><span class="sxs-lookup"><span data-stu-id="5d555-109">To set up CIDX message exchange</span></span>  
  
1.  <span data-ttu-id="5d555-110">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.</span><span class="sxs-lookup"><span data-stu-id="5d555-110">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span></span>  
  
2.  <span data-ttu-id="5d555-111">Dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5d555-111">In the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].</span></span>  
  
3.  <span data-ttu-id="5d555-112">Cliquez avec le bouton droit sur **Paramètres de configuration du processus**, pointez sur **Nouveau**, puis cliquez sur **Configuration du processus**.</span><span class="sxs-lookup"><span data-stu-id="5d555-112">Right-click **Process Configuration Settings**, point to **New**, and then click **Process Configuration**.</span></span>  
  
4.  <span data-ttu-id="5d555-113">Dans la boîte de dialogue nouvelles propriétés de Configuration de processus sur le **général** onglet, pour le **Standard** propriété, sélectionnez **CIDX**.</span><span class="sxs-lookup"><span data-stu-id="5d555-113">In the New Process Configuration Properties dialog box, on the **General** tab, for the **Standard** property, select **CIDX**.</span></span>  
  
5.  <span data-ttu-id="5d555-114">Sur le **activité** onglet, pour le **est la seule Action** propriété, sélectionnez **True**.</span><span class="sxs-lookup"><span data-stu-id="5d555-114">On the **Activity** tab, for the **Is Single Action** property, select **True**.</span></span>  
  
6.  <span data-ttu-id="5d555-115">Entrez les autres paramètres de configuration de processus en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="5d555-115">Enter other process configuration settings as needed.</span></span> <span data-ttu-id="5d555-116">Pour plus d’informations sur ces paramètres, consultez le tableau dans [comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="5d555-116">For information about these settings, see the table in [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).</span></span>  
  
7.  <span data-ttu-id="5d555-117">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5d555-117">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="5d555-118">Avec le bouton droit **accords**, pointez sur **nouveau**, puis cliquez sur **accord**.</span><span class="sxs-lookup"><span data-stu-id="5d555-118">Right-click **Agreements**, point to **New**, and then click **Agreement**.</span></span>  
  
9. <span data-ttu-id="5d555-119">Sur le **général**, **Ports**, **protocole**, et **propriétés personnalisées** onglets, entrez les valeurs pour les différents paramètres.</span><span class="sxs-lookup"><span data-stu-id="5d555-119">On the **General**, **Ports**, **Protocol**, and **Custom Properties** tabs, enter the values for the various settings.</span></span> <span data-ttu-id="5d555-120">Pour plus d’informations sur ces paramètres, consultez le tableau dans [création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).</span><span class="sxs-lookup"><span data-stu-id="5d555-120">For information about these settings, see the table in [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).</span></span>  
  
10. <span data-ttu-id="5d555-121">Dans la boîte de dialogue Propriétés de l’accord sur le **général** onglet, pour le **0 a 1 accord** propriété, sélectionnez **aucun 0 a 1**.</span><span class="sxs-lookup"><span data-stu-id="5d555-121">In the New Agreement Properties dialog box, on the **General** tab, for the **0A1 agreement** property, select **No 0A1**.</span></span>  
  
11. <span data-ttu-id="5d555-122">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5d555-122">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d555-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d555-123">See Also</span></span>  
 <span data-ttu-id="5d555-124">[Comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="5d555-124">[How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md) </span></span>  
 <span data-ttu-id="5d555-125">[Création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md) </span><span class="sxs-lookup"><span data-stu-id="5d555-125">[Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md) </span></span>  
 <span data-ttu-id="5d555-126">[Création ou modification d’une organisation d’origine](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md) </span><span class="sxs-lookup"><span data-stu-id="5d555-126">[Creating or Editing a Home Organization](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md) </span></span>  
 [<span data-ttu-id="5d555-127">Création ou modification d’un partenaire</span><span class="sxs-lookup"><span data-stu-id="5d555-127">Creating or Editing a Partner</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)