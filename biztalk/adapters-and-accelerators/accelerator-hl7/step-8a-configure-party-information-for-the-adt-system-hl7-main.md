---
title: "Étape 8 : configurer les informations de tiers pour le System_hl7_main ADT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 693fda8b-9a99-4a6e-89b7-294f84676350
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9285b926edb5ca4f1dccf18ed2d5f76b3af14ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8a-configure-party-information-for-the-adt-systemhl7main"></a><span data-ttu-id="49ce7-102">Étape 8 : configurer les informations de tiers pour le System_hl7_main ADT</span><span class="sxs-lookup"><span data-stu-id="49ce7-102">Step 8A: Configure Party Information for the ADT System_hl7_main</span></span>
<span data-ttu-id="49ce7-103">Dans cette étape, vous configurez les informations de tiers pour le système ADT.</span><span class="sxs-lookup"><span data-stu-id="49ce7-103">In this step, you configure the party information for the ADT System.</span></span>  
  
### <a name="to-configure-the-adt-system-party-information"></a><span data-ttu-id="49ce7-104">Pour configurer les informations de tiers ADT système</span><span class="sxs-lookup"><span data-stu-id="49ce7-104">To configure the ADT System party information</span></span>  
  
1.  <span data-ttu-id="49ce7-105">Dans la Console Administration de BizTalk, développez **Administration de BizTalk Server**, puis développez **groupe BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-105">In the BizTalk Administration Console, expand **BizTalk Server Administration**, and then expand **BizTalk Group**.</span></span> <span data-ttu-id="49ce7-106">Avec le bouton droit **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-106">Right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="49ce7-107">Dans la boîte de dialogue Propriétés du tiers dans le **nom** , tapez **ADT**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-107">In the Party Properties dialog box, in the **Name** field, type **ADT**.</span></span> <span data-ttu-id="49ce7-108">(La valeur que vous tapez dans cette zone doit correspondre à l’instance de message HL7 d’origine, QRY^Q01.txt MSH3).</span><span class="sxs-lookup"><span data-stu-id="49ce7-108">(The value you type in this box should match the original HL7 message instance, QRY^Q01.txt MSH3.)</span></span>  
  
3.  <span data-ttu-id="49ce7-109">Dans l’arborescence de la Console, cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-109">In the Console Tree, click **Send Ports**.</span></span>  
  
4.  <span data-ttu-id="49ce7-110">Dans le **Port d’envoi** volet, pour **nom** dans la première ligne, sélectionnez **ADT_Send**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-110">In the **Send Port** pane, for **Name** in the first row, select **ADT_Send**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="49ce7-111">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-111">Click **Start**, point to **Programs**, point to **Microsoft  BizTalk \<version> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
6.  <span data-ttu-id="49ce7-112">Dans l’Explorateur de Configuration BTAHL7, cliquez sur le **accusé de réception** onglet. Pour **Type d’accusé de réception**, sélectionnez **EnhancedMode**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-112">In BTAHL7 Configuration Explorer, click the **Acknowledgment** tab. For **Acknowledgment Type**, select **EnhancedMode**.</span></span>  
  
7.  <span data-ttu-id="49ce7-113">Dans les propriétés de l’accusé de réception dans le volet Inboiund Message, pour **MSH15 - accepter le Type d’accusé de réception**, sélectionnez **AL**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-113">In the Acknowledgment Properties in Inboiund Message pane, for **MSH15 - Accept Acknowledgment Type**, select **AL**.</span></span>  
  
8.  <span data-ttu-id="49ce7-114">Dans le volet des propriétés de l’accusé de réception pour **MSH16 - Type d’accusé de réception Application**, sélectionnez **Because**.</span><span class="sxs-lookup"><span data-stu-id="49ce7-114">In the Acknowledgment Properties pane, for **MSH16 - Application Acknowledgment Type**, select **NE**.</span></span>  
  
9. <span data-ttu-id="49ce7-115">Cliquez sur **enregistrer**, puis fermez l’Explorateur de Configuration de BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="49ce7-115">Click **Save**, and then close BTAHL7 Configuration Explorer.</span></span>  
  
 <span data-ttu-id="49ce7-116">Passez à [étape 8 : configurer les informations de tiers pour le système HI](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-hi-system.md).</span><span class="sxs-lookup"><span data-stu-id="49ce7-116">Proceed to [Step 8B: Configure Party Information for the HI System](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-hi-system.md).</span></span>